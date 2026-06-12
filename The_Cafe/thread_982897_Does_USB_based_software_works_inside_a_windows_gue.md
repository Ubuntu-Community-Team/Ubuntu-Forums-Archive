---
title: "Does USB based software works inside a windows guest in the VirtualBox?"
date: 2008-11-15
forum: The Cafe
---

### Post by legolas_w on 2008-11-15
Hi
Thank you for reading my post
I am just wondering whether software which need USB devices works fine in the  windows guest?
I intend to install Virtual Box in Ubuntu 8.10 and then install a Windows XP inside it and then I will install Microsoft ActiveSync and other WM 6.1 required software into that guest windows, but problem is that I do not know whether they can connect to my cell phone using the USB port or not?

bottom line: Does windows Guest in Virtual Box has access to USB?

Thanks.

---

### Post by mips on 2008-11-15
> **legolas_w said:**
> Hi
Thank you for reading my post
I am just wondering whether software which need USB devices works fine in the  windows guest?
I intend to install Virtual Box in Ubuntu 8.10 and then install a Windows XP inside it and then I will install Microsoft ActiveSync and other WM 6.1 required software into that guest windows, but problem is that I do not know whether they can connect to my cell phone using the USB port or not?

bottom line: Does windows Guest in Virtual Box has access to USB?

Thanks.

That depends on the version of Virtualbox. The OSE edition of Virtualbox does not provide support for USB, you will need the non-OSE version.

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)
[http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

---

