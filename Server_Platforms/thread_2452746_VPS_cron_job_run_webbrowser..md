---
title: "VPS cron job run webbrowser."
date: 2020-10-27
forum: Server Platforms
---

### Post by toadelite on 2020-10-27
Hello everyone. I would like to ask it,that possible,that vps to install  a browser and cron in a command onto a server to run interval? As if I  would go up with a desktop browser on a machine onto a given side?

---

### Post by TheFu on 2020-10-27
Anything is possible.

Whether it is easy or not depends on all sorts of things, mainly, what is the browser really trying to accomplish? 

If you can use any other tool than a browser, automation is much easier.  For example, RSS feeds are trivial to pull in an automatic way.  There's curl, wget, lynx for normal HTML without javascript. Many websites have a REST interface to skip the fancy, pretty, bloated javascript, and just get to the data. Those are much easier to automate.  It just depends.  For javascript-based web stuff with AJAX calls, you'll likely want to check out browser and website test automation tools.  Selenium is the most popular. [https://en.wikipedia.org/wiki/Selenium_(software)](https://en.wikipedia.org/wiki/Selenium_(software))  There are a number of front-ends to Selenium for different languages - ruby, perl, python all have popular front ends.

Possible? Yes.  Trivial, it depends.

BTW, when running a remote desktop on a VPS, please be certain to secure it. Most remote desktops have terrible security and are hacked much to easily. In short, if you don't use NX as the protocol, then you'll need a full VPN setup.

---

