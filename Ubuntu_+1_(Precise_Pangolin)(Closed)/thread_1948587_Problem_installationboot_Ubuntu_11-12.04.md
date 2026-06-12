---
title: "Problem installation/boot Ubuntu 11-12.04"
date: 2012-03-28
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by iankovski on 2012-03-28
Hi guys. I'm new here but have many years with Ubuntu. But, a few days ago I'm trying install a new Ubuntu version on my PC (I use Virtual Machine most part of time) and found an error that I never ever see.

First, I've downloaded the 12.04 beta version and the system not initialize via Live CD. Thus I've installed the OS normally but when a do a reboot the system initialization fail.

I've try the 11.04 and 11.10 version x64 and 386 and the same error occurs.

I looking for some forums and found some questions about mce parameter on grub initialization, but I've tried and not succeed.

Below I've attached an picture of the boot screen.

Someone here can send me some help?

Thanks guys and sorry about my poor English.

[IMG]http://www.inf.ufpr.br/hri06/CameraZOOM-20120326225614967.jpg[/IMG]

---

### Post by iankovski on 2012-03-29
Up guys!

---

### Post by Bucky Ball on 2012-03-29
Welcome.

At the kernel list at boot (the grub list where you choose the OS) could you try this? 

* Select the kernel you want to boot
* Hit 'e' to edit it
* Look for the line that ends in 'quiet splash'
* Add 'nodmodset' to the end of that line (after 'splash')
* Follow the instructions at the bottom of the screen to save and boot

Let us know how it went ...

---

### Post by iankovski on 2012-03-29
> **Bucky Ball said:**
> Welcome.

At the kernel list at boot (the grub list where you choose the OS) could you try this? 

* Select the kernel you want to boot
* Hit 'e' to edit it
* Look for the line that ends in 'quiet splash'
* Add 'nodmodset' to the end of that line (after 'splash')
* Follow the instructions at the bottom of the screen to save and boot

Let us know how it went ...
Hi friend. I tried it but not succeed. I tried insert nomce before "quiet splash" and I tried both options together and nothing. The system stay on black screen with an underscore blinding on the top.

I don't know what I do. Below a pic of grub. Thanks guy.

[img]http://www.inf.ufpr.br/hri06/CameraZOOM-20120329140149147.jpg[/img]

---

### Post by cariboo on 2012-03-29
I don't know if that was a typo in your last post, but the command is **nomodeset** not nomce.

---

### Post by iankovski on 2012-04-05
> **cariboo907 said:**
> I don't know if that was a typo in your last post, but the command is **nomodeset** not nomce.
I know man, I tried 3 formats: only nomce, only nomodset and both together. Now I read on google and see that the correctly is nomodeset. Thanks, I'll test that soon.

---

