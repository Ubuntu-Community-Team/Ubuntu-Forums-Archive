---
title: "Help with starting programs at boot"
date: 2010-07-10
forum: Server Platforms
---

### Post by redfox1160 on 2010-07-10
How would I make sure cron is running every time my server is turned on? I want to make cron jobs, but I need to know that it is running when the server boots. Thanks.

Also, I used a program at some point that was terminal based and it showed be what programs ran when the server booted up. It allowed me to check a box and select which programs I could run at boot. If someone could tell me this program, I would appreciate it.

---

### Post by rogerdg on 2010-07-10
I use WEBMIN to maintain my system.  It's a graphical system that runs via PHP in a web browser.  After installing webmin you simply point your web browser to [http://localhost:10000](http://localhost:10000) (or https: if https is enabled on your system) and select options from there.  It's a very nice system that permits system maintenance via a point-n-click interface.  Also, it gives access to start-up files in Linux and allows you to turn individual programs on or off at startup (and even start them if they aren't running yet.)

---

### Post by redfox1160 on 2010-07-10
> **rogerdg said:**
> I use WEBMIN to maintain my system.  It's a graphical system that runs via PHP in a web browser.  After installing webmin you simply point your web browser to [http://localhost:10000](http://localhost:10000) (or https: if https is enabled on your system) and select options from there.  It's a very nice system that permits system maintenance via a point-n-click interface.  Also, it gives access to start-up files in Linux and allows you to turn individual programs on or off at startup (and even start them if they aren't running yet.)

What is the program called in the repositories? (so i can use apt-get)

---

