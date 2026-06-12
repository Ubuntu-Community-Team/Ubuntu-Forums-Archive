---
title: "Single HDD (installed on) -&gt; Dual HDD RAID 1 migration"
date: 2011-06-17
forum: Server Platforms
---

### Post by craigcrawford114 on 2011-06-17
Hi,

I'd like advice on how to migrate all of my data from a single HDD to two new disks in RAID 1.

I'm a fairly apt Linux user but this is something I've never had to toil in.

I'll be purchasing the drives and then they'll arrive at the datacenter, be installed and ready for me to start configuring them.

How would I go about configuring the RAID 1 array, copying all my data to it, and then setting it as the boot device?

I'm running Ubuntu Linux 11.04 (Linux 2.6.38-8-server on x86_64).

Thank you in advance.

---

### Post by YesWeCan on 2011-06-18
Hi. How much detail do you need?

Create RAID device using mdadm.
Make it an LVM physical volume in order to create partitions on it.
Copy the contents of your old partitions to it and create a swap partition.
Change partition refs/UUIDs  in fstab.
Install Grub to the RAID device, setting the boot partition to be the RAID root partition

---

### Post by craigcrawford114 on 2011-06-18
A little bit more verbosity such as, how would I go about copying?
```
sudo cp -R / /mnt/md0
```
Or would that not be a wise thing to do?

What do I change the UUIDs to?
How do I install GRUB on the RAID array and ensure it boots?

---

### Post by YesWeCan on 2011-06-18
There are quite a lot of details involved. I recommend you take it step by step and Google for tutorials such as:
how to create a RAID1
how to copy a Ubuntu root partition
how to re-install grub

Then come back with specific questions about things that didn't work. :)

---

### Post by craigcrawford114 on 2011-06-18
> **YesWeCan said:**
> There are quite a lot of details involved. I recommend you take it step by step and Google for tutorials such as:
how to create a RAID1
how to copy a Ubuntu root partition
how to re-install grub

Then come back with specific questions about things that didn't work. :)
Probably a good set of steps to take. I can always fall back on booting from the original drive if things do go horribly wrong ;).

---

### Post by craigcrawford114 on 2011-06-18
I'm not having much luck.

I tried following (on a virtual machine):
[http://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-system-incl-grub2-configuration-ubuntu-10.04](http://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-system-incl-grub2-configuration-ubuntu-10.04)

While changing it around a bit (in order to accommodate two new HDDs rather than the addition of one).

But when I reboot I get an error from grub saying it can't find two files.

---

### Post by craigcrawford114 on 2011-06-18
I believe I've sorted it, seems like the Ubuntu guide is outdated so I followed the debian guide: [http://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-system-incl-grub2-configuration-debian-squeeze-p3](http://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-system-incl-grub2-configuration-debian-squeeze-p3)

and it seems to boot from the arrays!

---

### Post by YesWeCan on 2011-06-18
Well done! :)

---

### Post by craigcrawford114 on 2011-06-18
This is the exact steps I took for anyone needing them:
**1 (install mdadm and set up kernel modules):**
```
apt-get install mdadm
modprobe linear
modprobe multipath
modprobe raid0
modprobe raid1
modprobe raid5
modprobe raid6
modprobe raid10
```

**2 (set up RAID partitions on first drive):**
```
fdisk /dev/sdb
n, p, 1, default, 31, a
n, p, 2, default, +2G
n, p, 3, default, default
t, 1, fd, t, 2, fd, t, 3, fd
w
```

**3 (copy RAID partitions to second drive):**
```
sfdisk -d /dev/sdb | sfdisk --force /dev/sdc
```

**4 (set up the mdadm devices):**
```
mdadm --create /dev/md0 --level=1 --raid-disks=2 /dev/sdb1 /dev/sdc1
mdadm --create /dev/md1 --level=1 --raid-disks=2 /dev/sdb2 /dev/sdc2
mdadm --create /dev/md2 --level=1 --raid-disks=2 /dev/sdb3 /dev/sdc3
```

**5 (set up the filesystems):**
```
mkfs.ext4 /dev/md0
mkswap /dev/md1
mkfs.ext4 /dev/md2
```

**6 (set up mdadm auto configure):**
```
mdadm --examine --scan >> /etc/mdadm/mdadm.conf
```

**7 (mount the mdadm devices):**
```
mkdir /mnt/md0
mkdir /mnt/md2
mount /dev/md0 /mnt/md0
mount /dev/md2 /mnt/md2
```

**8 (set up fstab):**
```
nano /etc/fstab
```
Edit so /, /boot and swap point to the arrays.
```
/dev/md2	/	ext4		errors=remount-ro	0	1
/dev/md0	/boot	ext4		defaults		0	2
/dev/md1	none	swap		sw			0	0
```

**9 (set up mtab):**
```
nano /etc/mtab
```
Edit so that / and /boot point to the arrays.
```
/dev/md2 / ext4 rw,errors=remount-ro 0 0
/dev/md0 /boot ext4 rw 0 0
```

**10 (set up grub2 custom entry):**
```
cp /etc/grub.d/40_custom /etc/grub.d/09_swraid1_setup
nano /etc/grub.d/09_swraid1_setup
```
Add to the bottom:
```
menuentry 'Ubuntu, with Linux 2.6.38-8-server' --class ubuntu --class gnu-linux --class gnu --class os {
		recordfail
		insmod raid
		insmod mdraid1x
		insmod ext2
        set root='(md/0)'
        linux   /vmlinuz-2.6.38-8-server root=/dev/md2 ro quiet
        initrd  /initrd.img-2.6.38-8-server
}
```

**11 (set up grub2):**
```
nano /etc/default/grub
```
Uncomment:
```
GRUB_DISABLE_LINUX_UUID=true
```

**12 (update grub2 and initrd):**
```
update-grub
update-initramfs -u
```

**13 (copy the data over to the RAID array):**
```
cp -dpRx / /mnt/md2
cd /boot
cp -dpRx . /mnt/md0
```

**14 (install grub2 on the RAID array member disks):**
```
grub-install /dev/sdb
grub-install /dev/sdc
```

**15 (booting into the RAID environment):**
```
reboot
```
set boot device in BIOS to a RAIDed disk and continue booting.

**15 (remove the grub2 custom entry (no longer needed)):**
```
rm /etc/grub.d/09*
update-grub
update-initramfs -u
```

**16 (ensure grub2 is installed on the RAID array member disks one last time):**
```
grub-install /dev/sdb
grub-install /dev/sdc
```

**17 (finish up):**
```
reboot
```

---

### Post by tgalati4 on 2011-06-18
Nice tutorial.  Although I would have set up the drives differently:

For 1 TB drives:

Drive 1

20 GB Boot/OS partition
980 GB RAID1 Data partition

Drive 2

20 GB Boot/OS partition (rsync'd once a week or once a month)
980 GB RAID1 data partition

By keeping the OS out of the RAID, you have more options for troubleshooting.  By rsyncing the Boot/OS partition you have a weekly or monthly snapshot that you can either boot from directly or you can use for comparison and troubleshooting.

With your current configuration, when the RAID fails, you won't be able to boot; you will have to use a Live CD and not have any of your configuration or services set up.

---

### Post by YesWeCan on 2011-06-19
For general info:
An alternative rather than having 3 arrays, one could have one array and use LVM to subdivide it into 3 or more partitions. LVM is a lot more flexible. I am not sure what the relative performance is.

I have my OS on the RAID because I dont want any loss of service if I lose a disk. I havent found any problems with this myself.

Strictly speaking, swap doesnt have to be on a raid. Normally swap isnt used anyhow so losing it probably wont stop your system working unless it is using swap space when swap is lost. I am not sure how the OS would deal with that scenario.

---

### Post by craigcrawford114 on 2011-06-19
> **tgalati4 said:**
> Nice tutorial.  Although I would have set up the drives differently:

For 1 TB drives:

Drive 1

20 GB Boot/OS partition
980 GB RAID1 Data partition

Drive 2

20 GB Boot/OS partition (rsync'd once a week or once a month)
980 GB RAID1 data partition

By keeping the OS out of the RAID, you have more options for troubleshooting.  By rsyncing the Boot/OS partition you have a weekly or monthly snapshot that you can either boot from directly or you can use for comparison and troubleshooting.

With your current configuration, when the RAID fails, you won't be able to boot; you will have to use a Live CD and not have any of your configuration or services set up.

I'll be using rsnapshot to backup to a HDD that is separate from the array anyway :-).

---

