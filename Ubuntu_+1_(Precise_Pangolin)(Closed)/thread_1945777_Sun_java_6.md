---
title: "Sun java 6?"
date: 2012-03-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ELD on 2012-03-23
Is there any way to get the official sun java 6 on 12.04 for games like Minecraft? Doesn't work with openjdk or java 7

---

### Post by QIII on 2012-03-23
I recommend the following:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

I've tested it on Precise.

---

### Post by sammiev on 2012-03-23
> **QIII said:**
> I recommend the following:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

I've tested it on Precise.

Test and confirmed working on Precise as well. :)

---

### Post by QIII on 2012-03-23
Ha!  Beat you this time, sammiev!

---

### Post by dino99 on 2012-03-23
> **ELD said:**
> Is there any way to get the official sun java 6 on 12.04 for games like Minecraft? Doesn't work with openjdk or java 7

ferramroberto/java ppa have jre6

---

### Post by JMB74 on 2012-03-23
This also works for precise.

[https://github.com/rraptorr/sun-java6](https://github.com/rraptorr/sun-java6)

I've created by own .deb packages via that to install 6u31.

---

### Post by JMB74 on 2012-03-23
> **dino99 said:**
> ferramroberto/java ppa have jre6

No build for precise, and the oneiric ones are very very outdated.

I don't think there will be any new PPA builds allowed now, due to the changed java licensing.

This guy had his ppa pulled by Canonical. :(

[http://blog.flexion.org/2012/01/10/updated-sun-java6-packages-for-ubuntu/](http://blog.flexion.org/2012/01/10/updated-sun-java6-packages-for-ubuntu/)

---

### Post by sammiev on 2012-03-23
> **QIII said:**
> Ha!  Beat you this time, sammiev!

LOL and +1 boss!

---

### Post by craig10x on 2012-03-23
This was posted in the linux mint forums (see link) and it works great for ANY debian based distro (i have it installed on my ubuntu 11.10) it's a prepackaged deb file that installs it automatically...you just have to copy and paste each line and hit enter in the terminal (4 lines in all) one at a time of course....

It also shows a terminal command (1 line) that will always bring in the latest version (after you have done the initial install)...

[http://forums.linuxmint.com/viewtopic.php?f=42&t=93052](http://forums.linuxmint.com/viewtopic.php?f=42&t=93052)

this is not distro or ubuntu version specific...will work on anything!  I even installed it on a live session i ran of ubuntu 12.04!!!  easy as pie...

---

### Post by xajeiw9I on 2012-03-24
I am wondering why the open source Java is incompatible with those games. It does not make sense. Is it still a work in progress, that is why?

---

### Post by craig10x on 2012-03-24
open source version of java tends to work with many programs but it seems that it doesn't work on all programs or not always as well...i would imagine the coding must be somewhat different so it must cause incompatibility problems with some applications...

---

### Post by xajeiw9I on 2012-03-24
I recall reading something about Sun/Oracle complying Java with the OpenJDK. Can we expect applications to be updated to work 100% with it from now on?

---

### Post by craig10x on 2012-03-24
> **xajeiw9I said:**
> I recall reading something about Sun/Oracle complying Java with the OpenJDK. Can we expect applications to be updated to work 100% with it from now on?

That is what they (oracle) is claiming about version 7 (which is still in beta) but i tried the open source (jdk) version of 7 and the program i use that needs java runtime did not work any better under 7 then it did under 6....

As soon as i installed the Oracle (licensed) version....all was well... ;)

So to my observations, i am not seeing that so-called 100% compatability...

---

