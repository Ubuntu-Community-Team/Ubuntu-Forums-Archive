---
title: "Virtualizing Windows XP with VirtualBox"
date: 2010-11-23
forum: Virtualisation
---

### Post by jre6 on 2010-11-23
I recently virtualized Windows XP in Ubuntu 10.04.1 using VirtualBox 3.2. Is it possible to copy a file in this virtual machine from my Ubuntu partition?

---

### Post by lmarmisa on 2010-11-23
> **jre6 said:**
> I recently virtualized Windows XP in Ubuntu 10.04.1 using VirtualBox 3.2. Is it possible to copy a file in this virtual machine from my Ubuntu partition?

Yes, this is possible. You can use the Shared Folder feature of VirtualBox:

[http://www.virtualbox.org/manual/ch04.html#sharedfolders](http://www.virtualbox.org/manual/ch04.html#sharedfolders)

You will need to install the GuestAdditions in your VM prior to share your folders.

---

### Post by pricetech on 2010-11-23
Your XP does have to be running to do this though, so it might be just as easy to copy using windows with a share on Ubuntu.

Either set up Samba on your Linux box or use something like WinSCP on windows to copy using SSH.

Either way, treat your Ubuntu host as a network node when connecting.

---

### Post by jre6 on 2010-11-26
The shared folder feature works well in this case.

---

