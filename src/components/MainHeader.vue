<template>
  <div id="app">
    <div class="wrap">
      <header class="header">
        <div id="gnav__toggle" @click="openToggle()">
          <span class="gnav__toggle__icon"></span>
          <span class="gnav__toggle__icon"></span>
          <span class="gnav__toggle__icon"></span>menu
        </div>
        <div id="gnav__list" @click="closeToggle()">
          <ul>
            <li><router-link to="/">ホーム</router-link></li>
            <li><router-link to="/yamagatagyu">総称山形牛</router-link></li>
            <li><router-link to="/kinkabuta">純粋金華豚</router-link></li>
            <li><router-link to="/yonezawabuta">米澤豚</router-link></li>
            <li><router-link to="/shopinfo">店舗情報</router-link></li>
            <li><a href="http://www.110298.com/">通販ページ</a></li>
          </ul>
        </div>
      </header>
    </div>
  </div>
</template>

<script>
export default {
  name: "MainHeader",
  methods: {
    openToggle() {
      document.getElementById("gnav__toggle").classList.toggle("open");
      document.getElementById("gnav__list").classList.toggle("open");
    },
    closeToggle() {
      document.getElementById("gnav__toggle").classList.remove("open");
      document.getElementById("gnav__list").classList.remove("open");
    }
  },
  mounted() {
    window.addEventListener(
      "resize",
      function() {
        let w = window.innerWidth;
        if (w > 620) {
          document.getElementById("gnav__toggle").classList.remove("open");
          document.getElementById("gnav__list").classList.remove("open");
        }
      },
      false
    );
  }
};
</script>

<style lang="scss" scoped>
.wrap {
  position: relative;
  height: 48px;
}

.header {
  position: fixed;
  width: 100%;
  height: 48px;
  background: rgba(255, 255, 255, 0.7);
  a {
    color: black;
    text-decoration: none;
  }
}

#gnav__toggle {
  position: absolute;
  top: 8px;
  right: 8px;
  width: 32px;
  height: 32px;
  font-size: 8px;
  text-align: center;
  cursor: pointer;
}

.gnav__toggle__icon {
  display: block;
  position: relative;
  height: 2px;
  background: #5c6b80;
  -webkit-transition: ease 0.5s;
  transition: ease 0.5s;
}

.gnav__toggle__icon:nth-child(1) {
  top: 0;
}

.gnav__toggle__icon:nth-child(2) {
  margin: {
    top: 8px;
    bottom: 8px;
  }
}

.gnav__toggle__icon:nth-child(3) {
  top: 0;
}

/*OPEN時のトグルアイコンの動き*/
#gnav__toggle.open {
  .gnav__toggle__icon:nth-child(1) {
    top: 10px;
    -webkit-transform: rotate(45deg);
    transform: rotate(45deg);
  }
  .gnav__toggle__icon:nth-child(2) {
    -webkit-transform: translateY(-45deg);
    transform: translateY(-45deg);
    opacity: 0;
  }
  .gnav__toggle__icon:nth-child(3) {
    top: -10px;
    -webkit-transform: rotate(-45deg);
    transform: rotate(-45deg);
  }
}

#gnav__list {
  display: inline-block;
  position: absolute;
  top: -300px;
  right: 0;
  font-size: 1.2em;
  background-color: #f6f6f6;

  // li {
  //   padding: 1em;
  // }
}

/*OPEN時の動き*/
#gnav__list.open {
  position: absolute;
  top: 48px;
  right: 0;
  -webkit-transform: translate(0);
  transform: translateY(0);
  overflow-y: auto;
  -webkit-overflow-scrolling: touch;
  background: rgba(255, 255, 255, 0.9);
  ul {
    padding: 0;
  }
  li {
    list-style: none;
    font-size: 14px;
    padding: 1em;
  }
}

@media screen and (min-width: 620px) {
  .header {
    display: flex;
    position: fixed;
    top: 0;
    right: 0;
    flex-direction: row;
  }

  #gnav__toggle {
    display: none;
  }

  #gnav__list {
    position: absolute;
    top: 0;
    right: 0;
    -webkit-transform: translateX(0);
    transform: translateX(0);
    font-size: 14px;
    width: 100%;
    height: 48px;
    background: rgba(255, 255, 255, 0.7);
    justify-content: flex-end;
    ul {
      display: flex;
      height: 48px;
      padding: 0;
      flex-wrap: wrap;
      align-items: center;
      justify-content: flex-end;
    }
    li {
      list-style: none;
      padding: {
        right: 0.5rem;
        left: 0.5rem;
      }
      border-bottom: none;
    }
  }
}
</style>
