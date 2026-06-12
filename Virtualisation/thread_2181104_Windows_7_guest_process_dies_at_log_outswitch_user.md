---
title: "Windows 7 guest process dies at log out/switch user"
date: 2013-10-16
forum: Virtualisation
---

### Post by iLikeStrongJava on 2013-10-16
I have a Ubuntu 12.04 host running several guests using qemu/kvm.  All of the running guests are Ubuntu-based except one which is Windows 7 Professional. Windows guest has software installed but no changes to OS, and the latest software updates have been applied.  I manage the guests through Virtual Machine Manger 0.9.1.  

The problem is that every time I log off the Windows guest or switch users, the VM dies, and I have to start it in VMM again.  

When the guest dies, libvirtd.log simply reports:  1680: error : qemuMonitorIORead: 513 : Unable to read from monitor: Connection reset by peer

The guest machine's log reports: shutting down

Thinking that perhaps pGina 1.6 was causing the problem, I uninstalled it but still have the same behavior.  

Any help in what I should look into next to solve this problem would be greatly appreciated.

---

### Post by iLikeStrongJava on 2013-10-24
Well, I couldn't come up with anything easier to try so I rebuilt the vm and I've reinstalled pGina and it seems to be working.  I haven't activated Windows yet, nor have I installed the software I was using on the computer.  Those steps are today.

---

