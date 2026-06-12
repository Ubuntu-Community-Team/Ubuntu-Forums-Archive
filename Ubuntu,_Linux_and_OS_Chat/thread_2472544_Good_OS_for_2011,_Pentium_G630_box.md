---
title: "Good OS for 2011, Pentium G630 box"
date: 2022-03-02
forum: Ubuntu, Linux and OS Chat
---

### Post by breakdaze on 2022-03-02
let's chat about Linux OS, or any other. I have an old Acer x2610, 2GB RAM, 160GB SSD, Pentium G630 Sandy Bridge. Small case and motherboard. Lubuntu wouldn't install. What Linux/GNU or other OS would you personally try on this thing? Not a support question, just an opinion survey. Looking to try another distro. Maybe I'll try a BSD. I've ran OpenBSD before. Thanks.

---

### Post by QIII on 2022-03-02
Bodhi Linux would probably work.  Don't know how fast it would be ...

[System Requirements]("https://www.bodhilinux.com/w/system-requirements/")

---

### Post by guiverc on 2022-03-02
Outside of Lubuntu (*or a Ubuntu base system*) my next choice would be Debian GNU/Linux.

Lubuntu is using the `calamares` installer; which I find a little *fragil**e* myself, so if you're having issues with that and want to give Ubuntu a real try (*including Lubuntu*), I'd just use an ISO that has the `ubiquity`installer to see if that works, then switch your install to a Lubuntu/LXQt one post-install.

I can explain more if you don't know what I mean, but my current Lubuntu/Xubuntu install on

```
lenovo thinkpad sl510 (c2d-t6570, 2gb ram, i915)
```

I think I used a Xubuntu ISO on which I added `lubuntu-desktop`... I use the box last install for purposes of a Xubuntu RC QA (*Release Candidate Quality Assurance*) test as we'd completed the Lubuntu ones; and as I like Xubuntu; and would have added that desktop anyway to the system - I just used Xubuntu's ISO for my install.  It was my own box; I'd not backed up my data & was using it for a non-destructive install; and I trust `ubiquity` (*more than `calamares` actually!*)


*Anyway back to what distro...*

I still use numerous x86 or 32-bit *i386* boxes with only 1GB of RAM (& more), and whilst I do have one with Lubuntu 18.04 LTS on it, most just have Debian installed (the version varies on hardware; inc. 10 (*Buster*), 11 (*Bullseye*) & 12 (*Bookworm*) with I think two really old IBM Thinkpads still running 9 (*Stretch*) as I get better onscreen graphics performance with the older kernel found in *stretch* for those 2004 devices.

I QA-test Debian too (*though not as extensively as Ubuntu*) using the same hardware I use for Ubuntu; and I've only found *one *box (of ~25) where Lubuntu out performed it (*a really old & under-powered celeron from 2003; it just wasn't fun enough to use for me to explore why..*).  *On most boxes Debian & Ubuntu (or flavor) are ~equal.*

[B]I'd use Debian GNU/Linux; in fact I do :P
[/B]
FYI:  I'd not use Debian 9/Stretch; it's EOL in a few months; and I'll be kicking my two remaining installs to 10/Buster, as I know it works on them (I've already tried), I just felt 9/Stretch ran a little better for me, which is why they're still currently on 9/Stretch.


If you want to try BSD's you're welcome to; but I find they're a lot more work, especially getting hardware to work... I shifted to GNU/Linux as it was just *easier*.


All GNU/Linux I tend to find pretty equal; I'm using Lubuntu *jammy* currently as I am maybe 70% of my day as this is my primary box; but I'm often using more Debian if I count the number of boxes I use in a day. I have Fedora, OpenSuSE here too; but my preference would be Ubuntu/Debian.  

I can't say I'm a fan of *installers* which I gather is your issue, each has it's quirks & limitations, but given how different all the hardware we want to them to work on is; it's not really an easy job for developers I assume. I've already stated I find `calamares` a touch *fragile*... I'm not a *fan* of any of them, I just have more experience with `ubiquity`than others so maybe can better use it (*detect it's warning signs & know what to do, what **not ***to do*)*.  I'm not aware of any *installer *that stands out as *better* than others.

---

### Post by tea for one on 2022-03-03
Assuming your PC is 64bit, here are a couple of suggestions:-

Ubuntu based - [https://unit193.net/xubuntu/core/](https://unit193.net/xubuntu/core/)
Debian based - [https://peppermintos.com/guide/downloading/](https://peppermintos.com/guide/downloading/) (PeppermintOS-amd64.iso rather than the Ubuntu-based Peppermint 10 Respin)

Both these distros are minimal installations and the user will have to decide which packages to add.
For example, neither a media player nor browser are in the installation ISO.

---

### Post by breakdaze on 2022-03-03
Thanks for the suggestions. I might try all of those, also I had my eye on Slackware. Yes a Pentium G630 is 64bit.

---

### Post by GhX6GZMB on 2022-03-03
> **breakdaze said:**
> Lubuntu wouldn't install.

What exactly does this statement mean? If Lubuntu won't install, then Ubuntu, Kubuntu, Xubuntu, Mate etc. will also not install.

My 2008 HP/Compaq has no problem installing and running Lubuntu 20.04. Very fast, in fact. But you need to tickle the BIOS a bit.

---

### Post by breakdaze on 2022-03-03
I think you're mistaken. Ubuntu uses the ubiquity installer, while lubuntu uses calamares. It runs the live USB for either, but the installer failed due to a bug. See here for the discussion. Bug exists upstream in calamares. [https://ubuntuforums.org/showthread.php?t=2472438](https://ubuntuforums.org/showthread.php?t=2472438)

Also, saying stuff like "it worked fine for me isn't helpful."

Also, did I say that I ever installed any Linux on this box? I have not ever installed any OS whatsoever on this box, only ran live USB sessions. 

This Acer doesn't have BIOS, it has UEFI firmware. Saying UEFI BIOS is not a correct statement. UEFI and BIOS are different firmwares.

---

### Post by breakdaze on 2022-03-07
Well, I installed Slackware no problem on my system. It has a no frills but capable TEXT based installer, and allows you to set any mount point you like. Too bad the calamares is so fickle, and under the latest testing version of Lubuntu, does not allow a /boot mount point. This is Linux, not Windows, so I'm surprised about things like this.

Anyway, the whole process of how to install Slackware was well documented in the readme files, and following those, everything went well, except I chose to use GRUB for the bootloader, and not ELILO.

This was mainly because my entire SSD is LVM and a PV and no partition table. So, I just boot the system from a USB pen drive with GRUB and a menu entry for Slack.

After logging in, I just do startx, and the KDE desktop starts. Everything seems to work so far, and the desktop looks sweet.

Minimum RAM for Slackware is 1 GB. Although, this old PC can take more, and it is relatively cheap, so I will probably upgrade it. They make a point to not release the next version until it's as ready as they can make it. I appreciate that mindset. Things shouldn't be rushed, and version numbers inflated as a result.

Anyway, Ubuntu is cool too, for ease of use and Live ISO stuff. I wonder if each flavor has a human manager, or...? Slackware was started by Patrick Volkerding in 1993, as you can read on Wikipedia. I think having someone to guide the vision and quality all these years, as well as experience really helps for a stable distro. It is important in tech to have the perspective of older, and experienced gurus, and the end result, the product if you will, can be that much more stable.

Anyway, I will try this for a while, and see how it goes. I want to do some C programming from this platform, and it should be fine for that.

I have another old fixed disk or two around, and I will also try some other distros, like those suggested above.

happy Linuxing to all!

---

### Post by him610 on 2022-03-07
You might take a look at Raspberry Pi OS for PC and Mac - [https://www.raspberrypi.com/software/raspberry-pi-desktop/](https://www.raspberrypi.com/software/raspberry-pi-desktop/)
Here is what they say,
> If you have an old computer that is no longer powerful enough to run a modern commercial operating system, try Debian with Raspberry Pi Desktop: it can often make the computer usable once more.
It is installed on an early Atom-powered Acer Aspire One ZG5 netbook (Bios date: 2008) with 1.5GB RAM. It works great, but one's expectations must be tempered with the fact it is an older less capable computer. 
I have also successfully installed Xubuntu on it in the past - maybe two or three years ago.

---

### Post by breakdaze on 2022-03-08
> **him610 said:**
> You might take a look at Raspberry Pi OS for PC and Mac - [https://www.raspberrypi.com/software/raspberry-pi-desktop/](https://www.raspberrypi.com/software/raspberry-pi-desktop/)
Here is what they say,

It is installed on an early Atom-powered Acer Aspire One ZG5 netbook (Bios date: 2008) with 1.5GB RAM. It works great, but one's expectations must be tempered with the fact it is an older less capable computer. 
I have also successfully installed Xubuntu on it in the past - maybe two or three years ago.

Now that's pretty cool!

I have an actual Raspberry Pi also, but had no idea this existed, thanks.

---

### Post by mastablasta on 2022-03-09
> **breakdaze said:**
> Well, I installed Slackware no problem on my system. It has a no frills but capable TEXT based installer, and allows you to set any mount point you like. Too bad the calamares is so fickle, and under the latest testing version of Lubuntu, does not allow a /boot mount point. This is Linux, not Windows, so I'm surprised about things like this.


server image, install what you want/need, then add lubuntu-desktop

---

### Post by breakdaze on 2022-03-09
> **mastablasta said:**
> server image, install what you want/need, then add lubuntu-desktop

Yup, I considered that. I'm sure it would work. I'm really liking Slack. Has a security mailing list, so I can apply patches daily.

---

### Post by mastablasta on 2022-03-10
> **breakdaze said:**
> Yup, I considered that. I'm sure it would work. I'm really liking Slack. Has a security mailing list, so I can apply patches daily.

unnatended upgrade will apply the patches for you. you can select 
1. security patches only
2. feature patches/app upgrades (bug fixes?!)

more here:
[https://help.ubuntu.com/community/AutomaticSecurityUpdates](https://help.ubuntu.com/community/AutomaticSecurityUpdates)


i have it set on server to check once a day and apply security patches only. it will send me an email saying it did the security patches and also let me know which other packages can be updated. 

on desktop it checks every day for updates and i install them myself. 

unfortunately the mini.iso seems to be no more. it was a preferred way of installing if you wanted to "create your own OS" by adding only things you need or want. for example i had a virtualbox install on Single core PC. you can imagine the hardware limitations. but i installed the mini.iso, then added a very light desktop manager and only the basic XFCE and the apps i needed for testing. it was running faster than native WindowsXP at the time. anyway the server image can replace it because when you run th einstall it will install only the very basic things. verythign else then has to be added by tasksel or apt. at leats i think they still use tasksel. it's been a while since i used the server image.

more on Tasksel:
[https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel)

by the way, i know this is not always possible but adding more RAM can really be a good thing. i had this E-450 netbook that crawled with 2 GB ram it came with (that and windows 7 starter that was limited to max 2 GB ram). anyway i had to reactivate it for my kids online school, and the "suffered" it being slow to load anything. so i filled it with max it could take - 8 GB. it had Kubuntu on it. and let's juts say it now really is a descent internet laptop that can also play some old games (L4D, HL2...). my Single core desktop box had 4 GB ram and Athlon 3200 with a 2 GB GPU. it worked (well actually still works) quite fine but it started showing it's age with some games and you tube stuff. so i got a bit annoyed and did an upgrade. but sufficient RAM is what kept it going. i think i might change it into media PC as it never had any issues playing movies and such.

---

### Post by ajgreeny on 2022-03-10
A ***mini.iso*** is still available if you want to go down that road.
[http://archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/current/legacy-images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/current/legacy-images/netboot/mini.iso)
I have not used that installation method for a very long time, probably about 8 years, but it worked then, allowing me to install a very lean system using just a window manager, not a full DE.

As that mini.iso image is for 20.04, I imagine you will be able to upgrade to 22.04 in a couple of months if you want to try that, though I have never done this personally, always clean installing.

---

### Post by breakdaze on 2022-03-11
Thanks for the details everyone. 

What about Ubuntu appeals to all of you, as opposed to any other distro?

Ubuntu is actively developed, but so are others.

Just curious.

---

### Post by QIII on 2022-03-11
> **breakdaze said:**
> What about Ubuntu appeals to all of you, as opposed to any other distro?


This community.

But I also use Fedora about as much.

---

