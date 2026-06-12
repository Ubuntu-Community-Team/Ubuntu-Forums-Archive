---
title: "Ubuntu 16.04: Windows XP Guest will not launch"
date: 2018-03-29
forum: Virtualisation
---

### Post by brendonwp on 2018-03-29
Yesterday I was working with the VM. Did a normal apt-get update / upgrade, and received a VB update. Seemed to install fine, but this morning the same guest VM crashed during start. Gets to the Win XP "Failed to start properly last time", with menu of choices.
Starting in Safe Mode is fine. Restarting in Normal Mode crashes every time. The log file and png are attached.
I tried starting the prior version of the kernel, and it recompiled the kernel fine. Same error comes back. 



Thanks![ATTACH]279127[/ATTACH][ATTACH=CONFIG]279128[/ATTACH]

---

### Post by TheFu on 2018-03-29
This is a hard one.  WinXP support ended years ago, so my normal answer to re-reinstall the vbox-guest-extensions might not work.  Can you try that.

---

### Post by monkeybrain20122 on 2018-03-29
Why can't people just leave XP dead and let it RIP. :)

---

### Post by cruzer001 on 2018-03-29
OP could have some windows only apps like me.  Don't know how I live without space cadet pinball :)

There is another possibility

[https://www.reactos.org/](https://www.reactos.org/)

---

### Post by monkeybrain20122 on 2018-03-29
> **cruzer001 said:**
> OP could have some windows only apps like me.  Don't know how I live without space cadet pinball :)

There is another possibility

[https://www.reactos.org/](https://www.reactos.org/)


space cadet pinball apparently works very well in wine, get platinum rating. :)[https://appdb.winehq.org/objectManager.php?sClass=application&iId=1255](https://appdb.winehq.org/objectManager.php?sClass=application&iId=1255)

---

### Post by TheFu on 2018-03-29
> **monkeybrain20122 said:**
> Why can't people just leave XP dead and let it RIP. :)

My only license for MS-Office is installed in a WinXP virtual machine. I use it less and less, but sometimes I **need** MS-Visio.  My XP doesn't have any networking enabled. I run it under KVM, not Vbox, perhaps 1 time every 2-3 years.  I'll probably do the same when Win7 support ends.  No Win10 here and I never intend to install it.

Some people have to support embedded systems with XP and a virtual machine is the best method.  When the machinery being controlled costs $5M, no patches for the control SW ever provided and migrating to any newer version is $7M (for a new machine + SW), I really won't argue with someone needing to keep XP around.

Or perhaps some games won't work under newer Windows versions or WINE, so WinXP is the best answer? 

I miss a few OS/2 games.  Might need to load that into a VM.

Anyways, there are always reasons to run older systems.

---

### Post by cruzer001 on 2018-03-29
> **monkeybrain20122 said:**
> space cadet pinball apparently works very well in wine, get platinum rating. :)[https://appdb.winehq.org/objectManager.php?sClass=application&iId=1255](https://appdb.winehq.org/objectManager.php?sClass=application&iId=1255)
Won't go full screen in wine.

---

