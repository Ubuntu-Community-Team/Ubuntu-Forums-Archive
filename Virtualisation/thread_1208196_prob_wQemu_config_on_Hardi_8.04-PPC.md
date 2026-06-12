---
title: "prob w/Qemu config on Hardi 8.04-PPC"
date: 2009-07-08
forum: Virtualisation
---

### Post by magnussin on 2009-07-08
I've been dabbling with dual booting ubuntu on and off for several years now. Now I'm comfortable and ready to get serious. I have installed Hardy Heron 8.04 onto my iMac G5 with PPC architecture about six months ago.

 My other Computers are Windows Machines and I am quite fond of certain games like Civ4, Spore, and Halv Life(#1). The other machines are often occupied by the wife and kids (they don't understand the appeal of Ubuntu). I've had few problems I couldn't figure out, work around, or find an alternative to by reading forums and the community docs.  

Anyhow, the reason I posted this, I'm trying to install Qemu as per the instructions at, 

[https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo]("https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo")

and have hit a stumbling block at step #5.
 
---Change the content of /etc/modprobe.d/kqemu.conf to 

```
options kqemu major=0
```

I can't find the file /etc/modprobe.d/kqemu.conf in order to edit it. 

Have I done something wrong? I gone over the steps several times and can't seem to find the problem. Any help you can provide, advise to give, or wisdom to share would be much appreciated. It is very irritating when given step by step instructions to accomplish a task and the results don't jive with expectations. But alas, such is the way of the newbie learning curve.

Thank You for you time,

Magnussin.

---

