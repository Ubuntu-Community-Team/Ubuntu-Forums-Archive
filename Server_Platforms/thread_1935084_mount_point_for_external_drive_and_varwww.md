---
title: "mount point for external drive and /var/www"
date: 2012-03-03
forum: Server Platforms
---

### Post by ravengirl1960 on 2012-03-03
I think I have my server set up correctly. What I want to do is change the mount point (default is /var/www) to an external usb data drive that I have also set up.

I am a noob at this (though not necessarily Linux in general) and don't know how to do it. 

What I want to do is set up my photography site (a template I'm currently modifying in Kompozer) and put the site/files on the external drive.

What's the best way to do this?

---

### Post by volkswagner on 2012-03-03
It is best to use UUID's in /etc/fstab, more on this later.

Find what is already mounted.
```
mount
```

If your usb is already mounted, you will need to unmount it.  
```
sudo umount /path/to/drive
```

Find the device location for the usb.
```
sudo fdisk -l
```

Then mount it.  The following assumes your usb is formated as NTFS and is located @ /dev/sdc1.  If it's not you will need to adjust accordingly.
```
sudo mount -t ntfs-3g /dev/sdc1 /var/www
```

You may prefer to change it up a bit by going one folder deeper, such as /var/www/site1 or similar.

You may need to adjust permissions.  If this works you will then need an entry in /etc/fstab

---

