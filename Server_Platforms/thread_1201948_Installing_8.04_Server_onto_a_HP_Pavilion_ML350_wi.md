---
title: "Installing 8.04 Server onto a HP Pavilion ML350 with a HP Smart Array 6400"
date: 2009-07-01
forum: Server Platforms
---

### Post by wjhildreth on 2009-07-01
Hello all,

I am having a problem, though fixed for now, that I need some guidance on.

I have installed twice now Ubuntu 8.04.2 Server on a HP Pavilion ML 350 with a HP Smart array 6404 controller card with the exact same results.

The BIOS is set to an OS of Linux, CDROM is first boot device, First hard disk (set by controller order) is the second boot device.  First boot controller is set to Smart Array 6404.

Before starting I formatted both 36 GB drives in the machine with the SCSISelect utilities and disabled Host RAID on both channels. Next I created a RAID 1 with both drives.

I booted the Server CD and went through the install routine.

When I rebooted to the new system, The BIOS would show attempting to boot from drive C and hang there.

I rebooted the Server CD and went to rescue mode.  I mounted /dev/cciss/c0d0p1 as the root partition. Looking at Grubs menu list it shows the system booting from (hd2,0). I changed this to (hd0,0) and exited the terminal.  I reinstalled GRUB onto /dev/cciss/c0d0 and restarted the machine.

The machine will boot up now, but it gives several buffer IO message on /dev/sda1 then actually boots up.

Once started the system seems fine and running du on / looks to have activity on both drives in the RAID.

I have a couple of questions.

1)  Is there a bug with the grub install portion of the server software or is it my hardware.  How can I find out.

2)  How can I through the terminal know that my mirror is working?

Warm Regards,

Joe H.

---

