---
title: "[SOLVED] Server not booting (grub or kernel issue)"
date: 2008-08-14
forum: Server Platforms
---

### Post by chrislynch8 on 2008-08-14
Hi,

I edited my menu.lst file to ask me for a vga settings. I ran the update-grub command and rebooted the server.

On the reboot it freezes and these are the last couple of messages I get.

[I][B]RAMDISK: Compressed image found at block 0
RAMDISK: ran out of compressed data
invalid compressed format (err=1)
VFS: Cannot open root device "md0" or unknown-block(0,0)
Please append a correct "root=" boot option
Kernal panic - not syncing: VFS: Unable to mount fs on unknown-block(0,0)[/B][/I]

I have found alot of this using google but nothing that I could make sense of or use to work around, alot of what I found assumes that I can get into the machine and edit files.

Rgds
Chris

---

### Post by logos34 on 2008-08-14
Boot the live cd, mount / and post your menu.lst...looks like an error crept in to your 'kernel' line

---

### Post by chrislynch8 on 2008-08-14
Hi,

I have it sorted now. When I made changes to the menu.lst and ran update-grup and update-initramfs -u something was corrupt.

I compared the few files to a backup we had and the initrd.img file in my server was half the size of my backup file.

i just used Knoppix and copied in the backup and rebooted and it worked..

Rgds
Chris

---

### Post by TreeFinger on 2008-08-14
Next time you are editing your menu.lst you could write to a floppy or USB drive and test the configuration first. May save you some trouble next time.

---

