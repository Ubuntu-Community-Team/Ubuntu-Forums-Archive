---
title: "Trouble installing Mandriva 2009.0"
date: 2009-03-01
forum: The Cafe
---

### Post by gymophett on 2009-03-01
I am bound to try out this distro!
I've been trying to get it to install for a few hours. Heres what's happening.
First of all, I've been following this guide:
[http://www.howtoforge.com/the-perfect-desktop-mandriva-one-2009.0-gnome](http://www.howtoforge.com/the-perfect-desktop-mandriva-one-2009.0-gnome)
I get past all the steps with no problem. Then I get to where it says 'Please halt your computer, remove your live system, and restart your computer'.
So I restart, and teh loading bar at the bottom of the screen gets stuck, and stays, so I try again, and again, burn again, and again, and download from different sources yet nothing works! One time it even said Kernel Panic! A few times I was able to get to the boot menu, but then it gets stuck on the loading bar? Am I doing a step wrong when I am supposed to be restarting it or what? Someone out there can help me :(

BTW: I have an Acer 5315 and 1gb DDR2.

---

### Post by gymophett on 2009-03-01
Bump. I just got through installing again, and I'm at that last step, now what should I do?

---

### Post by thisllub on 2009-03-02
> **gymophett said:**
> Bump. I just got through installing again, and I'm at that last step, now what should I do?

Try the Mandriva forums?

---

### Post by cariboo on 2009-03-02
Boot up from a LiveCD and remove **quiet splash** from the kernel  line of /boot/grub/menu.lst, and watch the messages, it should tell you what is causing the problem.

Jim

---

### Post by gymophett on 2009-03-02
> **cariboo907 said:**
> Boot up from a LiveCD and remove **quiet splash** from the kernel  line of /boot/grub/menu.lst, and watch the messages, it should tell you what is causing the problem.

Jim

How do I get to the kernel line?

---

### Post by gymophett on 2009-03-02
Okay, it acted like it was going to finally install, and it went through a bunch of text and I got this! 
Kernel panic - not syncing: Attemped to kill init!

---

### Post by HermanAB on 2009-03-02
Much as I love Mandriva, if you are a new user and the installer of a Linux system won't work, then is best to try another distribution, rather than waste your time trying to figure out why it won't install.  However, if you are seriously serious, then you can try the usual "noapic nolapic acpi=off" options on the kernel boot line.

All distribution houses test with a zoo of machines, but nobody has every piece of kit ever made on this planet, so although Linux usually installs trouble free, sometimes it doesn't and the best thing for you is to shop around.  So, try Suse, Fedora and of course Ubuntu.

Cheers,

Herman

---

### Post by gymophett on 2009-03-02
Its working, its working!

---

