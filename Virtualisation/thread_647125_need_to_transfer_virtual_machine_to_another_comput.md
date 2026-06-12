---
title: "need to transfer virtual machine to another computer with different OS: vmware"
date: 2007-12-22
forum: Virtualisation
---

### Post by systemintheglitch on 2007-12-22
So for some reason (not important) i cant set up a virtual machine within ubuntu so i have to set up the virtual machine in windows or mac and then transfer it to vmware inside ubuntu.i will probably be using vmware sever on both operating systems. How do I do this? It is really a question of how to use vmware server. Is yhere some "export entire machine tosingle file" command?

---

### Post by AndyCooll on 2007-12-22
I would have thought the easiest wat is you to copy the folder containing your virtual machine to an external hard-drive or something like that, and then paste that folder into the folder where your images are on your Ubuntu machine. After that you'd simply need to open it up in your Ubuntu VMware Server app.

:cool:

---

### Post by danpre on 2007-12-23
> **systemintheglitch said:**
> So for some reason (not important) i cant set up a virtual machine within ubuntu so i have to set up the virtual machine in windows or mac and then transfer it to vmware inside ubuntu.i will probably be using vmware sever on both operating systems. How do I do this? It is really a question of how to use vmware server. Is yhere some "export entire machine tosingle file" command?

I have done this before: moving VM from windows host to ubuntu host.
Turn off VM
Compress VM files - most of them will compress very well (especially empty parts of vm disk) it will save a lot of time.
Copy from windows host to ubuntu host (you can use smb shares, ftp, external disk etc)
Uncompress on ubuntu host.
Probably you will have to change file permissions to be able to start vm.
Be carefull with debian virtual machines - I don't know why, but after moving vm to another host it sometimes changes NIC (for example from eth0 to eth1) so you will have to change /etc/network/interfaces.
There is no problems with moving windows xp vm .

---

### Post by TheTechGuy99 on 2011-08-23
I have the same issue but I was wondering what specific files will I need to transfer?

---

