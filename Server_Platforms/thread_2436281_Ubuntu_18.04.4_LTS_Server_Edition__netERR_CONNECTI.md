---
title: "Ubuntu 18.04.4 LTS Server Edition : net::ERR_CONNECTION_REFUSED"
date: 2020-02-03
forum: Server Platforms
---

### Post by marco910 on 2020-02-03
I put in this repository a tiny testing webapp: [https://github.com/marcoippolito/testproject](https://github.com/marcoippolito/testproject)

If I git clone it in a laptop using Linux 5.3 Ubuntu 18.04.3 LTS (Bionic Beaver)

with this environment:

    (base) marco@marco-U36SG:~/vueMatters/testproject$ vue info

    Environment Info:

      System:
        OS: Linux 5.3 Ubuntu 18.04.3 LTS (Bionic Beaver)
        CPU: (4) x64 Intel(R) Core(TM) i7-2620M CPU @ 2.70GHz
      Binaries:
        Node: 12.14.1 - ~/.nvm/versions/node/v12.14.1/bin/node
        Yarn: 1.21.1 - /usr/bin/yarn
        npm: 6.13.4 - ~/.nvm/versions/node/v12.14.1/bin/npm
      Browsers:
        Chrome: 79.0.3945.130
        Firefox: 72.0.2
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
        @vue/cli-plugin-babel: ^4.1.2 => 4.1.2 
        @vue/cli-plugin-eslint: ^4.1.2 => 4.1.2 
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


and then run the webapp:

    (base) marco@marco-U36SG:~/vueMatters/testproject$ npm run serve

    > testproject@0.1.0 serve /home/marco/vueMatters/testproject
    > vue-cli-service serve

     INFO  Starting development server...
    98% after emitting CopyPlugin

     DONE  Compiled successfully in 6588ms                                                               3:37:24 PM


      App running at:
      - Local:   [http://localhost:8080](http://localhost:8080) 
      - Network: [http://192.168.1.4:8080](http://192.168.1.4:8080)

      Note that the development build is not optimized.
      To create a production build, run npm run build.

I get the webpage with no error message in the web developer's console


But if I git clone the same repository into Ubuntu 18.04.04 LTS Server Edition:


    (base) marco@pc:~/vueMatters/testproject$ vue info

    Environment Info:

      System:
        OS: Linux 4.15 Ubuntu 18.04.4 LTS (Bionic Beaver)
        CPU: (8) x64 Intel(R) Core(TM) i7-4790K CPU @ 4.00GHz
      Binaries:
        Node: 12.11.0 - ~/.nvm/versions/node/v12.11.0/bin/node
        Yarn: 1.21.1 - /usr/bin/yarn
        npm: 6.11.3 - ~/.nvm/versions/node/v12.11.0/bin/npm
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
        vue: ^2.6.11 => 2.6.11 
        vue-eslint-parser:  5.0.0 
        vue-hot-reload-api:  2.3.4 
        vue-loader:  15.8.3 
        vue-style-loader:  4.1.2 
        vue-template-compiler: ^2.6.10 => 2.6.11 
        vue-template-es2015-compiler:  1.9.1 
      npmGlobalPackages:
        @vue/cli: 4.1.2


And, after stopping the nginx server:

    (base) marco@pc:~/vueMatters/testproject$ sudo systemctl stop nginx
    [sudo] password for marco: 
    (base) marco@pc:~/vueMatters/testproject$ sudo systemctl status nginx
    &#9679; nginx.service - A high performance web server and a reverse proxy 
    server
       Loaded: loaded (/lib/systemd/system/nginx.service; enabled; vendor 
    preset: enabled)
       Active: inactive (dead) since Mon 2020-02-03 16:14:07 CET; 5s ago
         Docs: man:nginx(8)
      Process: 5749 ExecStop=/sbin/start-stop-daemon --quiet --stop --retry
    QUIT/5 --pidfile /run/nginx.pid (code=exited, status=0/SUCCESS)
      Process: 919 ExecStart=/usr/sbin/nginx -g daemon on; master_process 
    on; (code=exited, status=0/SUCCESS)
      Process: 891 ExecStartPre=/usr/sbin/nginx -t -q -g daemon on; 
    master_process on; (code=exited, status=0/SUCCESS)
     Main PID: 925 (code=exited, status=0/SUCCESS)

    Feb 03 14:46:29 pc systemd[1]: Starting A high performance web server 
    and a reverse proxy server...
    Feb 03 14:46:30 pc systemd[1]: Started A high performance web server 
    and a reverse proxy server.
    Feb 03 16:14:07 pc systemd[1]: Stopping A high performance web server 
    and a reverse proxy server...
    Feb 03 16:14:07 pc systemd[1]: Stopped A high performance web server 
    and a reverse proxy server.

I run the tiny web-app:

    (base) marco@pc:~/vueMatters/testproject$ npm run serve

    > testproject@0.1.0 serve /home/marco/vueMatters/testproject
    > vue-cli-service serve

     INFO  Starting development server...
    98% after emitting CopyPlugin

     DONE  Compiled successfully in 1376ms                                                                                                                                                               4:16:25 PM


      App running at:
      - Local:   [http://localhost:8080](http://localhost:8080) 
      - Network: [http://192.168.1.7:8080](http://192.168.1.7:8080)

      Note that the development build is not optimized.
      To create a production build, run npm run build.


I get this errors:

    GET [http://localhost:8080/sockjs-node/info?t=1580743078903](http://localhost:8080/sockjs-node/info?t=1580743078903) 
    net::ERR_CONNECTION_REFUSED


Comparing the two environment infos, the only difference is the OS installed:
in the laptop, where the tiny webapp is regularly working fine,
    Linux 5.3 Ubuntu 18.04.3 LTS (Bionic Beaver) Desktop
in the pc, where the tiny webapp is giving the error "net::ERR_CONNECTION_REFUSED",
    Linux 4.15 Ubuntu 18.04.4 LTS (Bionic Beaver) Server Edition

So... how to solve the problem?

Looking forward to your kind help.
Marco

---

### Post by LHammonds on 2020-02-03
I doubt the problem lies in the web code.  It is more-likely in how nginx was installed / configured.

Go back to the basics and make sure you can view a super-simply index.htm that just says "hello world."  Make sure permissions are set correctly on the file as well.  Once you verify the web server can deliver the most simplistic of non-dynamic web pages, you can then start testing for more complex scenarios such as server-side program files like PHP or whatever you need.

I doubt its a firewall issue since you are issuing a "get" command directly on the server to "localhost" but if you get it working locally and cannot connect from another machine, the firewall is your next item to look at configuring for remote access.

LHammonds

---

