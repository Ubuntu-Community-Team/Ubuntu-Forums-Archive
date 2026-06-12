---
title: "Soft RAID1 problems (invalid raid superblock magic)"
date: 2008-08-25
forum: Server Platforms
---

### Post by toshko3 on 2008-08-25
Hi all,
I am ... let's say a sys admin, and I have this little problem every time I build a mirror with mdadm. I build it by the ubuntu install and there come the problems. The ubuntu version is 8.04.1, but it happens with 7.10 too. I am a little scared about the data on this raid because i use it everywhere. So this is the exact problem: install, configure raid1 with sda,sdb and the folowing message appears on random basis at the start up screen (this is from the syslog file but the same is shown at the start).

md: md0 stopped.
Aug 25 09:52:54 SupportivoFileserver kernel: [   36.004675] md: invalid raid superblock magic on sda
Aug 25 09:52:54 SupportivoFileserver kernel: [   36.004722] md: sda does not have a valid v0.90 superblock, not importing!
Aug 25 09:52:54 SupportivoFileserver kernel: [   36.004728] md: md_import_device returned -22
Aug 25 09:52:54 SupportivoFileserver kernel: [   36.004960] md: bind<sda2>
Aug 25 09:52:54 SupportivoFileserver kernel: [   36.078227] md: md0 stopped.

After a huge research I didn't find any solution, except that the metadata has to be set to v0.90 so the kernel could work properly. I checked the version and it IS 0.90. I put it also in the mdadm.conf file as a declaration but with no result. I switched the motherboard, assuming it could be the chipset/driver issue, I switched the PSU but with no result. Tested all the HDDs with Seatools and no problems (also they are almost new). I have no ideas what is happening. I would be very grateful if you help me with this!
Thanks!

---

### Post by fjgaude on 2008-08-25
Is the OS on the raid1 array?

What does **sudo mdadm -D /dev/md0** show?

---

### Post by toshko3 on 2008-08-26
> **fjgaude said:**
> Is the OS on the raid1 array?

What does **sudo mdadm -D /dev/md0** show?

mdadm -D /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Sat May 17 17:07:06 2008
     Raid Level : raid1
     Array Size : 146480576 (139.69 GiB 150.00 GB)
  Used Dev Size : 146480576 (139.69 GiB 150.00 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Aug 26 09:04:51 2008
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 238bedb9:81c82c3b:ab7016b1:7c803cea
         Events : 0.36

    Number   Major   Minor   RaidDevice State
       0       8        2        0      active sync   /dev/sda2
       1       8       18        1      active sync   /dev/sdb2

The strange thing is that now the raid is ok even after the error occurs. I had this problem in other systems too and didn't solve it yet. It started to occur in 7.10 and later for me. This is other helpful output I believe:
mdadm --examine /dev/sda2
/dev/sda2:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 238bedb9:81c82c3b:ab7016b1:7c803cea
  Creation Time : Sat May 17 17:07:06 2008
     Raid Level : raid1
  Used Dev Size : 146480576 (139.69 GiB 150.00 GB)
     Array Size : 146480576 (139.69 GiB 150.00 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Tue Aug 26 09:06:34 2008
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 100d5f30 - correct
         Events : 0.36


      Number   Major   Minor   RaidDevice State
this     0       8        2        0      active sync   /dev/sda2

   0     0       8        2        0      active sync   /dev/sda2
   1     1       8       18        1      active sync   /dev/sdb2
root@SupportivoFileserver:~# sudo mdadm --examine /dev/sdb2
/dev/sdb2:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 238bedb9:81c82c3b:ab7016b1:7c803cea
  Creation Time : Sat May 17 17:07:06 2008
     Raid Level : raid1
  Used Dev Size : 146480576 (139.69 GiB 150.00 GB)
     Array Size : 146480576 (139.69 GiB 150.00 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Tue Aug 26 09:06:34 2008
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 100d5f42 - correct
         Events : 0.36


      Number   Major   Minor   RaidDevice State
this     1       8       18        1      active sync   /dev/sdb2

   0     0       8        2        0      active sync   /dev/sda2
   1     1       8       18        1      active sync   /dev/sdb2
Thanks for the reply!

---

### Post by toshko3 on 2008-08-26
> **fjgaude said:**
> Is the OS on the raid1 array?

What does **sudo mdadm -D /dev/md0** show?

Oh I forgot, the OS is not on the raid1 array, after reading other recommendations about this. This is some more useful output:
root@SupportivoFileserver:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             8.4G  637M  7.8G   8% /
varrun                252M  200K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M   80K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
/dev/md0              140G   85G   56G  61% /home
/dev/md1              466G   33M  466G   1% /media/mirror500
/dev/sde1             299G   33M  299G   1% /media/wd320

root@SupportivoFileserver:~# fdisk -l /dev/sda

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02820282

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1094     8787523+  83  Linux
/dev/sda2            1095       19330   146480670   fd  Linux raid autodetect
/dev/sda3           19331       19457     1020127+  82  Linux swap / Solaris

root@SupportivoFileserver:~# fdisk -l /dev/sdb

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x29cd29cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1094     8787523+  83  Linux
/dev/sdb2            1095       19330   146480670   fd  Linux raid autodetect
/dev/sdb3           19331       19457     1020127+  82  Linux swap / Solaris
](*,)

---

### Post by fjgaude on 2008-08-26
Goah, I don't know what to suggest... everything looks as it should.

Suggest you backup the important data onto another media, drive.

---

