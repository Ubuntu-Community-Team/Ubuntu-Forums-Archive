---
title: "VmWare WinXP Guest on Gutsy Unusable"
date: 2008-01-03
forum: Virtualisation
---

### Post by HDave on 2008-01-03
Let me start out by saying I am really desperate to get this to work.  I have been all over the Ubuntu and VMware forums trying to find an answer because if I can't make this work, I can't use Ubuntu at the office!!!!  :mad:

I am running Ubuntu Gutsy 7.10 with VMWare Workstation 6.0.2 with a WinXP SP2 guest OS installed.

My machine is a Dell XPS M1210 laptop with a 2Ghz Intel Core 2 Duo.

When I run the VM, it periodically hangs for 1 to 10 seconds and then goes really really fast for a few seconds then hangs....fast/slow/fast/slow.  Watching the Windows system clock would make me think I am living in a worm hole!!  This is even with no programs running.  The CPU meter in the guest also shows this erratic behaviour.  I could almost live with this, except that the  CPU in the host OS is pegged at 70%-95% all the time.  If I try to run much other than VMWare my system locks up. 

Here's what I tried:

a) putting "clock=pit nohz=off" in the boot command in GRUB
b) using the special startup script that sets max_cstate to 1
c) turning off all extra devices (sound, cdrom, usb, etc.)
d) lowering the mem usage to 500MB (i have 3GB available)
e) Tried going with one core...and VMware simply pegs that one core.  It leaves the host OS (Gutsy) usable, but renders the guest OS (WinXP) unusable.
f) edited /etc/vmware/config to add the following things I have read about:
     host.cpukHz = 2000000
     host.noTSC = TRUE
     ptsc.noTSC = TRUE
     MemTrimRate = &#8220;0&#8243;
     sched.mem.pshare.enable = FALSE
     MemAllowAutoScaleDown = FALSE
g) reinstalling VMware Tools in the guest

Any other thought or ideas are quite welcome!!!

---

### Post by fjgaude on 2008-01-03
If you have activated two cores on the guest, that is likely your prime problem. Go with only one and the CPU overload issue goes away. AFAIK vmware is fixing the problem.

---

### Post by HDave on 2008-01-03
OK -- this is just wierd.

I just tried going to 1 CPU and is seems to be working.

Realize that I tried that already on several occasions and it did nothing!!!

So either:
a) Its the combination of 1 CPU and another change (or two!)
or
b) fjgaude is a physic super-hero and fixed my machine via mental telepathy :)

Will try to break it again in order to figure out the exact combination of things and report back.

---

### Post by fjgaude on 2008-01-03
Very good, I like the idea of being a psychic hero. <smile>

---

### Post by kamaboko on 2008-01-03
For grins and giggles have you tried Virtualbox?  I've had great success with that on Gutsy.

---

### Post by fjgaude on 2008-01-03
I have used VirturalBox for months and compared it to VMware on both my main box and my laptop. I have found for what I do VMware to be better, faster: cut and paste, opening and saving large graphic files to a software raid5 array. Notice my signature. I'm a graphic designer.

---

### Post by dpj23 on 2008-01-04
The reason for the slow down in performance was do to resource pools and having to wait for 2 pools to be available to process it...  Now, that the vm is configured to only use 1 resource pool...  As soon as one becomes available it will use it

While on the other hand it was waiting for both processors to become free and then process the call...  

Wait till you start working with 24 or 32 processors then the fun really begins...

---

### Post by HDave on 2008-01-04
I'll have to give VirtualBox a try...thanks for the tip.  I assume it too will need to be set to use only 1 cpu.

---

