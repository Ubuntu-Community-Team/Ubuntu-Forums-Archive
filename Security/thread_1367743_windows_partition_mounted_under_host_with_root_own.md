---
title: "windows partition mounted under /host with root owner automatically (?)"
date: 2009-12-29
forum: Security
---

### Post by Amit_Olkar on 2009-12-29
I've been using Ubuntu for over a year now and have played around it a bit. I'm at this moment using Karmic. My concern for this thread is thus: I had mounted my windows partition manually by editing /etc/fstab file. And it shows as expected in /media folder. What I discovered recently is that there is another folder /host which is exactly the same windows partition. The permissions for the folder show that it is owned by root. So I'm wondering if there's something on my system which mounted this partition and whether my system has already been compromised.

** For the moderator / administrator, If this is the wrong place to post this thread, please move it to the appropriate one and let me know.

---

### Post by meierfra. on 2009-12-30
That is the default setup for Wubi (Ubuntu installed inside Windows).  Since the ubuntu filesystem is just a file on your Windows partition (\ubuntu\disks\root.disk), the Windows partition needs to be mounted before Ubuntu  file system can be mounted.

---

