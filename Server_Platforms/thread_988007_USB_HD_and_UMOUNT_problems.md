---
title: "USB HD and UMOUNT problems"
date: 2008-11-20
forum: Server Platforms
---

### Post by uncle_numpty on 2008-11-20
Hi all,

It's my first post here so be gentle :)

I have a server ( current ubuntue server version ) that uses external USB HD's for backup and the procedure for doing this is to mount the drive, run rsync and then umount the drive.

Unfortunately, I seem to have  a USB HHD permanently mounted even when a drive is not connected. So when i dir /usbhd i get a directory and file listing without a connected drive.

I can still mount and unmount a drive without problem and this problem persist's after a reboot.

I've checked fstab and nothing is listed and fdisk -l doesn't show the usbhd either.

Anyone got an idea how I can fix this ??

Thanks for any and all replies

---

### Post by MJN on 2008-11-20
Your 'problem' is that you have files already in /usbhd i.e. in the base filesystem (not the USB HD).
 
Chances are you ran your backup with the USB HD unmounted hence all your files ended up in /usbhd. Of course, when you mount the USB HD it overlays the 'real' /usbhd and you see the files from the USB HD.
 
Your solution is to remove the files in /usbhd (with the drive unmounted and backups made of any files you want from there!).
 
You also ought to add a routine in your script to check the drive really is mounted before proceeding - checking for the existance of a hidden file on the USB HD is one of more common ways of doing this.
 
[Edit: Check out [this post]("http://ubuntuforums.org/showpost.php?p=3898726&postcount=16") for an example of how to do this]
 
Mathew

---

### Post by uncle_numpty on 2008-11-20
Thanks for that.

It's always the obvious isn't it ??

In my defence this is a server at another site which the locals are supposed to back up - obviously the 3 step written instruction is not idiot proof enough :)

Thanks for the link to the fix work around as well.

cheers

---

