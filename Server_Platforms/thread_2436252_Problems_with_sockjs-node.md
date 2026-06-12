---
title: "Problems with sockjs-node"
date: 2020-02-03
forum: Server Platforms
---

### Post by marco910 on 2020-02-03
As fully described in these GitHub's issue reports:
 1) [https://github.com/vuejs/vue-cli/issues/5129](https://github.com/vuejs/vue-cli/issues/5129)
 2) [https://github.com/webpack/webpack/issues/10329](https://github.com/webpack/webpack/issues/10329)
I'm having problems with nodejs-sockjs.

Webpack's people think it might be a problem of Linux 4.15 Ubuntu 18.04.4 LTS (Bionic Beaver) Server Edition, 
the OS I'm using in the PC, because they tried to use my tiny testing webapp, and they had no problems at all.


    (base) marco@pc:~/vueMatters/testproject$ vue info

    Environment Info:

      System:
        OS: Linux 4.15 Ubuntu 18.04.4 LTS (Bionic Beaver)
        CPU: (8) x64 Intel(R) Core(TM) i7-4790K CPU @ 4.00GHz
      Binaries:
        Node: 12.10.0 - ~/.nvm/versions/node/v12.10.0/bin/node
        Yarn: 2.0.0-rc.27 - ~/.nvm/versions/node/v12.10.0/bin/yarn
        npm: 6.13.6 - ~/.nvm/versions/node/v12.10.0/bin/npm
      Browsers:
        Chrome: Not Found
        Firefox: Not Found
      npmPackages:
        @vue/babel-helper-vue-jsx-merge-props:  1.0.0 
        @vue/babel-plugin-transform-vue-jsx:  1.1.2 
        @vue/babel-preset-app:  4.1.2 
        @vue/babel-preset-jsx:  1.1.2 
        @vue/babel-sugar-functional-vue:  1.1.2 
        @vue/babel-sugar-inject-h:  1.1.2 
        @vue/babel-sugar-v-model:  1.1.2 
        @vue/babel-sugar-v-on:  1.1.2 
        @vue/cli-overlay:  4.1.2 
        @vue/cli-plugin-babel: ^4.1.0 => 4.1.2 
        @vue/cli-plugin-eslint: ^4.1.0 => 4.1.2 
        @vue/cli-plugin-router:  4.1.2 
        @vue/cli-plugin-vuex:  4.1.2 
        @vue/cli-service: ^4.1.0 => 4.1.2 
        @vue/cli-shared-utils:  4.1.2 
        @vue/component-compiler-utils:  3.1.1 
        @vue/preload-webpack-plugin:  1.1.1 
        @vue/web-component-wrapper:  1.2.0 
        eslint-plugin-vue: ^5.0.0 => 5.2.3 
        vue: ^2.6.10 => 2.6.11 
        vue-eslint-parser:  5.0.0 
        vue-hot-reload-api:  2.3.4 
        vue-loader:  15.8.3 
        vue-style-loader:  4.1.2 
        vue-template-compiler: ^2.6.10 => 2.6.11 
        vue-template-es2015-compiler:  1.9.1 
      npmGlobalPackages:
        @vue/cli: 4.1.2

For sure, it's not a problem related to the nginx server I'm using, because it appears both with nginx on and with nginx off.

What kind of issue might be related to the specific Ubuntu OS Server Edition installed in the PC?

Looking forward to your kind help.
Marco

---

### Post by marco910 on 2020-02-03
I put in this repository the tiny testing app: [https://github.com/marcoippolito/testproject](https://github.com/marcoippolito/testproject)
I then git clone in a laptop with Ubuntu 18.04.03 Desktop and run the app without any problems:

(base) marco@marco-U36SG:~$ vue info

Environment Info:

  System:
    OS: Linux 5.3 Ubuntu 18.04.3 LTS (Bionic Beaver)
    CPU: (4) x64 Intel(R) Core(TM) i7-2620M CPU @ 2.70GHz
  Binaries:
    Node: 12.11.0 - ~/.nvm/versions/node/v12.11.0/bin/node
    Yarn: 1.21.1 - /usr/bin/yarn
    npm: 6.13.6 - ~/.nvm/versions/node/v12.11.0/bin/npm
  Browsers:
    Chrome: 79.0.3945.130
    Firefox: 72.0.2
  npmGlobalPackages:
    @vue/cli: 4.1.1



So, I must agree with webpack's people that there is something in Ubuntu 18.04.04 Server Edition which somehow causes the problem.

---

