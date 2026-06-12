---
title: "reconstruct raid 5 after reinstalling OS"
date: 2006-03-13
forum: Server Platforms
---

### Post by bond00 on 2006-03-13
I have my OS installed on one HD and then a raid 5 array where I store all the files. I would like to do a fresh install of the OS when dapper is officially released, but don't want to lose everything on my raid 5 array. I originally created the raid 5 array but kinda forgot how. I remember that I created a partition and formatted it when I originally created it, but this time around I don't want to do either. I just want mdadm to know that an array is already constructed and put together. Is there a way to simply reconstruct the array after reinstalling the OS without reformatting it and destroying any of the data? Thanks for the help...

---

### Post by Glut on 2006-03-13
mdadm has the assemble command for this very purpose... It's fairly simple to use, check your man page for mdadm.

---

