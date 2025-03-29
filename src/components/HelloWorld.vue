<template>
  <section class="intro">
    <h1 class="fade-in-right">
      {{ msgParts.before }}<span v-if="msgParts.emoji" class="wave-emoji">{{ msgParts.emoji }}</span>{{ msgParts.after }}
    </h1>
  </section>

  <hr />
  <h3 class="fade-in-right">⚠️ SITE IS NOT DONE!!! i will add my projects on this site </h3>

  <section class="about-me">
    <h2>About me</h2>

    <p>
      I'm a self-taught programmer and learning malware research from Russia.<br />
      I can do stuff with frameworks like: <br />
    </p>
    <div class="tech-icons">
      <i class="devicon-nextjs-plain colored" title="Next.js"></i>
      <i class="devicon-vuejs-plain colored" title="Vue.js"></i>
      <i class="devicon-vitejs-plain colored" title="Vite"></i>
      <i class="devicon-react-original colored" title="React"></i>
    </div>
  </section>

  <section class="tech-stack">
    <h3>I can do some stuff in:</h3>
    <div class="tech-icons">
      <!-- Render tech skills dynamically -->
      <i v-for="skill in techSkills" :key="skill.title" :class="skill.iconClass" :title="skill.title"></i>
    </div>
    <p>
      I enjoy exploring operating systems and retro consoles, especially Nintendo's.
      Check out my or YouTube channel for more!<br>
      Yep this site is sucks and not very epik but i made it in vue with vite <img src="/src/assets/contentface.webp" height="24" alt="">
    </p>
  </section>

  <section class="socials">
    <h3>Connect with me:</h3>
    <div class="social-links">
      <a v-for="social in socialLinks"
         :key="social.key"
         :href="social.href"
         target="_blank"
         rel="noopener noreferrer"
         :title="social.alt">
        <img :src="social.src" :class="['logo', social.key]" :alt="social.alt" />
      </a>
    </div>
  </section>

  <section class="interactive-example">
    <!-- <div class="card">
      <button type="button" @click="count++">Count is {{ count }}</button>
    </div> -->
    <p class="read-the-docs">Click on one of these logos, you will get on my social media!<br>
      © 2025, techplayz32. Estd 29th of March, in 2025. ~ v1.0.0
    </p>
  </section>

</template>

<script setup>
import { ref, computed } from 'vue';

const props = defineProps({
  msg: {
    type: String,
    required: true
  }
});

// --- Computed Property for Message Parsing ---
const waveEmoji = '👋';
const msgParts = computed(() => {
  const msg = props.msg || ''; // Ensure msg is a string
  const emojiIndex = msg.indexOf(waveEmoji);

  if (emojiIndex === -1) {
    return { before: msg, emoji: '', after: '' };
  } else {
    return {
      before: msg.substring(0, emojiIndex),
      emoji: waveEmoji,
      after: msg.substring(emojiIndex + waveEmoji.length),
    };
  }
});

// --- Data for v-for loops ---

// Helper function for asset URLs in Vite
// See: https://vitejs.dev/guide/assets.html#new-url-url-import-meta-url
const getAssetUrl = (path) => {
  // Assuming assets are in /src/assets/
  return new URL(`/src/assets/${path}`, import.meta.url).href;
};

const techSkills = ref([
  { iconClass: 'devicon-typescript-plain colored', title: 'TypeScript' },
  { iconClass: 'devicon-javascript-plain colored', title: 'JavaScript' },
  { iconClass: 'devicon-csharp-plain colored', title: 'C#' },
  { iconClass: 'devicon-cplusplus-plain colored', title: 'C++' },
  { iconClass: 'devicon-go-plain colored', title: 'Go' },
  { iconClass: 'devicon-lua-plain colored', title: 'Lua' },
  { iconClass: 'devicon-python-plain colored', title: 'Python' },
]);

const socialLinks = ref([
  { key: 'youtube', href: 'https://youtube.com/@techplayz001', src: getAssetUrl('youtube.svg'), alt: 'YouTube' },
  { key: 'discord', href: 'https://discord.gg/zzuHaFFSEc', src: getAssetUrl('discord.svg'), alt: 'Discord' },
  { key: 'twitter', href: 'https://x.com/techplayz32', src: getAssetUrl('twitter.svg'), alt: 'X (formerly Twitter)' },
  { key: 'github', href: 'https://github.com/techplayz32', src: getAssetUrl('github-mark-white.svg'), alt: 'GitHub' },
]);

</script>

<style scoped>
section {
  margin-bottom: 2rem;
}

hr {
  border: none;
  height: 1.25px;
  background-color: #555;
  margin: 2rem 0;
}

h2, h3 {
  margin-bottom: 0.8rem;
}

p {
  line-height: 1.6;
}

@keyframes fadeInRight {
  from { opacity: 0; transform: translateX(20px) }
  to { opacity: 1; transform: translateX(0); }
}

@keyframes waveHand {
  0%, 100% { transform: rotate(0deg); }
  10%, 30%, 50% { transform: rotate(10deg); }
  20%, 40% { transform: rotate(-5deg); }
}

.fade-in-right {
  animation: fadeInRight 0.7s ease-out forwards;
  opacity: 0;
}

.wave-emoji {
  display: inline-block;
  transform-origin: 70% 70%;
  animation: waveHand 1.8s ease-in-out 0.7s 1;
  cursor: default;
}

.tech-icons {
  margin-block: 1rem;
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  align-items: center;
}

.tech-icons i,
.about-me i {
  font-size: 2.2rem;
  vertical-align: middle;
  transition: transform 0.2s ease-in-out;
}
.tech-icons i:hover,
.about-me i:hover {
  transform: scale(1.15);
}

.devicon-vuejs-plain.colored { color: #4FC08D; }
.devicon-vitejs-plain.colored { color: #646CFF; }
.devicon-react-original.colored { color: #61DAFB; }
.devicon-nextjs-plain.colored { color: #000000; }

.devicon-typescript-plain.colored { color: #3178C6; }
.devicon-javascript-plain.colored { color: #F7DF1E; }
.devicon-csharp-plain.colored { color: #512BD4; }
.devicon-cplusplus-plain.colored { color: #00599C; }
.devicon-go-plain.colored { color: #00ADD8; }
.devicon-lua-plain.colored { color: #2C2D72; }
.devicon-python-plain.colored { color: #3776AB; }

@media (prefers-color-scheme: dark) {
  .devicon-nextjs-plain.colored { color: #FFFFFF; }
}

.social-links {
  display: flex;
  flex-wrap: wrap;
  gap: 0.8rem;
  align-items: center;
  margin-top: 1rem;
}

.logo {
  display: inline-block;
  width: 2.5rem;
  height: 2.5rem;
  filter: brightness(0) invert(1);
  vertical-align: middle;
  will-change: filter, transform;
  transition: filter 300ms, transform 300ms;
}

.logo:hover {
  transform: scale(1.1);
  filter: brightness(0) invert(1) drop-shadow(0 0 0.6em var(--logo-hover-glow, #646cfa));
}

.logo.twitter:hover { --logo-hover-glow: #1DA1F2; }
.logo.github:hover { --logo-hover-glow: #bdbdbd; }
.logo.youtube:hover { --logo-hover-glow: #FF0000; }
.logo.discord:hover { --logo-hover-glow: #5865F2; }


.card {
  margin-block: 1.5rem;
}
.read-the-docs {
  color: var(--color-text-secondary, #888);
  font-size: 0.9em;
}

@media (prefers-reduced-motion: reduce) {
  .fade-in-right,
  .wave-emoji,
  .tech-icons i,
  .logo {
    animation: none;
    transition: none;
    transform: none;
    opacity: 1;
  }
  .tech-icons i:hover,
  .logo:hover {
    transform: none;
  }
}

</style>