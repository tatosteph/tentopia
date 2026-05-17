<script setup>
import { computed, ref } from 'vue'
import logoUrl from '../556832490_17845602312577330_3850415441180532949_n.jpg'

const uploadedPhotos = import.meta.glob('../wetransfer_foto-s-website-tentopia_2026-05-17_1427/image*.jpeg', {
  eager: true,
  import: 'default',
  query: '?url'
})

const uploadedVideos = import.meta.glob('../wetransfer_foto-s-website-tentopia_2026-05-17_1427/*.mov', {
  eager: true,
  import: 'default',
  query: '?url'
})

const getPhoto = (name) => uploadedPhotos[`../wetransfer_foto-s-website-tentopia_2026-05-17_1427/${name}`]
const getVideo = (name) => uploadedVideos[`../wetransfer_foto-s-website-tentopia_2026-05-17_1427/${name}`]

const getPhotos = (start, end) =>
  Array.from({ length: end - start + 1 }, (_, index) => {
    const number = String(start + index).padStart(5, '0')
    return getPhoto(`image${number}.jpeg`)
  }).filter(Boolean)

const woodThemePhotos = getPhotos(1, 10)
const footballThemePhotos = [...getPhotos(11, 15), getPhoto('image00042.jpeg'), getPhoto('image00043.jpeg'), getPhoto('image00045.jpeg')].filter(Boolean)
const pastelThemePhotos = getPhotos(16, 25)
const gamingThemePhotos = [...getPhotos(26, 41), getPhoto('image00044.jpeg')].filter(Boolean)
const gamingThemeVideos = [
  getVideo('2762a359-5e4d-4bba-9be5-8b5b247a84f4.mov'),
  getVideo('instories_A884D396-7BA4-4B5A-9987-F728141FB658.mov')
].filter(Boolean)
const pastelThemeVideos = [getVideo('IMG_2237.mov')].filter(Boolean)

const translations = {
  fr: {
    navThemes: 'Thèmes',
    navPackages: 'Formules',
    navContact: 'Contact',
    heroEyebrow: 'Anniversaires · Pyjama parties · Fêtes privées',
    heroTitle: 'Des petites tentes décorées pour créer une fête magique.',
    heroText: 'Tentopia imagine et installe des univers thématiques pour enfants : tentes, coussins, guirlandes, accessoires et mise en scène pour un moment inoubliable.',
    heroPrimary: 'Voir les thèmes',
    heroSecondary: 'Demander un devis',
    heroCardLabel: 'Pack anniversaire',
    heroCardTitle: 'Installation clé en main',
    heroCardText: 'Décoration, montage et ambiance sur mesure.',
    themesEyebrow: 'Comme des stories Instagram',
    themesTitle: 'Choisis un thème',
    themesText: 'Clique sur un rond pour sélectionner le thème et découvrir son ambiance.',
    themeLabel: 'Thème',
    packagesEyebrow: 'Location & décoration',
    packagesTitle: 'Une expérience simple pour les parents',
    packageOneTitle: 'Choix du thème',
    packageOneText: 'Tu sélectionnes l’univers qui correspond à l’anniversaire ou à la fête.',
    packageTwoTitle: 'Installation',
    packageTwoText: 'L’équipe prépare les tentes, coussins, accessoires et décorations.',
    packageThreeTitle: 'Moment magique',
    packageThreeText: 'Les enfants profitent d’un décor chaleureux, sécurisé et photogénique.',
    contactEyebrow: 'Réserver une date',
    contactTitle: 'Prêt à créer une fête inoubliable ?',
    contactText: 'Envoie le thème souhaité, la date, la ville et le nombre d’enfants.',
    contactButton: 'Écrire à Tentopia',
    closePreview: 'Fermer l’aperçu',
    previewTheme: 'Aperçu thème',
    languageLabel: 'Langue',
    themes: {
      bois: {
        name: 'Bienvenue dans les bois',
        description: 'Une ambiance nature, chaleureuse et boisée pour une fête douce et immersive.'
      },
      football: {
        name: 'Football party',
        description: 'Un thème sportif avec ballons, lumières et ambiance stade pour les fans de foot.'
      },
      'anniversaire-pastel': {
        name: 'Anniversaire pastel',
        description: 'Une décoration douce avec ballons, cœurs et touches colorées pour un anniversaire tendre.'
      },
      gaming: {
        name: 'Gaming néon',
        description: 'Une ambiance bleue et lumineuse avec accessoires gaming, manettes et ballons colorés.'
      }
    }
  },
  nl: {
    navThemes: 'Thema’s',
    navPackages: 'Pakketten',
    navContact: 'Contact',
    heroEyebrow: 'Verjaardagen · Pyjamafeestjes · Privéfeesten',
    heroTitle: 'Versierde kindertentjes voor een magisch feest.',
    heroText: 'Tentopia bedenkt en plaatst thematische werelden voor kinderen: tentjes, kussens, lichtslingers, accessoires en styling voor een onvergetelijk moment.',
    heroPrimary: 'Bekijk de thema’s',
    heroSecondary: 'Vraag een offerte',
    heroCardLabel: 'Verjaardagspakket',
    heroCardTitle: 'Kant-en-klare installatie',
    heroCardText: 'Decoratie, opbouw en sfeer volledig op maat.',
    themesEyebrow: 'Zoals Instagram stories',
    themesTitle: 'Kies een thema',
    themesText: 'Klik op een rondje om een thema te kiezen en de sfeer te ontdekken.',
    themeLabel: 'Thema',
    packagesEyebrow: 'Verhuur & decoratie',
    packagesTitle: 'Een eenvoudige ervaring voor ouders',
    packageOneTitle: 'Thema kiezen',
    packageOneText: 'Je kiest de wereld die past bij de verjaardag of het feest.',
    packageTwoTitle: 'Installatie',
    packageTwoText: 'Het team bereidt de tentjes, kussens, accessoires en decoratie voor.',
    packageThreeTitle: 'Magisch moment',
    packageThreeText: 'De kinderen genieten van een warme, veilige en fotogenieke setting.',
    contactEyebrow: 'Datum reserveren',
    contactTitle: 'Klaar om een onvergetelijk feest te creëren?',
    contactText: 'Stuur het gewenste thema, de datum, de stad en het aantal kinderen.',
    contactButton: 'Schrijf naar Tentopia',
    closePreview: 'Voorbeeld sluiten',
    previewTheme: 'Voorbeeld thema',
    languageLabel: 'Taal',
    themes: {
      bois: {
        name: 'Welkom in het bos',
        description: 'Een natuurlijke, warme en bosrijke sfeer voor een zachte en meeslepende feestbeleving.'
      },
      football: {
        name: 'Voetbalfeest',
        description: 'Een sportief thema met ballonnen, lichtjes en stadionsfeer voor echte voetbalfans.'
      },
      'anniversaire-pastel': {
        name: 'Pastelverjaardag',
        description: 'Een zachte decoratie met ballonnen, hartjes en kleurrijke accenten voor een lieve verjaardag.'
      },
      gaming: {
        name: 'Neon gaming',
        description: 'Een blauwe, lichtgevende sfeer met gamingaccessoires, controllers en kleurrijke ballonnen.'
      }
    }
  }
}

const themes = [
  {
    id: 'bois',
    emoji: '🪵',
    color: '#9b6a43',
    cover: woodThemePhotos[0],
    photos: woodThemePhotos,
    videos: []
  },
  {
    id: 'football',
    emoji: '⚽',
    color: '#86b84c',
    cover: footballThemePhotos[0],
    photos: footballThemePhotos,
    videos: []
  },
  {
    id: 'anniversaire-pastel',
    emoji: '🎈',
    color: '#cdb6ff',
    cover: pastelThemePhotos[0],
    photos: pastelThemePhotos,
    videos: pastelThemeVideos
  },
  {
    id: 'gaming',
    emoji: '🎮',
    color: '#4f6dff',
    cover: gamingThemePhotos[0],
    photos: gamingThemePhotos,
    videos: gamingThemeVideos
  }
]

const currentLanguage = ref('fr')
const selectedThemeId = ref(themes[0].id)
const selectedMedia = ref(null)

const t = computed(() => translations[currentLanguage.value])
const localizedThemes = computed(() =>
  themes.map((theme) => ({
    ...theme,
    name: t.value.themes[theme.id].name,
    description: t.value.themes[theme.id].description
  }))
)
const selectedTheme = computed(() => localizedThemes.value.find((theme) => theme.id === selectedThemeId.value) || localizedThemes.value[0])

const openMedia = (type, src, label) => {
  selectedMedia.value = { type, src, label }
}

const closeMedia = () => {
  selectedMedia.value = null
}
</script>

<template>
  <main class="page-shell">
    <header class="hero">
      <nav class="navbar" :aria-label="currentLanguage === 'fr' ? 'Navigation principale' : 'Hoofdnavigatie'">
        <a class="brand" href="#top" :aria-label="currentLanguage === 'fr' ? 'Accueil Tentopia' : 'Startpagina Tentopia'">
          <span class="brand-logo">
            <img :src="logoUrl" alt="" />
          </span>
          <span>
            <strong>T E N T O P I A</strong>
          </span>
        </a>
        <div class="nav-links">
          <a href="#themes">{{ t.navThemes }}</a>
          <a href="#formules">{{ t.navPackages }}</a>
          <a href="#contact">{{ t.navContact }}</a>
        </div>
        <div class="language-switcher" :aria-label="t.languageLabel">
          <button type="button" :class="{ active: currentLanguage === 'fr' }" @click="currentLanguage = 'fr'">FR</button>
          <button type="button" :class="{ active: currentLanguage === 'nl' }" @click="currentLanguage = 'nl'">NL</button>
        </div>
      </nav>

      <section id="top" class="hero-content">
        <div class="hero-copy">
          <span class="eyebrow">{{ t.heroEyebrow }}</span>
          <h1>{{ t.heroTitle }}</h1>
          <p>{{ t.heroText }}</p>
          <div class="hero-actions">
            <a class="button primary" href="#themes">{{ t.heroPrimary }}</a>
            <a class="button secondary" href="#contact">{{ t.heroSecondary }}</a>
          </div>
        </div>

        <div class="hero-card" :aria-label="currentLanguage === 'fr' ? 'Aperçu d’une installation Tentopia' : 'Voorbeeld van een Tentopia-installatie'">
          <div class="tent-shape"></div>
          <div class="hero-card-content">
            <span>{{ t.heroCardLabel }}</span>
            <strong>{{ t.heroCardTitle }}</strong>
            <p>{{ t.heroCardText }}</p>
          </div>
        </div>
      </section>
    </header>

    <section id="themes" class="section themes-section">
      <div class="section-heading">
        <span class="eyebrow">{{ t.themesEyebrow }}</span>
        <h2>{{ t.themesTitle }}</h2>
        <p>{{ t.themesText }}</p>
      </div>

      <div class="story-row" :aria-label="currentLanguage === 'fr' ? 'Liste des thèmes' : 'Lijst met thema’s'">
        <button
          v-for="theme in localizedThemes"
          :key="theme.id"
          class="story-button"
          :class="{ active: selectedThemeId === theme.id }"
          type="button"
          @click="selectedThemeId = theme.id"
        >
          <span class="story-ring" :style="{ '--theme-color': theme.color }">
            <span class="story-image">
              <img :src="theme.cover" :alt="`${t.previewTheme} ${theme.name}`" />
            </span>
          </span>
          <strong>{{ theme.name }}</strong>
        </button>
      </div>

      <article class="theme-showcase">
        <div class="theme-info">
          <span class="theme-label" :style="{ color: selectedTheme.color }">{{ selectedTheme.emoji }} {{ t.themeLabel }}</span>
          <h3>{{ selectedTheme.name }}</h3>
          <p>{{ selectedTheme.description }}</p>
        </div>

        <div class="selected-theme-preview" :style="{ '--theme-color': selectedTheme.color }">
          <span>{{ selectedTheme.emoji }}</span>
        </div>
      </article>

      <div v-if="selectedTheme.photos.length || selectedTheme.videos.length" class="theme-gallery">
        <figure v-for="(photo, index) in selectedTheme.photos" :key="photo">
          <button type="button" @click="openMedia('image', photo, `${selectedTheme.name} photo ${index + 1}`)">
            <img :src="photo" :alt="`${selectedTheme.name} photo ${index + 1}`" />
          </button>
        </figure>
        <figure v-for="(video, index) in selectedTheme.videos" :key="video">
          <button type="button" @click="openMedia('video', video, `${selectedTheme.name} vidéo ${index + 1}`)">
            <video :src="video" playsinline preload="metadata" :aria-label="`${selectedTheme.name} vidéo ${index + 1}`"></video>
          </button>
        </figure>
      </div>
    </section>

    <section id="formules" class="section packages">
      <div class="section-heading">
        <span class="eyebrow">{{ t.packagesEyebrow }}</span>
        <h2>{{ t.packagesTitle }}</h2>
      </div>

      <div class="package-grid">
        <div class="package-card">
          <span>01</span>
          <h3>{{ t.packageOneTitle }}</h3>
          <p>{{ t.packageOneText }}</p>
        </div>
        <div class="package-card">
          <span>02</span>
          <h3>{{ t.packageTwoTitle }}</h3>
          <p>{{ t.packageTwoText }}</p>
        </div>
        <div class="package-card">
          <span>03</span>
          <h3>{{ t.packageThreeTitle }}</h3>
          <p>{{ t.packageThreeText }}</p>
        </div>
      </div>
    </section>

    <section id="contact" class="contact-section">
      <div>
        <span class="eyebrow">{{ t.contactEyebrow }}</span>
        <h2>{{ t.contactTitle }}</h2>
        <p>{{ t.contactText }}</p>
      </div>
      <a class="button primary" href="mailto:hello@tentopia.party">{{ t.contactButton }}</a>
    </section>

    <div v-if="selectedMedia" class="media-lightbox" role="dialog" aria-modal="true" @click.self="closeMedia">
      <button class="lightbox-close" type="button" :aria-label="t.closePreview" @click="closeMedia">×</button>
      <img v-if="selectedMedia.type === 'image'" :src="selectedMedia.src" :alt="selectedMedia.label" />
      <video v-else :src="selectedMedia.src" controls autoplay playsinline :aria-label="selectedMedia.label"></video>
    </div>
  </main>
</template>
