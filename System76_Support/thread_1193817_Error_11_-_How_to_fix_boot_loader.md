---
title: "Error 11 - How to fix boot loader?"
date: 2009-06-21
forum: System76 Support
---

### Post by gruntlips_ on 2009-06-21
This one is killing me. I did a routine update via update manager.  It asked for a reboot and I did so.  Then I received an Error 11, Unrecognized Device String.  I cannot boot at all under any of the options.  That was two days ago. I have no idea how to fix this. I am trying to boot from a live cd to reinstall grub into my MBR as per the first set of instructions in this link.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Using%20the%20Ubuntu%20Desktop/Live%20CD](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Using%20the%20Ubuntu%20Desktop/Live%20CD)

However, when booting with the live cd I am presented with these options at the splash screen:
Install Ubuntu
Boot from first hard drive
Rescue Broken System

My questions are:
1) How do I repair this error 11 in grub?
2) If I do repair it by reinstalling grub onto my MBR as per the first set of instructions in the link, how do I "Boot the Desktop Live CD and then open a terminal"?  Should it boot automatically or do I have to select repair broken system?

Thanks.  Any help is strongly appreciated.  At wits end.

I have a serval and am running 9.04 ONLY.

- gl

---

### Post by thomasaaron on 2009-06-22
Make sure you're using a current live CD. It should have an option that allows you to boot into the desktop without changing anything on your disk.

Once in the live session, you can open a terminal by going to Applications > Accessories > Terminal in the menu.

Then you can run the commands in the tutorial.

(I've never used "Fix a Broken System" before. But you might just boot into it and see if it brings you to a command prompt. If it does, you should be able to just run the commands in the tutorial from there.)

---

### Post by gruntlips_ on 2009-06-26
Thanks Thomasaaron, I had originally downloaded the alternate desktop by mistake which did not a straight boot option.  I downloaded the normal desktop live cd and tried reinstalling grub by opening a terminal and typing:

sudo grub
find /boot/grub/stage1
root (hd0,0)
setup (hd0)
quit

then rebooting.  However, the Error 11, Unrecognized Device String still persists and I cannot boot into my system.  

Any ideas on how to fix this? I really appreciate it.

- gl

---

### Post by gruntlips_ on 2009-06-26
Also, when I got look at or edit the /boot/grub/menu.lst file after reinstalling grub it is not there.  This didn't make sense either.

- gl

---

### Post by thomasaaron on 2009-06-26
Now when you were searching for /boot/grub/menu.lst, were you looking at the live CD's filesystem, or did you mount the hard drive partition and search for it?

If it's not on the filesystem contained on the actual hard drive, *that* is a serious problem. The live CD doesn't have a menu.lst, I don't think.

Can you boot from a live CD, go to Places > {and click on one of your hard drive partitions} and try again to find /boot/grub/menu.lst and post it's contents here?

---

### Post by gruntlips_ on 2009-06-26
You were correct.  The boot folder is on /sda1 I think.  Sorry about that.  The kernel portion of the menu.lst is posted below.  Here also is my file structure from fdisk:

title		Debian GNU/Linux, kernel 2.6.28-13-generic
root		d3fa23bc-bd25-4d02-ae37-273061790fbc
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=d3fa23bc-bd25-4d02-ae37-273061790fbc ro quiet splash
initrd		/boot/initrd.img-2.6.28-13-generic

title		Debian GNU/Linux, kernel 2.6.28-13-generic (recovery mode)
root		d3fa23bc-bd25-4d02-ae37-273061790fbc
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=d3fa23bc-bd25-4d02-ae37-273061790fbc ro single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Debian GNU/Linux, kernel 2.6.28-11-generic
root		d3fa23bc-bd25-4d02-ae37-273061790fbc
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d3fa23bc-bd25-4d02-ae37-273061790fbc ro quiet splash
initrd		/boot/initrd.img-2.6.28-11-generic

title		Debian GNU/Linux, kernel 2.6.28-11-generic (recovery mode)
root		d3fa23bc-bd25-4d02-ae37-273061790fbc
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d3fa23bc-bd25-4d02-ae37-273061790fbc ro single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Debian GNU/Linux, kernel memtest86+
root		d3fa23bc-bd25-4d02-ae37-273061790fbc
kernel		/boot/memtest86+.bin

and....

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1824    14651248+  83  Linux
/dev/sda2            1825        2310     3903795   82  Linux swap / Solaris
/dev/sda3            2311       24321   176803357+  83  Linux

---

### Post by gruntlips_ on 2009-06-26
OK, I noticed that the root line under the first kernel in my grub file is a string of letters and numbers that looks like gibberish.  I temporarily changed this by pressing e during the boot and then editing the line to say:

root (hd0,0)

because my root drive is /dev/sda1.  My serval booted, slowly - but it worked.  I assume I should now edit my menu.lst file to make this change permanent.

Is the likely cause of this error some update via synaptic either to grub itself or a kernel update that just messed up my menu.lst file somehow? Or should I be worrying about deeper more horrible things......

Thanks!

- gl

---

