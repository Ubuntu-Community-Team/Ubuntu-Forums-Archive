---
title: "Ubuntu 14.04 on Surface Pro 2: What do I need to know beforehand?"
date: 2014-03-17
forum: Ubuntu Development Version
---

### Post by Nickolai_Leschov on 2014-03-17
I'm going to receive a Microsoft Surface Pro 2 tablet/laptop and use it with Ubuntu 14.04 (I'll be installing it after Final Beta release).
There are horror stories on the internet about trying to dual-boot on UEFI systems:
[**Before you Dual Boot - The truth about MS, OEM's & Linux**]("http://www.eightforums.com/installation-setup/19739-before-you-dual-boot-truth-about-ms-oem-s-linux.html") ([Hacker News discussion]("https://news.ycombinator.com/item?id=7409166"))

To avoid all trouble, what do I need to avoid trouble when my Surface arrives?

In particular:
[LIST=1]
[*]do I need to switch to BIOS mode (or can I)?
[*]do I need to use a different boot manager from the one that gets installed by default (GRUB, I believe)
[*]do I need to use 64-bit OS? Presently, I feel no need to, and use 32-bit one.
[/LIST]

---

### Post by oldfred on 2014-03-17
There are several other threads on Surface Pro.

[http://ubuntuforums.org/showthread.php?t=2183946&highlight=surface+pro](http://ubuntuforums.org/showthread.php?t=2183946&highlight=surface+pro)
[http://ubuntuforums.org/showthread.php?t=2209247&highlight=surface+pro](http://ubuntuforums.org/showthread.php?t=2209247&highlight=surface+pro)

I would not expect with a Microsoft based hardware system that everything will work. Microsoft will not offer any help and since few users will use Linux the developers are not devoting much effort to separate development of drivers. Only if something is generic enough to be common would it perhaps work.

       [http://linux.slashdot.org/story/12/12/30/2340208/why-linux-on-microsoft-surface-is-a-tough-challenge](http://linux.slashdot.org/story/12/12/30/2340208/why-linux-on-microsoft-surface-is-a-tough-challenge)

---

### Post by grahammechanical on 2014-03-17
I have not found Trusty Tahr to be easier or harder to install than 12.04 or 13.04 or 13.10. The same warnings apply as with any attempt to dual boot with a Microsoft OS. There are many threads about this as well as wiki pages like this one.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Note these comments:

>  [COLOR=#333333][FONT=Ubuntu]Having a PC with EFI firmware does not mean that you need to install Ubuntu in EFI mode. What is important is below: [/FONT][/COLOR]

[LIST]
[*=left]if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer are installed in EFI mode, then you must install Ubuntu in EFI mode too.
[*=left][FONT=inherit]if the other systems (Windows, GNU/Linux...) of your computer are installed in Legacy (not-EFI) mode, then you must install Ubuntu in Legacy mode too. Eg if your computer is old (<2010), is 32bits, or was sold with a pre-installed Windows XP.[/FONT]
[*=left]if Ubuntu is the only operating system on your computer, then it does not matter, you can install Ubuntu in EFI mode or not.
[/LIST]
>  [COLOR=#333333][FONT=inherit]Use a 64bit disk of Ubuntu ([/FONT][/COLOR][Ubuntu32bit cannot be easily installed in UEFI mode]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555")[COLOR=#333333][FONT=inherit])[/FONT][/COLOR]

I have not noticed any information on this forum to indicate that the advice given is no longer accurate.  You will soon have a reason to use the 64bit Ubuntu. I did not follow this thread of yours. 

[http://ubuntuforums.org/showthread.php?t=2209247](http://ubuntuforums.org/showthread.php?t=2209247)

I doubt very much if the Ubuntu developers are targeting specific devices unless it is a personal project or part of a general trend. I cannot agree with this statement of yours:

> [COLOR=#000000]I understand that Canonical is focused on accommodating this class of devices (that's what they ditched perfectly fine Gnome 2 for, right?) [/COLOR]

It was the Gnome organisation that ditched Gnome 2 because they did not think that it was "perfectly fine." They saw limitations in it and switched development to Gnome 3 desktop environment and Gnome 3 shell user interface.

The Canonical developers had their own ideas about what a user interface should look and work like and when they found that the Gnome developers were not receptive to their ideas they chose to put Unity as a replacement to Gnome shell and not just as an extension of Gnome shell.

Regards.

---

### Post by espectalll123 on 2014-04-26
I tested Ubuntu 14.04 on my Surface Pro 2. It's **smooth**, but I can't get my Type Cover to work. Also, the Wi-Fi drivers don't come by default, so you'll need an Ethernet adaptor for the installation. And by installing Ubuntu (alongside Windows or formatting the hard disk) you void your warranty, so you have to be REALLY sure that you want to install it.

---

### Post by javispedro2 on 2014-04-26
Type covers can be get to work, just read the other Surface Pro threads.
> **espectalll123 said:**
>  And by installing Ubuntu (alongside Windows or formatting the hard disk) you void your warranty, so you have to be REALLY sure that you want to install it.
You don't. Where did you hear that? Why would that EVEN happen? Just search nearly _any_ other thread in this forum for counterexamples.

---

### Post by Elfy on 2014-04-27
If you have issues with released versions of Ubuntu then use the main support forums not the development one. 

Closed.

---

