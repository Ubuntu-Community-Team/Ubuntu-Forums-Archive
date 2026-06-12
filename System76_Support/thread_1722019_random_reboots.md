---
title: "random reboots"
date: 2011-04-05
forum: System76 Support
---

### Post by itcave on 2011-04-05
My pc has been randomly rebooting on it's own.  Is there a log file somewhere I can look at that will give a clue as to why this is happening?

Thanks,


Pangolin Performance
panp7

---

### Post by Malcolm Waterman on 2011-04-05
Hello,
        Most of the log files are available from System -> Administration -> Log File Viewer. Since it's rebooting randomly try the debug.*, kern.log.*, messages.*, syslog.*, user.log.* etc.

Also, could you mention how long you've had that computer and where the computer comes from along with the computer's specs.

---

### Post by isantop on 2011-04-05
Go ahead and remove the battery and AC power. Then, remove the large main panel on the bottom of the computer. Be careful, as the fan is attached to the panel and plugged into the motherboard.

Once you have that off, take all of your memory cards out and then reseat them, making sure that they're seated well. Did that fix it?

---

### Post by itcave on 2011-04-10
Since reseating the ram I haven't got a single reboot.  Thanks!

---

### Post by kireeti on 2011-04-10
hey check ur ram .if u have played with it arround try put it properly .

---

### Post by itcave on 2011-04-10
> **itcave said:**
> Since reseating the ram I haven't got a single reboot.  Thanks!

Spoke too soon.  Just rebooted again.

---

### Post by isantop on 2011-04-11
Okay, it may still be a bad RAM module. Go ahead and hold the Shift key immediately after the System76 splash page. This will take you to the Grub menu. Select the MemTest86 option without the Serial console mode, then give that a try.

---

