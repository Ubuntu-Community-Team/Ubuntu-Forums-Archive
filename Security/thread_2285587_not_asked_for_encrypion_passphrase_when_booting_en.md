---
title: "not asked for encrypion passphrase when booting encrypted drive after upgrade to 15."
date: 2015-07-07
forum: Security
---

### Post by lister171254 on 2015-07-07
I've posted this in the installation & Upgrade forum ([http://ubuntuforums.org/showthread.php?t=2281600](http://ubuntuforums.org/showthread.php?t=2281600)), but have not had a reply in three weeks. Maybe somebody in this forum can help

I've had '/' and '/home' on two separate encrypted drives and was always prompted for both passphrases during boot.

After upgrading to 15.04, I'm only prompted for the '/' drive.

Following is the the fstab file, the /dev/mapper folder and the result from df

Thanks

Leo



```
llist@LeosGameLaptop:/var/log$ more /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
/dev/mapper/sda2_crypt / ext4 errors=remount-ro 0 1
# /boot was on /dev/sda1 during installation
UUID=10585694-d533-4792-800a-f5121a20b432 /boot ext4 defaults 0 2
/dev/mapper/sda4_crypt /home ext4 defaults 0 2
/dev/mapper/sda5_crypt none swap sw 0 0
```
```
llist@LeosGameLaptop:/var/log$ ls -lsa /dev/mapper
total 0
0 drwxr-xr-x 2 root root 120 Jun 8 13:24 .
0 drwxr-xr-x 20 root root 5240 Jun 8 13:24 ..
0 crw------- 1 root root 10, 236 Jun 8 13:24 control
0 lrwxrwxrwx 1 root root 7 Jun 8 13:24 sda2_crypt -> ../dm-0
0 lrwxrwxrwx 1 root root 7 Jun 8 13:24 sda4_crypt -> ../dm-2
0 lrwxrwxrwx 1 root root 7 Jun 8 13:24 sda5_crypt -> ../dm-1
```
```
llist@LeosGameLaptop:/var/log$ df -h
Filesystem Size Used Avail Use% Mounted on
udev 7.8G 0 7.8G 0% /dev
tmpfs 1.6G 11M 1.6G 1% /run
/dev/dm-0 138G 12G 120G 9% /
tmpfs 7.8G 156K 7.8G 1% /dev/shm
tmpfs 5.0M 4.0K 5.0M 1% /run/lock
tmpfs 7.8G 0 7.8G 0% /sys/fs/cgroup
/dev/sda1 1.9G 113M 1.6G 7% /boot
/dev/mapper/sda4_crypt 763G 535G 190G 74% /home
tmpfs 1.6G 52K 1.6G 1% /run/user/1000
/dev/sdb3 18G 676M 17G 4% /media/llist/a27ca082-db83-46be-add6-b58eea9d6661
/dev/sdb2 518G 455G 38G 93% /media/llist/42f15844-5afc-41d4-ae97-3d918a666a5f
/dev/sdb1 1.3T 1.1T 238G 83% /media/llist/41481C8B5686EF95
encfs 763G 535G 190G 74% /home/llist/pers1
encfs 763G 535G 190G 74% /home/llist/pers2
```

---

### Post by TheFu on 2015-07-07
Please use "code tags" so things line up. Hard to read otherwise, so fewer volunteers will bother. You can edit the OP.

Appears to me like 2 different types of encryption are being used now.  Whole drive encryption for the OS, /home and encfs for HOME directory encryption over that. Home directory encryption uses the login password to decrypt /home/$USER directories.

The output from **lsblk** would be helpful to see how these things all relate.

---

### Post by ajgreeny on 2015-07-07
On your behalf I have added code tags to your post; see how much easier it is to read now.

For a "How-to" see my signature below.

---

### Post by lister171254 on 2015-07-07
Thanks for the quick reply, the explanation on code tags and fixing the original post

the output from lsblk:
```
sudo lsblk
NAME           MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda              8:0    0 931.5G  0 disk  
&#9500;&#9472;sda1           8:1    0   1.9G  0 part  /boot
&#9500;&#9472;sda2           8:2    0 139.7G  0 part  
&#9474; &#9492;&#9472;sda2_crypt 252:0    0 139.7G  0 crypt /
&#9500;&#9472;sda3           8:3    0     1K  0 part  
&#9500;&#9472;sda4           8:4    0 775.1G  0 part  
&#9474; &#9492;&#9472;sda4_crypt 252:2    0 775.1G  0 crypt /home
&#9492;&#9472;sda5           8:5    0  14.9G  0 part  
  &#9492;&#9472;sda5_crypt 252:1    0  14.9G  0 crypt [SWAP]
sdb              8:16   0 232.9G  0 disk  
&#9492;&#9472;sdb1           8:17   0 232.9G  0 part  
sr0             11:0    1  1024M  0 rom   

```

---

### Post by TheFu on 2015-07-07
That is NOT what I expected.  See how I have 1 encrypted block, but multiple LVM LVs inside it?

```
$ lsblk
NAME                            MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda                               8:0    0 119.2G  0 disk  
&#9500;&#9472;sda1                            8:1    0   243M  0 part  /boot
&#9500;&#9472;sda2                            8:2    0     1K  0 part  
&#9492;&#9472;sda5                            8:5    0   119G  0 part  
  &#9492;&#9472;sda5_crypt (dm-0)           252:0    0   119G  0 crypt 
    &#9500;&#9472;c720--vg-root (dm-1)      252:1    0  51.9G  0 lvm   /
    &#9500;&#9472;c720--vg-lv--swap (dm-2)  252:2    0   4.1G  0 lvm   [SWAP]
    &#9492;&#9472;c720--vg-lv--Stuff (dm-3) 252:3    0    50G  0 lvm   /stuff

```

Could you post /etc/crypttab?

---

### Post by lister171254 on 2015-07-07
crypttab looks as follows

```
sda2_crypt UUID=0043e354-ccdf-4e1e-a619-1ff210375cbd none luks
sda4_crypt UUID=884ee544-b6d6-49e5-a99d-bbf4e86c4b3b none luks
sda5_crypt /dev/sda5 /dev/urandom cipher=aes-xts-plain64,size=256,swap
```

fstab looks like this

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/sda2_crypt /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=10585694-d533-4792-800a-f5121a20b432 /boot           ext4    defaults        0       2
/dev/mapper/sda4_crypt /home           ext4    defaults        0       2
/dev/mapper/sda5_crypt none            swap    sw              0       0

```

Just to confirm, all this worked as expected prior to the upgrade to 15.04

---

### Post by TheFu on 2015-07-07
> **lister171254 said:**
> Just to confirm, all this worked as expected prior to the upgrade to 15.04

Perhaps I missed it - but what do you mean by "worked as expected?"

that you had to type in 4 passwords?
* 1 for each encrypted partition
* 1 for the password

---

### Post by lister171254 on 2015-07-07
> **TheFu said:**
> Perhaps I missed it - but what do you mean by "worked as expected?"

that you had to type in 4 passwords?
* 1 for each encrypted partition
* 1 for the password

At boot time I had to enter two passwords. one for '/' one for '/home'. 

swap from memory has a system generated password

---

### Post by TheFu on 2015-07-07
As a guess - if you want to enter only 1 password, if there was just 1 encrypted area, that should work.
There are many different ways to accomplish this and I certainly don't know all of them.  If you look at my lsblk above, you can see how the sda5 partition is fully encrypted, but LVM is used to create LVs (logical volumes) under the encrypted partition - only 1 password is needed to decrypt the disk and access the storage holding the OS, apps, /home and swap.

Without knowing exactly how the system was configured before the OS install, we cannot tell how it worked then.  I cannot call 15.04 an "upgrade" - sorry. Every non-LTS release is always "beta software" to me.

Does this make sense?

Just to be clear, I did about 5 installations to get this layout the way I wanted. Then restored from prior backups being very careful NOT to overwrite any files important to the encryption. Took some extra research for me to figure out exactly how all this stuff fits together. Not sure I have it all, but enough that everything I've done recently has worked the first time. ;)

---

### Post by lister171254 on 2015-07-07
Setup in 14.10 was pretty straight forward.

I created 4 partitions during the installation

"/boot"
"/"
"/home"
"swap"


I then chose to encrypt "/" and "/home" for which I was asked the password for each partition.
I also chose to encrypt "swap" for which I was not asked for a password.

That's it. All worked when I booted as expected as I was asked for two passwords during boot

---

### Post by TheFu on 2015-07-07
Looks like you checked the box to "encrypt home" too. Is that what you recall or not?  Not that it helps or matters at this stage ... 

For the 15.04 install - did you use **sudo do-release-upgrade**?  Any log files left over from that? Anything interesting inside those? Just trying to determine what the system had pre-15.04. That's all.

---

### Post by lister171254 on 2015-07-08
I did a manual config of all partition. something I do for all my Ubuntu installation.

I did the upgrade via the Software updater.

The logs are attached.

---

### Post by TheFu on 2015-07-08
> **lister171254 said:**
> I did a manual config of all partition. something I do for all my Ubuntu installation.

I did the upgrade via the Software updater.

The logs are attached.

If you use LVM, then 1 partition would be encrypted and each LV could be separate as you like and usually they can be modified while the system is still running. Ah - the power of LVM. It is like an extremely flexible partition manager that doesn't need reboots for any changes.  That helps for "next time" and LVM does have some complexity if a bone-head setup isn't used.  Mine is bonehead - trying to KISS the storage (so I don't get confused later).

If it isn't clear, I think you'll need to reformat to fix this issue. Are you willing?  Have you tried setting the passphrases for all encrypted storage to be the same? Did that work?

---

### Post by lister171254 on 2015-07-08
I'm sure LVMs are another option to achieve what I want(ed), but the point is that this worked they why I set it up in 14.10 and it now doesn't.

I'm trying the get an explanation at to why this stopped working before figuring out what to do next.

I'm not in a position to try things out as this may leave me with an unusable laptop.


Thanks.

---

