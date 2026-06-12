---
title: "How to Install OS via cmd window?"
date: 2015-04-07
forum: Windows
---

### Post by nick180 on 2015-04-07
Here is my issue.

I have a Samsung RV-511-S01UK
i3 380M @2.53Ghz
6GB RAM
Nvidia discrete 1GB dedicated

It came pre-installed with Win 7 x64 and currently runs 8.1 with no issue.

I tried out the Win 10 TP in a VM and liked what I was seeing... so figured I'd use a spare SSD and clean install the Win 10 TP and see how it runs using my real hardware instead of the emulated hardware in a VM.

Problem: It will not go past the initial logo screen at boot initiation, regardless of whether I use DVD or USB installer and regardless of build number.... just stops completely at this point which suggests the process is locked out by the BIOS... but in order to discover exactly where it's failing I need to observe the process in action.

So by process of elimination I'd like to initiate the install from within a CMD window to see exactly which instruction is failing to try to figure out why the install stops at this point.... but I've never learnt the language of CMD code so I need help please.

Questions :

1. I'm guessing I would need an already installed OS to open a CMD window....?

2. If I do then I'm guessing I'll ideally need to create a dual boot system with an appropriately partitioned drive...?

3. If I create that environment, can someone please advise the correct code to initiate the other OS install from within a CMD window so it will log the process in real time and show exactly where the fail is occurring...?

4. Would this process be easier to do from within a Linux environment and install say Ubuntu 14.04 on the first partition of a new SSD instead of Windows...?.... (hence why I'm here)

cheers,

Nick

---

### Post by dino99 on 2015-04-07
everything depend on an 'installer', mainly setup.exe (or the like) for windows; ubuntu (and most of his friends) boot from and iso file which does the work automatically (with some user answers about its own prefered choices)

more info with the link below  ):P

---

### Post by QIII on 2015-04-07
Moved to the Windows sub-forum.

You will not be able to attempt to install Windows on another drive from the Linux command line in order to diagnose this issue.

I would suggest you seek advice on a Windows forum.

---

