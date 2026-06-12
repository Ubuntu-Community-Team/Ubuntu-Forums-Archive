---
title: "perl+fcgiwrap+nginx"
date: 2017-01-17
forum: Server Platforms
---

### Post by zemson on 2017-01-17
Hello!
I have Ubuntu server 16.04.2 with perl+fcgiwrap+nginx. Everything is fine, scripts are running. But if I query the same script many times (more then 2) simultaniously fcgiwrap (with 10 childs) will run it one instance by another, not all them at once. Scripts with different names runs altogether very well not sequentially. Is that normal operation of fcgiwrap? Or I am doing something wrong?
I tried that on Ubuntu desktop 10.04 with the same results.
All soft is from repo with standard config.

upd
The problem above was in my browsers (Firefox and Chromium). They don't allow to send the equal queries from many tabs at one time. I took IE and curl and got all I want. 
But I have another problem with spawn-fcgi. It don't fork childs more then one, even if I wrote in config /etc/init.d/fcgiwrap DAEMON_OPTS="-c 10".

---

