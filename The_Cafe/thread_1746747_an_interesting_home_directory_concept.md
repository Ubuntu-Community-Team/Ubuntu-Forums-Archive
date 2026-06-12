---
title: "an interesting home directory concept"
date: 2011-05-02
forum: The Cafe
---

### Post by wizard10000 on 2011-05-02
Decided to post this in the cafe instead of the support forums to keep people from breaking their own stuff  :)

A guy I respect over on the Kubuntu forums gave me a whole new outlook on home directories. Rather than maintaining a separate home partition he maintains a /data partition and just symlinks in the stuff he wants in his home directory - so I decided I'd try it today. 

I changed fstab so the previous home partition was mounted as /data, fired up the netbook in single-user mode and created a home directory for me, then chowned it to my user account. 

su to my user account, ran mc and symlinked in my email, documents, multimedia, downloads, scripts, .emerald and .claws-mail, then moved everything else over into my new home directory. 

The reason is that it's been my experience that I end up replacing almost all the dotfiles during an upgrade, so I'm gonna try just keeping the data and the dotfiles I really want and letting the rest of the dotfiles get blown away with a new install. 

Using mc it took me about 30 minutes including the smoke break and seems to work pretty well so far. 

I'm gonna do my desktop PC this morning and along with the rest of it, get /tmp and /var/log off my SSD. So far, so good ;)

---

### Post by mips on 2011-05-02
Thanks for sharing.

---

### Post by NightwishFan on 2011-05-02
I always link my folders from a partition mounted to /mnt/data. It is the best if you distro hop on real hardware to keep from having junky configuration files.

---

### Post by YeOK on 2011-05-02
I do something similar and have done for years. /archive for data I want to keep, /share for stuff shared between user accounts. I share my music with the girlfriend so they are symlinked in each user directory, as you say, its great if your home directory gets broken in an update, just rm -Rf /~ and start again.

---

### Post by 3Miro on 2011-05-02
I figured that one out when I started playing with various distributions. I have both / and /home on the same partition, but then I have a separate HDD for Documents, Downloads, Music and so on. That way, I can safely zap all the files in the /home and not worry about conflicts between Gnome2, Gnome3, KDE 4.5, KDE 4.6, XFCE 4.6, XFCE 4.8 ....

You can do something similar without a separate partition. When you install the new OS, move the old /home/your_user_name folder to a new folder (/home/backup), install the new OS, then just move Documents, Downloads, Music and so on from backup to your new /home/your_user_name.

---

### Post by anaconda on 2011-05-02
> **3Miro said:**
> I figured that one out when I started playing with various distributions. I have both / and /home on the same partition, but then I have a separate HDD for Documents, Downloads, Music and so on. That way, I can safely zap all the files in the /home and not worry about conflicts between Gnome2, Gnome3, KDE 4.5, KDE 4.6, XFCE 4.6, XFCE 4.8 ....

You can do something similar without a separate partition. When you install the new OS, move the old /home/your_user_name folder to a new folder (/home/backup), install the new OS, then just move Documents, Downloads, Music and so on from backup to your new /home/your_user_name.

+1

I have been doing the same for ages.

The extra bonus, is that I dont have any of those hidden "dotfiles" on my data disk. (dont know why anyone would like to save them over an distribution upgrade anyway...

---

