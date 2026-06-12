---
title: "GUI tool for drive mounting, ownership and permissions"
date: 2008-08-24
forum: The Cafe
---

### Post by silkstone on 2008-08-24
We get many questions about mounting/automounting drives/partitions and sorting out ownerships and permissions, especially if someone has formatted a drive ext2/3.

Would it be possible to write a GUI utility to assist with this, rather than having to use fdisk, chown, chmod, etc and manually edit fstab?

It's beyond my skills, but maybe there are gurus out there who could come up with a user-friendly Disk Management tool?

---

### Post by fballem on 2008-08-24
> **silkstone said:**
> We get many questions about mounting/automounting drives/partitions and sorting out ownerships and permissions, especially if someone has formatted a drive ext2/3.

Would it be possible to write a GUI utility to assist with this, rather than having to use fdisk, chown, chmod, etc and manually edit fstab?

It's beyond my skills, but maybe there are gurus out there who could come up with a user-friendly Disk Management tool?

I'd like to add my support for this request, especially the part about not having to directly edit fstab. For newbies, this is a real challenge, especially since on multiple drive machines, the primary drive is the only one that is recognised out of the box.

---

### Post by techmarks on 2008-08-24
It doesn't sound very difficult to do, but hasn't it been done already.

If you are using a file manager with your desktop most likely it has a tab to set permissions, Thunar (for Xfce mostly) and Rox filer have one.  The Gnome file manage does also.

---

### Post by silkstone on 2008-08-24
It may be possible to set permissions in a file manager or something like gnome-commander, but that won't help with fstab and automounting a drive/partition with the correct defaults.

It would be useful to have a GUI app that covered all this - I've been using Ubuntu for over 18 months and I'm still not convinced I understand how to set up ext3/FAT32/NTFS automount and permissions!

---

### Post by bigbrovar on 2008-08-24
```
sudo aptitude install pysdm 
```

i think that might just be what u are looking for .. although i have not used it before and i dont know how it works  but it looks straight forward and easy to use .. however i still prefer editing fstab by hand .. cause there are some things i consider too critical to leave in the hands of GUI Config tools .. but that is just MHO .. if u need sumtin for NTFS drives ```
sudo apt-get install ntfs-config
```

---

### Post by silkstone on 2008-08-24
Thanks for that. It seems to go part way towards a solution, but there are some missing elements such as automatically backing up fstab and also allowing volume name changes.

Also, when you click on a partition you are invited to configure it before going any further, with no explanation as to what this actually means.

It looks as if pysdm could be the basis for a good GUI disk manager, but perhaps need to be taken a few steps further.

---

