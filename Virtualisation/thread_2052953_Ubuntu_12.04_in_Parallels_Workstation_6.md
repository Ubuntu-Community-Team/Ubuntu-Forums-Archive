---
title: "Ubuntu 12.04 in Parallels Workstation 6"
date: 2012-09-04
forum: Virtualisation
---

### Post by kaffelars on 2012-09-04
Has anyone had any success running Ubuntu 12.04 on Parallels Workstation 6?

Parallels Tools does not support 12.04, but it is possible to get it installed - however the mouse does not work.

I have managed to get it kind of working though - by disconnecting the mouse, and then reconnecting it and select that it is ONLY available for the VM, it works but the cursor is invisible. By using mouse tracking, one can see that the cursor has been moved.

Has anybody gotten the mouse to work better than this? :p

(There seems to be a lot of confusion between Parallels **Desktop** (for Mac) and Parallels **Workstation** (for Win/Linux). Please don't reply with "it works on the Mac version", because the software is not the same (and it seems like Parallels is giving the Mac version all the love ;)

---

### Post by kaffelars on 2012-09-06
I actually got it working pretty well yesterday!
I downloaded Parallels Desktop 8 (the .dmg-file for Mac), extracted it using dmg2img (in Ubuntu), and found the ISOs with Parallels Tools (which are newer than the ones for Parallels Workstation).

I then install linux-kernel-headers and build-essentials from apt, and mounted the ISO (prl-tools-lin.iso) in the VM.
These tools installed just fine :D

After installing, a process called prlcc caused the VM to use nearly 100% CPU - I fixed this by going to "startup applications" in Ubuntu, and disabled Parallels Control Center.

To me, everything seems to work fine now - sound, video, networking works flawlessly :)

If you have a Mac, I guess that creating the VM in Parallels Desktop 8 and then copying to Parallels Workstation 6 should work similarly.

**I consider this a temporary solution - I guess that the Parallels Tools for Parallels Desktop also are bound to the 30 days of trial use.**

---

### Post by jj97403 on 2012-09-07
Thanks for posting your solution.  It is kind of lame that Workstation 6 still isn't supported for Ubuntu 12.04, but I have no problems using it with Ubuntu as host and window 7 guest. But it doesn't support Aero, and audio is so-so at best.  If your workaround doesn't last, you could always use 11.10 until 12.04 is suppported. I am not certain, but with Windows 7 host and Ubuntu 11.10 as guest, Parallel Tools can be installed.

---

### Post by kaffelars on 2012-09-07
Yes, I really hope they come up with something good, considering the long wait.

I have asked them, but they don't give any real answers :(

Would love to see 3D/Aero support too, silly that The Mac version has it but you need the Extreme version ($1300) to have it working on a PC. VMware has this, for "only" $300 ;)

---

### Post by Robertjm on 2012-10-10
Maybe I'm misunderstanding what your issue was? You're talking about Ubuntu 12.04 HOST, right? I've got Ubuntu 12.04 64-bit host, running W8 and WXP virtual machines.

When I installed mine I just used the normal linux PW6 build. I didn't have to do anything special, or hack a Mac version. Been running it since last Winter.

The one problem I do have is that if there's a kernel update, PW won't load anymore. Haven't been able to figure a fix for that yet. I basically just boot into the older kernel when I know I'm going to be doing anything in PW6.

---

### Post by kaffelars on 2012-10-10
No, I'm talking about 12.04 as a guest (sorry that I didn't specify this).

Using it as a host works fine :)

---

