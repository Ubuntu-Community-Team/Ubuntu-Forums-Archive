---
title: "setti9ng up an encrypted /tmp"
date: 2007-05-28
forum: Server Platforms
---

### Post by Xbehave on 2007-05-28
im trying to setup my /tmp as an encrypted file, i just cant seem to find any howtos or tutorials on it so wonderd if somebody could tell me where im going wrong, or how i can find out the errors? as its durring boot the error shoots past and then i cant seam to find it in any of my logs

i added the following like to my etc/crypttab
> temp /dev/sdb6 /dev/urandom tmp,loud

and my fstab has 
> /dev/mapper/temp	/tmp	 xfs		defaults	0	2

id cant find /dev/mapper/temp so i assume this means that it doesn't format it according to the tmp setting?
if tried it with an xfs formatted partition
and with a luks formatted partition

if somebody could give me some pointers or a solution i would really appreciate it as i started encrypting my partions just to learn about it but am completely stuck now as i cant get to any errors

thx

---

### Post by ruy_lopez on 2007-05-28
There a good howto for encrypted filesystems here,

[https://help.ubuntu.com/community/EncryptedFilesystemHowto3](https://help.ubuntu.com/community/EncryptedFilesystemHowto3)

Try it on a new folder first, before doing it with /tmp

---

### Post by Xbehave on 2007-05-28
thanks but it only covers root, home,swap not temp. i did read alot of its sources and have found the following at [http://www.gentoo.org/proj/en/hardened/disk-cryptography.xml](http://www.gentoo.org/proj/en/hardened/disk-cryptography.xml)
> For /tmp we don't want to keep it between boots (there is no point) and so we don't want to have a specific key for it as we would have to type it in every time we boot, which is a waste of time/effort. So, we need to have it keyed from /dev/urandom. The way to do this is to use the options="" argument in the cryptfs line for /tmp. Everything in the options="" argument is passed directly to cryptsetup so all we need do is: options="-d /dev/urandom" and we're good to go.

Our next problem is that because we change the key every time we boot, the filesystem won't exist any more (we've changed the key so the old device will look like garbage to the kernel). To get around this we need to run an mkfs on boot. The pre_mount="" option in the cryptfs lets us do this. So, we add pre_mount="mke2fs ${dev}" to our /tmp cryptfs line. The ${dev} variable is replaced with the path to the unencrypted end of the mapping at runtime.

We're all set to encrypt /tmp now, right? Nope... we're afraid not. There is another problem. Because we wipe the filesystem each time we boot, we also wipe the file permissions on /tmp which means it loses its 1777 mode and things break because they can't write to /tmp.

We have to add another flag to the /tmp cryptfs line to compensate for this. After the filesystem has been mounted, we need to fix the ownership and permissions on the mount point. We can do this using the post_mount="" hook. So, we add another option post_mount="chown root:root ${mount_point}; chmod 1777 ${mount_point}". Now, finally, we can have an encrypted /tmp without the hassle of typing in pass phrases. 


unfortunately ubuntu doesn't have /etc/conf.d , ther must be an equivilent tho right?

---

### Post by ruy_lopez on 2007-05-28
To encrypt any filesystem, home, temp, you need a separate partition, or a external drive. Unless you want to format and repartition everything. You could probably do it on a 1gb memory stick.

---

### Post by Xbehave on 2007-05-28
i have, i set myself up a separate temp partition specifically because i want to have it randomly encrypted
i have 
10GB root encrypted with luks
5GBwill be /tmp to be encrypted randomly(i went with 5GB because i backup my system in tars and that seams to eat up alot of tmp) 
seperate home

---

### Post by ruy_lopez on 2007-05-28
/etc/defaults/cryptdisks might help you recreate what conf.d/cryptfs does on the Gentoo system.

---

### Post by ruy_lopez on 2007-05-28
The "tmp" option in /etc/crypttab formats the partition on boot using mke2fs, so to mount it you would use fstype ext2, in /etc/fstab. I just tried it using a memory stick and it worked fine.

```
/etc/fstab

/dev/mapper/temp  /media/memorystick ext2 defaults 0 2

```
```
/etc/crypttab

<target> <device>  <keyfile> <options>
temp     /dev/sda1   /dev/urandom    tmp
```

---

### Post by cookfromfrozen on 2007-05-28
Using the tmp option in /etc/crypttab automatically formats the volume at Ext2 at each boot.  The error you're getting is because you're trying to mount the volume as XFS in /etc/fstab, when the volume has been formatted to Ext2.

Change XFS to ext2 and it will work.  Unfortunately I don't think there is a way to specify a different file system, but an advanced journalling file system like XFS is overkill for a temp partition anyway, Ext2 is fine.  You don't need to journal temp data because if the system crashes you don't need the temp data any longer anyway.

---

### Post by Xbehave on 2007-05-30
thank you for the help, i managed to get it to work by changing xfs to auto and corrupting the partion, with my files setup as posted above
thx for the help guys

---

