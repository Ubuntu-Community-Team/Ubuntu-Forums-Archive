---
title: "Unattended-upgrades"
date: 2017-09-06
forum: Server Platforms
---

### Post by george.ene on 2017-09-06
Hi There, 

I have been searching around but have not had much success to date regarding unattended upgrades. 

The environment I am looking at managing has its prod + dev instances of more or less the same ubuntu 14.04 boxen. 

The aim is to install all security patches only in a staggered fashion; IE Dev machines on the first monday or the month, Prod on the second monday, so to avoid any obvious problems around dependencies, kernels acting up and the like. 

It seems the majority of the configs do not address scheduling per se, but rather choose to roll these our on a nightly basis. Great for home, but not so much for enterprise level. 

Has anyone managed to get something similar to the above implemented?  And if so, would you be willing to share your /etc/apt/apt.conf.d files as a guideline?


Many thanks in advance, 
George

---

### Post by mastablasta on 2017-09-06
man cron
or cron-apt

in other words this is defined in the cron task.

no doubt you read this: [https://help.ubuntu.com/community/AutomaticSecurityUpdates](https://help.ubuntu.com/community/AutomaticSecurityUpdates)

this also holds some useful info: [https://wiki.debian.org/UnattendedUpgrades](https://wiki.debian.org/UnattendedUpgrades)

basically schedule as you want it in cron.

it might make sense to only be notified on production machines that they require the upgrade rather than going throough it automatically. although security patches shouldn't cause issues on LTS. and if you installed the first verison of 14.04 the kernel stays the same with only security patches added. 

i will let business users/admins comment on when is best to apply security patches. 1 week seems a long time. just today i read abotu security flaw in one of apache components. they said it is so easy to exploit and you can take over the whole OS that it iwll be abused within minutes of releasing it. while i can not say if this is true (i guess it is if the security experts says so) i will tell you that my website got hacked within about 8 hours after they release the information regarding the exploit. the devs didn't patch the plugin on time and at the time i wasn's notified and didn't have an update system. so my web site server started spamming people all over the world. i had to restore it all from a very old backup. taught me a lot regarding importance of a good regular backup :)

---

