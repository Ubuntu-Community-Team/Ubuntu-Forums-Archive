---
title: "Problem with permissions on a samba share"
date: 2009-03-02
forum: Security
---

### Post by Oni-san on 2009-03-02
Hello,

I've a share on my NAS hosting an encrypted file created with TrueCrypt.

I'm now unable to mount it as truecrypt says that permission is denied.

Here's the permission I see when doing ls -l:

```

-rw---x--x 1 oni-san oni-san 21474836480 2009-02-15 23:37 /media/private/encrypted2

```

(other files are showing drwxrwxrwx)

So I tried to change it by chmod 555 -> permission denied
I also tried to do sudo chmod 555 -> permission denied

I wonder if this can come from my mount options ...
My fstab entry:

```

//192.168.13.10/private /media/private cifs user,auto,rw,username=qisope,password=*****,iocharset=utf8,gid=1000,uid=1000 0 0

```

Any idea ?

---

### Post by lensman3 on 2009-03-02
The /media file  system, I think, is managed by the autofs managers.  This has a low level kernel file system link.  autofs manages the mounting and umount of devices/filesystems/files.  

What happens if you try to do "mkdir /media/junk".  Can you create a mount point under /media.  If you can't then autofs is controlling the mount point.

If you can't create the junk file or directory, then stop autofs and see what happens.  The control files for autofs are located in /etc.   Look at the the auto* files.  The autofs programs have been around since the mid eighties when Sun Micros designed the interface for mounting NFS.  

I don't know if this is the problem, but your symptoms are the same as mount points controlled by autofs.

---

### Post by Oni-san on 2009-03-03
The mountpoint is working well in /media.

To be sure, I moved it to /mnt.

Same problem. I've this single file with permissions that I cannot change.

```

oni-san@oni-san-desktop:~$ chmod 555 /mnt/private/encrypted
chmod: changing permissions of `/mnt/private/encrypted': Permission denied
oni-san@oni-san-desktop:~$ sudo chmod 555 /mnt/private/encrypted
chmod: changing permissions of `/mnt/private/encrypted': Permission denied
oni-san@oni-san-desktop:~$ sudo chmod 555 /mnt/private/test.txt 
oni-san@oni-san-desktop:~$ 

```

---

### Post by Oni-san on 2009-03-03
I finally solved this.
The problem came from cifs.
I was able to change the permissions with NFS. I'll investigate to permanently use NFS instead of samba now.

---

