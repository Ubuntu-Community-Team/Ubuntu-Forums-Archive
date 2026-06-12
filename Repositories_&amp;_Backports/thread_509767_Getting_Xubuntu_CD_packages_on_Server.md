---
title: "Getting Xubuntu CD packages on Server"
date: 2007-07-25
forum: Repositories &amp; Backports
---

### Post by Shardsofmetal on 2007-07-25
I just installed Ubuntu Server on my laptop with 64MB RAM. It doesn't have an internet connection right now. I have a driver I need to compile for an internet connection on a flash drive. I have 2 questions.

1. How do I get Ubuntu Server to access a flash drive? When I plug in the drive, the device doesn't show in /media like with Ubuntu.

2. I have the Xubuntu CD in the drive right now. How can i get aptitude to install packages from that CD?

Thank you.

---

### Post by smartboyathome on 2007-07-26
I don't know what package manager Xubuntu uses, but with the CD in, you should be able to go into Synaptic, choose tools>repositories, third-party repositories, and finally click add CD.

---

### Post by Seisen on 2007-07-26
You are going to have to edit your source list by using vim or nano and comment out all of the other repos except for the one about the cd.

---

### Post by smartboyathome on 2007-07-26
Or gedit. I find gedit better than vim or emac

---

### Post by Seisen on 2007-07-26
> **smartboyathome said:**
> Or gedit. I find gedit better than vim or emac

If he just has a server install than he can't use gedit.:lolflag:

---

### Post by smartboyathome on 2007-07-26
Oh, right xD

---

