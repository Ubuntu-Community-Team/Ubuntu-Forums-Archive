---
title: "What Port/s does Flash Player use?"
date: 2013-04-02
forum: Security
---

### Post by ScousaJAY on 2013-04-02
hi everyone, 

i have been having issues with flashplayer on windows for a few weeks now and i need to watch a live stream today, but after switching to my linux OS, i just realised that UFW is preventing me from viewing it.  i was just wondering if anyone could tell me the ports that flash uses so i can add the rules to UFW in linux. 

thanks for your time :)

---

### Post by Frogs Hair on 2013-04-02
The default setting in UFW allows all connections unless you have created a rule and in that case you would know what rules you have created and which to change .The following  page includes some basic UFW commands which are still applicable. [https://help.ubuntu.com/8.04/serverguide/firewall.html](https://help.ubuntu.com/8.04/serverguide/firewall.html)

---

### Post by kungfupete on 2013-04-04
interesting, I have never had any issues with ufw and flash.  have you ran netstat to list the ports while running whatever flash sites you are having issues with?

---

