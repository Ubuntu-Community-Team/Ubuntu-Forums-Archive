---
title: "Please Digg:  Boot an existing XP install with VirtualBox"
date: 2008-08-09
forum: The Cafe
---

### Post by Sand Lee on 2008-08-09
I have been working on this tutorial in the forums for maybe a year now to prep it for general consumption. I hope it is good enough. Please digg this story so it doesn't slip into the nether-regions of digg!! It's a slow day for linux news - perhaps this could spark some interest. :guitar:

Story here: [http://digg.com/linux_unix/Boot_an_existing_XP_Physical_HD_install_with_VirtualBox](http://digg.com/linux_unix/Boot_an_existing_XP_Physical_HD_install_with_VirtualBox)

---

### Post by Sand Lee on 2008-08-09
Hate to do this... bump

---

### Post by BTMark on 2008-08-09
Dugg it. I'm currently using VMWare to achieve the same thing, but likely will switch over since I just don't like VMWare :P

---

### Post by init1 on 2008-08-09
I just use
```
qemu /devsda
```
Virtualbox would probably be faster though. I'll digg it :D

---

### Post by Stex on 2008-08-09
Very nice, I'll try it out later.

I think you've missed two bits that makes it easy to follow though (especially for a discerning digg crowd):

1- You never say to install virtualbox (and the closed source version at that?)

2- Go into a bit more detail on the hard disk, just saying "-rawdisk /dev/sda -partitions 2 is what I put" isn't going to help everyone

Thanks, I hope this works when I try it...

---

### Post by Sand Lee on 2008-08-09
Thanks for the feedback (and diggs) guys.

@Stex
I give a hint to install the closed-source version in Step 2. It should be easy for users to see...
About the disk info, I will reword my sentence to focus on *what* users should edit.

@init1
Does qemu really let you do the same task so simply?

---

### Post by MaxIBoy on 2008-08-09
How does Qemu know how much RAM to give the emulated machine?

---

### Post by init1 on 2008-08-09
> **MaxIBoy said:**
> How does Qemu know how much RAM to give the emulated machine?
Don't know, its never been an issue. There's probably a config file that can be edited for that.

---

### Post by Sand Lee on 2008-08-10
Only need 10 more diggs guys! :popcorn:

---

