---
title: "How do I reduce the size of a VDI?"
date: 2014-03-28
forum: Virtualisation
---

### Post by kschiff on 2014-03-28
I have a Windows guest that is currently 30GB and I have reduced the amount of space it uses within the guest (it's XP). It would be better if it was 15 GB. The original is dynamically allocated and I tried doing:

VBoxManage modifyhd "XP Plain-desk1.vdi --resize 15000

VBoxManage: error: Resize hard disk operation for this format is not implemented yet!

I made a clone with Virtual Disk Manager and changed the allocation to standard, and still get this error.

Is there a way to shrink this?

---

### Post by TheFu on 2014-03-28
If you want 15G, shouldn't that be 15000?
or
you can create a new vHDD of the size you want and use a file system data mirror tool to copy everything over. I'd think a recovery disk will be necessary to correct the boot after - might not be a big deal with XP.

---

### Post by kschiff on 2014-03-28
Yes, you are right regarding the resize error. I fixed that, but I couldn't get this to work either with this command, or various clone/compact  CLI commands in Ubuntu.  I ended up shrinking the partition first in Windows using Easeus partition manager (freeware version) from within the guest (gparted Live didn't work). Then I used the VDIClone tool to clone and compact (in a different Windows virtual machine). Now all is good.

---

