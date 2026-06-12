---
title: "Ubuntu proves the greatness of linux"
date: 2007-09-25
forum: Testimonials &amp; Experiences
---

### Post by blackcp on 2007-09-25
I've been trying Linux for a bout month and a half. I started off with Vector Linux 5.8 standard gold, but at some point I thought to learn about Linux, Ubuntu would be better since it is easier. During that time was the first time I ever did disk partitioning.

Why did I want to venture into the world of Linux anyway? I wanted to see out of curiousity. I didn't want to get vista that's for sure. I wanted to see a world outside of microshit. 

I did have a few rough starts with ubuntu, but the forums made a huge differance in helping with my installation. That and I'm also willing to learn about Linux since I want to develop some programming skills. What better way than Linux even though you don't have to be a programmer to use it. But if you are than more power to you. =)

\Ubuntu has served me pretty well. The only reason I even have windows xp still in my system is because I don't know how to properly get my dell a940 all in one scanner function working. The printing part of it is obsolete (hardware issue) even under xp. 


I like how linux just keeps getting better with hardware support. I was able to get my Kodak digital camera import photos to my computer under Ubuntu without the need for the software cd that came with the digital camera. I won't even bother to try it on xp anytime soon. 

And plus I dig gpl. 

The only issues I have are installing software that isn't in the repositories, And using anti-virus protection (updating it particularly) but I got patience to sort it out. I'll post any help in other appropriate threads since this is about testimonials. 

From the way I look at it, the more skilled I become with Linux, the less I will need microshit. Thankfully, there's Wine.

---

### Post by scrooge_74 on 2007-09-25
Good to hear you came to the light :)

On the issue of software installing, if you enable the other repositories chances are you will find like 99% of what you need there. As for anti virus, you can also install from the repositories so your friends dont get a virus from you (which you probably will resend by mistake), but you are safe from those nasty viruses for MS systems.

Keep learning, you will be amaze all the things  you can do

---

### Post by sstusick on 2007-09-25
What I like the most about Linux is... there is no need for bloated Microshit drivers. I plugged in my printer and within 30 seconds I was printing with it.. true plug and play. I didn't have to wait the 10 minutes for the HP software driver to load 300 MB's of junk onto the PC. Though I did come up with a way to bypass this on Windows, but still, the size of most Windows software is ridiculous, and the average user isn't going to do what I did just to install the necessary driver. The idiots who write these drivers/software should make an option "Install necessary Drivers Only."

 My evdo, which I use for internet, was enabled with a small script that took less time to configure than it would to have installed the Verizon bloatware driver+software on Windows. That is if you're lucky enough to have the VZ software recognize their own card, if not, you have to reboot.

Overall, my hardware works better on Linux than it did on Windows, and I am very pleased :-D

---

### Post by ukripper on 2007-09-26
CLAM AV is really good antivrus which will protect your friends Windows PC to receive any virus or trojan from your side but won't affect your system. That is one of million selling point of Linux, mind it but for free.

Here is good tutorial forthat -
[http://ubuntuforums.org/showthread.php?t=30060](http://ubuntuforums.org/showthread.php?t=30060)
[https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)

---

### Post by wolfen69 on 2007-09-26
glad to hear you like it. do this for more package choices:
open terminal:
```
gksudo gedit /etc/apt/sources.list
```
add the following 2 lines:
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

then:
```
sudo apt-get update
```
you will now have many choices in synaptic.
peace. have fun.

---

### Post by blackcp on 2007-09-26
> **ukripper said:**
> CLAM AV is really good antivrus which will protect your friends Windows PC to receive any virus or trojan from your side but won't affect your system. That is one of million selling point of Linux, mind it but for free.

Here is good tutorial forthat -
[http://ubuntuforums.org/showthread.php?t=30060](http://ubuntuforums.org/showthread.php?t=30060)
[https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)

Everytime I enter a command to upgrade clam via "freshclam" (without quotes) I get this:

blackcenterpoint@blackcenterpoint-desktop:~$ freshclam
ERROR: Can't open /var/log/clamav/freshclam.log in append mode (check permissions!).
ERROR: Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log).

To Wolfen69, 

When Enter the first listed command, am I supposed to space before I enter the following lines? 

I tried that and a test list came up in a separate window. Am I supposed to save it? Or close without saving it?

---

