---
title: "Performed package updates, now cannot connect to server"
date: 2016-05-12
forum: Server Platforms
---

### Post by biggyk on 2016-05-12
Moved into a new house but all same equipment. I finally got around to getting my home network setup and accessed my server to do updates. The updates went fine using webmin and then rebooted. Now it seems like the server lost connection. I cannot access webmin or use ssh. I have rebooted a couple times, even changed the cat6 cable just in case. My router does not see it in connected devices. Im not sure where to turn, I dont have a spare monitor around anymore to plug in.

---

### Post by darkod on 2016-05-13
Unfortunately the only thing you can do now is connect a monitor and keyboard and check what is going on. Spare or no spare, get it from your desktop.
Webmin? I'm not saying webmin did this, but it is not a recommended and supported tool. Try to get rid of it and use ssh.

---

### Post by Bashing-om on 2016-05-13
biggyk; Hello ;

Release 14.04 ? AND have the GUI network-manager installed on this server ?
Maybe then see if you too are a victim of the update bug :
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1539634](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1539634)

[INDENT][INDENT]maybe yes ?
[/INDENT][/INDENT]

---

