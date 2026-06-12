---
title: "What OS should I use?"
date: 2016-12-14
forum: Ubuntu, Linux and OS Chat
---

### Post by ozfer2 on 2016-12-14
So I am getting a new low-end compact laptop to bring around with me for portability. It is a lenovo N22 with 4GB ram and 64GB SSD with a 11.6' touchscreen. It comes with windows 10 but I really want to ditch it and use linux. 

This leads to my question of what OS should I choose? I was stuck between using Ubuntu(with LXDE), Mint, Lubuntu, Puppy tahr (ubuntu based with LXDE), or potentially something else altogether. I really like the buntu flavor of linux in general and is why all my choices are some form of ubuntu but this is not mandatory. My goal is to have the most lightweight system possible without sacrificing usability, and I need full battery management. The laptop claims to get up to 10 hours run time with windows 10 and I would like that to be at least the same using linux. My first idea was to use FreeBSD but I decided against it since the battery/driver support is pretty atrocious...

Quite frankly it becomes confusing since I don't really know what the difference is between Ubuntu with LXDE, Lubuntu(LXDE), Mint with LXDE, and Puppy tahr with LXDE. If the only difference is some software that is loaded on and the desktop environment I think I would just stick with Ubuntu LTS and load LXDE on. If Lubuntu cuts out some major OS bloat other than just the default programs and LXDE I would probably go with that. If tahr pup has 100% ubuntu support and is even lighter than lubuntu I would probably go with that. The major hurdle for me is what the actual different with these systems is other than the desktop manager? For me, the desktop manager doesn't seem to warrant a different release but it seems most people comparing Linux distros only compare the desktop manager. Also being able to use the touch screen is not mandatory for me as I won't really be using it much (bonus points if it works with the recommended OS).

It all comes down to maximum usability with the least bloat possible.

---

### Post by mastablasta on 2016-12-14
DE means desktop environment not desktop manager. each DE has a full set of applications which is why it is looked at separatelly. e.g. a battery power management app is different in KDE than in Unity. same goes for other things and applications. due to modular nature of linux you can mix and match as you like. however KDE dekstop apps for example were tested to work together. they didnt' test if gnome power management works just well in KDE or that there are no issues with running kmail in gnome.

you mentioned battery is very important to you. this means you need to choose the one that manages it best on your hardware.  

as for "bloat" - well for some it is bloat for others it is a usefull feature. for example my desktop doesn't need battery power management, bluetooth etc. (so bloat?!), but your laptop would very much need it. you can also install minimal iso and then add what you want to it. that way you will end with bare minimum.

[URL="https://help.ubuntu.com/community/Installation/MinimalCD"]https://help.ubuntu.com/community/Installation/MinimalCD
[/URL]

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

edit: oh and if you ask me, you should go with Kubuntu. Or Ubuntu. and if possible go with a LTS.

---

### Post by poorguy on 2016-12-14
Although it will have Windows 10 installed I would suggest a dual boot setup with Windows 10 and Linux as I hate wiping a supported OS.
You may find a time where the Windows 10 OS may be needed.

This is only my opinion.

---

### Post by ozfer2 on 2016-12-14
Sorry, I meant DE. I probably will just go with ubuntu LTS and just change the DE. I can install it to a SD card to be able to keep windows 10 and will probably try that at first.

---

### Post by &amp;KyT$0P# on 2016-12-14
> **ozfer2 said:**
> I probably will just go with ubuntu LTS and just change the DE. 
Why go through all that on a fresh install?  Lubuntu **_is_** Ubuntu with LXDE as the DE.

Unless, of course, you want to use both Unity and LXDE on this machine.  But since your goal is having a lightweight system, I'd guess not.

---

### Post by Bucky Ball on 2016-12-14
> **halogen2 said:**
> Why go through all that on a fresh install?  Lubuntu **_is_** Ubuntu with LXDE as the DE.

+1. Prefer Xubuntu myself. Uses xfce4, lightweight also and very easy to customise.

Only you know what OS you should use. To find out, try them in a 'live' session or as virtual machines before installing them.

[QUOTE=ozfer2]It all comes down to maximum usability with the least bloat possible.  [/QUOTE]

If you want that, go the minimal install and install your own desktop and only the apps/software you want or need. About as stripped back as you can get Ubuntu (with a desktop). I use Xubuntu-core myself which is pretty much the mini install with xfce4 and a couple of default xfce4 things. That's it. You add the rest (via a package manager if you're not up to a terminal). 

Good luck and have fun.

---

### Post by mastablasta on 2016-12-15
> **ozfer2 said:**
> Sorry, I meant DE. I probably will just go with ubuntu LTS and just change the DE. I can install it to a SD card to be able to keep windows 10 and will probably try that at first.

sure you can. you can also install on USB (the tiny ones are barely noticable) but you will want to reduce swapiness: [SIZE=2]https://help.ubuntu.com/community/SwapFaq

and be prepared to have a system that can suddenly fail (easy to solve if with regular imaged backup).

Best way is on disk and do a dual boot if you can.

halogen2 is right - Lubuntu is Ubuntu with LXDE.

[/SIZE]

---

### Post by vasa1 on 2016-12-15
> **ozfer2 said:**
> Sorry, I meant DE. I probably will just go with ubuntu LTS and just change the DE. I can install it to a SD card to be able to keep windows 10 and will probably try that at first.
As others have advised, it's better to finally go with a clean install of the flavor of Ubuntu that offers the DE of your choice.

Lubuntu, for example, does not come with much of the software that comes with Ubuntu.

In my brief experience with using Lubuntu from a pendrive (USB2) on an oldish laptop, a system with persistence is much, much slower than one without persistence.

---

### Post by TheFu on 2016-12-15
> My goal is to have the most lightweight system possible without sacrificing usability,
There are always trade-offs.  Usability for me is ZERO DE and abut 15 quick-launch keyboard shortcuts.  With a terminal, all is possible (that I want).  Highly usable to me.  Many others would find it completely unusable.

Lubuntu is **Not** Ubuntu with LXDE, though that is part of it.  There are specific applications installed with Lubuntu, claimed to be tuned for the total experience.

GUI tools seldom have any special control over the OS. The OS, including power management, is a low-level thing.  There are libraries and system calls shared by all programs which claim to manipulate those things.  Some GUIs are "usable", but only support a tiny subset of the available management options.  Usually there is a CLI tool which implements 95-100% of the management options.  Get used to that with any Unix-like system.  The CLI provides complete control. The GUI is 10%-80% control, depending on the project.  IME, 40% control is about normal for GUI apps.

The more "cheese" that is displayed on the screen, the more power that is used. Turn down the cheese, popups, and use a dark theme, then turn down the screen brightness

> 
The laptop claims to get up to 10 hours run time with windows 10 and I would like that to be at least the same using linux. 
This is an unrealistic expectation.  The vendor only worked with and for running that other OS. They didn't test or consider Linux much, if at all.  Don't want to say that power management under Linux cannot be fantastic.  My chromebook gets 8+ hrs on a full charge.  Turning down the screen brightness makes the most difference, but it also can disable wifi, bt, and slow down disk access to eek more savings.  There are ways to setup each of these things using the power management CLI tools.
```
$ batt-chk.sh 
Battery 0: Discharging, 98%, 16:13:16 remaining
Battery 0: design capacity 4000 mAh, last full capacity 4016 mAh = 100%

```
For example.  That isn't fair, I just unplugged from power and turned the screen down all the way.

Turned up the brightness all the way .... 
```
$ batt-chk.sh 
Battery 0: Discharging, 98%, 06:48:07 remaining
```
It is actually toooooo bright to use, but the point is made.  

Plus, battery use predictions are next to complete bunk. Only real world testing matters.

With all that said, I suspect you are too new to Linux to find my setup acceptable.  IMHO, Ubuntu-Mate is the most usable, lite, solution today. The GUI controls appear very complete (to me). I would install Ubuntu-Core, then add Mate DE and any other major tools that I liked.  

I would avoid puppy-based installs for a number of security reasons.  IMHO, puppy is useful for a save-your-butt need, not as a general desktop.  Also, stay with 16.04. Don't bother with non-LTS distros. They just don't have enough support life for my interest.

Anyway, hope this perspective helps.

---

### Post by anakai on 2016-12-15
Why not do something real fun, install ubuntu minimal or server and then maybe openbox on top of it, fluxbox or something other..There you will have a minimal setup with nothing on it...You will have the stable ubuntu base with a nice desktop of you're choice

---

