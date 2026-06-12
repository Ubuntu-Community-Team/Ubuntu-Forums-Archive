---
title: "chroot ubuntu 13.04."
date: 2013-04-13
forum: Ubuntu Development Version
---

### Post by serdotlinecho on 2013-04-13
I tried to chroot using live usb ubuntu 13.04 but i get this error:

```
chroot: failed to run command ‘/bin/bash’: No such file or directory
```

I'm using this commands:

```
mkdir /mnt/raring
mount /dev/sda2 /mnt/raring
mount -t proc none /mnt/raring/proc
mount -o bind /dev /mnt/raring/dev
mount -o bind /sys /mnt/raring/sys
mount -o bind /run /mnt/raring/run
chroot /mnt/raring
```

Ubuntu 13.04 live usb:

```
ubuntu@ubuntu:~$ uname -a
Linux ubuntu 3.8.0-17-generic #27-Ubuntu SMP Sun Apr 7 19:40:26 UTC 2013 i686 i686 i686 GNU/Linux
```

Anyone can show me the right way to chroot on ubuntu 13.04? I successfully chroot fedora with fedora 18 live usb using the above commands.

---

### Post by dino99 on 2013-04-13
[http://askubuntu.com/questions/56687/how-to-chroot-ubuntu1](http://askubuntu.com/questions/56687/how-to-chroot-ubuntu1)

---

### Post by sgage on 2013-04-13
> **serdotlinecho said:**
> I tried to chroot using live usb ubuntu 13.04 but i get this error:

```
chroot: failed to run command ‘/bin/bash’: No such file or directory
```

I'm using this commands:

```
mkdir /mnt/raring
mount /dev/sda2 /mnt/raring
mount -t proc none /mnt/raring/proc
mount -o bind /dev /mnt/raring/dev
mount -o bind /sys /mnt/raring/sys
mount -o bind /run /mnt/raring/run
chroot /mnt/raring
```

Ubuntu 13.04 live usb:

```
ubuntu@ubuntu:~$ uname -a
Linux ubuntu 3.8.0-17-generic #27-Ubuntu SMP Sun Apr 7 19:40:26 UTC 2013 i686 i686 i686 GNU/Linux
```

Anyone can show me the right way to chroot on ubuntu 13.04? I successfully chroot fedora with fedora 18 live usb using the above commands.

Here's what's always worked for me:

```
sudo mkdir /mnt/raring
sudo mount /dev/sda2 /mnt/raring/
sudo mount -o bind /proc /mnt/raring/proc
sudo mount -o bind /dev /mnt/raring/dev
sudo mount -o bind /dev/pts /mnt/raring/dev/pts
sudo mount -o bind /sys /mnt/raring/sys
sudo cp /etc/resolv.conf /mnt/raring/etc/resolve.conf
sudo chroot /mnt/raring /bin/bash
```

---

### Post by serdotlinecho on 2013-04-13
> **sgage said:**
> Here's what's always worked for me:

```
sudo mkdir /mnt/raring
sudo mount /dev/sda2 /mnt/raring/
sudo mount -o bind /proc /mnt/raring/proc
sudo mount -o bind /dev /mnt/raring/dev
sudo mount -o bind /dev/pts /mnt/raring/dev/pts
sudo mount -o bind /sys /mnt/raring/sys
sudo cp /etc/resolv.conf /mnt/raring/etc/resolve.conf
sudo chroot /mnt/raring /bin/bash
```

Do i need to create mount point for /proc /dev /dev/pts /sys? 

[IMG]http://i.imgur.com/wG6tF7Ll.png[/IMG]


[IMG]http://i.imgur.com/6fAwNGQl.png[/IMG]


```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a9583

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      487423      242688   83  Linux
/dev/sda2          487424    25663487    12588032   83  Linux
/dev/sda3        25663488    29857791     2097152   82  Linux swap / Solaris
/dev/sda4        29857792   312580095   141361152   83  Linux

Disk /dev/sdb: 2041 MB, 2041577472 bytes
63 heads, 62 sectors/track, 1020 cylinders, total 3987456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62     3984119     1992029    c  W95 FAT32 (LBA)


ubuntu@ubuntu:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 149.1G  0 disk 
&#9500;&#9472;sda1   8:1    0   237M  0 part 
&#9500;&#9472;sda2   8:2    0    12G  0 part 
&#9500;&#9472;sda3   8:3    0     2G  0 part [SWAP]
&#9492;&#9472;sda4   8:4    0 134.8G  0 part 
sdb      8:16   1   1.9G  0 disk 
&#9492;&#9472;sdb1   8:17   1   1.9G  0 part /cdrom
loop0    7:0    0 757.6M  1 loop /rofs
```

```
ubuntu@ubuntu:/mnt/raring/@/etc$ cat fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=a901b001-99f4-404c-bc38-5d721f27fb9e /               btrfs   defaults,subvol=@ 0       1
/dev/sda1       /boot           btrfs   defaults        0       2
# /home was on /dev/sda4 during installation
UUID=c1697efa-995e-45be-8db5-ff5350e4ea93 /home           btrfs   defaults,subvol=@home 0       2
# swap was on /dev/sda3 during installation
UUID=442bfab1-883b-40ce-afbb-32dd7c853e94 none            swap    sw              0       0
```

---

### Post by sgage on 2013-04-13
> **serdotlinecho said:**
> Do i need to create mount point for /proc /dev /dev/pts /sys? This is PITA...

[IMG]http://i.imgur.com/wG6tF7Ll.png[/IMG]


[IMG]http://i.imgur.com/6fAwNGQl.png[/IMG]


```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a9583

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      487423      242688   83  Linux
/dev/sda2          487424    25663487    12588032   83  Linux
/dev/sda3        25663488    29857791     2097152   82  Linux swap / Solaris
/dev/sda4        29857792   312580095   141361152   83  Linux

Disk /dev/sdb: 2041 MB, 2041577472 bytes
63 heads, 62 sectors/track, 1020 cylinders, total 3987456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62     3984119     1992029    c  W95 FAT32 (LBA)


ubuntu@ubuntu:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 149.1G  0 disk 
&#9500;&#9472;sda1   8:1    0   237M  0 part 
&#9500;&#9472;sda2   8:2    0    12G  0 part 
&#9500;&#9472;sda3   8:3    0     2G  0 part [SWAP]
&#9492;&#9472;sda4   8:4    0 134.8G  0 part 
sdb      8:16   1   1.9G  0 disk 
&#9492;&#9472;sdb1   8:17   1   1.9G  0 part /cdrom
loop0    7:0    0 757.6M  1 loop /rofs
```

I have these commands in a text file, and just sequentially cut and paste them into a terminal window. What's one more line :KS  

I'm not sure if /dev/pts is absulutely necessary - all I know is that this recipe has always worked for me. Note the addition of /bin/bash to the chroot command...

---

### Post by dino99 on 2013-04-13
Follow #3 above, and when done, remember to umount each line (in reverse order: the last first, ...)

---

### Post by zika on 2013-04-13
Just one question: /etc/resolv.conf is symlinked to /run/resolvconf/resolv.conf... Does that make any problem in case of chroot?...

---

### Post by serdotlinecho on 2013-04-13
```
sudo mount -o bind /proc /mnt/raring/proc
mount: mount point /mnt/raring/proc does not exist
```

---

### Post by dino99 on 2013-04-13
> **zika said:**
> Just one question: /etc/resolv.conf is symlinked to /run/resolvconf/resolv.conf... Does that make any problem in case of chroot?...

have always followed that way, and never got visible issue.

---

### Post by zika on 2013-04-13
> **dino99 said:**
> have always followed that way, and never got visible issue.I was not clear enough... Mea culpa. I'm not sure if /run survives reboot... I've always copied existing file to /etc/resolv.conf so I did not get a chance to use empty or non-existing file, ergo, I'm not sure what happens with /etc/resolv.conf on a system that needs chroot... That was a point of my previous post...

---

### Post by Rukiri on 2013-04-13
mount -t proc none /mnt/raring/proc
mount --rbind /sys /mnt/raring/sys
mount --rbind /dev /mnt/raring/dev
mount --rbind /run /mnt/raring/run

chroot /mnt/raring /bin/bash
export PS1="(chroot) $PS1"

try that.

---

### Post by serdotlinecho on 2013-04-14
Thanks everyone for helping me. I have figured out the way to chroot because i'm using btrfs.

```
ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# mkdir /mnt/raring
root@ubuntu:/home/ubuntu# mount /dev/sda2 /mnt/raring
root@ubuntu:/home/ubuntu# cd /mnt/raring
root@ubuntu:/mnt/raring# ls
@  etc
root@ubuntu:/mnt/raring# cd @
root@ubuntu:/mnt/raring/@# pwd
/mnt/raring/@
root@ubuntu:/mnt/raring/@# for fs in proc sys dev dev/pts run;
> do mount --bind /$fs /mnt/raring/@/$fs;
> done
root@ubuntu:/mnt/raring/@# cp /etc/resolv.conf /mnt/raring/@/etc/resolv.conf
cp: &#8216;/etc/resolv.conf&#8217; and &#8216;/mnt/raring/@/etc/resolv.conf&#8217; are the same file
root@ubuntu:/mnt/raring/@# chroot /mnt/raring/@
root@ubuntu:/# ping google.com
PING google.com (74.125.135.102) 56(84) bytes of data.
64 bytes from ni-in-f102.1e100.net (74.125.135.102): icmp_req=1 ttl=53 time=18.0 ms
64 bytes from ni-in-f102.1e100.net (74.125.135.102): icmp_req=2 ttl=53 time=14.8 ms
64 bytes from ni-in-f102.1e100.net (74.125.135.102): icmp_req=3 ttl=53 time=14.4 ms
64 bytes from ni-in-f102.1e100.net (74.125.135.102): icmp_req=4 ttl=53 time=16.8 ms
^C
--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 14.411/16.036/18.007/1.466 ms
```

Thanks again everyone :D

---

### Post by jdthood on 2013-04-15
> **sgage said:**
> Here's what's always worked for me:

```
sudo mkdir /mnt/raring
sudo mount /dev/sda2 /mnt/raring/
sudo mount -o bind /proc /mnt/raring/proc
sudo mount -o bind /dev /mnt/raring/dev
sudo mount -o bind /dev/pts /mnt/raring/dev/pts
sudo mount -o bind /sys /mnt/raring/sys
sudo cp /etc/resolv.conf /mnt/raring/etc/resolve.conf
sudo chroot /mnt/raring /bin/bash
```

Note that there is a typo there. It's `resolv.conf`, not `resolvE.conf`.

> **zika said:**
> Just one question: /etc/resolv.conf is symlinked to /run/resolvconf/resolv.conf... Does that make any problem in case of chroot?...

If using resolvconf (which is the default for both Ubuntu Server and Ubuntu Desktop) then /etc/resolv.conf should be symlinked to "../run/resolvconf/resolv.conf" and not to "/run/resolvconf/resolv.conf". The relative symlink is more compatible with chroot environments.

---

### Post by ping-wu on 2013-04-15
Chroot did not allow me to connect to the internet via wireless connection.  Is this normal?

---

### Post by cariboo on 2013-04-15
> **ping-wu said:**
> Chroot did not allow me to connect to the internet via wireless connection.  Is this normal?

No that isn't normal, if wireless works in the installation you are chrooting from, networking whether wired or wireless should work.

---

### Post by ping-wu on 2013-04-16
Thanks.  Didn't notice the author's correction:  It should be cp /etc/resolv.conf /mnt/raring/etc/resolv.conf .  All is well now, thanks again!

---

### Post by ping-wu on 2013-04-16
> **sgage said:**
> Here's what's always worked for me:

```
sudo mkdir /mnt/raring
sudo mount /dev/sda2 /mnt/raring/
sudo mount -o bind /proc /mnt/raring/proc
sudo mount -o bind /dev /mnt/raring/dev
sudo mount -o bind /dev/pts /mnt/raring/dev/pts
sudo mount -o bind /sys /mnt/raring/sys
sudo cp /etc/resolv.conf /mnt/raring/etc/resolve.conf
sudo chroot /mnt/raring /bin/bash
```

Except the second from the last line, this script works quite well.  To avoid similar errors, could you please edit the second line from the rest to read:

```
sudo cp /etc/resolv.conf /mnt/raring/etc/resolv.conf
```

Also, it is helpful to mention too more steps in order to run x applications:

In the chroot shell:

```
export DISPLAY=:0.0
```

In the host shell:

```
xhost +local
```

I should also add that b/c the new Windows notebooks all come with 64-bit UEFI, in order to dual-boot with Windows 8, it becomes almost imperative (at least to me) to install the 64-bit version of Raring (instead of the 32-bit recommended for desktops as I used to do).  But many of us also have a need to run 32-bit applications (e.g., WINE, draftlight, IBM Symphony, etc.)  Again at least to me, the importance of understanding how chroot works cannot be understated.

---

### Post by Rukiri on 2013-04-16
Glad the issue got resolved, google is your friend by the way.
"Linux + Chroot"

---

