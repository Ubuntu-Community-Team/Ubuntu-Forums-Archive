---
title: "VMWare messes up ubuntu keyboard"
date: 2008-08-05
forum: Virtualisation
---

### Post by 4Play on 2008-08-05
Hello, I have VmWare Workstation 6.0.4.93057 x86_64 installed, and I have a 32bit Windows XP Professional installed as a VM. Now the problem is that, *sometimes* when I am using the Windows VM and switch back to Linux, all the keyboard mappings are gone, the keys all do weird stuff (like I open a terminal -- with the mouse -- and try to type anything, the window closes) only a restart of X resolves this issue.

I have a Dell XPS M1530 running 64bit Ubuntu 8.04, with most of Compiz's effects turned on.

I think this *might* have something to do with compiz, since I commonly use the VM in full screen on one desktop, and use compiz to switch to another desktop (linux) by banging the pointer up at the corner of the screen(I mapped the upper right corner to the "Window Picker") but I'm not sure, I'm hopping somebody else around here has had a similar issue and has a solution or a hint of some kind, because this is becoming very frustrating...

Thanks for any help :D

---

### Post by mawdryn on 2008-08-06
Hi,

I don't believe it's a Compiz issue. I get a similar issue with VMPlayer 2.0.4 on Hardy (2.6.24.19), where after a while, if I switch back to Ubuntu or close VMPlayer, every key I press closes whatever application I have opened. 

Only fix is to restart X Windows. I don't have any desktop effects turned on.

Evidently, it seems that VMWare is messing with the X Keyboard driver. I wouldn't have the foggiest about how to fix it though.

---

### Post by mmitton on 2008-08-06
I have the same results with vmware workstation 6.0.3 and hardy. After switching to xp vm fullscreen, no ctrl keys work and touching any other key closes whichever window is open.

Core 2 Duo 2Ghz, 2048Mb Ram

---

### Post by Masoris on 2008-08-06
Here is related bug:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/195982](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/195982)
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/196277](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/196277)

To solve this problem, you should run "*setxkbmap*" every time you are on this bug.

---

### Post by 4Play on 2008-08-07
> **Masoris said:**
> Here is related bug:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/195982](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/195982)
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/196277](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/196277)

To solve this problem, you should run "*setxkbmap*" every time you are on this bug.

Thanks man! it's not the most elegant solution, but its enough until a more permanent fix comes out...

:)

update: the setxkbmap command works like a charm, but I found something else that also helps: pressing ctr+alt to release control from the VM has yet to cause the keyboard anomaly for me. It always happens when I have the VM in full screen and change my linux desktop without pressing ctr+alt first.

---

