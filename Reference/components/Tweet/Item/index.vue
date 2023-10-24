<template>
  <div>
    <TweetItemHeader :tweet="props.tweet" />

    <div :class="tweetBodyWrapper">
      <p
        class="flex-shrink w-auto font-medium text-gray-800 dark:text-white"
        :class="textSize"
      >
        {{ props.tweet.text }}
      </p>

      <div
        v-for="image in tweet.mediaFiles"
        :key="image.id"
        class="flex my-3 mr-2 border-2 rounded-2xl"
        :class="twitterBorderColor"
      >
        <img :src="image.url" class="w-full rounded-2xl" />
      </div>

      <div class="mt-2" v-if="!props.hideActions">
        <TweetItemActions
          :tweet="props.tweet"
          :compact="props.compact"
          @on-comment-click="handleCommentClick"
        />
      </div>
    </div>
  </div>
</template>
<script setup>
const { twitterBorderColor } = useTailwindConfig();
</script>
