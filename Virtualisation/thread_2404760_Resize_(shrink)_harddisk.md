---
title: "Resize (shrink) harddisk"
date: 2018-10-28
forum: Virtualisation
---

### Post by panja on 2018-10-28
I'm running Ubuntu 18.04.1 LTS on a VMware ESXi host.
At the moment the drive I assigned to the virtual machine is 30GB.
I want to shrink this to 20GB.

How can I shrink the size in Ubuntu (using LVM)?

---

### Post by howefield on 2018-10-28
Thread moved to the "*Virtualisation*" forum.

---

### Post by Dennis N on 2018-10-28
There is a utility named **virt-resize** that will resize a virtual machine's disk. More complicated than you might think. Information:

[http://manpages.ubuntu.com/manpages/xenial/man1/virt-resize.1.html](http://manpages.ubuntu.com/manpages/xenial/man1/virt-resize.1.html)
[http://libguestfs.org/virt-resize.1.html](http://libguestfs.org/virt-resize.1.html)

I used it just once, to expand a virtual machine disk; but from the references, you can reduce them as well.  
Note: The one I expanded was in a KVM/QEMU virtual machine, and not on VMware or VirtualBox.

---

### Post by panja on 2018-10-28
Isn't there an easier way to do this?
To be honest I think it's pretty damn hard to shrink an Ubuntu LVM disk.
Even Windows is pretty straight forward doing this...

---

