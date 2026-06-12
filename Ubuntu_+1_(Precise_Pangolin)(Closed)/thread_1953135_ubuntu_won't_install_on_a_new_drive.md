---
title: "ubuntu won't install on a new drive?"
date: 2012-04-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by blm14 on 2012-04-05
I've been running ubuntu 10.04 until now and it finally started acting kind of glitchy so I figured it would be time to install 12.04. I have two SATA drives and I added a third drive and I want to install 12.04 on the brand new 1TB sata drive. I downloaded the 12.04 ISO and used unetbootin to copy the contents to a 2GB flash drive. I can boot from the flash drive and get into ubuntu 12.04 from it. So far, so good.

When I start up the gparted, the new 1TB drive is /dev/sdd. I formatted /dev/sdd1 to ext3 and can mount it.

I click the "install ubuntu 12.04 LTS" icon from the desktop, and when given the chance I select "something else" because I want to leave both of the old drives alone and just install on the brand new 1TB drive.

BUT SDD DOES NOT SHOW UP AS AN OPTION! This is driving me crazy. What the hell am I doing wrong? Bad drive maybe?

---

### Post by ventrical on 2012-04-05
> **blm14 said:**
> I've been running ubuntu 10.04 until now and it finally started acting kind of glitchy so I figured it would be time to install 12.04. I have two SATA drives and I added a third drive and I want to install 12.04 on the brand new 1TB sata drive. I downloaded the 12.04 ISO and used unetbootin to copy the contents to a 2GB flash drive. I can boot from the flash drive and get into ubuntu 12.04 from it. So far, so good.

When I start up the gparted, the new 1TB drive is /dev/sdd. I formatted /dev/sdd1 to ext3 and can mount it.

I click the "install ubuntu 12.04 LTS" icon from the desktop, and when given the chance I select "something else" because I want to leave both of the old drives alone and just install on the brand new 1TB drive.

BUT SDD DOES NOT SHOW UP AS AN OPTION! This is driving me crazy. What the hell am I doing wrong? Bad drive maybe?

Isn't that suppossed to be ext4 filesystem or are you talking about the boot partition?

---

### Post by blm14 on 2012-04-05
I can reformat the new drive as EXT4. Let me try that right now...

---

### Post by ronacc on 2012-04-05
how many drives does it show (drives not partitions )? you may have to format it in a way that you can identify that drive , there is a long standing flaw in the partitioner that ubiquity uses . It does not report the same drive designations as gparted or for that mater as they would be reported by an actual installation , also it does not show drive labels . this can be quite frustrating . did you format the drive with gparted ? I always partition and format with a standalone gparted before I attempt an installation .

---

### Post by ventrical on 2012-04-05
> **blm14 said:**
> I've been running ubuntu 10.04 until now and it finally started acting kind of glitchy so I figured it would be time to install 12.04. I have two SATA drives and I added a third drive and I want to install 12.04 on the brand new 1TB sata drive. I downloaded the 12.04 ISO and used unetbootin to copy the contents to a 2GB flash drive. I can boot from the flash drive and get into ubuntu 12.04 from it. So far, so good.

When I start up the gparted, the new 1TB drive is /dev/sdd. I formatted /dev/sdd1 to ext3 and can mount it.

I click the "install ubuntu 12.04 LTS" icon from the desktop, and when given the chance I select "something else" because I want to leave both of the old drives alone and just install on the brand new 1TB drive.

BUT SDD DOES NOT SHOW UP AS AN OPTION! This is driving me crazy. What the hell am I doing wrong? Bad drive maybe?

One more thing... when  I bought my new 1/2TB SATA HDD I had problems installing Oneiric to the SDD. I had to  load the "live" cd from USB and choose "install to Disk" from the Unity Launcher. Same thing with Precise Alpha2 . Not sure it applies to your situation.

Another thing is that I also had an IDE drive on the same machine and I had to remove the IDE to be able to install on the SDD .. but it worked and I was able to set up a RAID afterwards, and I had to do some BIOS fandangling too.

---

### Post by blm14 on 2012-04-05
Nope that didn't help. If I go into nautilus and mount all my drives:

```

ubuntu@ubuntu:~$ mount
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sda1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdc2 on /media/111dd2d9-8e88-4a42-95dc-0f6435ffebfc type ext3 (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1 on /media/e56ae2ba-ea38-4478-b5e8-f26f4e819d27 type ext3 (rw,nosuid,nodev,uhelper=udisks)
/dev/sdd1 on /media/f10156e5-7e22-4f84-81dc-1e672eba9056 type ext4 (rw,nosuid,nodev,uhelper=udisks)

```

sdb1 and sdc2 are my two old drives and sdd1 is the drive that I want to install 12.04 on to.

So I unmount the three old partitions, I click install ubuntu 12.04 LTS from the desktop, I click "download updates while installing" and "install third party software" and on the next screen the only drives that I see from the dropdown are /dev/sdb, /dev/sdb1, /dev/sdc and /dev/sdc1. /dev/sdd and /dev/sdd1 are not available in the dropdown to install GRUB and nothing under /dev/sdd shows up in the little browse window just above that either

---

### Post by philinux on 2012-04-05
From the usb stick what does;

sudo fdisk -l 

Show.

---

### Post by blm14 on 2012-04-05
> **ronacc said:**
> how many drives does it show (drives not partitions )? you may have to format it in a way that you can identify that drive , there is a long standing flaw in the partitioner that ubiquity uses . It does not report the same drive designations as gparted or for that mater as they would be reported by an actual installation , also it does not show drive labels . this can be quite frustrating . did you format the drive with gparted ? I always partition and format with a standalone gparted before I attempt an installation .

Just the two old 500GB ones. But gparted sees all three, and I can format the new 1TB one from gparted without any problems (in fact I just reformatted it from ext3 to ext4)...

---

### Post by blm14 on 2012-04-05
> **philinux said:**
> From the usb stick what does;

sudo fdisk -l 

Show.

```
ubuntu@ubuntu:~$ sudo fdisk -l 

Disk /dev/sda: 2006 MB, 2006974464 bytes
13 heads, 13 sectors/track, 23194 cylinders, total 3919872 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        8064     3919871     1955904    c  W95 FAT32 (LBA)

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000498c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   953409554   476704746   83  Linux
/dev/sdb2       953409555   976768064    11679255    5  Extended
/dev/sdb5       953409618   976768064    11679223+  82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000687c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63    50331644    25165791    5  Extended
/dev/sdc2        50331645   976768064   463218210   83  Linux
/dev/sdc5             126    50331644    25165759+  82  Linux swap / Solaris

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x49e2fd2f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048  1953523711   976760832   83  Linux
ubuntu@ubuntu:~$ 

```

:-/

---

### Post by blm14 on 2012-04-05
I even tried disconnecting the sata cables from my two old drives and then the ubuntu installer shows only the flash drive. GRRRRRRRRR!!!!!

This is my work machine and I can't get anything done until this problem is resolved <sigh>

---

### Post by blm14 on 2012-04-05
Could this be a problem with GRUB?

---

### Post by ventrical on 2012-04-05
> **blm14 said:**
> I've been running ubuntu 10.04 until now and it finally started acting kind of glitchy so I figured it would be time to install 12.04. I have two SATA drives and I added a third drive and I want to install 12.04 on the brand new 1TB sata drive. I downloaded the 12.04 ISO and used unetbootin to copy the contents to a 2GB flash drive. I can boot from the flash drive and get into ubuntu 12.04 from it. So far, so good.

When I start up the gparted, the new 1TB drive is /dev/sdd. I formatted /dev/sdd1 to ext3 and can mount it.

I click the "install ubuntu 12.04 LTS" icon from the desktop, and when given the chance I select "something else" because I want to leave both of the old drives alone and just install on the brand new 1TB drive.

BUT SDD DOES NOT SHOW UP AS AN OPTION! This is driving me crazy. What the hell am I doing wrong? Bad drive maybe?


 Ya know .. I just remembered that there was a problem with unetbootin .. etc.. somthing or other .. I forget off hand. I am not saying for sure and I don't want you to spend extra down time on this but I always Use Startup Disk Creator to copy the ISO to flash drive. I haven't used Unetbootin in over 2 years .. so I cannot really say if there is a GRUB related problem.

---

### Post by ventrical on 2012-04-05
> **blm14 said:**
> I even tried disconnecting the sata cables from my two old drives and then the ubuntu installer shows only the flash drive. GRRRRRRRRR!!!!!

This is my work machine and I can't get anything done until this problem is resolved <sigh>


On my Intel based motherboard I had to go into the BIOS and set the SATA drive as a primary boot drive , otherwise it would not detect.

Check the back jumpers  on the drive. Could it be that they are still set for factory and not master ??

What type of machine is it?

---

### Post by ventrical on 2012-04-05
I had to have it set in the Hard Disk Boot Priority, otherwise I was not able to get it to recognize/install . I went through this similar thing during Oneiric Ocelot testing.

---

### Post by ventrical on 2012-04-05
I found the old forum where I mentioned my problem with the SATA.

Not sure it will help.
[http://ubuntuforums.org/showthread.php?t=1839945&highlight=install+sata+hard+drive](http://ubuntuforums.org/showthread.php?t=1839945&highlight=install+sata+hard+drive)

---

### Post by ronacc on 2012-04-05
since gparted can see the drive and a live session can see the drive file a bug against parted ( the partitioner ubiquity uses ) .

---

### Post by coffeecat on 2012-04-05
@blm14, since you say that the 1TB drive that is not being seen in the installer is brand-new, this is most likely completely irrelevant, but I'll say it anyway. Even though brand-new, did you set it up in a RAID array before you (re)formatted it and tried to install to it?

Residual RAID metadata on a single drive prevents Ubiquity from seeing it, even though Gparted will.

---

