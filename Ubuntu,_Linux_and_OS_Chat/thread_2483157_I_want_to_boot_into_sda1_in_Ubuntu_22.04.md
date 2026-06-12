---
title: "I want to boot into sda1 in Ubuntu 22.04"
date: 2023-01-21
forum: Ubuntu, Linux and OS Chat
---

### Post by brevardo2 on 2023-01-21
I installed Ubuntu 22.04 to a 995 GB Dell and so far I really love it. However I made a mistake where I ended up installing three different Partitions or Mounts? Meaning, when I log into sda3 which is what I'm using now it says Computer has 463GB and over to the left Favorites that run along the side I can see my two other Mounts as one of them is an 83GB Mount and the other is a 453 GB Mount. Is there a way I can reboot and instead of booting to the sda3 I can boot into sda1? I know that GRUB comes up for a quick few seconds when I reboot but I don't think I see sda1? It does have a few other options that maybe I need to hit in order to boot into sda1? Please advise as to how I can get there. Thanks, Rich

---

### Post by oldfred on 2023-01-21
Best to see details, and if sda1 has bootable install.

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version over somewhat older ISO with your USB installer  or any working install.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by ajgreeny on 2023-01-21
Difficult to give you any details without knowing more about what is already on your disk. Assuming that the system uses UEFI boot mode it may be that sda1 is your EFI partition but the commands below will tell us a lot more.

Please show us the output of commands ```
sudo fdisk -l
df -hT -x tmpfs -x devtmpfs
```
Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted.
See my signature below for a **How-to**

---

### Post by brevardo2 on 2023-01-21
Here is what the results are (please see attached image below )

---

### Post by ajgreeny on 2023-01-21
Please don't use images of terminal output as you did as it is much less easy to both read and respond to if necessary.
Copy the text in terminal by either highlighting it with the mouse and then right click in the text and use copy from the context menu, or use Ctrl+Shift+C (you still need to highlight the text first).
Ctrl+C is the shortcut in terminal for Cancel so does not work as you may have expected.

Your sda1 appears to be an unused partition which I suspect is mounted after you clicked on its shortcut in the file manager. You can not boot to that as there is no OS nor anything else of use probably on the partition.
It would be very helpful to see a screenshot from gparted which is on the live system you used to install your system or you can be install in your OS with command ```
sudo apt install gparted
```
You can not use that installed version to edit any of your partitions as you can not work on mounted partitions, but it will show the current partitions and how they are sitting on the disk, ie their order which is important when wishing to perhaps rearrange them.

By the way, the first command I showed was not as you typed it but should have a lower case L at the end, not a capital I or even the pipe character | which it appears to be.  Please run that again correctly, and please copy and then paste that output using code tags as I requested last time.

---

### Post by brevardo2 on 2023-01-21
Okay. Sorry about that. I just tried it again and here are the results:


```
rich@rich-Inspiron-3847:~$ sudo fdisk -l
[sudo] password for rich:
Disk /dev/loop0: 4 KiB, 4096 bytes, 8 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 249.08 MiB, 261177344 bytes, 510112 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 116.7 MiB, 122363904 bytes, 238992 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 55.61 MiB, 58310656 bytes, 113888 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 61.96 MiB, 64970752 bytes, 126896 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 63.27 MiB, 66347008 bytes, 129584 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 238.48 MiB, 250060800 bytes, 488400 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: ST1000DM003-1CH1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: F51AE018-BDFA-4045-ACF1-3ACA1E1DB118

Device          Start        End   Sectors   Size Type
/dev/sda1        2048  905216121 905214074 431.6G Linux filesystem
/dev/sda2  1788119040 1789169663   1050624   513M EFI System
/dev/sda3  1789169664 1953523711 164354048  78.4G Linux filesystem
/dev/sda4   905218048 1788119039 882900992   421G Linux filesystem

Partition table entries are not in disk order.


Disk /dev/loop8: 400.8 MiB, 420265984 bytes, 820832 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop9: 346.33 MiB, 363151360 bytes, 709280 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop10: 91.69 MiB, 96141312 bytes, 187776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop11: 91.88 MiB, 96337920 bytes, 188160 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop12: 389.69 MiB, 408621056 bytes, 798088 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop13: 45.86 MiB, 48091136 bytes, 93928 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop14: 45.93 MiB, 48160768 bytes, 94064 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop15: 284 KiB, 290816 bytes, 568 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop16: 304 KiB, 311296 bytes, 608 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop17: 49.83 MiB, 52248576 bytes, 102048 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop18: 238.7 MiB, 250298368 bytes, 488864 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
[COLOR=#000000]rich@rich-Inspiron-3847:~$
```

---

### Post by brevardo2 on 2023-01-21
I also did this as well:
```
rich@rich-Inspiron-3847:~$ df -hT -x tmpfs -x devtmpfs
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sda4      ext4  414G  153G  240G  39% /
/dev/sda2      vfat  512M  5.3M  507M   2% /boot/efi
/dev/sda1      ext4  424G  3.3G  399G   1% /media/rich/a3be214f-1085-473f-a964-30118a8b23f1
```

---

### Post by brevardo2 on 2023-01-21
Sorry for having to take another picture ( see below ) Here is what GParted looks like. I can't seem to take screenshot as I take one and then I don't know how to paste it somewhere in Ubuntu? I hope this helps. I would really like to just take the space from the SDA1 partition and use it on this Partition that I've been working off of. I wasn't sure if GParted would let me tap into that extra space?

---

### Post by ajgreeny on 2023-01-21
Please, as I requested last time, use code-tags for all pasted terminal output.
You can see from the edits I made how much easier it is to read when all columns are lined up properly.

There is a How-to in my signature at the bottom of all my posts.

Thanks for the image of the gparted window which helps a lot.
I'm afraid I don't have time to deal with that at the moment as it is late and I need a clear head to make sure I get my suggestions right.

---

### Post by brevardo2 on 2023-01-21
Okay. No worries. I really appreciate your help.

---

### Post by grahammechanical on 2023-01-22
I would just like to clarify a few things.

We can only boot into a partition that has an operating system in it. The motherboard UEFI settings utility looks in sda2 (EFI Systems Partition - esp) for bootloader code. Grub then looks to sda4 for the Linux kernel. 

Perhaps to really want to access sda1. Yes? If you want to shrink sda1 and enlarge sda4 then you can do that with GParted. You can shrink sda1 from the right to create unallocated space between sda1 and sda4. Then you expand sda4 to the left to take up the unallocated space. This guide will explain how to do it.

[https://gparted.org/](https://gparted.org/)

Regards

P.S. To access sda1 to put files on it and to open those files - use the File Manager (Files)>Other Locations and then click on sda1. It is possible to edit a system configuration file so that other partitions are automatically "mounted" and accessible. That would be a different question.

---

### Post by brevardo2 on 2023-01-22
Okay. This is Great information. I'm going to read the Parted guide and try and shrink the one partition in order to free up space. This would definitely solve my problem. When I do use the system I'm on now I can see the other two SDA's as they are Mounted. However, I can only access files from the smaller one- 83GB. I think this is because I was actually booting on to that 83GB partition initially and it does have an operating system. I am not able to access any files on the other Partition though, even though it too is Mounted and showing up on the side and I can see it. I probably would need to figure out how to edit the configuration in order to move files there. I like the GParted idea though the best. I'll give you an update soon. Thanks again for your assistance.

---

### Post by TheFu on 2023-01-22
> **brevardo2 said:**
> Okay. This is Great information. I'm going to read the Parted guide and try and shrink the one partition in order to free up space. This would definitely solve my problem. When I do use the system I'm on now I can see the other two SDA's as they are Mounted. However, I can only access files from the smaller one- 83GB. I think this is because I was actually booting on to that 83GB partition initially and it does have an operating system. I am not able to access any files on the other Partition though, even though it too is Mounted and showing up on the side and I can see it. I probably would need to figure out how to edit the configuration in order to move files there. I like the GParted idea though the best. I'll give you an update soon. Thanks again for your assistance.

There are lots of different philosophies about partitioning of Linux systems.
Some people use the "1 bug partition" method, and this is what is usually created by the default install.
Long time users will typically split out storage based on the specific use for the storage and so that greater security options can be used where needed.  This is the method I follow.
Of course, for a play system or a system expected to live for just a few months, I don't bother having too many different storage areas.  But for a system I expect to use for 4+ years, I want that storage to be extremely flexible, make non-corrupt backups easier, and be able to resize or move storage around easily.  

This takes a little more time and effort, but I have systems with storage that has been migrated forward from 2005 running.  All the storage is newer and the computer hardware has all been replaced, but the original storage architecture is still working fine.

I also know that I've never guess the size for any specific storage area correctly during the initial install.  I don't think it is possible, at least not for me.  Even for a simple desktop, used by a single user, I initially didn't allocate enough storage and ran out.  Fortunately, I made some smart storage choices during the install which provided tremendous flexibility for the system.  It started with 30GB allocated, then I added another 10G to it later and shared the new allocation across 2 file systems.  Flexibility.  That's possible.

I have a few rules for my storage setups.  You probably don't want to follow them all, but perhaps a few will open your eyes.
1. Put the OS on separate storage from swap, logs, data and user's HOME directories.  In a simplistic world, that would  mean 5 partitions, sized correctly are necessary.  Why?  At some point, the system logs will grow very fast and if the log location runs out of storage and that storage is on 1 huge storage area, then the OS will be unusable. It is bad. Sometimes the OS will lock up.  By putting them to a separate location, it is clear that runaway logging is the issue and 2 commands can get the system to running again as I research the root cause for the issue.  Unix systems don't like full disks.  Dumb users will often download stuff and fill the storage area.  Again, if this is shared with the OS, it can lock up the OS.  Best to always have the places that user's are allowed to create files separate from the OS.   BTW, sometimes, I'm the "dumb user" too.  Best to avoid the issue completely by putting user HOME  directories onto their own storage allocation.

2. When deciding how to allocate storage to a partition, think about backups.  Backups need to be performed for the entire partition while it is frozen, not changing.  Corrupted backups really suck. It is like they don't exist, so best to ensure no corruption can happen.  For end-user files, corruption risk is minimal, since only if the file is being changed at the instant it is being pulled into the backup storage area would cause corruption. highly unlikely.  For the OS, things are a bit different. There are file-based databases all of the OS. We have less and less control over when things run which might change those DBs and if that happens during a backup, ouch.  Inside a Fortune 10 enterprise, I'd check the backups for corruption for my different systems.  It is unsettling to see a failed backup, then dig deeper to find that the package manager DB backup at failed every night for the last 2 weeks.  I mentioned it to the official admin for our 100 systems and he said that error happened on those systems, but that 1 in 20 backups would not be corrupted, so it was fine.  All the other files in the backups were fine, just that 1 wasn't ... for about 3 weeks.  I find that unacceptable for systems that I manage.

3. When a file system is mounted, there are different options which can be used to improve security.  For example, it is possible to prevent the setuid flag for any files placed in a user's HOME, if that mount has the nosuid option specified.  This is a huge security consideration.  Don't allow setuid flags on files that shouldn't have it.  Basically, only the files in the OS should, not files controlled by end-users.  File in /tmp/ need the same protections.  Same idea follows for device files, nodev is the mount option..  Those should only be allowed in the OS.  And purely data storage shouldn't be allowed to have programs, so the noexec flag is needed on those storage mounts.  These 3 options are mount options, so they can only be set at mount time, which can only happen at a file system level ... in simple partitioning, that's a partition.  Linux has more advance volume management tools, so a partition isn't the only method, but the mounts of those spaces are limited to the mount options for the file system.  From my notes:
  /home nodev,nosuid
  /tmp  nodev,nosuid,noexec
  /var  nodev,nosuid,noexec
Of course, / is allowed suid, exec, and dev files. We want our OS to boot and run, after all.

4. I don't allow any file system to be larger than my backup storage can support.  If I can't backup the primary storage, then I don't want it.

5. Always use GPT partition tables.  Always.  Avoid MBR/MSDOS partition tables.

6. My typical sizes for different partitions are:
```
# Part  mount           part_type       fs_type size
1       /boot/efi       EFI             fat32   50MB (dual+boot needs more)
2       /boot           LINUX           ext2    600MB
3       LVM             LVM             na      Remaining storage
 root   /               LV              ext4    35GB
 home   /home           LV              ext4    40GB
 var    /var            LV              ext4    1GB
 swap   swap            LV/SWAP         swap    4.1GB
```
Those are my initial targets. Each system has those sizes tweaked a bit, especially /var and /home.  I've never needed to touch the swap ro root / storage areas.  Larger EFI areas can be needed if you dual, tri, quad boot. I don't, so 50MB is almost 10x larger than I've ever needed. 6.1MB is what my EFI partition is using on a new 20.04 system. I feel foolish allocating 50MB and I think Ubuntu's default will allocate 500MB for it. No clue why.

There are things about those above which wouldn't be good for someone doing a simple partitioning setup.  That list has 7 partition and sizing all of those correctly during the install would be hard.  For example, /var/ at 1GB is just to get started.  With snap packages and lxd containers, both want to use /var/ for storage, 1GB would never be sufficient.  Maybe start with /var/ sized at 10G and hope for the best?  On a new 20.04 system here, /var/ is using 26GB and allocated 35GB total.  I need to look into why that is.

The OS at 35G is generous for most needs, I've found. On another system, the OS is using 22G, but has 32G allocated. Plenty of extra room, especially since 5% is reserved for the OS/root use by default in most file systems. The system will prevent users from using that last 5% of storage so the OS has a little breathing room for human mistakes.  5% of 400G .... that's 20G effectively wasted.  5% of 35G is 1.75G, much more reasonable for emergency needs by the OS.

Those are my main rules.  There are reasons for each, even if I didn't spell them all out.  I'd post some concrete examples, but I don't really use partitions as my storage for file systems. I use LVM and posting some of that would likely confuse someone really new to this stuff.  I think having a separate /boot partition isn't mandated anymore, but it used to be. Booting from an LVM /bool/ LV is something I've not tried, ever.  It would make for a much cleaner and more flexible setup. I need to try it in a test area before I do it in production.

Anyway, hope this is helpful and not too confusing.  At least you've seen some options.

---

### Post by brevardo2 on 2023-01-24
I was able to unallocated and shrink sda1 drive down to about 10 GB from around 463GB. However, I tried to then expand SDA4 which is the Operating System that I'm working from and running GPArted on. However it is giving me Error messages as it says I need to "Unmount" this drive before it can expand it. I try to Unmount and it's telling me Target is Busy ( see attached photos below ) Do I need to do it another way? GPArted seems like it should be easy to use but its really not?

---

### Post by TheFu on 2023-01-24
Partitions that are mounted cannot be modified.
Boot into a "Try Ubuntu" flash drive (aka Desktop installer) and make the partition changes.

If the UUID for the partition changes, then the /etc/fstab file will need to be updated for the new/changed UUIDs. Do this from the "Try Ubuntu"  boot too.  If you don't delete or add partitions, then the UUID shouldn't change, but it is easy to check to be certain.

---

### Post by brevardo2 on 2023-01-29
I'm sorry I haven't replied back in a few days. I have good news! I was able to shrink the SDA1 partition down to 10GB and that allowed me to have an additional 425GB of Unallocated space. I then rebooted my Computer with the USB Version of Ubuntu ( which I initially used to install the Operating system ) Once I was using the USB disk version and not Operating on my sda4 partition I was able to then open GParted and successfully expand my SDA4 partition. It went from about 460GB to around 820GB. It works great! I really appreciate the great support from the members of this community.

---

