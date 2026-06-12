---
title: "Boot failure"
date: 2013-05-31
forum: Virtualisation
---

### Post by mmehra on 2013-05-31
I was running Ubuntu 12.04 on Virtual Box. Due to some failure, the filesystem got corrupted and the VM does not boot now. I tried boot-repair but that did not help either. Following is the pastebin link
 
[http://paste.ubuntu.com/5721706/](http://paste.ubuntu.com/5721706/)

Please help

---

### Post by 2F4U on 2013-06-01
Boot repair doesn't help if the filesystem is corrupted. You should boot from a liveCD and run fsck on the filesystem in question. Note that the filesystem you are attempting to repair must be unmounted (therefore the liveCD):

[http://www.ehow.com/how_5941208_recover-damaged-file-system-ubuntu.html](http://www.ehow.com/how_5941208_recover-damaged-file-system-ubuntu.html)

---

### Post by mmehra on 2013-06-01
Thanks a lot. That solved the issue :-)

---

