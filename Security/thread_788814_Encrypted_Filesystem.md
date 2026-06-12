---
title: "Encrypted Filesystem"
date: 2008-05-10
forum: Security
---

### Post by posseidon on 2008-05-10
I created a new partition, configured with cryptsetup and added the boot configuration.

Basically this page resumes the thing: [https://help.ubuntu.com/community/EncryptedFilesystemHowto#head-8ed0125a2cad7d8942a1a85f0c0e5f63dd94f855](https://help.ubuntu.com/community/EncryptedFilesystemHowto#head-8ed0125a2cad7d8942a1a85f0c0e5f63dd94f855)

I can access the encrypted partition without any problem after the configuration process but when I restart I have the error that the /dev/mapper/crypt wasn't find! And the true is that is not there! I tried with ext3 and reseirfs...

8.04.. Any suggestion?

---

### Post by hyper_ch on 2008-05-10
paste output of:

```

cat /etc/crypttab

```


```

cat /etc/fstab

```

---

### Post by posseidon on 2008-05-10
crypttab```
crypt /dev/sda3
```

fstab```
proc /proc proc defaults 0 0
# Entry for /dev/sda4 :
UUID=8a7d2ebe-be70-49c0-9c54-8a9952a9a9c4 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda1 :
#UUID=07D8-0319 /media/sda1 vfat defaults,utf8,umask=007,gid=46 0 1
# Entry for /dev/sda2 :
UUID=10F05E94F05E7FC0 /media/sda2 ntfs-3g defaults,locale=en_GB.UTF-8 0 1
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0

/dev/mapper/crypt /crypt reiserfs defaults 0 1
```

tks hyper_ch

---

### Post by hyper_ch on 2008-05-10
hmmm, looks ok to me....

so post:
```

sudo fdisk -l

```

it might well be, that the designation of the drive changes... from sda to sdc... it happens since gutsy on my computer...

In that case use the UUID in crypttab and not /dev/sda3

---

### Post by posseidon on 2008-05-10
fdisk```
/dev/sda1               1          15      120456   de  Dell Utility
/dev/sda2   *          16        8586    68846557+   7  HPFS/NTFS
/dev/sda3            8587        9596     8112825   83  Linux
/dev/sda4            9597       19457    79208482+  83  Linux

```

I did what you suggested and replaced the path by the UUID in crypttab.. 

crypttab
crypt 5981c748-a505-4c51-81f0-bbc647e0d0f8

fstab
/dev/mapper/crypt /crypt ext3 defaults 0 1

And again, after the process I could mount and access the crypted partition...

I used "udevinfo -q env -n /dev/sda3" to get the UUID before I executed the mkfs. But after the restart udevinfo doesn't print the UUID anymore.

The boot error is "fsck.ext: No such file or directory while trying to open /dev/mapper/crypto" (I was trying with ext3 now..)

I'm not sure what can I do more...

---

### Post by hyper_ch on 2008-05-10
use this:

```

 /dev/disk/by-uuid/XXXXXXXXX-XXX-XXXX-XXXX-XXXXXXXXXX

```

Just find out your UUID of that partition

---

### Post by posseidon on 2008-05-10
The sda3 is not there...

I assume that's a side effect of "mkfs /dev/mapper/crypt"!

After that command if I open GParted for example the partition fylesystem is set to unknown.

---

### Post by hades_6_6_6 on 2008-07-07
I'm experiencing exactly the same issue.
Have found a solution in between?

---

### Post by hyper_ch on 2008-07-07
what problem exactely?

what do
```

cat /etc/crypttab
cat /etc/fstab
ls -al /dev/mapper/by-uuid

```
return?

---

### Post by hades_6_6_6 on 2008-07-07
At boot, I had a mount error "/dev/mapper/crypt not found".
I thought it was an encryption issue. But thanks to your question I found out the problem was located (once more) 30cm in front of the screen:).

```

> cat /etc/crypttab
# <target name>	<source device>		<key file>	<options>
**data** /dev/sda7 none luks
> cat /etc/fstab
# encrypted partition
/dev/mapper/**crypt** /data ext3 defaults 0 1

```

I'm afraid I'm too stupid:(
Thank you for your help

---

