---
title: "Resolution issues with ubuntu 12.04 in VBox"
date: 2012-05-13
forum: Virtualisation
---

### Post by tech9tcv on 2012-05-13
Odd thing just happened. I'm running Ubuntu via virtualbox and I was having the same problem. Reinstalled 3 times trying all these commands with the same results. I could never find anything on the additional drivers search except for the virtualbox drivers for ubuntu. This last time, I decided to install said drivers. Ubuntu rebooted and now I'm at 1920x1080. I don't know what the virtualbox drivers have to do with the screen resolution, but when I click on displays it no longer says "laptop", it says "VBX". Just thought I'd let you know.

---

### Post by uRock on 2012-05-13
Hello and welcome to the forums.

Were you having problems after installing VBox Guest Additions? In the past I have had trouble with ubuntu running 3D in a VBox, but running 2D has always run fine.

Moving this to *Virtualization*, since it has nothing to do with the OP..

---

### Post by asadmalik on 2012-05-15
for adjusting the resolution in vbox, you need to install the virtualbox guest additions.
Until then you would be stuck with the default screen resolution and unity 2d.

---

### Post by bluefly on 2012-05-15
I'm having this same problem, and I have installed guest additions.  My computer has a 16:9 ratio, and I only get 4:3 ratio options.

---

### Post by j3sp1 on 2012-05-20
You have to install the Guest Addition through the Terminal to get the resolution stuff work :-)

---

### Post by Ahmed_Gad on 2013-02-21
Try to remove the machine from virtual box without removing the machine's hard drive to prevent losing your machine's data,then add a new machine with the old hard drive.
this works for me.

---

