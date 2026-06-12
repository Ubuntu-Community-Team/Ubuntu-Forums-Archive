---
title: "autostart vino-server"
date: 2007-05-07
forum: Server Platforms
---

### Post by 95aspire on 2007-05-07
hey guys how do i make vino-server, (vnc server) start at login, id like to make my server a headless unit, i have telnet server setup and i can vnc into my server but only if i start it on my server first, 

im using xubuntu i think it is but the version is dapper, 

any help is appriciated, ive been searching but have found nothing.

---

### Post by 95aspire on 2007-05-08
anyone? i cant find anything on this theres several threads but ive seen no solution thats worked

---

### Post by jimcooncat on 2007-05-09
Possibly you didn't get much response because vino-server uses the actual display; but if you're doing a headless server there's no need to control the actual display. If you're using this remotely, you don't  want to do this anyway -- if someone turns on the display they can see what you're doing!

Check out "HOWTO: Set up VNC server with resumable sessions":
[http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)
I think it will do what you want over a LAN. 

Let me know if you need to connect over the internet, I have a bunch of links and info about SSH tunnelling.

---

