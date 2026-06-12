---
title: "Strange Black Screen?"
date: 2008-06-26
forum: Virtualisation
---

### Post by SafariAl on 2008-06-26
I have tried reinstalling countless times. I have 8.04, 64 bit. After setup, I mounting the iso (ripped from the CD for faster speed), and started it. I get nothing but a black screen, and that's it. I have tried every possible solution I've found and have nothing. According to a friend, it should provide me with a screen telling me to install a system if I haven't mounted a cd or iso. I do not get this screen either, just a black screen. Any help would be nice, Thanks

-Al

---

### Post by jw5801 on 2008-06-26
> **SafariAl said:**
> I have tried reinstalling countless times. I have 8.04, 64 bit. After setup, I mounting the iso (ripped from the CD for faster speed), and started it. I get nothing but a black screen, and that's it. I have tried every possible solution I've found and have nothing. According to a friend, it should provide me with a screen telling me to install a system if I haven't mounted a cd or iso. I do not get this screen either, just a black screen. Any help would be nice, Thanks

-Al

What are you using for virtualisation?

---

### Post by SafariAl on 2008-06-26
Sorry about that. I'm using virtual box.

---

### Post by jw5801 on 2008-06-26
Ok so when you start virtualbox it doesn't bring up an interface or anything, just blacks your screen? The whole screen? Or displays a window with the contents blank. If it's recoverable (ie, you can close the window or switch to a tty and kill the program) then try running it from a terminal to take advantage of any debug output, although I don't know that it will give any. Also take a look at your dmesg output (dmesg | tail) after attempting to run it.

---

### Post by SafariAl on 2008-06-26
Well, I start it up, see the interface and all. I launch one of the machines (Windows 2k) and It just shows a black screen.

---

### Post by prshah on 2008-06-26
> **SafariAl said:**
> I have tried reinstalling countless times. I have 8.04, 64 bit. 


Stupid question: Are you using a 64bit host OS? Or are you trying to install a 64-bit guest onto a 32-bit host? (Quick way to answer: What OS is VirtualBox running on?)

---

### Post by forger on 2008-06-26
virtualbox doesn't support 64-bit guest operating system, you should use the iso with the 32-bit ubuntu
(or use kvm: [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM))

---

### Post by jw5801 on 2008-06-26
> **forger said:**
> virtualbox doesn't support 64-bit guest operating system, you should use the iso with the 32-bit ubuntu
(or use kvm: [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM))

I believe he's running at 64-bit host, with Win 2000 guest. Which should work swimmingly.

So when you attempt to start the installation of a guest operating system it fails? The VirtualBox menu still works fine, just the Virtual Machine hangs?

---

### Post by SafariAl on 2008-06-26
ok here's what i am seeing when launching the machine (too large to embed, so to not take up space there's a link):

[http://img105.imageshack.us/img105/7404/screen1mz0.png](http://img105.imageshack.us/img105/7404/screen1mz0.png)

also, i get this when trying to close it. I cannot press any keys that make it do anything, sort of like it's frozen:

[http://img105.imageshack.us/img105/3088/screen2gq8.png](http://img105.imageshack.us/img105/3088/screen2gq8.png)

---

### Post by SafariAl on 2008-06-26
wow just realized that it seems to try to run when i exit the machine. Please someone help me solve this :(

---

### Post by forger on 2008-06-27
I think that if you have two different operating systems (i.e. freebsd and windows) ran in virtualbox, it will lockup

Are you running any other virtual machines at the same time?
Also do you have any other virtual machine software installed?

You could try kill everything related to virtualbox:
```
 ps ax | grep -i "virtualbox\|vbox" 
```
then use ```
 kill -9 pid
``` to force-kill them

---

### Post by SafariAl on 2008-06-30
Sorry for the late reply, things got hectic, and i tried vmware, and am now sick of it. Many issues :(, but it works the way i'd like vbox too. I'm still trying to get vbox to work

> **forger said:**
> 
Are you running any other virtual machines at the same time?
Nope, just Windows XP

> **forger said:**
> 
Also do you have any other virtual machine software installed?
nope, at the moment yes, but not earlier when the black screen problem arose.

---

