---
title: "Shorewall taking an age to restart"
date: 2010-05-11
forum: Server Platforms
---

### Post by chrislynch8 on 2010-05-11
Any time I try and restart the Shorewall it takes forever. Sometimes I have to reboot the File Server as its faster.

In the shorewall-init.log it seems to stick on the loading modules and goes no further. Anyone come accross this before.

I have Ubunut 8.04LTS - everything seemed to be working OK until I installed NFS, NIS, AUTOFS - but I can't be 100% sure.

Rgds
Chris

---

### Post by chrislynch8 on 2010-05-12
An update on this.

Everything is running correctly until I install NIS. Even if I stop NIS before even setting it up and then try to restart shorewall

sudo /etc/init.d/shorewall restart

It will take so long that power down the server and booting it back up is faster. But before I install NIS the shorewall would restart in a couple of seconds. I cannot see anything in the logs to suggest a problem

Rgds
Chris

---

