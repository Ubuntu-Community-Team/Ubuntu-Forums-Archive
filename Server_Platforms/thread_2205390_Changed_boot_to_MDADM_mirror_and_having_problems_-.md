---
title: "Changed boot to MDADM mirror and having problems - can only manual boot system"
date: 2014-02-13
forum: Server Platforms
---

### Post by luminarycrush on 2014-02-13
Hi, I had a disk fail and this encouraged me to move to software RAID1  for my OS drive (already run RAID5 on data drives).  Now I can boot the  system manually from the GRUB command line (option 'c') but the boot  menu/autoboot don't work.

I've tried to edit the GRUB boot options from the boot menu manually using the 'e' command and boot - this fails also.

I have two SSDs I boot from, identical partition layout which is:

p1:  /dev/sd{a,b}1  ext2 (/boot)
p2:  /dev/sd{a,b}2 swap
p3:  /dev/sd{a,b}3 lvm which is then mounted as "/"

To convert to mdadm RAID boot I did the copying of boot block from my  backup image using "dd if=/dev/rootimage.img of=/dev/sda bs=446 count=1"  to avoid overwriting the partition table per Googled instructions on  this.  I copied all the other files in place and was able to boot via  the GRUB 'c' option to manually boot.  I was up and running and then ran update-grub and reinstalled GRUB to both drives,  and update-initramfs.  The boot drive order is set correctly in the BIOS.

To boot using the 'c' option, I type:

set root=(md/100)                                                             <- this is the md for the mirror at /dev/sd{a,b}1
linux /boot/<kernel name> root=/dev/mapper/vg_atlantis1-root          <- this is lv on vg on md of /dev/sd{a,b}3
initrd /boot/<initrd img name>
boot

This works fine.  If I let the system boot normally to the same kernel I  boot to CLI above it just hangs.  If I try to 'e' edit the command line  from GRUB and try to emulate the GRUB CLI syntax I think mimics my  actions it just hangs but I'm not completely clear on the syntax, even  after much Googling.  I've tried about 10 iterations though.

I've tried editing stuff in /etc/grub.d to reflect the system  configuration and repeat the update-grub/install/update process above  and it just hangs.  Some of these attempts have rendered the system  unbootable even via the CLI method I list above, so I re-copy the files  from my backup image to /boot via a rescue USB and then I can use the  CLI to boot again...but that's it.

I installed "Boot Repair", which uninstalled GRUB and re-installed it.   This did not fix the problem.  Boot Repair did create a boot environment  summary, which you can see here:

[http://paste.ubuntu.com/6881171/](http://paste.ubuntu.com/6881171/)

After these update attempts I re-try to 'e' the command line as well - still no luck.  But after all this, the system boots normally using the 'c' option and issuing the commands in GRUB I mentioned above.

Can anyone see what silly thing I'm missing?

---

