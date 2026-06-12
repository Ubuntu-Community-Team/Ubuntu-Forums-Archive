---
title: "ubuntu server 9.10 fails to start ureadahead-other status 4"
date: 2010-04-13
forum: Server Platforms
---

### Post by FranJPR on 2010-04-13
Hi,

My ubuntu server was working normally but it suddenly failed to start, stopping after the following message:
init: ureadahead-other main process (587) terminated with status 4
 after this message, the system halts and does not finish the start up processes.
 

If I start the server in recovery mode, I get:
init: ureadahead-other main process (587) terminated with status 4
[ 21.892940] ACPI: I/O resource w83627hf [0x295-0x296] conflicts with ACPI region HWMI [0x295-0x296]
 the system also halts and does not start.
 Right now, I can not use the server at all. Any idea how to fix it?.
 
Thanks

---

### Post by cdenley on 2010-04-13
Try turning off acpi.

[https://help.ubuntu.com/community/Grub2#Editing%20Menus%20During%20Boot](https://help.ubuntu.com/community/Grub2#Editing%20Menus%20During%20Boot)

On the line that starts with "linux" add "acpi=off" to the end.

---

### Post by FranJPR on 2010-04-14
I added acpi=off noapic nolapic. I get the same error and it is not able to start. According to this thread [http://ubuntuforums.org/showthread.php?t=1434502](http://ubuntuforums.org/showthread.php?t=1434502) ureadahead-other does not interfere in the boot process. Any idea how to check what is going on?. During boot, process halts when reaches init steps. I do not know how to provide further info.

Thanks

---

