---
title: "Eliminating a partition and using free space"
date: 2010-02-14
forum: Server Platforms
---

### Post by jus71n742 on 2010-02-14
I screwed up with my Ubuntu Server Grub2 on 9.10.
I want to know since I just did a reinstall on top of the old one.
Can I eliminate one of them (doesn't matter) and return it to Ubuntu and 7.  
Now grub shows the new install, win 7 and the old ubuntu's that I had before and they all 3 work.  so how can I restore grub in the old ones to a default setting and then eliminate the new one? or just eliminate the old ones?

Or should I do what I think is prob what I will have to do and completely reinstall Windows and then put Ubuntu back on?

---

### Post by volkswagner on 2010-02-15
You can safely remove partitons you have no intention of booting.

You need to be careful that you edit the correct partitions.

This command will show your partitions.

```
sudo fdisk -l
```

If you boot Ubuntu Live CD, you can use gparted to edit the partitions, or you can use a Gparted live CD.

System > Administration > Partition Editor.  

You will need to unmount any partitions you want to edit.

You can then edit your grub menu.lst file.  This can also been done via the live cd.

You should post the output of the fdisk command and post what you plan to do, if you are uneasy with the process.

---

