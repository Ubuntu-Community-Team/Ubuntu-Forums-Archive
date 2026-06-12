---
title: "dm-crypt error and problems can not mount sdb"
date: 2008-06-24
forum: Security
---

### Post by spike_strip on 2008-06-24
Well I got my self in a situation; I followed the step 1-7 under 'Examples' hear: [https://help.ubuntu.com/community/EncryptedFilesystemHowto](https://help.ubuntu.com/community/EncryptedFilesystemHowto)

I have preformed this on a second hard drive /dev/sdb1 it generally mounts at /media/sdb now it no longer mounts, at boot, and when I attempt to: ```
 sudo mount -t ext3 /dev/sdb1 /media/sdb
mount: /dev/sdb1 already mounted or /media/sdb busy
``` 

During the boot process I am prompted for a PASSPHRASE – when Crypt disk starts - and then an error: ```
File system check failed. Please repair manually. Control-D will exit this shell and continue system start up.

```

**I am entering the correct passphrase.**

I am not sure what is going on or how to trouble shoot the issue. Or how to simply reverse the process and continue on as normal. 

My orignal concept was to Encrypt the second drive and do back up there.

Any feedback is much appreciated!

Q: Does anyone know what command I can enter - at the shell - when prompted ```
File system check failed. Please repair manually.
``` ... or just where to start to fix the issue.  


uname -a ```
2.6.15-52-server #1 SMP Mon Jun 9 18:30:21 UTC 2008 i686 GNU/Linux
```

---

### Post by spike_strip on 2008-06-24
So; I fixed this error: 

> **spike_strip said:**
> 
During the boot process I am prompted for a PASSPHRASE – when Crypt disk starts - and then an error: ```
File system check failed. Please repair manually. Control-D will exit this shell and continue system start up.

```

However, no access to my data on sdb. 

It appears to be mounted do I need to run a command to make the encrypted dated accessible? 

Thanks--

---

### Post by spike_strip on 2008-06-25
Hear is some aditional information: 

out-put from, ls -l /dev/mapper/ ```
total 0
crw-rw---- 1 root root  10, 63 2008-06-25 07:11 control
brw-rw---- 1 root disk 254,  8 2008-06-25 07:13 crypt
brw-rw---- 1 root disk 254,  3 2008-06-25 07:13 lvm2|Ubuntu|root
brw-rw---- 1 root disk 254,  4 2008-06-25 07:13 lvm2|Ubuntu|swap_1
brw-rw---- 1 root disk 254,  5 2008-06-25 07:13 sda5
brw-rw---- 1 root disk 254,  2 2008-06-25 07:13 sda6
brw-rw---- 1 root disk 254,  6 2008-06-25 07:13 sdb1
brw-rw---- 1 root disk 254,  7 2008-06-25 07:13 sdb5
brw------- 1 root root 254,  0 2008-06-25 07:11 Ubuntu-root
brw------- 1 root root 254,  1 2008-06-25 07:11 Ubuntu-swap_1
```

out-put from,  cat /etc/crypttab ```
# <target name> <source device>         <key file>      <options>
crypt /dev/sdb1
```

and from, dmesg | tail ```

[42949460.110000] 
Bluetooth: HCI device and connection manager initialized
[42949460.110000] Bluetooth: HCI socket layer initialized
[42949460.130000] Bluetooth: L2CAP ver 2.8
[42949460.130000] Bluetooth: L2CAP socket layer initialized
[42949460.130000] Bluetooth: RFCOMM socket layer initialized
[42949460.130000] Bluetooth: RFCOMM TTY layer initialized
[42949460.130000] Bluetooth: RFCOMM ver 1.7
[42949763.440000] device eth0 left promiscuous mode
[42949763.500000] device eth0 entered promiscuous mode
[42950040.390000] ufs was compiled with read-only support, can't be mounted as read-write
```

The last line regarding 'ufs' is refering to sdb1.

I am not able to unlock sdb1 do not know how to repair—any feedback is much appreciated!

---

### Post by spike_strip on 2008-06-25
Could someone give me the steps to revers the process? In other words un-do what I have done.  

As it is now I have no access to this drive with complete loss of data! I know there is a Ubuntu genius from Switzerland, that post hear from time to time--no ideas.

To make it worse the hard drive is completely useless, at his stage, and I have used all my available resources to fix the problem ... no luck so far!

---

### Post by hyper_ch on 2008-06-26
ok, once booted, run

```

ls -al /dev/mapper

```

and

```

sudo fdisk -l

```

and

```

df -l

```

and

```

cat /etc/crypttab

```

and

```

cat /etc/fstab

```

---

### Post by spike_strip on 2008-06-26
ls -al /dev/mapper: 
```

total 0
drwxr-xr-x  2 root root     240 2008-06-26 06:55 .
drwxr-xr-x 15 root root   15000 2008-06-26 06:59 ..
crw-rw----  1 root root  10, 63 2008-06-26 06:47 control
brw-rw----  1 root disk 254,  8 2008-06-26 06:55 crypt
brw-rw----  1 root disk 254,  3 2008-06-26 06:50 lvm2|Ubuntu|root
brw-rw----  1 root disk 254,  4 2008-06-26 06:50 lvm2|Ubuntu|swap_1
brw-rw----  1 root disk 254,  5 2008-06-26 06:50 sda5
brw-rw----  1 root disk 254,  2 2008-06-26 06:50 sda6
brw-rw----  1 root disk 254,  6 2008-06-26 06:50 sdb1
brw-rw----  1 root disk 254,  7 2008-06-26 06:50 sdb5
brw-------  1 root root 254,  0 2008-06-26 06:47 Ubuntu-root
brw-------  1 root root 254,  1 2008-06-26 06:47 Ubuntu-swap_1 
```


sudo fdsck -l ```

Disk /dev/sda: 73.4 GB, 73407868928 bytes
255 heads, 63 sectors/track, 8924 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        8924    71681998+   5  Extended
/dev/sda5   *           1          31      248944+  83  Linux
/dev/sda6              32        8924    71432991   8e  Linux LVM

Disk /dev/sdb: 73.4 GB, 73407868928 bytes
255 heads, 63 sectors/track, 8924 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        8559    68750136   83  Linux
/dev/sdb2            8560        8924     2931862+   5  Extended
/dev/sdb5            8560        8924     2931831   82  Linux swap / Solaris
 
```

df -l:
```


Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/Ubuntu-root
                      67430000   3723028  60281692   6% /
varrun                  517292        84    517208   1% /var/run
varlock                 517292         4    517288   1% /var/lock
udev                    517292       116    517176   1% /dev
devshm                  517292         0    517292   0% /dev/shm
/dev/sda5               233303     32671    188185  15% /boot 
```

cat /etc/crypttab:
```
crypt /dev/sdb1
```

cat /etc/fstab:
```
proc            /proc           proc    defaults        0       0
/dev/mapper/Ubuntu-root /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       /boot           ext3    defaults        0       2
/dev/mapper/Ubuntu-swap_1 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom2   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom3   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom4   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom5   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom6   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom7   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom8   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom9   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb1       /media/sdb      ufs     defaults 0      2
/dev/mapper/crypt /crypt reiserfs defaults 0 1
```

Any information is much appreciated&#8212;as I am not sure how to proceed! 

~Corbin

---

### Post by hyper_ch on 2008-06-26
is there a reason why you use ufs and reiserfs?

---

### Post by spike_strip on 2008-06-26
Yes; this is how I was able to get around the original error. I changed fstab; it previously read ```
dev/sdb1       /media/sdb      ext3     defaults 0      2

``` And mounted on boot with no issues—prior to this mistake! When I  receive the above error message. I then change, fstab, to what it currently reads ```
dev/sdb1       /media/sdb      ufs     defaults 0      2

``` I was then able to enter my PASSPHRASE with no errors and boot normal!

---

### Post by hyper_ch on 2008-06-26
strange... well, if it works again it's good.

---

### Post by spike_strip on 2008-06-26
However, I am able to enter my PASSPHRASE and the system boots. I thought I would--A. Beable to maualy mount sdb or; B. sdb would mount on boot as desinged. None of this has worked I am not sure I am using the correct syntax to mount sdb&#8212;however it fails with error such as: ```
mount: /dev/sdb1 already mounted or /media/sdb busy
mount: wrong fs type, bad option, bad superblock on /dev/mapper/crypt,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

---

### Post by hyper_ch on 2008-06-26
Wanna start over again with that drive?

---

### Post by spike_strip on 2008-06-26
So the perplexing part for me is crypto disk appears to function; it prompts me for my PASSPHARSE and accepts it with no errors and boots normally. I would be purely speculating as to why I have no access to drive sdb.

---

### Post by spike_strip on 2008-06-26
OK; I omitted the 'ufs' in fstab and ran sudo mount -t reiserfs and got this error: 
```
  mount: /dev/sdb1 already mounted or /media/sdb busy
```

---

### Post by spike_strip on 2008-06-26
> **hyper_ch said:**
> Wanna start over again with that drive?

Yes: that is most likely my best option at this point the data on the drive is not an issue&#8212;in other words complete loss of data, not great but OK!

---

### Post by hyper_ch on 2008-06-26
I don't know what you do and what you have done in the past... I'd start all over again.

---

### Post by hyper_ch on 2008-06-26
you can start on step V here:

[http://www.howtoforge.com/ubuntu_dm_crypt_luks](http://www.howtoforge.com/ubuntu_dm_crypt_luks)

---

### Post by spike_strip on 2008-06-27
Thanks, hyper_ch for you input on the encrypted hard drive issue [dm-crypt]. I followed the 'How To' and never was able to mount the drive always received errors—started over new. So up and running with the drive just not encrypted!

~Corbin

---

