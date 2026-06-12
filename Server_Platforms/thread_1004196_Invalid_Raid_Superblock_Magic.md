---
title: "Invalid Raid Superblock Magic"
date: 2008-12-07
forum: Server Platforms
---

### Post by sam702 on 2008-12-07
Hello Ubuntu Gurus!

I get an "Invalid Raid Superblock Magic on sda1" error when I boot up.

I have...

ASUS P5Q-EM motherboard (Intel G45 Chipset)
Two identical sata drives on Software Raid 1
Bios setting is AHCI for the sata drives
Ubuntu Intrepid Ibex, Samba fileserver
Headless fileserver setup

I get the error message and it drops out of the shell.  Sometimes when I wait awhile and reboot from the initramfs prompt it still gives me the "invalid raid superblock magic" error, but it still boots.  When it does boots, I check the /proc/mdstat and it says every thing is good with the raid.

I made edits to the /boot/grub/menu.lst to include the rootdelay=90 on the kernel line, but I still run into the error.

I did apt-get update and upgrade and still the problem persists.  How can I resolve this issue?  Please help.

Thanks.

---

### Post by bthessel on 2009-02-15
> **sam702 said:**
> Hello Ubuntu Gurus!

I get an "Invalid Raid Superblock Magic on sda1" error when I boot up.

I have...

ASUS P5Q-EM motherboard (Intel G45 Chipset)
Two identical sata drives on Software Raid 1
Bios setting is AHCI for the sata drives
Ubuntu Intrepid Ibex, Samba fileserver
Headless fileserver setup

I get the error message and it drops out of the shell.  Sometimes when I wait awhile and reboot from the initramfs prompt it still gives me the "invalid raid superblock magic" error, but it still boots.  When it does boots, I check the /proc/mdstat and it says every thing is good with the raid.

I made edits to the /boot/grub/menu.lst to include the rootdelay=90 on the kernel line, but I still run into the error.

I did apt-get update and upgrade and still the problem persists.  How can I resolve this issue?  Please help.

Thanks.

Did you ever find a way to fix this? I am having the same problem.

---

### Post by fjgaude on 2009-02-15
Hard to say what is causing this. I'd try adding a delay here:

Edit this file, adding the sleep line after the **mount**: /usr/share/initramfs-tools/init   # to stop a race condition with md. The line numbers may not be the same for your system.

```
   187 maybe_break mount
   188 sleep 10
   189 log_begin_msg "Mounting root file system..."
```
Then run this to rebuild the image

```
sudo /usr/sbin/update-initramfs -uk all
```

Let us know if this works.

---

