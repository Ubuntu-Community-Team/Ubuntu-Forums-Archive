---
title: "Is Ubuntu Studio better with Wacom tablets than plain Ubuntu?"
date: 2010-06-21
forum: Ubuntu Studio
---

### Post by KonfuseKitty on 2010-06-21
I'm having problems with getting my Wacom Graphire3 to work properly in plain Ubuntu 10.04. I see on the Ubuntu Studio webpage they mention Wacom, and so my question: are Wacom tablets better supported on Studio?  I don't really want to go through the hassle of installing it if it's all the same really.

---

### Post by AutoStatic on 2010-06-21
No. Wacom support is part of the kernel and X and those are the same with Ubuntu and Studio.

---

### Post by KonfuseKitty on 2010-06-21
Thanks, that helps me save some time.

---

### Post by philip5 on 2010-06-21
Even if you run Lucid with a wacom tablet they are behind the linux wacom tablet project. You should check out [http://sourceforge.net/projects/linuxwacom/](http://sourceforge.net/projects/linuxwacom/) and get the latest drivers and tools from their and use for the best wacom experience.

Good luck!

---

### Post by KonfuseKitty on 2010-06-22
Thanks, Philip. I have tried the update and it resulted in the tablet not being recognised at all. Reverting to the Ubuntu driver takes me back to where I started. I'll keep looking for a solution in the official Wacom thread.

---

### Post by Favux on 2010-06-22
Hi KonfuseKitty,

What are the problems you are having with your Graphire3?

As for installing the latest linuxwacom wacom.ko and xf86-input-wacom see the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

---

### Post by KonfuseKitty on 2010-06-22
Thanks for your response, Favux.

The problem is simple: when the Mode is set to Relative, I have no pressure sensitivity, when set to Absolute, the pressure sensitivity is there. I have tried most, if not all, suggestions in the main Wacom thread and in the official documentation at this site to no avail, the outcome is always the same. The best, clunky workaround I have arrived at is to set the Stylus to Relative and Eraser to Absolute. So I can paint with normal cursor movement when I don't need pressure, and then when pressure is required, turn the pen around and paint with the Eraser, with the annoying cursor movement of Absolute mode.

This isn't acceptable, and I'm still looking for a proper solution. I have followed the official guide to upgrading to 0.8.8-3 and as stated, it resulted in the tablet not being even turned on (the light is off) and no devices showing up in Gimp. Clearly, I should have followed the advice you have created in the link you quoted. However, with all due respect, I find the advice unuseable. There are simply too many caveats, too many ifs and buts to even get started.

What needs to happen is for your good self or someone else to write advice that is as simple and straghtforward as possible: for one Ubuntu version. Write it for Lucid Lynx, so you don't have to constantly qualify your statements with "for Karmic do this, for Intrepid this, see point 6 below", yada, yada. I don't mean to be rude, I recognise the incredible work you're putting into this, but see it from a user perspective. I've spent the past 4 days almost full time on this problem, with no solution in sight.

---

### Post by Favux on 2010-06-22
You probably want to upgrade to the linuxwacom 0.8.3-3 and the Xorg xf86-input-wacom 0.10.7 (actually clone the git repo.).  That mostly straightened out my Bamboo Pen and Touch.

For the wacom.ko (remember you're not installing linuxwacom, so no 'sudo make install') see:  [http://ubuntuforums.org/showpost.php?p=9485092&postcount=833](http://ubuntuforums.org/showpost.php?p=9485092&postcount=833) and remember to change the version number to 0.8.8-3.

For xf86-input-wacom follow Appendix 5 in the linuxwacom HOW TO.  It should be more straight forward.  This one you do install.

---

### Post by robert shearer on 2010-06-22
> **KonfuseKitty said:**
> 
However, with all due respect, I find the advice unuseable. There are simply too many caveats, too many ifs and buts to even get started.

Yeah, not to mention too many threads.

I have a Bamboo on order and thought I would research setup while I waited for it to arrive.

From the 30+ threads I have read there doesn't seem to be one that says "everything works fine".

I'm thinking I should quit while I am ahead and just cancel the order. Seems I would save myself a whole lot of time and frustration.

Or are there Bamboo and/or Intuos4 (may be persuaded to step up if this works) users out there that have full functionality  ???


@Favux. What is > clone the git repo.?

---

### Post by Favux on 2010-06-22
Hi robert shearer,

In response to multiple complaints I've posted a one stop shop HOW TO, see:  [http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562)  It should also basically work for other Wacom tablets.  Just need to fine tune the xsetwacom script.

Git is the new tracking tool invented by Linus Torvalds for the kernel.  Then many others worked on and improved it.  It tells you when and who made changes to the code along with a bunch of other stuff.  It's very decentralized and you can have your own local tree/repository for experimental changes but still able to synch with the master.  Many projects use it now.  Cloning is what they call downloadig the most recent git master repository.

---

### Post by robert shearer on 2010-06-22
Favux, just waiting for the smoke to clear from the speed of your reply  :)

Thanks for the link and explanation !

I see that mathsguy has posted success with the Bamboo CTH-661.

This is the model I have on order so most heartened.

regards, Bob.

---

