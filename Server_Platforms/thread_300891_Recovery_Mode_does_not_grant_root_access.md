---
title: "Recovery Mode does not grant root access"
date: 2006-11-16
forum: Server Platforms
---

### Post by gravyface on 2006-11-16
[Apparently]("http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch08.html#gainrootwithoutlogin") you can select Recovery Mode from the GRUB menu, boot, and be granted root access. 
I found myself without root access on my Dapper server -- I accidentally removed my user from the *admin* group that has sudo permissions -- and desperately needed this to work, but it didn't.  However, appending *rw init=/bin/bash* to the boot arguments worked, as per [these instructions]("http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch08.html#id2538744"). 
I'm not discounting PEBKAC here (it was fairly late) but we tried this recovery mode technique several times to no avail; after each time, regardless of hitting CTRL-D to continue or entering into maintenance mode, we were presented with the "normal" login prompt, which afforded no root privileges or sudo to my user after logging in.

---

### Post by lfloyd on 2007-02-03
Did ever figure out how to fix this problem.  I can't login to root in recovery mode after trying to configure samba and gdm to work with Windows Business Server.  Any help would be appreciated

Thanks Loretta

---

### Post by gravyface on 2007-02-03
[These instructions]("http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch08.html#id2538744") from Linuxtopia worked:

8.2. 	

How to modify kernel boot-up arguments, to gain root user access?
	

   1. Boot-up computer
   2. If GRUB menu is hidden, press Esc to enter the GRUB menu
   3. If GRUB password is set, press p to unlock the GRUB menu
   4. Select Ubuntu, kernel 2.6.12-8-386
   5. Press e to edit the commands before booting
   6. Select kernel /boot/vmlinuz-2.6.12-8-386 root=/dev/hda2 ro quiet splash
   7. Press e to edit the selected command in the boot sequence
   8. Add rw init=/bin/bash to the end of the arguments: 
[FONT="Courier New"]grub edit> kernel /boot/vmlinuz-2.6.12-8-386 root=/dev/hda2 ro quiet splash rw init=/bin/bash[/FONT]

   9. Press b to boot

---

### Post by lfloyd on 2007-02-03
Thanks I tried this, but does not work because root user does not exist because password file has been corrupted.  Without a user you can't do anything.  Thanks



Loretta

---

