---
title: "KDE + VNC + SSH + Encryption"
date: 2008-09-01
forum: Server Platforms
---

### Post by KuraKai on 2008-09-01
Ok, so this might not make any sense to anyone but I am a very very very newbish person when it comes to Linux. I just got my hand on a server that is currently running the server version of Ubuntu with no extra features. (I.E. SSH and the core)
However the problem is that all the computers I want to connect to the server with are going to be running Windows(Booo! Sorry Can't Get Rid Of It Yet).  Anyways I need help in setting up my server to have three configurations for different ways of accessing it.

1) At The Computer(At The Monitor): NO GUI, just plain old console
2) SSH: Connect over the internet using PuTTY, however I would like it setup so that the connection is encrypted and secured and doesn't require a login. (Private Key)
3) SSH + VNC: For when I miss the good old GUI times, just like it should be setup for SSH just using forwarding to make the VNC connection secure, also it must have sessions that don't quit unless I logout. (Resumable; Forgot how to spell it) Note: KDE not Gnome

Some of this may seem easy to do but like I said I am a newb wanting to know how to do it right and I guess you can say from scratch. I am open for people pointing me to tutorials or if you want to help me out by giving me step by step instructions! :)

PS: I know there might be a few guides, like the VNC setup/configuration. Just that they assume you have a GUI to begin with.
PSS: REINSTALLING IS NOT AN OPTION!

---

### Post by mellowd on 2008-09-01
This is for number 2. It's what I used to set my access up.

[http://the.earth.li/~sgtatham/putty/0.58/htmldoc/Chapter8.html](http://the.earth.li/~sgtatham/putty/0.58/htmldoc/Chapter8.html)

---

