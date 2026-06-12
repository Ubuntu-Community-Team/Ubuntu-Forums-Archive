---
title: "Back to an Ubuntu server"
date: 2005-09-07
forum: Server Platforms
---

### Post by endy on 2005-09-07
I have a spare box I use as a home server until recently a friend needed to use a PC for a few weeks and I installed the Ubuntu Desktop on it. Now he's finished with it I'd like to remove all the desktop packages and strip it back down to just being a server again.

Is there an easy way to do this? When I remove the Ubuntu-desktop package thats all thats removed. Any ideas?

---

### Post by KingBahamut on 2005-09-07
Reinstall 

at the boot prompt type 

boot: server 


and hit enter. 

Youll get a bare box with nothing on it save the base install, then just apt get to your hearts content.

---

### Post by endy on 2005-09-08
That's what I thought :( 

Problem is, I don't want to have to move it over here and plug in the monitor, keyboard etc... Heh, can you remotely install Ubuntu like via a SSH login or something, when the install disc boots?

---

