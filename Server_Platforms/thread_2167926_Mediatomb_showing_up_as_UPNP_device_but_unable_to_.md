---
title: "Mediatomb showing up as UPNP device but unable to play files"
date: 2013-08-15
forum: Server Platforms
---

### Post by ads2996 on 2013-08-15
Hi,

I just set up my home server but i am unable to play the files shared via mediatomb. I havent edited any setting except to enable the web ui.

Any help greatly appreicated

---

### Post by cariboo on 2013-08-15
What did you do to solve the problem?

---

### Post by ads2996 on 2013-08-16
I completely removed media tomb running the commands
Sudo mediatomb stop
Sudo apt-get purge mediatomb
Sudo apt-get autoremove 

I then rebooted and reinstalled media tomb, I have webmin installed sink used it to edit the upstart and changed the interface on the script to eth0, as I had the problem of it using the vibr0 interface

---

