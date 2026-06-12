---
title: "My PC does not have touch screen"
date: 2015-08-30
forum: Ubuntu Development Version
---

### Post by cigtoxdoc on 2015-08-30
I had already installed the Gnome version of 15.10 on 2 desktop PCs.  I just tried the Ubuntu beta of 15.10 (amd 64) on my DELL Vostro 3500 desktop, and Ubuntu thinks it is a cell phone.  I have installed gdm, but got the endless login loop.  I have tried the recovery console without much success except for apparently correcting some packages.  Attempts at normal boot stalls at Stopping User Manager for UID 119...  Upstart in advanced gives me blank screen.  Using dpkg in recovery console after starting networking shows missing ver for about 20 files and then wants to do numerous other changes, which i let it do.  Then it stops with Error getting authority Error initializing authority, Could not connect No such file or directory g-io-error-quark, 1.  Then it says Starting oFono Mobile telephony stack followed by similar g-io-error-quark, 1 error messages.

What is best way of getting this straightened out?

John

---

### Post by dino99 on 2015-08-30
Looks like you have installed the ubuntu-next image of 15.10 (for tablets & ...), not the desktop image as usual

---

### Post by PaulW2U on 2015-08-30
> **cigtoxdoc said:**
>  I just tried the Ubuntu beta of 15.10 (amd 64) on my DELL Vostro 3500 desktop, and Ubuntu thinks it is a cell phone.

Unless you have a reason for keeping that installation I would start again by downloading from:

[http://iso.qa.ubuntu.com/qatracker/milestones/340/builds/101064/testcases](http://iso.qa.ubuntu.com/qatracker/milestones/340/builds/101064/testcases) or [http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/)

As dino99 said you have probably downloaded the wrong version, the one that uses Unity 8. The above links are for the desktop version which uses Unity 7.

---

### Post by grahammechanical on 2015-08-30
The last ISO image for Ubuntu Desktop Next was built on 29th May. Desktop Next is no longer being developed. It was only meant as a limited life span image to show what was being accomplished with the Ubuntu Phone OS. It does indeed think it is a phone. Sadly, it did not transform my desktop machine into a phone of any kind. Mobile or otherwise. :)

---

### Post by cigtoxdoc on 2015-08-30
This problem has been solved except for the touch-screen issue has been solved.  All the non-touch-screen problems were caused by the fact that there was a leftover user (john 1001) from when Canonical support personnel had me create a new user when my original user profile had become corrupt.  This resulted in Ubuntu 15.10 seeing both johnl and 1001.  Problem was solved by changing the ownership of .Xauthority and all the other files and folders in my home folder from 1001 to johnl using sudo chown-R.  The only way I found out how to fix this was by doing a Google search on the g-io-error-quark, 1 .  All the other installation errors were apparently due to this ownership issue.  I found the answer at [http://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop](http://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop) .

John

---

### Post by cigtoxdoc on 2015-08-30
Thank you for your reply.

The image I downloaded was from the "Beta" page and was marked amd 64 desktop.  The touchscreen would not have been a major issue except for the .Xauthority ownership issue as installation of gdm would have solved the problem.  All is well now.  My main reason for rushing into 15.10 on my production machine was the my most used application, evolution, had an annoying e-mail formatting issue with version 3.16.0.  That was fixed with 3.16.3, which requires 15.10.

John

---

### Post by fjgaude on 2015-08-30
I'm using 3.16.0-46 om 14.04.3, or am I missing something?

---

### Post by PaulW2U on 2015-08-30
> **fjgaude said:**
> I'm using 3.16.0-46 om 14.04.3, or am I missing something?

cigtoxdoc was taking about his version of evolution (3.16.3) and not his version of the kernel which is probably 4.1.0-3. :)

---

