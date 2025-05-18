<template>
  <div ref="container" class="container">
    <div ref="title" class="title">
      <span class="dear">Уважаемые</span> <br>
      <span class="name">{{ name1 }}<br>и<br>{{ name2 }}</span>
      <span class="invite">
        Приглашаем вас на <br></br><span class="weeding">свадьбу</span>
      </span>
    </div>
    <div ref="box" class="box">
      <div ref="offer" class="offer">
        Приглашаем вас на свадьбу
      </div>
    </div>
    <div ref="galleryAleksey" class="gallery gallery-aleksey">
      <div class="gallery-wrap" ref="galleryPhotoImg" v-for="image in galleryAlekseyPhoto">
        <div class="gallery-photo" :style="{ backgroundImage: `url(${image.url})` }">
        </div>
        <img :style="{
          [image.positionX]: image.x,
          [image.positionY]: image.y,
          width: image.width
        }"
             :src="image.url" alt=""
             :ref="image.id"
        >
      </div>
    </div>
    <div ref="articlesBlock" class="articles">
<!--      <div class="">-->
<!--        <h2 class="text">This is some text</h2>-->
<!--        <h2 class="typing_text-heading">-->
<!--          <span class="typing_text"></span><span class="cursor">_</span>-->
<!--        </h2>-->
<!--      </div>-->
      <div ref="articlesPosts" v-for="article in articles" class="article">
        <h2>{{ article.title }}</h2>
        <p>{{ article.desc }}</p>
      </div>
    </div>
    <div ref="leadingJob" class="leading-job">
      Ведущий
    </div>
    <div ref="leadingVideo" class="leading">
      <div class="leading-wrap">
        <div ref="leadingName" class="leading-name">
          Савин<br>&nbsp;&nbsp; Александр
        </div>
        <video ref="mainVideo" muted loop playsinline webkit-playinginline id="mainVideo">
          <!-- <source v-if="!isMobile" :src="mainVideoUrls.desktop" type="video/webm"> -->
          <source poster="https://koshta.c.roky.rocks/uploads/mainposter_ba70b0b94a.png?updated_at=2022-10-19T17:58:47.272Z" src="/leading.mp4" type="video/mp4">
          <!--        <source v-if="isMobile" poster="https://koshta.c.roky.rocks/uploads/mainpostermobile_dbb55586ea.png?updated_at=2022-10-19T17:58:46.214Z" :src="require('@/assets/video/mainvideomobile.webm')" type="video/webm">-->
          <!--        <source v-if="isMobile" poster="https://koshta.c.roky.rocks/uploads/mainpostermobile_dbb55586ea.png?updated_at=2022-10-19T17:58:46.214Z" :src="mainVideoUrls ? mainVideoUrls.mobile : ''" type="video/mp4">-->

          <!-- <source v-if="isMobile" :src="mainVideoUrls.mobile" type="video/mp4"> -->
        </video>
      </div>
    </div>
    <div ref="site" class="site">
      <div class="site-wrap">
        <div ref="siteDesc" class="site-job">
<!--          Ресторан<br>"Беллуга на Волге"-->
        </div>
        <iframe ref="siteMap" class="siteMap" src="https://yandex.ru/map-widget/v1/?um=constructor%3A18cc83fede03b7bb33f34b319ec91e87a30c08365afd15b594d72c3575a96a71&amp;source=constructor" width="500" height="400" frameborder="0"></iframe>
        <img class="siteImg1" src="https://i.ibb.co/TMJcwk4c/GWM9-FRUa-Zrc.jpg" alt="">
        <div ref="siteImg2" class="siteImg2">
          <div class="siteImg2_cover">
            <div ref="siteTitle" class="site-name">
              <span>Ресторан</span>
              <br>"Беллуга на Волге"
            </div>
            <img src="https://i.ibb.co/TMhhLt2R/2025-04-10-13-25-06.png" alt="">
            <div ref="coverSite" class="coverSite"></div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import gsap from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';
import GalleryPhoto from '@/components/GalleryPhoto/index.vue'
const queryParams = new URLSearchParams(window.location.search);
const name1 = queryParams.get('name1')
const name2 = queryParams.get('name2')
const mainVideo = ref(null)
const siteVideo = ref(null)
const siteTitle = ref(null)
const siteDesc = ref(null)
const site = ref(null)
const siteMap = ref(null)
const siteImg2 = ref(null)
const leadingVideo = ref(null)
const coverSite = ref(null)
const leadingJob = ref(null)
const leadingName = ref(null)
const galleryAlekseyPhoto = ref([
  {
    id: 'photo1',
    url: 'https://i.ibb.co/1G8DD198/photo-2025-02-23-06-01-46.jpg',
    positionX: 'left',
    positionY: 'top',
    x: '10%',
    y: '10%',
    width: '80%'
  },
  {
    id: 'photo2',
    url: 'https://i.ibb.co/WpfYSwk4/photo-2025-03-03-15-55-52.jpg',
    positionX: 'right',
    positionY: 'bottom',
    x: '10%',
    y: '10%',
    width: '50%'
  },
  {
    id: 'photo3',
    url: 'https://i.ibb.co/ns3SZHbr/photo-2025-03-03-15-55-55.jpg',
    positionX: 'left',
    positionY: 'bottom',
    x: '10%',
    y: '20%',
    width: '60%'
  },
  {
    id: 'photo4',
    url: 'https://i.ibb.co/Zp54LTrP/photo-2025-03-03-15-56-01-3.jpg',
    positionX: 'right',
    positionY: 'top',
    x: '10%',
    y: '2%',
    width: '60%'
  },
  {
    id: 'photo6',
    url: 'https://i.ibb.co/1J9VYDDg/photo-2025-03-03-15-56-01.jpg',
    positionX: 'left',
    positionY: 'bottom',
    x: '10%',
    y: '10%',
    width: '80%'
  },
  {
    id: 'photo5',
    url: 'https://i.ibb.co/JwQ3C0px/photo-2025-03-03-15-56-01-2.jpg',
    positionX: 'left',
    positionY: 'bottom',
    x: '10%',
    y: '0%',
    width: '80%'
  },

])
const galleryPhotoImg = ref([])
const box = ref(null);
const container = ref(null);
const offer = ref(null);
const galleryAleksey = ref(null);
const title = ref(false);
const articlesPosts = ref([])
const articlesBlock = ref(null)

// Регистрация ScrollTrigger
gsap.registerPlugin(ScrollTrigger);

const articles = ref([
  {
    title: 'Где собираемся?',
    desc: 'Сбор у ЗАГСа на Полевой в 15:30'
  },
  {
    title: 'Нет звука приятнее, чем трубный призыв',
    desc: 'В своём стремлении повысить качество жизни, они забывают, что внедрение современных методик выявляет срочную потребность прогресса профессионального сообщества.'
  },
  {
    title: 'Обереги никого не защитили!',
    desc: 'Каждый из нас понимает очевидную вещь: глубокий уровень погружения однозначно определяет каждого участника как способного принимать собственные решения касаемо инновационных методов управления процессами.'
  },
  {
    title: 'Цена вопроса не важна, когда небо темнеет',
    desc: 'Сложно сказать, почему сделанные на базе интернет-аналитики выводы являются только методом политического участия и смешаны с не уникальными данными до степени совершенной неузнаваемости, из-за чего возрастает их статус бесполезности.'
  }
])


// Ссылка на элемент


const startAnim = () => {
  gsap.to(box.value, {
    scrollTrigger: {
      trigger: container.value, // Элемент, который запускает анимацию
      start: '100', // Начало анимации (когда верх элемента достигает центра экрана)
      end: '800', // Конец анимации
      scrub: 1, // Связь анимации с прокруткой
      // markers: false,
    },
    // clipPath: 'polygon(0% 0%, 100% 0%, 100% 100%, 0% 100%)', // Конечное значение clip-path||
    clipPath: 'inset(0% 0%)', // Конечное значение clip-path
    ease: 'none',
    duration: 1,
  });

  gsap.fromTo(
      title.value,
      {
        opacity: 1, // Начальное значение прозрачности
        y: 50, // Начальное смещение текста по вертикали
      },
      {
        scrollTrigger: {
          trigger: container.value,
          start: '800', // Начало анимации текста совпадает с началом анимации блока
          end: '+=100%',
          scrub: 1, // Синхронизация с анимацией блока
        },
        opacity: 0, // Конечное значение прозрачности
        y: 0, // Конечное положение текста
        ease: 'none',
        duration: 1,
      }
  );

  // Анимация появления текста
  gsap.fromTo(
      offer.value,
      {
        opacity: 0, // Начальное значение прозрачности
        // y: 50, // Начальное смещение текста по вертикали
      },
      {
        scrollTrigger: {
          trigger: container.value,
          start: '100', // Начало анимации текста совпадает с началом анимации блока
          end: '800',
          scrub: 1, // Синхронизация с анимацией блока
        },
        opacity: 1, // Конечное значение прозрачности
        // y: 0, // Конечное положение текста
        scale: 1,
        ease: 'none',
        duration: 1,
      }
  );

  gsap.to(box.value, {
    scrollTrigger: {
      trigger: document.body, // Триггер на весь документ
      start: '1600', // Начало анимации, когда центр блока достигает центра экрана
      end: '2500', // Продолжительность анимации относительно прокрутки
      scrub: 1, // Плавное завершение анимации
      markers: false, // Отладочные маркеры (можно удалить в продакшене)
    },
    right: '100%', // Конечное значение top (элемент уходит вверх)
    ease: 'none',
    duration: 1,
  });

  const startGallery = 2800
  const endGallery = 9000

  // galleryAleksey
  gsap.to(galleryAleksey.value,{
    scrollTrigger: {
      trigger: document.body, // Триггер на весь документ
      start: startGallery, // Начало анимации, когда центр блока достигает центра экрана
      end: endGallery, // Продолжительность анимации относительно прокрутки
      scrub: 1, // Плавное завершение анимации
      markers: false, // Отладочные маркеры (можно удалить в продакшене)
    },
    // x: 100, // Конечное значение top (элемент уходит вверх)
    y: '-100%',
    ease: 'none',
    // opacity: 1,
    duration: 1,
  });

  gsap.to(galleryAleksey.value, {
    scrollTrigger: {
      trigger: document.body, // Триггер на весь документ
      start: '1600', // Начало анимации, когда центр блока достигает центра экрана
      end: '2500', // Продолжительность анимации относительно прокрутки
      scrub: 1, // Плавное завершение анимации
      markers: false, // Отладочные маркеры (можно удалить в продакшене)
    },
    right: '100%', // Конечное значение top (элемент уходит вверх)
    ease: 'none',
    duration: 1,
  });
  // gsap.to(galleryAleksey.value,{
  //   scrollTrigger: {
  //     trigger: document.body, // Триггер на весь документ
  //     start: startGallery, // Начало анимации, когда центр блока достигает центра экрана
  //     end: endGallery, // Продолжительность анимации относительно прокрутки
  //     scrub: 1, // Плавное завершение анимации
  //     markers: false, // Отладочные маркеры (можно удалить в продакшене)
  //   },
  //   // x: 100, // Конечное значение top (элемент уходит вверх)
  //   x: '-100%',
  //   ease: 'none',
  //   // opacity: 1,
  //   duration: 1,
  // });

  galleryPhotoImg.value.forEach((image, index) => {
    const img = image.querySelector('img');
    gsap.to(img,{
      scrollTrigger: {
        trigger: document.body, // Триггер на весь документ
        start: startGallery + index * 100, // Начало анимации, когда центр блока достигает центра экрана
        end: endGallery, // Продолжительность анимации относительно прокрутки
        scrub: 4, // Плавное завершение анимации
        markers: false, // Отладочные маркеры (можно удалить в продакшене)
      },
      // x: 100, // Конечное значение top (элемент уходит вверх)
      y: '-60%',
      ease: 'none',
      // opacity: 1,
      duration: 1,
    });

    // gsap.to(img,{
    //   scrollTrigger: {
    //     trigger: document.body, // Триггер на весь документ
    //     start: endGallery + 400, // Начало анимации, когда центр блока достигает центра экрана
    //     end: endGallery + 1000, // Продолжительность анимации относительно прокрутки
    //     scrub: 1.5, // Плавное завершение анимации
    //     markers: false, // Отладочные маркеры (можно удалить в продакшене)
    //   },
    //   // x: 100, // Конечное значение top (элемент уходит вверх)
    //   x: '-300%',
    //   ease: 'none',
    //   // opacity: 1,
    //   duration: 1,
    // });
  })

  // gsap.to(galleryAleksey.value,{
  //   scrollTrigger: {
  //     trigger: document.body, // Триггер на весь документ
  //     start: endGallery + 600, // Начало анимации, когда центр блока достигает центра экрана
  //     end: endGallery + 1400, // Продолжительность анимации относительно прокрутки
  //     scrub: 1, // Плавное завершение анимации
  //     markers: false, // Отладочные маркеры (можно удалить в продакшене)
  //   },
  //   // x: 100, // Конечное значение top (элемент уходит вверх)
  //   y: '-120%',
  //   ease: 'none',
  //   // opacity: 1,
  //   duration: 1,
  // });

  const endBlockGalleryTransition = endGallery - 600
  const startArticlesBlock = endBlockGalleryTransition + 200
  const endArticlesBlock = articlesPosts.value.length
  console.log('arti')

  gsap.fromTo(
      galleryAleksey.value,
      {
        opacity: 1, // Начальное значение прозрачности
      },
      {
        scrollTrigger: {
          trigger: document.body,
          start: endBlockGalleryTransition, // Начало анимации текста совпадает с началом анимации блока
          end: startArticlesBlock,
          scrub: 1, // Синхронизация с анимацией блока
        },
        opacity: 0.1, // Конечное значение прозрачности
        ease: 'none',
        duration: 1,
      }
  );
  // let textElem = document.querySelector('.text')
  // console.log(textElem.innerText, 'TEST')
  // gsap.to(".typing_text", {
  //   // text: {
  //   //   value: 'TYPING TEXT'
  //   // },
  //   text: 'TYPING TEXT',
  //   scrollTrigger: {
  //       trigger: document.body,
  //     // pin: ".typing_text-heading",
  //     start: 500 , // Начало анимации, когда центр блока достигает центра экрана
  //     end: 1000, // Продолжительность анимации относительно прокрутки
  //     scrub: true,
  //     markers: true
  //   }
  // });
  articlesPosts.value.forEach((post, index) => {
    gsap.to(post,{
      scrollTrigger: {
        trigger: document.body, // Триггер на весь документ
        start: startArticlesBlock + index * 100, // Начало анимации, когда центр блока достигает центра экрана
        end: startArticlesBlock + index * 1000, // Продолжительность анимации относительно прокрутки
        scrub: 2, // Плавное завершение анимации
        markers: false, // Отладочные маркеры (можно удалить в продакшене)
      },
      // x: 100, // Конечное значение top (элемент уходит вверх)
      y: '0',
      ease: 'none',
      opacity: 1,
      duration: 1,
    });
  })
  // Поднятие описания
  gsap.to(articlesBlock.value,{
    scrollTrigger: {
      trigger: document.body, // Триггер на весь документ
      start: startArticlesBlock, // Начало анимации, когда центр блока достигает центра экрана
      end: startArticlesBlock + endArticlesBlock * 1000, // Продолжительность анимации относительно прокрутки
      scrub: 1, // Плавное завершение анимации
      markers: false, // Отладочные маркеры (можно удалить в продакшене)
    },
    // x: 100, // Конечное значение top (элемент уходит вверх)
    y: '-200%',
    ease: 'none',
    // opacity: 1,
    duration: 1,
  });
  // Video
  const endArticlseBlock = startArticlesBlock + articlesPosts.value.length * 1000
  const leadingVideoDuration = 3000
  const startLeading = endArticlseBlock - 1000

  gsap.to(leadingVideo.value,{
    scrollTrigger: {
      trigger: document.body, // Триггер на весь документ
      start: startLeading, // Начало анимации, когда центр блока достигает центра экрана
      end: startLeading + leadingVideoDuration, // Продолжительность анимации относительно прокрутки
      scrub: 1, // Плавное завершение анимации
      markers: false, // Отладочные маркеры (можно удалить в продакшене)
    },
    // x: 100, // Конечное значение top (элемент уходит вверх)
    y: '-100%',
    ease: 'none',
    // opacity: 1,
    duration: 1,
  });
  // Должность Ведущего
  gsap.to(leadingJob.value,{
    scrollTrigger: {
      trigger: document.body, // Триггер на весь документ
      start: startLeading + 100, // Начало анимации, когда центр блока достигает центра экрана
      end: startLeading + leadingVideoDuration - 2000, // Продолжительность анимации относительно прокрутки
      scrub: 1, // Плавное завершение анимации
      markers: false, // Отладочные маркеры (можно удалить в продакшене)
    },
    // x: 100, // Конечное значение top (элемент уходит вверх)
    x: '0',
    ease: 'none',
    // opacity: 1,
    duration: 1,
  });

  gsap.to(leadingName.value,{
    scrollTrigger: {
      trigger: document.body, // Триггер на весь документ
      start: startLeading + 3000, // Начало анимации, когда центр блока достигает центра экрана
      end: startLeading + 4000, // Продолжительность анимации относительно прокрутки
      scrub: 1, // Плавное завершение анимации
      markers: false, // Отладочные маркеры (можно удалить в продакшене)
    },
    // x: 100, // Конечное значение top (элемент уходит вверх)
    x: '0',
    ease: 'none',
    // opacity: 1,
    duration: 1,
  });
  // Имя Ведущего
  const endLeading = startLeading + 4000
  const siteVideoDuration = 4000
  const startSiteVideo = endLeading - 2000
  console.log(endLeading, 'endLeading')
  gsap.to(site.value,{
    scrollTrigger: {
      trigger: document.body, // Триггер на весь документ
      start: startSiteVideo + 2500, // Начало анимации, когда центр блока достигает центра экрана
      end: startSiteVideo + siteVideoDuration, // Продолжительность анимации относительно прокрутки
      scrub: 1, // Плавное завершение анимации
      markers: false, // Отладочные маркеры (можно удалить в продакшене)
    },
    // x: 100, // Конечное значение top (элемент уходит вверх)
    y: '-100%',
    ease: 'none',
    // opacity: 1,
    duration: 1,
  });
  console.log(siteTitle.value)
  const siteDuration = 3500
  gsap.to(siteTitle.value,{
    scrollTrigger: {
      trigger: document.body, // Триггер на весь документ
      start: startSiteVideo + 4500, // Начало анимации, когда центр блока достигает центра экрана
      end: startSiteVideo + siteVideoDuration + siteDuration, // Продолжительность анимации относительно прокрутки
      scrub: 1, // Плавное завершение анимации
      markers: false, // Отладочные маркеры (можно удалить в продакшене)
    },
    // x: 100, // Конечное значение top (элемент уходит вверх)
    y: '20%',
    ease: 'none',
    // opacity: 1,
    duration: 1,
  });


  gsap.to(siteImg2.value,{
    scrollTrigger: {
      trigger: document.body, // Триггер на весь документ
      start: startSiteVideo + 5500, // Начало анимации, когда центр блока достигает центра экрана
      end: startSiteVideo + siteVideoDuration + siteDuration, // Продолжительность анимации относительно прокрутки
      scrub: 1, // Плавное завершение анимации
      markers: false, // Отладочные маркеры (можно удалить в продакшене)
    },
    // x: 100, // Конечное значение top (элемент уходит вверх)
    y: '0',
    ease: 'none',
    // opacity: 1,
    duration: 1,
  });

  gsap.fromTo(
      coverSite.value,
      {
        opacity: 0, // Начальное значение прозрачности
      },
      {
        scrollTrigger: {
          trigger: document.body, // Триггер на весь документ
          start: startSiteVideo + siteVideoDuration + 4000, // Начало анимации, когда центр блока достигает центра экрана
          end: startSiteVideo + siteVideoDuration + 6000, // Продолжительность анимации относительно прокрутки
          scrub: 1, // Плавное завершение анимации
          markers: false, // Отладочные маркеры (можно удалить в продакшене)
        },
        opacity: 0.7, // Конечное значение прозрачности
        ease: 'none',
        duration: 1,
      }
  );

  gsap.to(siteMap.value,{
    scrollTrigger: {
      trigger: document.body, // Триггер на весь документ
      start: startSiteVideo + siteVideoDuration + 4000, // Начало анимации, когда центр блока достигает центра экрана
      end: startSiteVideo + siteVideoDuration + 6000, // Продолжительность анимации относительно прокрутки
      scrub: 1, // Плавное завершение анимации
      markers: false, // Отладочные маркеры (можно удалить в продакшене)
    },
    // x: 100, // Конечное значение top (элемент уходит вверх)
    y: '0',
    ease: 'none',
    // opacity: 1,
    duration: 1,
  });

  const endSite = startSiteVideo + siteVideoDuration + 9000

  document.documentElement.style.height = endSite + 'px'
  console.log(document.body.style.height)
}

const heightWindow = ref(window.innerHeight)

onMounted(() => {
  // Настройка анимации clip-path с помощью GSAP и ScrollTrigger
  const documentHeight = () => {
    const doc = document.documentElement
    doc.style.setProperty('--doc-height', `${window.innerHeight}px`)
    heightWindow.value = window.innerHeight
  }
  window.addEventListener('resize', documentHeight)
  mainVideo.value.addEventListener('loadeddata', (e) => {
    //Video should now be loaded but we can add a second check
    // console.log('load')
    mainVideo.value.play()
    if(mainVideo.value.readyState >= 3){
      //your code goes here
      // loading.value = false
      // console.log('loaded')
    }

  });
  documentHeight()
  startAnim();
});
</script>

<style scoped lang="scss">
@import url('./style.scss')
</style>
