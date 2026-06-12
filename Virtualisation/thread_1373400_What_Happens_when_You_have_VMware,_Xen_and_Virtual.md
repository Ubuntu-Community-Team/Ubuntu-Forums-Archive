---
title: "What Happens when You have VMware, Xen and VirtualBox on same Computer?"
date: 2010-01-05
forum: Virtualisation
---

### Post by sam-c on 2010-01-05
[SIZE="4"]On Ubuntu 9.04 I have at least 3 VM systems installed. 
 VMWare, VirtualBox, Xen.
Do they interact or any other Problems.[/SIZE]:P

---

### Post by mkvnmtr on 2010-01-06
I see you did not get an answer. I was hoping someone with experience would answer. I believe I read in the Sun manual that you should not run at the same time two different apps. I assume that you could have them installed just run them at different times. I have been so happy with Virtual Box that I havent tried the others.

---

### Post by HermanAB on 2010-01-07
Virtualizers do not play well in groups...

You got to pick one and stick to it.

---

### Post by aeon.flux on 2010-01-07
there is no problem to install both of them, i have it and have no problem, but i didn't try to run VM at once and i guess i'll not try it, because it need a lot of RAM and strong CPU and my old 1,7 dual core could not survive that :D

---

### Post by fjgaude on 2010-01-07
I had VBox and VMware Server running at one time, but never had VMs that could be accessed by each. I don't do this any more as I've gone with VMware Player, it's all I need and works fine as kernels are updated.

---

### Post by juancarlospaco on 2010-01-07
a huge cosmic black hole comes up...
*You are Warned!*

---

### Post by SeattleOtaku on 2010-01-07
Do not taunt Happy Fun Ball.  :P

---

### Post by kungfupandda on 2010-01-09
> **sam-c said:**
> [SIZE=4]On Ubuntu 9.04 I have at least 3 VM systems installed. 
 VMWare, VirtualBox, Xen.
Do they interact or any other Problems.[/SIZE]:P

You mentioned that you have already installed 3 of them, what is your experience with it now, I am very curious

---

### Post by AlexandreP on 2010-01-09
> **sam-c said:**
> [SIZE="4"]On Ubuntu 9.04 I have at least 3 VM systems installed. 
 VMWare, VirtualBox, Xen.
Do they interact or any other Problems.[/SIZE]:P

I never tried Xen.

VirtualBox can use a virtual disk made for VMWare (.vmdk) ; if I'm not wrong, VMWare can't use VirtualBox virtual disks (.vdi), but don't hesitate to correct me if I'm wrong.

The machines themselves are not shared between multiple programs, and the same virtual disk can't be used at the same time by two virtual machines.

---

### Post by sam-c on 2011-07-01
> **kungfupandda said:**
> You mentioned that you have already installed 3 of them, what is your experience with it now, I am very curious

Since then a lot of Revolutions on my overworked Desktop. I Still find Virtual Box easiest for testing and Now Oracle VM even installs faster and Solves Dependents more easy.

---

### Post by NoFriends on 2011-07-08
I have vmware installed & virtualbox installed and running the same time most days, I have never come across an interaction problem at all, I cannot comment on Xen as i have never used this.

---

