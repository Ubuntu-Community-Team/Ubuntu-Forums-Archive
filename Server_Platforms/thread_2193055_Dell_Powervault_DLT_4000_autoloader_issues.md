---
title: "Dell Powervault DLT 4000 autoloader issues"
date: 2013-12-11
forum: Server Platforms
---

### Post by devin0 on 2013-12-11
Im looking to make backups to this Dell powervault 120T autoloader. Drive shows up as 2 different devices on boot, the autoloader and the dlt 4000 drive itself.
Upon boot the system hangs, and produces an infinite row of scsi timeout errors.The drive itself keeps an amber "busy" light flashing until i shut the machine off. Not sure what to do from here. I really want to get this working. Drive was working under the windows environment, and passes its start up and calibration tests fine. The machine does not hang when the auto loader is not connected.

Any help is much appreciated.

---

### Post by devin0 on 2013-12-16
Issue is resolved. Settings in my scsi controllers bios were incorrect, parity and termination settings were set incorrectly. Setting them both to Auto fixed the problem.

---

