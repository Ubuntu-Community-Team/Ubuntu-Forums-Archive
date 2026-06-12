---
title: "Reread SCSI devices"
date: 2008-02-25
forum: Server Platforms
---

### Post by BillDozer on 2008-02-25
Hi,

I have a DLT tape device, that is connected via an SCSI cable. I do not have it on all the time. But when I turn the power on, the device is not automatically registered in the system is there a command that can read the devices.

BTW.: it works ok when i start my server when  the device is turned on.

Thanks in advance.

---

### Post by Brazen on 2008-02-25
You might try running this:
[http://www.garloff.de/kurt/linux/rescan-scsi-bus.sh](http://www.garloff.de/kurt/linux/rescan-scsi-bus.sh)

It's just a bash script.  You save it, make it executable and then run it.  If you want it to scan devices higher than id 7, then you need to add the -w switch.  I've used it in the past after hotswapping scsi harddrives and it worked fine.

---

### Post by BillDozer on 2008-02-26
Thanks,

I haven't tried it yet, but looked at the source and it looks very complete.

Thank you.

---

