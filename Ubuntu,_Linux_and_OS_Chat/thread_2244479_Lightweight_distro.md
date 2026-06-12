---
title: "Lightweight distro ??"
date: 2014-09-16
forum: Ubuntu, Linux and OS Chat
---

### Post by dylan0005 on 2014-09-16
hi everyone

I wold to know about a lightweight distro that has LibreOffice, Good browser, webcam manager and if it possible that runs portable programs  as simple as it. My truly problem is the Hard disk drive space... that's why I need a lightweight version. **Any suggestions?** Please let me know, I'd appreciate your answers.

---

### Post by grahammechanical on 2014-09-16
Please tell us the specifications of your computer as disk space might not be the only thing to consider. What CPU? How much memory (RAM)? What graphic adapter? How much of it own memory does it have? Or does it share system memory (RAM)? What other OS is installed? How much disk space can you give the OS? Ubuntu will install into less than 6GB.

These are the minimum system requirements for Ubuntu. Xubuntu and Lubuntu. As you can see, all three require 5 GB of disk space.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Regards.

---

### Post by endlessinstant on 2014-09-16
Assuming you have a system that was sold in the last ten years or so, you likely don't need to search any further than Xubuntu or Lubuntu to build a working system.  If you have something very arcane or oddball (Raspberry Pi for instance) you might want something smaller.  [Damn Small Linux]("http://www.damnsmalllinux.org/") is a great example of an ultra-light distro that would be used for specialty or old hardware.  

If you don't really need the extra software support made available by the Ubuntu repos, just go with an Xfce or LXDE build of Debian.   Debian stable is very heavily tested and has few bugs.  It doesn't typically use the most up-to-date software but you won't need that for basic office work anyway.  Debian takes very well to older systems and has the added advantage of using the *.deb package format that you are probably already familiar with if you are an existing Ubuntu user.

---

### Post by PondPuppy on 2014-09-17
If you can afford an 8 GB USB thumb drive you could also boot Porteus or Puppy. Once booted, both are quick; both can be installed as persistent so changes you make will be saved to the thumb drive.

---

### Post by robin7 on 2014-09-17
> **endlessinstant said:**
> 
If you don't really need the extra software support made available by the Ubuntu repos, just go with an Xfce or LXDE build of Debian.   Debian stable is very heavily tested and has few bugs.  **It doesn't typically use the most up-to-date software** but you won't need that for basic office work anyway.  Debian takes very well to older systems and has the added advantage of using the *.deb package format that you are probably already familiar with if you are an existing Ubuntu user.

And if you want the wonderful stability and reliability of lightweight Debian, but *also* want more up-to-date applications that are rigorously tested with older hardware in mind, have a look at [MX-14]("http://mepiscommunity.org/mx") - a project of AntiX with the Mepis community. It features the lightweight simplicity and elegance of the Xfce desktop, the awesomeness and rock-solid dependability and reliability of Debian, up-to-date applications, and a friendly, helpful community to support it. I wrote a little review of this wonderful ultralight distro [here]("http://technophobeconfessions.wordpress.com/2014/05/19/mx-14-mepis-magic-in-a-lightweight-xfce-distro/").

---

### Post by jerrylamos on 2014-09-17
I've had good luck with Lubuntu for a lightweight linux.  Comes with Firefox.  I prefer Libre Office to Abiword.  

As far as disk space, my pc's will boot from USB hard drives.  
I had some 2.5 inch lap top hard drives laying around, they're cheap anyway, used or new, ordered $10 usb hard drive cases from Amazon, away I go.  
The 40 GB hard drive has a couple 10 GB partitions for testing, a swap, and an archive partition.  
The rest are 80 GB hard drives, even a solid state one.  More room.

BTW, personal preference, I put Lubuntu's LXDE desktop launcher on the left side, adjust icon sizes, looks like unity.  Better in my opinion since I use transparent background for the icons & the wallpaper shows thru.  My monitors, built in or external, are wide screen so I've got more room on the sides.

Unity likes a panel at the top as well as a hide/unhide launcher usually on the left.

---

### Post by help_me2 on 2014-09-17
I vote for Lubuntu, or better yet a minimal install.

---

### Post by Stinger on 2014-09-18
[LXLE]("http://lxle.net/")
> [list]
[*]light on resources; heavy on functions.
[*]always based on ubuntu/lubuntu lts.
[*]uses an optimized lxde user interface.
[*]four familiar desktop layout paradigms.
[*]prudent full featured apps preinstalled.
[/list]
And the list goes on.. :)

---

### Post by Mike_Walsh on 2014-09-21
> **PondPuppy said:**
> If you can afford an 8 GB USB thumb drive you could also boot Porteus or Puppy. Once booted, both are quick; both can be installed as persistent so changes you make will be saved to the thumb drive.

I agree with PondPuppy on this one. I've been using 'Precise' Puppy 5.7.1 for quite a while now; the whole thing installs into RAM (so it's lightning fast!), and how on earth Barry Kauler and the Puppy team managed to cram the best part of 150 applications into about as many Mb is a minor miracle in itself. It'll answer all your requirements, with perhaps the exception of the browser....it uses Mozilla's 'SeaMonkey' (but it's based on Firefox anyway). If you specifically want Firefox, try Puppy 'Slacko' 5.7.....the most recent release. It uses Firefox 17 ESR; it's several releases old, but it's like the LTS versions of Ubuntu.....still supported, and still receives updates, so still secure.

The only other difference is that it uses the lightweight AbiWord, instead of Libre Office's Writer; but I don't know many people that use anything other than the word processor component of an office suite anyway.

As PondPuppy says (and I'll back this up), it'll install to a flashdrive.....so it will run on any computer that will boot from USB, and you can take it ANYWHERE with you. Unless that box happens to run Vista; then you'll not get it to run, try as you might.....Vista's a complete pain in the behind when it comes to letting anything else use its resources; I have personal experience of this. :p


Regards,

Mike.

---

### Post by Tar_Ni on 2014-09-21
If you have a hardrive of at least 10GB and 512MB of RAM I say go for Lubuntu. It works well on old hardware, you can easy remove Abiword and install LibreOffice. It comes with Firefox preinstalled but you can always install Chromium, Chrome, Midori or whatever you choose.

---

### Post by Mike_Walsh on 2014-09-22
> **Tar_Ni said:**
> If you have a hardrive of at least 10GB and 512MB of RAM I say go for Lubuntu. It works well on old hardware, you can easy remove Abiword and install LibreOffice. It comes with Firefox preinstalled but you can always install Chromium, Chrome, Midori or whatever you choose.

That's a good idea. The one snag with Puppy is it's not very easy to change applications; you run into all sorts of permission problems with the 'Rox-filer' file system.....it takes some getting used to. I don't know (since I've not been using Linux for very long), but I'm guessing  it's a bit more how Linux USED to be, before Canonical started making it easier for the masses to use.....more 'geeky', if you like. 

In other words, designed for people who KNOW what they're doing, and don't mind pulling their system apart and re-building it!

Lubuntu is about as simple as they come. I run it myself; it's bog standard, with the exception of adding Chrome (which I had in my 'Apps' folder from a couple of weeks ago for somebody else), Thunderbird, Skype, and Wine (so that I can run ONE graphics application that I just CANNOT find an open-source equivalent for)...and that's it.

I would thoroughly recommend it for beginners.

Regards,

Mike.

---

### Post by dylan0005 on 2014-09-25
Thanks to all for your suggestions I appreciate it.
I finally picked **Lubuntu 14.04 **It runs pretty well actually but I found out that Lubuntu has trouble when it comes to running portables programs and I have to execute them from the terminal because of the permissions. It's really tedious doing in that way if you know what I mean. 
Anyway if someone has a better idea to run portable programs faster than that I would appreciate it so much.

---

