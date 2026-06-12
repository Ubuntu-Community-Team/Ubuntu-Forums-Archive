---
title: "Running Ubuntu but says Trisquel"
date: 2017-09-21
forum: Ubuntu/Debian BASED
---

### Post by allanwatts87 on 2017-09-21
I recently ran an update and now when I boot up my boot up manager says I'm running trisquel linux. Is this supposed to happen? Is there a way to fix it? Should I even be concerned?

---

### Post by oldfred on 2017-09-22
Are you sure you did not install Trisquel?
It is based on Ubuntu, but not an official flavor of Ubuntu.

Post these:
lsb_release -d
cat /etc/*release

 [https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)

---

### Post by allanwatts87 on 2017-09-22
DISTRIB_ID=Trisquel
DISTRIB_RELEASE=6.0.1
DISTRIB_CODENAME=toutatis
DISTRIB_DESCRIPTION="Trisquel GNU/Linux 6.0.1, Toutatis"
```
DISTRIB_ID=Trisquel
DISTRIB_RELEASE=6.0.1
DISTRIB_CODENAME=toutatis
DISTRIB_DESCRIPTION="Trisquel GNU/Linux 6.0.1, Toutatis"
```

---

### Post by oldfred on 2017-09-22
Moved to Ubuntu based sub-forum.

Looks like you have Trisquel.

---

### Post by allanwatts87 on 2017-09-27
How can I get my screenfetch program to display Ubuntu then?

---

### Post by QIII on 2017-09-27
Hello!

Not sure what you mean by "screen fetch".  Do you mean what most people would refer to as a "splash screen"?

Since you are running Trisquel, not Ubuntu, wouldn't it be preferable to keep the Trisquel splash screen?

I haven't used Trisquel beyond trying it out, but I do believe there is a settings menu that lets one change the splash screen and greeter based on an image of your choice.

---

### Post by Frogs Hair on 2017-09-27
> **allanwatts87 said:**
> How can I get my screenfetch program to display Ubuntu then?

Screenfetch will dispaly the distribution you are running not that it is Ubuntu based.

---

### Post by QIII on 2017-09-27
Ah.  Then it is not likely that screenfetch can be made to return "Ubuntu" without modifying text in a config file, since it is gathering system info.

---

### Post by vasa1 on 2017-09-27
> **allanwatts87 said:**
> I recently ran an update and now when I boot up my boot up manager says I'm running trisquel linux. Is this supposed to happen? Is there a way to fix it? Should I even be concerned?
You'll have to be far more detailed about what you started with and what you did leading up to this update. 
> Is this supposed to happen?Not unless you've done something to make this happen.
> Should I even be concerned?That depends on you and your usage.
> Is there a way to fix it?We'll need to know exactly what you did ever since you installed whatever it is you've installed.

Regarding changing the name from Trisquel to Ubuntu... Why? At best, it's misleading to people trying to help you.

Regarding Screenfetch, we mostly prefer to have information sourced from the terminal provided as code between code tags so that others can readily pick what they want and repost those lines when replying to you. Many people like *inxi*.

BTW, you can get rid of the ASCII art by using "-n":```
$ screenfetch -n
 vasa1@aes-Inspiron-15-3567
 OS: Ubuntu 16.04 xenial
 Kernel: x86_64 Linux 4.10.0-35-generic
 Uptime: 1h 34m
 Packages: 2217
 Shell: bash 4.3.48
 Resolution: 1366x768
 DE: KDE5
 WM: KWin
g2bird [GTK2]
, g3bird [GTK3]
 Icon Theme: breeze
 Font: Ubuntu Mono
 CPU: Intel Core i3-6006U CPU @ 2GHz
 GPU: Mesa DRI Intel(R) HD Graphics 520 (Skylake GT2) 
 RAM: 1522MiB / 7851MiB
$ 
```

---

### Post by allanwatts87 on 2017-09-28
> **vasa1 said:**
> You'll have to be far more detailed about what you started with and what you did leading up to this update.
I remember running some sort of sudo apt-get remove command? I think it was to clean something up after I uninstalled a program.

> **vasa1 said:**
> We'll need to know exactly what you did ever since you installed whatever it is you've installed.
That's the problem, I didn't really install anything other than Ubuntu. It's an Ubuntu disk image I burned to a USB, and an Ubuntu installation I put on my disk partition. I honestly have no clue what I did and when.

> **vasa1 said:**
> Regarding changing the name from Trisquel to Ubuntu... Why? At best, it's misleading to people trying to help you.
I didn't think that was important, I apologize. I thought perhaps Trisquel was based off of Ubuntu, therefore I could just change the ASCII art and screenfetch info to Ubuntu since it would technically be true or something.

---

### Post by oldfred on 2017-09-28
These are the official flavors of Ubuntu that are Ubuntu.
[https://www.ubuntu.com/about/about-ubuntu/flavours](https://www.ubuntu.com/about/about-ubuntu/flavours)

Others based on Ubuntu then are not Ubuntu, but just based on Ubuntu. 
I believe legal requires all references to Ubuntu be removed.

---

### Post by mc4man on 2017-09-28
You either started with a 3+ year old Trisquel install or [migrated to Trisquel]("https://trisquel.info/en/wiki/migrate-ubuntu-trisquel-without-reinstalling"). It would appear 6.0.1 is based off of ubuntu 12.04
Sounds like a dead end any which way you look at it..

---

### Post by oldfred on 2017-09-29
Do you have two installs in your system and you switched boot to an older Trisquel?

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

And post this to list sources lists.
 find /etc/apt/  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;

---

### Post by iggar on 2017-12-29
Hello,

I had a similar problem and just fixed it. I've posted details here: [https://askubuntu.com/a/990616/767716](https://askubuntu.com/a/990616/767716)

I hope it helps.

---

