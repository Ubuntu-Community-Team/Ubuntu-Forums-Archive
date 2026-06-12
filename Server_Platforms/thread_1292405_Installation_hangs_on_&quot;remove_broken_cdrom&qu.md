---
title: "Installation hangs on &quot;remove_broken_cdrom&quot;"
date: 2009-10-15
forum: Server Platforms
---

### Post by master_script_maker on 2009-10-15
Hi guys, I'm trying to install Ubuntu 9.04 on my machine. All goes well, but then it hangs on the "final installation" "remove_broken_cdrom" step. I've tried it with multiple disks and all of them ran the disk check fine. Is there anything I can try?

Thanks,
Alex

---

### Post by neil593 on 2009-11-12
I have the same issue installing 9.04 server on PPC hardware (a G4 PowerMac).  There is a thread somewhere here ([http://ubuntuforums.org/showthread.php?t=1239934&highlight=remove_broken_cdrom](http://ubuntuforums.org/showthread.php?t=1239934&highlight=remove_broken_cdrom)) that has a solution but I need to get up and running ASAP so am thinking about trying 8.10 instead.

---

### Post by jamesturner on 2013-03-01
Try the following when the "remove_broken_cdrom" message appears:

ALT+F2 to switch to a new console, then ENTER to activate it
Type the command: killall vol_id
ALT+F1 to switch back to the installer

---

