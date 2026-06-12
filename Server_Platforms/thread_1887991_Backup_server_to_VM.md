---
title: "Backup server to VM"
date: 2011-11-28
forum: Server Platforms
---

### Post by schander on 2011-11-28
Hi All,
I'm not sure that this is correct sub-forums for this, but here goes.
I have HP Proliant microserver. The main os (Ubuntu 10.10 x64 server) on a 8gb usb stick, along with 2 x 2TB(raid 1) and 2 x 750gb (raid 1)
Now I would like replicate this entire system on a VM  including the raid 1 arrays (by creating vm hd's of 10% the size). This is to, enable me to test on the vm before installing/upgrading on my live system.

So my question is how do I convert the 8gb usb stick into a vm hd? My preference for VM software is VirtualBox, however I'm flexible if there is a easy solution. I have just come across [this]("http://www.vmware.com/products/converter/resources.html").
However there is no support of OSX, which my main workstation.

Any ideas?

Regards
Satpal

---

### Post by aeiah on 2011-11-28
not that i have any experience with this, but perhaps try using something like clonezilla or remastersys to take a snapshot of your system, and instead of restoring it to a real machine, you restore it to a virtual machine.

---

### Post by haqking on 2011-11-28
clone it with clonezilla and clone it into the VM.

If you intend to clone the raid arrays and intend on them being 1/10th you caannot do that as a clone destination needs to be same size or larger, however you could resize them afterwards.

---

### Post by schander on 2011-11-29
Thanks for the replies.
Will give clonezilla a go.

Satpal

---

### Post by Vegan on 2011-11-29
another idea is to use rsync

---

### Post by schander on 2011-11-29
> **Vegan said:**
> another idea is to use rsync

It's an interesting idea however would need to setup a exclude list, which could be tricky.

Thanks
Satpal

---

