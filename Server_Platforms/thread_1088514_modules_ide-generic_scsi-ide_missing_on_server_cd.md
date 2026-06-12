---
title: "modules ide-generic scsi-ide missing on server cd?"
date: 2009-03-06
forum: Server Platforms
---

### Post by scotty64 on 2009-03-06
I am trying to install Ubuntu 8.10 server on an older machine. The machines CDROM is not detected and I found in the forums that the generic IDE modules have to be loaded in order to do that. The problem is that any attempt to load one these modules with modprobe fails with a "not found" error. I checked the /lib/modules and I cannot find any of these modules there. Only a "cdrom" module - the one and single option offered in the "select a module for your CDROM" dialog.
thanks for any help, Mark

---

### Post by matey3 on 2009-03-06
I wonder if you have any thing in /media directory ?

BTW not really a solution but does the machine have any USB ports?
If so may be you can use a USB stick? Linux is really good about detecting those. like I said this i not a solution really but may be allow you to load modules or run the whole CD from there?

---

### Post by scotty64 on 2009-03-06
> **matey3 said:**
> I wonder if you have any thing in /media directory ?

BTW not really a solution but does the machine have any USB ports?
If so may be you can use a USB stick? Linux is really good about detecting those. like I said this i not a solution really but may be allow you to load modules or run the whole CD from there?

Thats a good idea, but I "solved" the problem by trying out 8.04 server. The "Hardy Heron" server CD contained the missing modules and the install is running without problems. So I think they forgot the module on the 8.10 server cdimages. No problem for me now as I generally prefer LTS releases.

I will probably file a bug about this.

---

