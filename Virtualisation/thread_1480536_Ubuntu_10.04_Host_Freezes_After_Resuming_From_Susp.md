---
title: "Ubuntu 10.04 Host Freezes After Resuming From Suspend"
date: 2010-05-11
forum: Virtualisation
---

### Post by unbu on 2010-05-11
Hi all,    

I was wondering if anyone has encountered a similar problem described below. This is 100% reproducible for me.    

Setup:  

[LIST]
[*]Intel Core2 Duo E8400.
[*]Gigabyte EP45T-U3DP with latest BIOS. Virtualization extension enabled in BIOS.
[*]ATI HD4670 video card, 8GB DDR3 RAM
[*]Ubuntu 10.04 64-bit host OS (2.6.32-22-generic #33-Ubuntu SMP)
[*]Virtualbox 3.1.6 (downloaded from virtualbox.org)
[*]Windows XP Pro 32-bit guest OS
[/LIST]
Problem: 
The virtual machine can be started with Intel VT-x/AMD-V without any problem when the host is freshly booted. If the host is suspended (S3-suspend to RAM) and subsequently resumed, then Virtualbox will completely freeze the host when I attempt to start any virtual machine (the freeze actually occurs after the virtual machine BIOS stage). If VT-x/AMD-V is disabled, then the virtual machine will run and won't freeze the host.    

The freeze:  
No keyboard (even Alt+Print Scrn), no mouse.  However, it appears if I quickly switch to console (say Ctrl+Alt+1) before it freezes, the console seems to remain responsive, but as soon as I do Ctrl+Alt+7, everything freezes.  Could this be a problem related to X or video card?  Same freezing occurs when VMware Player is run instead of Virtualbox.

(Display 2D/3D acceleration setting in Virtualbox/Vmware does not appear to have any effect on freezing.  ATI proprietary or open source radeon driver doesn't make a difference, either.)  

This problem doesn't happen when Windows XP Pro (32-bit) is the host, so it's probably not a BIOS issue.

Not really sure how to troubleshoot this issue...  There is a ticket 5048 that describes the same problem ([http://www.virtualbox.org/ticket/5048](http://www.virtualbox.org/ticket/5048)), but I don't understand the resolution :(  

Any insight is appreciated.

---

### Post by mikeashelby on 2010-05-13
Hmmm... This seems like a very similar problem to what I'm having.. at least - the freeze itself is.

I actually can't run the virtual box application at all - as soon as I click the icon, the whole host freezes. Running it from the console does the same, with no output to speak of. I can't click anything, can't make anything happen with keys (caps lock light still functions, but ctrl-alt-del and such do nothing).

Again, any insight into this would be massively appreciated - I could really do with running my VB again!

---

