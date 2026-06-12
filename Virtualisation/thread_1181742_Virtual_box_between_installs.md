---
title: "Virtual box between installs"
date: 2009-06-08
forum: Virtualisation
---

### Post by Niksko on 2009-06-08
If I format my Ubuntu partition to install Jaunty, will I be able to access the virtual machines I currently have setup in VirtualBox when I install VirtualBox again under Jaunty?

---

### Post by sneakernet on 2009-06-08
Your virtual machines are saved in the .VirtualBox folder in your home directory, which are hidden (Ctrl+H to unhide). If you have /Home on a separate partition you should be able to access them after you install VirtualBox again. Otherwise, you will need to back them up before formatting.

---

### Post by axel206 on 2009-06-08
sneakernet is correct. In case you don't have a seperate partition for /home read this guide:

[How to copy and transfer or backup a Virtualbox Virtual Machine .vdi](http://www.my-guides.net/en/content/view/155/26/)

---

### Post by albinootje on 2009-06-08
> **axel206 said:**
> sneakernet is correct. In case you don't have a seperate partition for /home read this guide:

[How to copy and transfer or backup a Virtualbox Virtual Machine .vdi](http://www.my-guides.net/en/content/view/155/26/)

Indeed. Or go for a separate /home partition (after making backups) : [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by bodhi.zazen on 2009-06-08
Or a data partition ;)

---

### Post by Niksko on 2009-06-08
Thanks. I was planning on moving my home folder to a separate partition before I installed Jaunty anyway. Now let's hope it comes in the mail soon.

Thanks again

-Nik

---

