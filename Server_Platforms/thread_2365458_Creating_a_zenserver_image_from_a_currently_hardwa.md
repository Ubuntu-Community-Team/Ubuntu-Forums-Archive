---
title: "Creating a zenserver image from a currently hardware installed 16.04 LAMP server."
date: 2017-07-07
forum: Server Platforms
---

### Post by Heeter on 2017-07-07
Hey all

Wondering if this can be done.

Have a stable up to date ubuntu 16.04 LAMP server running.

Bought new servers, and have zen installed on them, with a few new images spun up.

Trying to figure out how move this current into an image 

I did this with WindowsServer a few years back, using systools, located right the Windows Install disc, and it worked like a charm.

Regards

---

### Post by TheFu on 2017-07-07
No special tools needed. Linux isn't Windows and doesn't only install a specific kernel based on the underlying hardware.

Backup your server in the normal way.
Create a new VM under Xen with the virtual hardware you want.
Restore the server in the normal way.

Check that the network device names are ok.  Be happy.

Only issues would be HW tied like RAID cards or proprietary video drivers. Remove those dependencies before starting ... or fix them from a live-boot ISO in the system settings (/etc/ files).  Odd drivers that had to be manually installed on the old hardware are where the issues will be, if any.  Normal network cards, SAS, SATA controllers won't be any issue.

Oh ... and if "zen" isn't really "Xen", then ignore everything I've written.

---

### Post by Heeter on 2017-07-07
Great, Thank you,

I will do that.

Regards

---

### Post by TheFu on 2017-07-07
When planning this migration - do exactly the same thing you would do if moving from an old server to new server with different hardware.  

For example, if the BIOS was legacy and you are moving to EFI ... then you need to handle that.  Tried EFI inside a VM years ago and didn't understand why it didn't work.  Heard that works fine now, but I've never used it.

---

