---
title: "Grub vs Burg"
date: 2010-08-03
forum: The Cafe
---

### Post by Elmer Fudd on 2010-08-03
Can someone point me to a thread discussing the choice Grub vs Burg as the default loader. I have been putting Burg on all my converts computers and find it a much more polished interface to show to the noob dual booters. There must be a good reason why it is not the default.
thanks--

---

### Post by marshmallow1304 on 2010-08-03
[QUOTE=http://code.google.com/p/burg/]burg is a **brand-new** boot loader based on GRUB.[/QUOTE]

Might have something to do with it.

---

### Post by Kyentei on 2010-08-03
It's just an extra that you can put over your GRUB right? It requires GRUB in order to run, and adds nothing to grub but eye-candy. I guess therefore, and because it's quite new, it's not included in Ubuntu / the repos (yet)

---

### Post by Elmer Fudd on 2010-08-03
It is highly based on Grub but I don't believe that it requires Grub to be installed.

---

### Post by realzippy on 2010-08-03
It requires grub.It is kind of a GUI for grub with optional (animated) grub backrounds..

```
sudo add-apt-repository ppa:bean123ch/burg
sudo apt-get update
sudo apt-get install burg burg-themes
```

---

### Post by Elmer Fudd on 2010-08-03
The documentation suggests that it is a replacement for Grub and the installed file sizes support that theory. I guess I'll have to get up the nerve to unistall grub2 to see if that is true.  
No.. not that brave.

---

### Post by Hman242 on 2010-08-03
I uninstalled GRUB and installed BURG and I seem to be doing just fine ;) BURG is a modified GRUB with a GUI. It doesn't require GRUB to be installed because it is essentially GRUB itself.

---

### Post by oaxacamatt1 on 2010-08-03
Hi All,
Thought you might be interested to learn that some fool installed BURG over GRUB.  And believe me it wasn't that difficult. Did I let that one out? Oh well.  

I had a perfectly good version of Grub2 with Ubuntu 10.04 and by using apt-get I was able to install Burg OVER Grub.  Interestingly when I rebooted Burg came up as if nothing ever changed.  I do think that Burg is a little slower than my previous version of Grub2. But I think I will change it back to Grub, now that I have tried it.  I have no need for fancy splash screens, etc.
HTH,
M

---

### Post by realzippy on 2010-08-04
In case of a kernel update you have to run manually

```
sudo update-burg
```
every time...

or edit the */etc/kernel-img.conf* once:

replace *&#8220;update-grub&#8221;* with *&#8220;update-burg&#8221;*

---

### Post by SunnyRabbiera on 2010-08-04
I can chalk up two reasons why BURG is not default:

1: its new
2: its probably very unstable

Also GRUB allows you to choose between kernels, sometimes the latest kernel is not always the greatest.

---

### Post by realzippy on 2010-08-04
*its probably very unstable*

...why should it?It is grub in new clothes.

Burg also lets you choose between different kernels.This is a bootloader's intention...

---

### Post by Elmer Fudd on 2010-08-04
> **SunnyRabbiera said:**
> 
Also GRUB allows you to choose between kernels, sometimes the latest kernel is not always the greatest.

BURG not only allows you to choose between whatever kernels are installed but also to hide (folding mode) the, potentially long, list of earlier kernels. 

I have had no problems with the installs that I have done with BURG other than this last (and only this last) kernel update that re-installed GRUB (easily fixed). BURG even fixed GRUB issues on a couple of machines (using the --alt install).

I started this thread to find out what kind of problems/complaints/concerns/stability_issues that people have had with BURG.
 
Techies don't need the more elegant face that BURG presents at boot but all the noobs that I have dual booting find it more comforting than the stark GRUB screen. (Incidentally all have ended up having me change the default to UBUNTU.) 

I would like to see more than 1% of users on Linux. Compatablility/Installablity is the biggest issue but Appearance is part of the challenge.

These commands (activate this list with F1 or 'h')
are available from the BURG boot screen

    * t - Open theme selection menu
    * f - Toggle between folding mode
    * n - Jump to the next item with the same class
    * w - Jump to the next Windows item
    * u - Jump to the next Ubuntu item
    * e - Edit the command of current boot item
    * c - Open a terminal window
    * 2 - Open two terminal windows
    * h - Display help dialog 
    * i - Display about dialog 
    * q - Return to old grub menu
    * F5/ctrl-x - Finish edit
    * F6 - Switch window in dual terminal mode
    * F7 - List the folded boot items
    * F8 - Toggle between graphic and text mode
    * F9 - shutdown
    * F10 - reboot
    * ESC - quit from the current popup menu or dialog.

---

### Post by Elmer Fudd on 2010-08-04
> **realzippy said:**
> 

In case of a kernel update ... 

edit the */etc/kernel-img.conf* once:
replace *“update-grub”* with *“update-burg”*

realzippy
thanks for this fix

---

### Post by spiralx on 2010-08-07
I didn't find it unstable.  It is, though, quite new, and clearly a work-in-progress.

But it does work just fine.  And looks a HUGE amount better than GRUB2's crude and DOS-ugly appearance!

The installation is a bit of a pain.  This is what I found worked for me, in the end (thank you, *Smart Viking*):

[http://code.google.com/p/burg/wiki/InstallUbuntu](http://code.google.com/p/burg/wiki/InstallUbuntu)

There is a new Burg Manager, but I couldn't persuade it to install because of the ambiguity in the line "public key -O-":

[http://www.omgubuntu.co.uk/2010/07/burg-boot-loader-installation-themeing.html](http://www.omgubuntu.co.uk/2010/07/burg-boot-loader-installation-themeing.html)

I un-installed in the end, and re-installed GRUB2 (using Synaptic Packet Manager), because it was noticeably slower than GRUB2, and wouldn't open my Win-7 partition, though there may be a way round that:

[http://ubuntuforums.org/showthread.php?t=1458329](http://ubuntuforums.org/showthread.php?t=1458329)

---

