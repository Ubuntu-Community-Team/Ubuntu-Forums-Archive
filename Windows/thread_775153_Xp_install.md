---
title: "Xp install"
date: 2008-04-29
forum: Windows
---

### Post by fedex1993 on 2008-04-29
Okay i am going to dual boot my laptop because one i need to do work while on the road with photoshop and ubuntu with wine doesnt work with cs3. I insert the disc boot up from the xp disc i cclick and button to boot from the cd then it says inspecting hardware then it goes to a blank screen and never loads. What is the problem here?

---

### Post by jrusso2 on 2008-04-30
Does your laptop use sata hard drive?  If you using XP without service pack 2 that can be a problem.

Did the laptop originally come with XP?  Are you using a regular xp cd or the one that came with the laptop to restore XP?

---

### Post by coolaj86 on 2008-04-30
Be careful, windows will eat grub and make it hard for you to access your linux partitions. If you don't want the hassle of a dual-boot and you only need access to a few applications, just try using VirtualBox to run windows.

```
apt-get install virtualbox
```

It will appear under Applications >> System Tools >> innotek VirtualBox. The setup is pretty self-explanatory, but feel free to ask if you have any questions.

It has a nice 'seamless' mode which is like 'unity' in VMware Fusion.

---

### Post by fedex1993 on 2008-04-30
well it orignally came with vista yuck and i cant run a virtual box with windows xp because there isnt enough ram to go around.

---

### Post by jrusso2 on 2008-05-01
My advice is to see if the mfg of your laptop has all the XP drivers for it.  You might need to install the sata driver for it before the install.

---

### Post by hardyn on 2008-05-01
CD source?  If its not an MS screened disk, make sure your checksums are okey and the disk was burned as a slower than normal rate.

---

### Post by ACGarland on 2008-05-03
If you are installing XP for the first time on a laptop with an SATA hard disk, then be advised that the Windows XP CD you buy retail lacks the needed SATA drivers.

The symptom of this situation is that during the install process, at the point where XP normally would display the various drives and partitions to ask you where to install XP, it will show a blank listing and the message **setup did not find any hard disk drives installed on your computer**.

This happened to me because I purchased my DELL Inspiron 1420n with Ubuntu 7.1 preinstalled so it didn't come with an XP disk with SATA drivers.  I purchased XP pro from a separate source.  (Incidentally, I contacted Dell support prior to reverting to XP and asked specifically if there was anything I needed special and was told I could just purchase XP retail and that it should install.)

I found the following website which explains how to use your XP disk to create a cloned version which adds the necessary SATA driver. After making this disk, you use it instead of your initial XP CD and proceed normally.

[http://www.laptops-drivers.com/dell-laptop/how-to-install-windows-xp-on-dell-inspiron-1420-part-i.html]("http://www.laptops-drivers.com/dell-laptop/how-to-install-windows-xp-on-dell-inspiron-1420-part-i.html")

[http://www.laptops-drivers.com/dell-laptop/install-windows-xp-on-dell-inspiron-1420-part-2.html]("http://www.laptops-drivers.com/dell-laptop/install-windows-xp-on-dell-inspiron-1420-part-2.html")

So, sad to say, I've decided to go backwards to XP. Even though I've run linux as a server for over a decade, my experience with Ubuntu/Kubuntu on a laptop was very frustrating. I figured that buying it preinstalled would make it pretty easy, but not so.

I'm a software engineer by profession with several decades of experience and have run both redhat and suse at the workplace for a number of years. So I'm not exactly a novice.

The issue for me came down to two main items: 1) unreliable laptop-related functions (e.g., suspend, hibernate, crt/lcd switching, touchpad control) and 2) instability in other areas (wireless configuration, printer operation, etc.).  I almost wish I'd kept a detailed list of all the issues I spent time trying to work-around or solve.  In most cases, although I was able to sleuth out a solution or work-around, I eventually just wore out. Plus, the system was *still* not reliable (e.g., resume wouldn't work every now-and-then, plus many other 'details').

I was fortunate to have several weeks of down-time between jobs to devote to this experiment. Eventually, I just needed to get on with my work and have something that was reliable and fully functional.  As much as a dislike XP, it does meet these basic needs.

One caveat I'd mention: I would be considered a 'power desktop user' in that my requirements for a productive desktop are probably larger than many who would find Ubuntu preinstalled workable for basic needs.  Still, there are troubling issues in my mind--I certainly did not receive a product that worked 100% even as preinstalled.  Just search on suspend/hibernate issues in the forum and you'll see what I mean.

Linux has come a long way with Ubuntu and I'm sure will get there. But for now I need to have a computer that does the jobs I need to get done and will have to reluctantly back away from Ubuntu. :-(

---

### Post by tadcan on 2008-05-03
I had the exact same thing happen to me. I had installed ubuntu first and then tried to install xp to set-up a dual boot.

The way out was to install vista, then xp over it and then ubuntu/linux os.

---

