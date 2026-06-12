---
title: "/dev/mapper/[machine name]--vg-root full"
date: 2016-06-29
forum: Server Platforms
---

### Post by Asday on 2016-06-29
I've got ubuntu server running in a virtual machine on my windows host, and upon SSHing in to it today, I got some interesting errors.  My MotD told me that there are some security updates, which is new and possibly contributory.  After that, virtualenv hit an IOError:

```
Traceback (most recent call last):
  File "/usr/lib/python2.7/runpy.py", line 174, in _run_module_as_main
    "__main__", fname, loader, pkg_name)
  File "/usr/lib/python2.7/runpy.py", line 72, in _run_code
    exec code in run_globals
  File "/usr/local/lib/python2.7/dist-packages/virtualenvwrapper/hook_loader.py", line 223, in <module>
    main()
  File "/usr/local/lib/python2.7/dist-packages/virtualenvwrapper/hook_loader.py", line 145, in main
    output.close()
IOError: [Errno 28] No space left on device
```

And after that, another interesting error:

```
-bash: cannot create temp file for here-document: No space left on device
```

Which is then repeated every time I try to tab-complete a path.  After that, I got my prompt.

Doing some digging, it appears that some manner of partition is full.  Being a virtual machine, this is easier to fix than a real PC; I just resized the .VDI file housing ubuntu, and came to resize the partition on the command line, but I have no idea which one or how to.  The output of df -h is

```
Filesystem                         Size  Used Avail Use% Mounted on
udev                               7.9G     0  7.9G   0% /dev
tmpfs                              1.6G  8.8M  1.6G   1% /run
/dev/mapper/ubuserv--dev--vg-root  3.0G  3.0G     0 100% /
tmpfs                              7.9G  8.0K  7.9G   1% /dev/shm
tmpfs                              5.0M     0  5.0M   0% /run/lock
tmpfs                              7.9G     0  7.9G   0% /sys/fs/cgroup
/dev/mapper/ubuserv--dev--vg-home  4.1G   45M  3.9G   2% /home
/dev/sda1                          472M  159M  289M  36% /boot
C                                  238G  139G  100G  59% /media/sf_C
D                                  450G  439G   12G  98% /media/sf_D
tmpfs                              1.6G     0  1.6G   0% /run/user/1000
/home/asday/.Private               4.1G   45M  3.9G   2% /home/asday
```

Leaving me to assume that it's /dev/mapper/ubuserv--dev--vg-root that's full.  I got as far as `sudo fdisk /dev/mapper/ubuserv--dev--vg-root`:

```
Welcome to fdisk (util-linux 2.27.1).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.

/dev/mapper/ubuserv--dev--vg-root: device contains a valid 'ext4' signature; it is strongly recommended to wipe the device with wipefs(8) if this is unexpected, in order to avoid possible collisions

Device does not contain a recognised partition table.
Created a new DOS disklabel with disk identifier 0x769f05a1.

Command (m for help):
```

At which point I'm lost in the woods.  I have no idea what to change, and I have every possibility of nuking an important partition in blind idiocy.

Before all this, I tried `umount /tmp` (not mounted) and `umount overflow` (mountpoint not found) as per a StackOverflow post I found.

---

### Post by Asday on 2016-07-27
Is bumping threads acceptable here?

---

### Post by howefield on 2016-07-27
Yes, once a day is good, or even a little more often that that.

Moved to the "Server Platforms" forum.

---

### Post by Asday on 2016-07-27
Here's some extra info:

fdisk -l

```
Disk /dev/sda: 16 GiB, 17179869184 bytes, 33554432 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xa5489a69

Device     Boot   Start      End  Sectors  Size Id Type
/dev/sda1  *       2048   999423   997376  487M 83 Linux
/dev/sda2       1001470 16775167 15773698  7.5G  5 Extended
/dev/sda5       1001472 16775167 15773696  7.5G 8e Linux LVM


Disk /dev/mapper/ubuserv--dev--vg-root: 3.1 GiB, 3288334336 bytes, 6422528 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/ubuserv--dev--vg-swap_1: 196 MiB, 205520896 bytes, 401408 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/cryptswap1: 195.5 MiB, 204996608 bytes, 400384 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/ubuserv--dev--vg-home: 4.3 GiB, 4580179968 bytes, 8945664 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
```

I tried following the instructions [here]("https://blog.jyore.com/2013/06/virtualbox-increase-size-of-rhelfedoracentosscientificos-guest-file-system/"), but when I got to the reboot step, it failed to boot, and I got chucked to a shell with an (initramfs) prompt.

Sensibly though, I just trashed the VM HDD and restored a backup from before I followed the instructions.

From what I understand, I want to extend /dev/sda2, then extend /dev/sda5 into it, but blast if I can figure out how.

EDIT:  Ok, I booted a live disk in the VM and used GParted to stretch out the partitions and it worked ok, my fdisk -l now reads:

```
Disk /dev/sda: 16 GiB, 17179869184 bytes, 33554432 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xa5489a69

Device     Boot   Start      End  Sectors  Size Id Type
/dev/sda1  *       2048   999423   997376  487M 83 Linux
/dev/sda2       1001470 33554431 32552962 15.5G  5 Extended
/dev/sda5       1001472 33552383 32550912 15.5G 8e Linux LVM


Disk /dev/mapper/ubuserv--dev--vg-root: 3.1 GiB, 3288334336 bytes, 6422528 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/ubuserv--dev--vg-swap_1: 196 MiB, 205520896 bytes, 401408 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/ubuserv--dev--vg-home: 4.3 GiB, 4580179968 bytes, 8945664 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/cryptswap1: 195.5 MiB, 204996608 bytes, 400384 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
```

So I can see that sda5 is bigger now, but /dev/mapper/ubuserv--dev--vg-root is still teenyweeny.

df:

```
Filesystem                        1K-blocks      Used Available Use% Mounted on
udev                                8197148         0   8197148   0% /dev
tmpfs                               1643272      8952   1634320   1% /run
/dev/mapper/ubuserv--dev--vg-root   3095280   3078896         0 100% /
tmpfs                               8216352         4   8216348   1% /dev/shm
tmpfs                                  5120         0      5120   0% /run/lock
tmpfs                               8216352         0   8216352   0% /sys/fs/cgroup
/dev/sda1                            482922    162484    295504  36% /boot
/dev/mapper/ubuserv--dev--vg-home   4271416     45224   3986168   2% /home
C                                 249493500 153473268  96020232  62% /media/sf_C
D                                 471596072 460917484  10678588  98% /media/sf_D
tmpfs                               1643272         0   1643272   0% /run/user/1000
/home/asday/.Private                4271416     45224   3986168   2% /home/asday
```

---

### Post by Asday on 2016-07-28
Aha, got it.

I booted a live disc on the virtual machine to use gparted because I'm too stupid to know how to use fdisk properly, and stretched out sda2 and sda5 to fill the rest of the hard drive.  I rebooted into the installed ubuntu server and butted my head against the wall in despair for a day.  Today I went on the warpath.

I made a few bytes of space by nuking /var/tmp.  With that few bytes, I did an apt-get purge on way too many kernel images.  When I was finished, /boot was empty, which was no good, so I apt-get installed the same kernel as I was running as reported by uname -a.

I rebooted to make sure I hadn't hosed my VM, and it worked.  Excellent.

With this newfound free space, I followed the rest of the instructions from [here]("https://blog.jyore.com/2013/06/virtualbox-increase-size-of-rhelfedoracentosscientificos-guest-file-system/"), starting at pvresize.  I did it on sda2, my uh...  "Container" partition?  Whatever it's called I did it on that, and the rest of the instructions ran properly.  pvresize was failing before because it failed to allocate disk space.

I couldn't make my disk bigger because it was full.  Ok cool.

Well either way, I feel a little smarter for figuring it out by myself.

---

### Post by steeldriver on 2016-07-28
Well done fixing it

You might want to address how the root filesystem got completely full (to the point of being unable to run simple commands) - normally, ext filesystems reserve 5% of blocks exactly for this reason, but yours appears to have used the entire 3.0G/3.0G

Assuming /dev/mapper/ubuserv--dev--vg-root is formated ext2/3/4 you can check the reserved block count using dumpe2fs 

```

sudo dumpe2fs /dev/mapper/ubuserv--dev--vg-root | grep -i 'block count'

```

and change it using tune2fs

---

### Post by Asday on 2016-07-28
Well it happened at the same time as my MotD told me about security updates, so I assume it was the downloaded data for those that filled me up.

How it filled me up to the byte is a mystery.  It could have been ok, but then my logon scripts filled it up?  I know virtualenv tries to allocate some manner of file.

It *does* try to reserve some blocks though.

```
asday@ubuserv-dev:~$ sudo dumpe2fs /dev/mapper/ubuserv--dev--vg-root | grep -i 'block count'
[sudo] password for asday:hunter2
dumpe2fs 1.42.13 (17-May-2015)
Block count:              2899968
Reserved block count:     123369
```

I mean, I'm not super worried, 'cause it's just a VM, I can trash it, resize it, muck around in any way, no real huge issue if it hoses itself, but it does seem weird.

---

### Post by Asday on 2016-08-05
bemp

---

### Post by darkod on 2016-08-05
Can you please clarify what kind of help you need? You can bump the thread but I don't really see any questions you asked... :)

Plus, you have 480MB /boot and 3GB root and you are wondering why they get full??? Really? Is that the only space you can afford to give them?

What size is the HDD (virtual hdd) and how you have it partitioned?

PS. For very small disks you shouldn't have used LVM in fact. What benefit is LVM to you in this setup? On the other hand, the little space you have you are splitting it up so you have LVs that are full, and LVs that are empty. Your root LV is full but the home LV has 4GB free (which is more than the total size of the root). If it was all in one partition you would have around 50-50 used-free space, and not a full root.

---

### Post by Asday on 2016-08-06
Steeldriver said > You might want to address how the root filesystem got completely full (to the point of being unable to run simple commands) - normally, ext filesystems reserve 5% of blocks exactly for this reason, but yours appears to have used the entire 3.0G/3.0G

And gave me some diagnostic commands to run, but I'm unsure of where to go next to find out how the fs got that full, and how to prevent it in future.

The sizes are so small because it was really just a throwaway project that evolved into something more, as throwaway projects usually do.  It was originally meant to be a linux command line interface (with linux tools) to my windows system, which has much better things to offer me away from the command line, (VS, video games, etc.).  It has now become a staging web server.

The VHD started out at 8GiB, and I let ubuntu server's installer deal with the partitioning.  I'm pretty new to LVM, so I didn't understand which options I should change.  The VHD is now 16GiB, which is, for now, plenty of room.  In the future I imagine I'll be trying to figure out how to transplant its current state; a VirtualBox VM, to a FreeBSD jail on a FreeNAS box.  Then it'll have about 24TiB of space to play with.

---

### Post by darkod on 2016-08-06
I can't see the full 16GB being used, so you are missing something somewhere... Post the output of:
```
sudo vgdisplay
sudo lvdisplay
```

Also, it seems you are mounting the home LV at /home but then also mounting /home/asday/.Private at /home/asday. That looks like mounting one inside the other. Why are you doing this? You have your /home and use it, no need to mount from from inside /home/asday again at /home/asday.

---

### Post by Asday on 2016-08-06
I think the .Private stuff is to do with the home directory encryption I opted to do when installing.

```
asday@ubuserv-dev:~$ sudo vgdisplay
[sudo] password for asday:hunter2
  --- Volume group ---
  VG Name               ubuserv-dev-vg
  System ID
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  7
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                3
  Open LV               3
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               15.52 GiB
  PE Size               4.00 MiB
  Total PE              3973
  Alloc PE / Size       3973 / 15.52 GiB
  Free  PE / Size       0 / 0
  VG UUID               uFJ7ui-FICv-THqr-aqkS-gfVB-NxPx-1Q6w3M

asday@ubuserv-dev:~$ sudo lvdisplay
  --- Logical volume ---
  LV Path                /dev/ubuserv-dev-vg/root
  LV Name                root
  VG Name                ubuserv-dev-vg
  LV UUID                NSrWsP-5WVy-Cfbj-VPZ5-31Px-Ngxl-nPSayu
  LV Write Access        read/write
  LV Creation host, time ubuserv-dev, 2016-05-07 13:05:47 +0100
  LV Status              available
  # open                 1
  LV Size                11.06 GiB
  Current LE             2832
  Segments               2
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0

  --- Logical volume ---
  LV Path                /dev/ubuserv-dev-vg/swap_1
  LV Name                swap_1
  VG Name                ubuserv-dev-vg
  LV UUID                1od0aB-qeqe-U5cz-gZe2-20ru-p8O7-XNxkbA
  LV Write Access        read/write
  LV Creation host, time ubuserv-dev, 2016-05-07 13:05:47 +0100
  LV Status              available
  # open                 1
  LV Size                196.00 MiB
  Current LE             49
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1

  --- Logical volume ---
  LV Path                /dev/ubuserv-dev-vg/home
  LV Name                home
  VG Name                ubuserv-dev-vg
  LV UUID                2pNlS4-3GqL-gX8d-tu5T-jNhb-wrPr-Lw7d8D
  LV Write Access        read/write
  LV Creation host, time ubuserv-dev, 2016-05-07 13:05:47 +0100
  LV Status              available
  # open                 1
  LV Size                4.27 GiB
  Current LE             1092
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:2
```

---

### Post by darkod on 2016-08-06
OK, you have assigned 11GB to the root LV but I think you didn't expand the filesystem after that. So the root is still mounted as 3GB. You can check that with df -h. If that shows root of only 3GB, try expanding the filesystem with:
```
sudo resize2fs /dev/ubuserv-dev-vg/root
```

After that check again with df -h and root should be 11GB woth plenty of free space.

---

### Post by Asday on 2016-08-06
I did that already, noted in [this]("https://ubuntuforums.org/showthread.php?t=2329249&p=13523629#post13523629") post, but I neglected to post the output of all the commands that time.

```
asday@ubuserv-dev:~$ df -h
Filesystem                         Size  Used Avail Use% Mounted on
udev                               7.9G     0  7.9G   0% /dev
tmpfs                              1.6G  8.8M  1.6G   1% /run
/dev/mapper/ubuserv--dev--vg-root   11G  2.4G  8.0G  24% /
tmpfs                              7.9G  8.0K  7.9G   1% /dev/shm
tmpfs                              5.0M     0  5.0M   0% /run/lock
tmpfs                              7.9G     0  7.9G   0% /sys/fs/cgroup
/dev/mapper/ubuserv--dev--vg-home  4.1G  141M  3.8G   4% /home
/dev/sda1                          472M   78M  370M  18% /boot
C                                  238G  146G   93G  62% /media/sf_C
D                                  450G  445G  5.5G  99% /media/sf_D
tmpfs                              1.6G     0  1.6G   0% /run/user/1000
/home/asday/.Private               4.1G  141M  3.8G   4% /home/asday
```

All that's a mystery to me at the moment is how something managed to actually fill the HDD when ext is meant to reserve a couple sectors.

---

### Post by darkod on 2016-08-06
I don't think you should waste your time with that... You had a 3GB root and it got filled, that's not a surprise... Now if you want to check if it was filled "until last sector etc" you can go on, but I don't see any benefit from it. Don't forget that few free sectors would still show as 100% full because they are not a big part of the partition. A sector is only 512B. You can have hundreds of them free and still root will show 100% full.

---

