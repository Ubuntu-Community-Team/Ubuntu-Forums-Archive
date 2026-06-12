---
title: "New to Linux, VM questions"
date: 2016-11-17
forum: Virtualisation
---

### Post by digi84 on 2016-11-17
Hope this is the right place for this.

So I recently installed Ubuntu and I really like it, except for the fact that I can't get World of warcraft and Diablo 3 to run very well, I have tried with just Wine and Playonlinux.  I was thinking of trying a VM.  I currently have 2 SSD in my computer.  One has Ubuntu 16.04 64-bit. The other has windows 10.  Can I use VM to run Windows while booted in Linux?  If so, how?  Currently if I try to explore the SSD with Windows from Linux, it tells me the drive isn't mounted.

Not sure what other info might be needed.  Any info is appreciated.

Please and thank you.

---

### Post by QIII on 2016-11-17
If the VM technology you are looking at is either VirtualBox or VMWare, your graphical performance will be poor.  Each exposes a hardware abstraction layer that provides a very poor virtual graphics processor.

No, you can't use a virtualization solution to run a natively installed operating system like that.

You can get nearly bare-metal performance with something like KVM if you do a passthrough, but you need two GPUs and a bit of savvy.

Dual booting may very well be the best choice if you really must have Windows-based games -- and there is NO problem with that!

---

### Post by digi84 on 2016-11-17
Okay.  Thanks for the info!  I really wanna try to find a way to run wow/d3 on Linux though.  But this at least answers one question.

---

### Post by Bucky Ball on 2016-11-18
Not a gamer at all but was under the impression WoW worked fine under WINE. [Check here]("https://help.ubuntu.com/community/WorldofWarcraft") and also have a dig online as there are plenty of links and info.

---

