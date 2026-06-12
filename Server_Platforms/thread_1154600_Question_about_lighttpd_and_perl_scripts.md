---
title: "Question about lighttpd and perl scripts"
date: 2009-05-09
forum: Server Platforms
---

### Post by spetsacdc on 2009-05-09
Hi, I plan to set up a webserver on my ubuntu box for developing a website.

I am trying to plan the type of server correctly on my development machine so I can repeat the process on the VPS. I am trying to minimize the amount of ram the server uses so I can buy a cheaper VPS. My plan is to setup:

1. lighttpd
2. php
3. fastcgi (to run php)
4. mysql

Now, I am wondering about a few things:

1. Do people usually use fastcgi to run perl scripts, or do you just use the cgi module?
2. I have read that phpmyadmin uses a lot of ram. How else do people manage the mysql database when it is hosted on another shared/VPS server (terminal/some program?)?


Thanks

---

