---
title: "Installing Windows XP alongside Ubuntu"
date: 2009-05-11
forum: System76 Support
---

### Post by farruinn on 2009-05-11
I need to install Windows XP alongside my Ubuntu install on my Serp4.  I have resized my ubuntu partition and created an NTFS partition at the beginning of the disk with the ubuntu live CD.  Unfortunately when I try to start the windows installer it loads all of its libraries but then complains that it can't find a hard disk.  Thinking perhaps it can't see the hard drive because it is SATA I tried specifying that I need to install "special SCSI or RAID drivers" - it paused, I inserted the JFL92 driver CD, but then the Windows installer said it couldn't find a floppy drive and asked for the install CD.

So, at this point I don't know if the Windows installer can't see the Ubuntu drive because of hardware or because I have Ubuntu installed.  I have to admit I am not a very savvy Windows user! I've always used Macs and Linux so if anyone has suggestions I would very much appreciate it.

---

### Post by thomasaaron on 2009-05-11
Ubuntu being there definitely isn't the problem.

Try going into your BIOS and disabling AHCI mode.

If that doesn't work, you may have to slipstream the sata drivers into you installation cd.

Also, you're following this tutorial, right?
[http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine](http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine)

---

### Post by farruinn on 2009-05-11
Thank you, turning off AHCI was exactly what I needed. And sorry, I wasn't able to follow your link as I was behind content filtering router that identifies the wiki as "personal pages" or somesuch. The directions for re-enabling Grub will be useful though.

---

### Post by thomasaaron on 2009-05-12
**Reinstall GRUB Bootloader and MBR (Master Boot Record)**

Pop in that Ubuntu Desktop Install Disk and Boot to it again.
Open a Terminal - Applications > Accessories > Terminal (One command per line)

```
sudo grub
root (hd0,0)
setup (hd0)
quit
```

Reboot - Grub will now allow you to boot into Ubuntu but not Windows - One more step. Boot into Ubuntu.

```
sudo gedit /boot/grub/menu.lst
```

Add the following lines to the bottom of the file

```
title Windows
root (hd0,1)
chainloader +1
```

Reboot and you're all done! Press escape when you see GRUB to boot into your Windows partition.

---

### Post by adamkittelson on 2009-05-13
I ordered a Pangolin last week, haven't received it yet, but I wanted to say that the turorial was very helpful in setting up my desktop to dual boot Ubuntu and Windows 7 RC. :D

---

