---
title: "Permission on NTFS through Linux"
date: 2008-05-29
forum: Security
---

### Post by marcon00 on 2008-05-29
Hello,

I have dual boot, all my documents are stored on NTFS partition,on vista i got myself a protection by FolderLock Xp handy tool from sneaky people, anyways i tried changing permission on linux of these folders and i cant ! i wanted to make them only root accessible. I tried makin random folder on the desktop and setting permission, it worked. So the way i see it, its because of NTFS , i guess .i tried through termial, and through gksudo nautilus . didnt work ! 

Is there any way to lock folder * set permissions * over NFTS system on ubuntu ? 

Thanks in advance.

---

### Post by The Cog on 2008-05-30
Because NTFS doesn't store UNIX file properties, those properties have to be emulated. When an NTFS or FAT partition is mounted, mount options cat set the apparent owner and permissions of all the files on the partition. For ntfs and fat, mount takes these options (and they can be set in fstab for permanent configuration):
uid= sets the owner of the files, e.g. uid=1000
umask= sets the inverse of the permissions bits on the file, e.g. umask=077
I think uid=0,umask=077 is probably what you want.
Use the commands "man mount" and "man fstab" to see details ("q" to quit).
So setting uid=

---

### Post by marcon00 on 2008-05-31
I figured it had something to do with the mounting , but im just 2 months into *nix world :) but my progress is satisfactory ;) I will work on it in 2 days, after my exams and will post you back with my results ! Thanks

---

### Post by aysiu on 2008-05-31
You can't really lock Ubuntu out of an NTFS partition, as it won't support *nix permissions.

---

### Post by marcon00 on 2008-05-31
i don't want to lock out, i want to block out anyone that does not have password to access my files if i leave my laptop unattended . :)

---

### Post by aysiu on 2008-05-31
> **marcon00 said:**
> i don't want to lock out, i want to block out anyone that does not have password to access my files if i leave my laptop unattended . :)
Create a keyboard shortcut for locking the screen, then.

And also know that if you leave your laptop unattended for a long period of time, if you don't trust the people who have access to it, and if they have any technical knowledge, they essentially have root access to everything on your laptop anyway.

---

### Post by marcon00 on 2008-05-31
ALt+ctrl+L ? :) i want to have extra security over a folder, to at least give me this extra couple of min of security, in case of my family using my laptop. very much simple , normal people do not have even visual access over my laptop, family is the problem. I just want lock the folder so it wont be easy as double-click to enter it.

---

### Post by aysiu on 2008-05-31
Okay. So you trust them to use your computer and you also think they know nothing of how to get around security through obscurity, but you don't want them snooping around your NTFS drive?

If that's the case, you might be able to make access to the NTFS drive inconvenient, but it'll be inconvenient for you as well.

Paste these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo fdisk -l
``` Check to see what your NTFS drive is called. Let's say, for this example, it's /dev/sda1 ```
sudo umount /dev/sda1
sudo mkdir /ntfsdrive
sudo nano -B /etc/fstab
``` Comment out (put a # sign in front of) the line that already refers to /dev/sda1 (or whatever it's UUID is). Then add a new line ```
/dev/sda1 /ntfsdrive ntfs nouser,noauto,nls=utf8,umask=0222 0 0
``` Then save (Control-X, Y, Enter)

Now, if they double-click the drive, they'll get an error message saying they can't mount the drive because they don't have permission. To mount the drive, you will need to issue the command ```
sudo mount /dev/sda1
```

---

### Post by esteckis on 2008-05-31
Instead of Folder lock (which I used in the past) I use Truecrypt which there is a windows version and Linux version and each one can access off different drive formats. You can also do a read only with it.

[http://www.truecrypt.org/](http://www.truecrypt.org/)

Also, as a side note, if you use roboform on windows, I use Keepass (XP) Keepassx (linux) as a substitute.

---

