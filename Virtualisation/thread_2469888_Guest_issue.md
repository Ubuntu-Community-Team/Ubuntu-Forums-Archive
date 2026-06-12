---
title: "Guest issue"
date: 2021-12-12
forum: Virtualisation
---

### Post by peter-1984 on 2021-12-12
Hi,
Guest VM is with Ubuntu 18.04 and host is Win 2019 server. I shared path of Win server to Guest VM and cannot see the path within Ubuntu. How to resolve it?

---

### Post by KBar on 2021-12-12
It sounds like Guest Additions aren't installed. You're going to have to install it within guest. Consider reading through this documentation: [https://www.virtualbox.org/manual/UserManual.html#sharedfolders](https://www.virtualbox.org/manual/UserManual.html#sharedfolders)

---

### Post by peter-1984 on 2021-12-13
Guest addition is installed properly but the files I've copied into the same shared path, are not avaialble to the host machine.

---

### Post by wildmanne39 on 2021-12-13
Moved to virtualization sub-forum.

---

### Post by QIII on 2021-12-13
Is the shared path the same as what you  are asking about in [this]("https://ubuntuforums.org/showthread.php?t=2469889") thread?

---

### Post by peter-1984 on 2021-12-13
No, I also tried to share one path (from host) to the VM, but I cannot see files within VM, after I've copied files into the path from host machine.

---

### Post by MAFoElffen on 2021-12-14
I'm a little behind in reading this and guessing at what was edited out, so trying to catch up, while keeping what was edited out safe and secure..

Just to be clear, and not have to be assuming anything... And because a few things were edited out before I got a chance to see what they were...

You siad the host was Win Server 2019... What is the host VM system? How are you viewing the VM? And I got that an URL was used... Is it on the same network and/or subnet of the Host? What is the Network virtual switch type being used for the VM guest?

---

### Post by peter-1984 on 2021-12-14
This is running Virtualbox and issue is that inside Ubuntu VM, I cannot read files within one shared path from Win 2019 host.

---

### Post by TheFu on 2021-12-14
If virtualbox sharing from the host to the guest is used, then there is a **vboxsf** driver needed inside the guestOS which is used by the mount command.
[https://help.ubuntu.com/community/VirtualBox/SharedFolders](https://help.ubuntu.com/community/VirtualBox/SharedFolders) explains how.
Once we know to use the vboxsf driver and mount "type" this just works ... though file locking has always been an issue with virtualbox shares of this type. It doesn't behave like we expect a share to behave on a Unix system.

If the sharing is using normal MS-Windows CIFS shares, then you can use either CIFS mounts or a samba client. Morbius1 was trying to help with that in another thread. He's the expert.

---

