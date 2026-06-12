---
title: "Ubuntu Server 10.04 frozen at grub boot menu"
date: 2013-10-22
forum: Server Platforms
---

### Post by remush on 2013-10-22
Hi all,

I lost power to the ubuntu server, and when it boots up now, it freezes on the grub boot menu.

the keyboard is non responsive.

I've moved the usb keyboard plug to another port, but that did not work, I've also tried a few other usb keyboards.

Suggestions welcome.

Thanks.

---

### Post by Bashing-om on 2013-10-22
remush; Hi !

Try this:
1. Boot from the Ubuntu Live CD;
2. Open/Run Terminal;
3. Type: sudo fdisk -l (to get the device name) - looking for the partition marked with a "*" in the boot column - then press ENTER;
4. Type: sudo fsck /dev/sda1 - where "sda1" assumes that the "*" is that location, adjust accordingly - this checks and tries to repair the file system - then press ENTER;
5. Restart the system and boot normally.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by remush on 2013-10-28
This system did not have a cd drive, and I could not get the live cd working from usb, so I've replaced the pc with another one with a cd rom drive. And reinstalled.

Everything is working fine, if I get this problem again, I'll try the suggestions here.

thanks to all for your help.

---

### Post by Bashing-om on 2013-10-28
remush; Hey ! That is a solution.

Glad ya up and running.

Please mark this thread as solved, 1st post ->thread tools.
Helps keep the forum tidy.

[INDENT][INDENT]don't be a stranger,
[INDENT][INDENT][INDENT]come back often
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

