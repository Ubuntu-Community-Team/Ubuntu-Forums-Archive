---
title: "mdadm booting: md stopped"
date: 2008-07-24
forum: Server Platforms
---

### Post by kriebel on 2008-07-24
Guru's

I happen to have a typical problem with mdadm. I made a dump of my original (Ubuntu 8.04 server) system with dump. The original system had the following RAID1 configuration:

md0	/dev/sda1
	/dev/sdb1

and

md1	/dev/sda2
	/dev/sdb2

I destroyed the original system and booted with sysrescd. I recreated the devices with fdisk en created the RAID array including a mkfs.ext3. Cylinders of the partitions are the same on both disks. The arrays sync without problems (as far as I can see). This all looks good when I do a cat /proc/mdstat. After that I restored the original system with restore on /dev/md0. After the restore I can mount /dev/md0 and a fsck detects no problems. Reinstalled grub without errors. Also changes the UUID number in /etc/mdadm/mdadm.conf on the restored disk with mdadm --detail --scan >> /mnt/custom/etc/mdadm/mdadm.conf.

When booting the system the problem occurs. Grub starts and the system starts to boot. Disk are detected (Attached scsi etc) but right after that I get 4 messages saying: md: md0 stopped and md: md1 stopped. 

Then I get Busybox which tells me:

Check root= bootarg cat /proc/cmdline or missing modules, devices: cat /proc/modules ls /dev

ALERT! /dev/md0 does not exist

md0 and md1 do exist in /dev and cat /proc/cmdline gives root=/dev/md0 ro

I'm probably missing a step in the procedure but I can't figure out which one. Any experts around here who have an idea? Would be very much appreciated ](*,)





p.s. As you can see I'm testing if mdadm is suitable for me in my production environmnts and a disaster recovery is an important issue. Im testing this in a virtualmachine inside Virtualbox but I don't expect it to be an issue in this situation

---

### Post by ihuerta on 2010-09-20
Exact same problem here. Did you ever find a solution?

---

### Post by ihuerta on 2010-09-22
Ok, I found the solution after many many tries. Now I can install Ubuntu Servers with RAID+LVM in minutes :D.

There are some things you have to take into account when you use fsarchiver + Ubuntu Server with RAID1:

- Make sure the partitions flags are right. That means: make sure you have checked the "raid" flag. I'm using the "set" command in parted for this.

- Rebuild the mdadm.conf file correctly. Let's imagine you are in SRCD, you have finisted recovering the FSA and you have mounted the ubuntu root partition in "/mnt/ubuntu" and the boot partition in /mnt/ubuntu/boot. Now execute this magic command:
mdadm --examine --verbose --scan >> /mnt/ubuntu/etc/mdadm/mdadm.confWork is not finished. Edit the file
nano /mnt/ubuntu/etc/mdadm/mdadm.confComment the old lines and check that there are not extra partitions in the new ones (In my case it adds /dev/sda -yes, the whole disk- as a raid partition!).


- Rebuild the initramfs. After some screaming to my computer, I realised that mdadm.conf goes inside the initramfs file. So after editing this file, execute "update-initramfs -u". If you are in SRCD, use "chroot" like this:
chroot /mnt/ubuntu update-initramfs -u 
If someone needs more info, just say!

---

### Post by kriebel on 2010-09-22
Hi ihuerta

Great! Thanks for the reply. For business reasons I had to switch to RHEL but I'll try this for sure.

Rgds, Kriebel

---

