---
title: "HELP - Samba won't start"
date: 2005-01-12
forum: Server Platforms
---

### Post by anund on 2005-01-12
A strange problem has occured. Running Ubuntu 4.10. Samba 3.0.7-Ubuntu

Installing samba via "apt-get install samba", the installation hangs when "Starting Samba daemon".

The log files in /var/log/samba show that nmbd loads fine, but smbd generates this:

[2005/01/12 14:40:28, 0] smbd/server.c:main(760)
  smbd version 3.0.7-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2004
[2005/01/12 14:40:29, 0] lib/fault.c:fault_report(36)
  ===============================================================
[2005/01/12 14:40:29, 0] lib/fault.c:fault_report(37)
  INTERNAL ERROR: Signal 11 in pid 4435 (3.0.7-Ubuntu)
  Please read the appendix Bugs of the Samba HOWTO collection
[2005/01/12 14:40:29, 0] lib/fault.c:fault_report(39)
  ===============================================================
[2005/01/12 14:40:29, 0] lib/util.c:smb_panic2(1456)
  smb_panic(): calling panic action [/usr/share/samba/panic-action 4435]
/etc/samba/gdbcommands:1: Error in sourced command file:
Previous frame inner to this frame (corrupt stack?)
log.smbd (END)


I have checked the disk for errors with fsck, but no corruption was revealed.

smbclient works fine, but I'd really like to install samba as well :)

Any idea? What is wrong?

(I saw another thread on a somewhat similar problem, but that seemed to have been resolved with a hardware error)

anund

---

### Post by anund on 2005-01-21
It seems to me that there is something wrong with the samba_3.0.7-1Ubuntu6.3 package. I removed all the related packages and reinstalled from the Warty CD (samba 3.0.7-1Ubuntu6) and now everything is working perfectly again.

---

### Post by DonnyViszneki on 2007-05-13
gdbcommands is a command-history file placed in the current working directory by the GNU Debugger (gdb) when someone uses it. Somehow it seems to have found its way into the Debian samba-common package:

saltpit:/etc/samba# dpkg -L samba-common | grep gdbcommands
/etc/samba/gdbcommands

It seems that whoever was maintaining the samba-common package accidentally packaged his gdbcommands file. I am not experiencing any problems as a result of having this file, however I suspect that if you simply use this command:

echo > /etc/samba/gdbcommands

..you'll experience relief.

You should file a bug with Debian.

---

