---
title: "installing 16.04 LTS beta - is apt-get enough to get final?"
date: 2016-03-24
forum: Ubuntu Development Version
---

### Post by BeeOnRope on 2016-03-24
I'm looking to install Ubuntu on my new laptop and I'm an LTS kind of guy. So 16.04 looks like the version for me, since I want as long a window as possible before I have to upgrade versions. 

I'm traveling indefinitely on limited internet access, and as it happens it would be a great time for me to download 16.04 over the next couple of days. 

The downside, of course, is that 16.04 final is not out. What I'm curious about is if I grab whatever is out now for 16.04, eg final beta, will a simple apt-get upgrade bring me an equivalent install to installing the final .ISO once it is out - or do I need a re-install?

---

### Post by howefield on 2016-03-24
Thread moved to the "*Ubuntu Development Version*" forum.

You don't need to reinstall once 16.04 is released on 21st April - keep updating and you will get to the finished release.

Bear in mind that much will be done over the next few weeks and using a development release, even this close to the release date has it's potential risks.

---

### Post by grahammechanical on 2016-03-24
They are called daily ISO images because they are built daily. If you download the daily image from the 25th but install on the 30th and tick the box to install updates at the same time, then you will get the same as what is on the daily image built on the 30th. Or you can  install and run update manager afterwards and get the updates that way.

I have an install of 16.04 that I put in yesterday (24th) and another install that I put in at the start of the 26 week development period. They are both equal as to the code they have. And that is done by updating/upgrading the OS once it is installed and doing it regularly.

Regards.

---

### Post by Bucky Ball on 2016-03-24
> **howefield said:**
> 
Bear in mind that much will be done over the next few weeks and using a development release, even this close to the release date has it's potential risks.

+1. But give it this:
> 
sudo apt-get update
sudo apt-get dist-upgrade

... and, like the little red caboose, you'll get there in the end. ;)

Bear in mind that both 15.10 and the stable long-term support release 14.04 LTS are both upgradeable to 16.04 later in the year (and for 14.04 LTS, anytime til April 2017).

If you're after a bit of a learning curve with possible breakage, 16.04 LTS it is. If you'd just like to start using and getting to know Ubuntu, stick 14.04 LTS in there and upgrade to 16.04 LTS before 14.04 reaches end-of-life. LTS releases have five years support, everything else nine months. 

Good luck.

---

### Post by Skaperen on 2016-03-24
> **Bucky Ball said:**
> +1. But give it this:


... and, like the little red caboose, you'll get there in the end. ;)

Bear in mind that both 15.10 and the stable long-term support release 14.04 LTS are both upgradeable to 16.04 later in the year (and for 14.04 LTS, anytime til April 2017).

If you're after a bit of a learning curve with possible breakage, 16.04 LTS it is. If you'd just like to start using and getting to know Ubuntu, stick 14.04 LTS in there and upgrade to 16.04 LTS before 14.04 reaches end-of-life. LTS releases have five years support, everything else nine months. 

Good luck.

is that needed even on a 16.04RC install?

---

### Post by QIII on 2016-03-24
Yes.

And you need to keep doing that to keep your system updated thereafter.

---

### Post by Bucky Ball on 2016-03-24
Is what needed???

---

### Post by vasa1 on 2016-03-25
OP, please see [http://ubuntuforums.org/showthread.php?t=2318164&p=13459871#post13459871](http://ubuntuforums.org/showthread.php?t=2318164&p=13459871#post13459871)

---

### Post by BeeOnRope on 2016-03-25
> **Bucky Ball said:**
> +1. But give it this:


... and, like the little red caboose, you'll get there in the end. ;)


Thanks, that's what I'll do then.

> 

Bear in mind that both 15.10 and the stable long-term support release 14.04 LTS are both upgradeable to 16.04 later in the year (and for 14.04 LTS, anytime til April 2017).



My in-place major version upgrade experience (e.g., 12.04 to 14.04) has been pretty disastrous so far with Ubuntu. I have only ever ended up with a working system by doing a re-install from scratch. Furthermore, I want to install 16.04 now, since I won't have the capability to download all the binaries needed for a full install once I leave where I'm staying tonight. So I want do the bulk of the download here, and then selectively update stuff later, which should take less bandwidth.

> 
If you're after a bit of a learning curve with possible breakage, 16.04 LTS it is. If you'd just like to start using and getting to know Ubuntu, stick 14.04 LTS in there and upgrade to 16.04 LTS before 14.04 reaches end-of-life. LTS releases have five years support, everything else nine months. 

I'm actually a long-time Ubuntu user, even if my perhaps basic question belies that. I'm OK with being a bit unstable - I'm only going to be doing basic stuff for the time being. I'm running on fairly new hardware (Dell XPS 9550) where having the most recent kernel and related drivers is apparently pretty useful.

Thanks for all your help.

---

### Post by BeeOnRope on 2016-03-25
> **vasa1 said:**
> OP, please see [http://ubuntuforums.org/showthread.php?t=2318164&p=13459871#post13459871](http://ubuntuforums.org/showthread.php?t=2318164&p=13459871#post13459871)

Thanks - it seems like the summary for that thread is "it should work in theory, but in practice there has been a need for a fresh install from time to time". So I think I'll grab Beta 2 and cross my fingers that I can smoothly update it to final when the time comes.

---

### Post by grahammechanical on 2016-03-25
I have been running xenial xerus (16.04) as my daily driver since the first day of its 26 weeks development period. I have found it very stable. I have not had to re-install due to breakage. I would not recommend anyone using the development version of Ubuntu as their one and only Ubuntu without first warning them to expect breakage.

That being said, for a couple years now the official intention has been for the development branch to be stable enough for application developers to use it as a development platform. And I think that the Ubuntu developers have succeeded in this.

Regards

---

### Post by Skaperen on 2016-03-28
i can do *apt-get dist-upgrade* a few times but eventually i want a normal *apt-get upgrade* to keep my 16.04 LTS upgraded, including point releases as has been working on 14.04.X for me. is this doable starting with a 16.04RC fresh install?

---

### Post by Bucky Ball on 2016-03-29
> **Skaperen said:**
> i can do *apt-get dist-upgrade* a few times but eventually i want a normal *apt-get upgrade* to keep my 16.04 LTS upgraded, including point releases as has been working on 14.04.X for me. is this doable starting with a 16.04RC fresh install?

Makes no difference. dist-upgrade does it all. It has nothing to do with upgrading your installed version to a newer one so don't quite follow you.

dist-upgrade upgrades everything in your currently running install, including doing a 'apt-get upgrade' in the process. Six of one, half a dozen of the other. Even if you only use the upgrade command you should be running 'dist-upgrade' after it anyway if you want to be completely up to date, so think you might be misinterpreting what dist-upgrade does.

Open a terminal and type this in:

```
man apt-get
```

Scroll down the page a bit and under 'Description' all will be revealed.

```
dist-upgrade
           dist-upgrade in addition to performing the function of upgrade,
           also intelligently handles changing dependencies with new versions
           of packages; apt-get has a "smart" conflict resolution system, and
           it will attempt to upgrade the most important packages at the
           expense of less important ones if necessary. The dist-upgrade
           command may therefore remove some packages. The
           /etc/apt/sources.list file contains a list of locations from which
           to retrieve desired package files. See also apt_preferences(5) for
           a mechanism for overriding the general settings for individual
           packages.
```

dist-upgrade does it, but does it better. Always run 'apt-get update' before using either upgrade or dist-upgrade.

---

