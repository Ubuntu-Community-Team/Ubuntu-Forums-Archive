---
title: "New Serval won't boot."
date: 2010-04-24
forum: System76 Support
---

### Post by reid_rsv869 on 2010-04-24
Hi - I just got my Serval yesterday.  While it originally booted fine and loaded the OS and ran for a few hours, now things are not so great. 

The machine it POSTs fine, but while the OS is loading I get a show-stopper message which says:

"One of more mounts listed in /etc/fstab cannot be mounted: Swap: waiting for uuid=<long alphanumeric string>.  Press ESC to enter recovery shell."

It waits of course.  If I press ESC the screen fades to white then dark then stalls totally.

Interestingly, I have an ubuntu 9.10 disk, and when I put that in the drive and reboot the errors still occur but flash by and the machine runs (more or less) as expected.  Not sure why that works but it does.

What should my next steps be?  Is this an /etc/fstab config error I can fix?  Was this is a system load error or is it hardware?  Or is it just a reload of 9.10?

thanks

Reid

---

### Post by thomasaaron on 2010-04-26
It sounds like you chose to encrypt your home partition during the initial set-up.

Can you boot into recovery mode and then post the output of this command...

cat /etc/fstab | grep -i swap

---

### Post by reid_rsv869 on 2010-04-26
Thanks Thomas.  All is working now.  I did as asked and have rebooted several time. Problem seems corrected.

Below is the corrected /etc/fstab, with the erroneous line entry commented out.  

(FYI the board, bad entry is the second-to-last and show this...."UUID=4dcb7a74.....")

reid@system76-pc:~$ more /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc	/proc	proc	defaults	0	0
# / was on /dev/sda1 during installation
UUID=2c20b79b-bb2c-4422-9d48-d1cc487b189f	/	ext3	errors=remount-ro	0	1	# /dev/sda1
# /home was on /dev/sda3 during installation
UUID=46ad1127-89ed-4d27-886e-3ad3898f9243	/home	ext3	defaults	0	2	# /dev/sda3
# swap was on /dev/sda2 during installation
# UUID=4dcb7a74-0f73-4f1f-9215-a1dcef29549e	none	swap	sw	0	0	# /dev/sda2
/dev/mapper/cryptswap1 none swap sw 0 0
reid@system76-pc:~$ 



much obliged.  

Reid

---

