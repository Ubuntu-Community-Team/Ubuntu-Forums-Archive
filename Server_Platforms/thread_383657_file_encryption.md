---
title: "file encryption?"
date: 2007-03-13
forum: Server Platforms
---

### Post by Mia_tech on 2007-03-13
is there any file encryption in ubuntu? GUI and or CLI

---

### Post by Frosty Cold Drink on 2007-03-13
I'm a fan of EncFS. It uses FUSE to provide a virtual encrypted file system, so you don't need to fudge with your mount tables or anything like that.

Its available in the universe, so you need to enable that first. Here is some info:

[quote=http://arg0.net/encfs]EncFS provides an encrypted filesystem in user-space. It runs without any special permissions and uses the FUSE library and Linux kernel module to provide the filesystem interface. You can find links to source and binary releases below. EncFS is open source software, licensed under the GPL.

As with most encrypted filesystems, Encfs is meant to provide security against off-line attacks; ie your notebook or backups fall into the wrong hands, etc. The way Encfs works is different from the “loopback” encrypted filesystem support built into the Linux kernel because it works on files at a time, not an entire block device. This is a big advantage in some ways, but does not come without a cost.[/quote]

[http://arg0.net/encfs](http://arg0.net/encfs)

---

### Post by Mia_tech on 2007-03-13
ok, I installed encfs & Kencfs which is a neat GUI apps for encfs, but so far there's no help file or anything, I used kencfs and set up AES as encryption and mount the dir and it mounted some odd directory
/home/username/.kde/share/apps/kencfs/encrypted

what do I have to do in orderr to encrypt my home folders and files?
may be I'm missing something.

thanks

---

### Post by Frosty Cold Drink on 2007-03-13
You may want to play around a bit before encrypting your home folder.

With EncFS, you get 2 folders. In your case, /home/username/.kde/share/apps/kencfs/encrypted is the "real" folder where you files are stored. Whereever you mounted that will seem like plain, readable files, but everything in there is actualy encrypted. Anyhing you put in there will get encrypted, and is actualy stored in the above folder.

I haven't tried this, but you *should* be able to use PamEncfs to mount at least most of a home directory as you log in. That would give you something similar to OS X's FileVault. I haven't tried this, so I can't really help you there.

You can read about PamEncfs here: [http://hollowtube.mine.nu/wiki/index.php?n=Projects.PamEncfs](http://hollowtube.mine.nu/wiki/index.php?n=Projects.PamEncfs)

---

### Post by Mia_tech on 2007-03-14
> **Frosty Cold Drink said:**
> You may want to play around a bit before encrypting your home folder.

With EncFS, you get 2 folders. In your case, /home/username/.kde/share/apps/kencfs/encrypted is the "real" folder where you files are stored. Whereever you mounted that will seem like plain, readable files, but everything in there is actualy encrypted. Anyhing you put in there will get encrypted, and is actualy stored in the above folder.

I haven't tried this, but you *should* be able to use PamEncfs to mount at least most of a home directory as you log in. That would give you something similar to OS X's FileVault. I haven't tried this, so I can't really help you there.

You can read about PamEncfs here: [http://hollowtube.mine.nu/wiki/index.php?n=Projects.PamEncfs](http://hollowtube.mine.nu/wiki/index.php?n=Projects.PamEncfs)

is there any way to change the location of the default mount dir? to lets say /home/username/docs?

---

### Post by Mia_tech on 2007-03-14
ok after creating mount point /media/crypto, I tried to mount it using encfs and went through the setup which ask me for password and after it gave this error

jorge@5601-RM00-00:~$ encfs /home/jorge/documents /media/crypto
EncFS Password: 
fuse: failed to exec fusermount: Permission denied
fuse failed.  Common problems:
 - fuse kernel module not installed (modprobe fuse)
 - invalid options -- see usage message

I have already check that fuse was installed

jorge@5601-RM00-00:~$ cat /proc/filesystems | grep fuse
nodev   fuse

any ideas?

---

### Post by Frosty Cold Drink on 2007-03-14
Who is the owner of and what are the permissions on /media/crypto ? If you can't write to it, you shouldn't be able to mount anything there.

---

### Post by Mia_tech on 2007-03-14
> **Frosty Cold Drink said:**
> Who is the owner of and what are the permissions on /media/crypto ? If you can't write to it, you shouldn't be able to mount anything there.

yeah, just did it with sudo and it mounted just fine just to make sure I made myself the owner of the folder /media/crypto....and worked!!!

I have all my mounted drives or folder showing on my desktop which they are mapped at logon time, whether they are network share or local folder, but when I do mount -a
all drives should mount that one is not showing up on my desktop
but I know it mounted because Im able to write to /media/crypto and is showing on /home/username/documents.

do you know why? 

meanwhile Im still searching and google around
thnaks

---

### Post by Frosty Cold Drink on 2007-03-14
mount -a reads /etc/fstab and mounts that way. You would have to set up mounts for encfs in /etc/fstab if you want the encrypted stuff to mount on boot. The problem with this is that the password for the encrypted file system would have to be stored in /etc/fstab I belive.

PamEncfs seeks to help here, since it takes your password when you log in and does the mounting then, so yout password isn't laying around anywhere. Plus, you don't have to mount manually or enter your password multiple times.

---

### Post by Mia_tech on 2007-03-14
> **Frosty Cold Drink said:**
> mount -a reads /etc/fstab and mounts that way. You would have to set up mounts for encfs in /etc/fstab if you want the encrypted stuff to mount on boot. The problem with this is that the password for the encrypted file system would have to be stored in /etc/fstab I belive.

PamEncfs seeks to help here, since it takes your password when you log in and does the mounting then, so yout password isn't laying around anywhere. Plus, you don't have to mount manually or enter your password multiple times.

thanks, I will try PamEncfs then, but yes you're right /etc/fstab reads credentials from /root/.smbcredentials which is pretty much in a clear txt format

---

