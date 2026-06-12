---
title: "Help me with choosing the right OS"
date: 2015-11-01
forum: Ubuntu, Linux and OS Chat
---

### Post by ivan109 on 2015-11-01
Hello,

I'm a new Linux user and i need a linux OS that has drivers for my PC
Here are my spec:
CPU - Intel Core 2 Duo E4500 @ 2.20GHz
RAM - 2,00GB Dual-Channel DDR2 @ 266MHz
GPU - 512MB ATI Radeon X1600/1650 Series
Motherboard - ASUSTeK Computer INC. P5GC-MX

Thanks

---

### Post by Shane_Carmichael on 2015-11-01
I would say your top linux os options are ubuntu, linux mint, Redhat and openSUSE. Not necessarily in that order. Ubuntu 14.10 has user-level container control which allows for greater security as users can run the containers with assigned superuser privileges. It also has one of the best GUI and most functionality out of the box. Like Ubuntu, Linux Mint 17 will come preloaded with all your day to day work and personal application. But Mint 18 isn't going to be released in 2016, so you may want to wait. If you are looking for an RPM-based distro, I would go with Redhat or OpenSUSE. TechRadar has a great article on the recommended top 12 Linux OS with the specs: [http://www.techradar.com/us/news/software/operating-systems/best-linux-distro-five-we-recommend-1090058](http://www.techradar.com/us/news/software/operating-systems/best-linux-distro-five-we-recommend-1090058)

---

### Post by ivan109 on 2015-11-02
I tried Linux Mint 17 but the graphic driver didn't work...I'm playing Leagu of Legends and had 15FPS usualy i have 80 on Windows...if somehow i can fix that i would go back on Mint 17 but i dont think i can. So i'm searchig for a linux OS that has everything that i need ;)
Thanks for the help

---

### Post by coffeecat on 2015-11-02
@ivan109, you posted this thread in the Mint sub-forum which limited you to technical support for Mint only, and would mean that many who could give you good advice may not have seen your thread. So I've moved this to the Ubuntu, Linux and OS Chat forum where you should get more thread views and possibly help.

That graphics card is about 10 years old, isn't it? That would mean that you can't use the AMD proprietary driver and would have been using the open source radeon driver. Whatever distro you use, you are going to be relying on the open source driver, the only difference from distro to distro would be the version of the Linux kernel used.  I'm no expert on AMD graphics cards and drivers, but I doubt you'll ever get the performance you need for League of Legends in a Linux-based OS with that particular card. If your need is to play League of Legends in a Linux-based OS, I suggest you consider replacing that old card. But whether you can find a suitable one for your motherboard, I don't know. Hopefully someone will be able to advise you.

---

### Post by ivan109 on 2015-11-02
Thanks for moving the thread, that was my bad...I hope someone know the answer ;)

---

### Post by Bucky Ball on 2015-11-02
You can try any of them from a Live session, meaning, from the install media, USB or DVD. Most of the flavours should work on those specs (perhaps start with lighter ones), but as coffeecat mentions, graphics won't be spectacular.

Download the ISO, create a bootable USB or disk, boot from it, choose 'Try *buntu'. That way you can test Xubuntu, Lubuntu, Ubuntu Mate, and others with installing to hard drive or changing your hard drive. Here are a few useful links:

Get Ubuntu:
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

Xubuntu:
[http://xubuntu.org/](http://xubuntu.org/)

Lubuntu:
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

Install Ubuntu:
[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

See what you like, what works best, then install. Good luck. :)

---

### Post by mastablasta on 2015-11-02
> **ivan109 said:**
> I tried Linux Mint 17 but the graphic driver didn't work...I'm playing Leagu of Legends and had 15FPS usualy i have 80 on Windows...if somehow i can fix that i would go back on Mint 17 but i dont think i can. So i'm searchig for a linux OS that has everything that i need ;)
Thanks for the help


suggest you use Windows for Windows stuff.

x1600 is not supported. well in fact the X series from AMD are really hit or miss with opensource drivers for some reason.

if you need Linux for study or some school work install Lubuntu in virtual box and avoid the pain. or if it's a desktop replace the GPU and it Will fly. you can use something like nVidia GT 730 or maybe even Radeon R7.

though that chip should have full support: RV530/RV560                 Radeon X1600/X1650/X1700
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

perhaps for some reason it doesn't have it. hard to say what goes wrong.

you can start troubelshooting in hardware section if you wish. you Will need to post output of this for starters:

> 
To look for boot messages/errors, check ```
dmesg | egrep 'drm|radeon'
```To see your OpenGL information, you can run the commands below. Make sure your OpenGL renderer string does not say "software rasterizer" or "llvmpipe" because that would mean you have no 3D hardware acceleration: 

```
sudo apt-get install mesa-utils
LIBGL_DEBUG=verbose glxinfo
```



then you can do some testing using maybe with glmark2 to see what goes wrong.

in any case for Windows programs, Windows is still the best option.

---

### Post by grahammechanical on 2015-11-02
I am using an Asus P5B Delux with a built in Asus WiFi adapter. It has an Intel Core 2 Duo 2.40 GHz CPU. I installed Ubuntu in 2007 and everything worked out of the box. And I have run every version of Ubuntu since then on this machine. And all the hardware is detected and drivers installed.

I use Nvidia not ATI. You will find that the open source video driver works fine. Keep in mind that the latest proprietary video drivers may not support that older video adapter. If you want a proprietary video driver than you may need to install a legacy (older) driver that is in the Ubuntu repositories. The Additional Drivers utility will take care of that for you.

But you will also notice as I did that a video adapter with 512 MB of  its own memory is just not good enough for modern Ubuntu with its need  for hardware accelerated 3D rendering. I now have an Nvidia card with  1GB of its own memory and that is able to keep up with the latest  versions of Ubuntu.

So, you may need to consider Lubuntu, Xubuntu or Ubuntu Mate. But as for drivers, I do not see any problems. Unless, they come from your choice of WiFi adapter. Problems with drivers come for those who want to install Linux on the very latest hardware.

Regards.

---

### Post by ivan109 on 2015-11-02
Thank you all for helping me out....i think i'll upgrade the GPU so i don't have any problems in the future...you can mark this threat closed if you want.
Thanks again! ;)

---

### Post by night_sky2 on 2015-11-02
Xubuntu 14.04 would be a perfect fit for this hardware. But that's no gaming machine though..

---

### Post by Bucky Ball on 2015-11-02
> **ivan109 said:**
> ...you can mark this threat closed if you want.
Thanks again! ;)

We don't close 'em. Please see the first link in my signature and mark the thread as solved. Thanks.

---

