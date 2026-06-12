---
title: "Finally figured it out!"
date: 2007-10-18
forum: The Cafe
---

### Post by Sand Lee on 2007-10-18
I have a 28.63GB HD for Ubuntu and I've finally figured out a partition scheme that will last for a very long time. Here goes:

[LIST]
[*]hda1[COLOR="White"]___[/COLOR] / [COLOR="White"]______________[/COLOR] 9GB[COLOR="White"]______[/COLOR] Stable Ubuntu Release
[*]hda2[COLOR="White"]___[/COLOR] /test[COLOR="White"]_______ _ _[/COLOR] 5GB[COLOR="White"]______[/COLOR] Ubuntu Testing Release/ Other distro
[*]hda3[COLOR="White"]___[/COLOR] /data[COLOR="White"]______ ___[/COLOR] 13.63[COLOR="White"]_ _ _[/COLOR] Interdistro data (what would be in home)    
[*]hda4[COLOR="White"]___[/COLOR] linux-swap[COLOR="White"]_ ___[/COLOR] 1GB
[/LIST]
:guitar:

---

### Post by -grubby on 2007-10-18
nice

---

### Post by HermanAB on 2007-10-18
Hmm, next time, make a /home partition too, so that you don't have to delete all your data when you install the next version...

---

### Post by Sand Lee on 2007-10-18
I chose to make a /media/data partition instead of a /home partition because I don't like config files to be transferred over when I install a new version of Ubuntu. With a /media/data partition, I can keep all my data when installing a new release. I just have to chose not to format the partition during installation and mount it in the same location.

---

### Post by HermanAB on 2007-10-18
Good, I use a more traditional /export partition, since it is usually NFS shared with other machines too, but I don't like it when my desktop schtuff gets nuked, so I keep a /home around as well.

---

### Post by Sand Lee on 2007-10-28
This was my old partitioning scheme:
> 
[LIST]
[*]hda1[COLOR="White"]___[/COLOR] / [COLOR="White"]______________[/COLOR] 9GB[COLOR="White"]______[/COLOR] Stable Ubuntu Release
[*]hda2[COLOR="White"]___[/COLOR] /media/test[COLOR="White"]____[/COLOR] 5GB[COLOR="White"]__ ___[/COLOR] Ubuntu Testing Release/ Other distro
[*]hda3[COLOR="White"]___[/COLOR] /media/data[COLOR="White"]___[/COLOR] 13.63[COLOR="White"]____[/COLOR] Interdistro data (what would be in home)    
[*]hda4[COLOR="White"]___[/COLOR] linux-swap[COLOR="White"]_____[/COLOR] 1GB
[/LIST]

I have now updated the original post to show my new scheme. I moved the /media partitions into the root directory in order to limit the cruft in the Places menu. It might just be me, but the system seems to work faster now. :)

---

### Post by pelle.k on 2007-10-28
Other mountpoints should traditionally be placed in /media or /mnt.
The nice thing is, the patched gnome in ubuntu, places partitions mounted under (not /mnt ) /media at the desktop (and places menu), and the rest in computer:// so things don't get messy.

Also, you've got to have a swap partition at least as large as your RAM (preferably even more) to hibernate your computer without problems.

---

