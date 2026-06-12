---
title: "Need Some Apache/ModRewrite Help"
date: 2018-07-18
forum: Server Platforms
---

### Post by acascianelli on 2018-07-18
Running Ubuntu 18.04.

I'm trying to setup a web client for KeePass called KeeWeb:

[https://github.com/keeweb/keeweb](https://github.com/keeweb/keeweb)

There is an option to reference a JSON config file from the URL to specify some options, but I cannot figure out what mod_rewrite rule I need in order to append the query string to the end of the page index.  See link for details.

[https://github.com/keeweb/keeweb/wiki/Configuration](https://github.com/keeweb/keeweb/wiki/Configuration)

I know I could just modify the index.html to include the path to the config file, but I don't want to run it that way.

Basically I need to convert [https://www.example.com/KeeWeb/index.html](https://www.example.com/KeeWeb/index.html) to [https://www.example.com/KeeWeb/index.html?config=config.json](https://www.example.com/KeeWeb/index.html?config=config.json)

---

