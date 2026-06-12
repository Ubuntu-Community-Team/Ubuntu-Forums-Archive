---
title: "Run a Windows Domain?"
date: 2010-10-23
forum: Server Platforms
---

### Post by doublez2 on 2010-10-23
Can Ubuntu Server by itself manage a windows domain and active directory. Would I be able to log onto roaming accounts on windows machines that were stored on the Ubuntu Server.
Thanks, I'm pretty new to Linux.

---

### Post by Groodles on 2010-10-23
Linux can handle the client & server aspects of Windows shares easily via Samba 3.x

The latest version of Samba (Samba 4) is aiming to provide an AD Domain Controller implementation on the linux platform.  However, Samba 4 is still in alpha at the moment.

[http://wiki.samba.org/index.php/Samba4](http://wiki.samba.org/index.php/Samba4)

So to directly answer your questions:

At this time, Ubuntu cannot manage a windows domain and active directory by itself.

Yes, you would be able to log onto roaming account on windows machines that were stored on the Ubuntu server.... if a Windows box was the PDC and the Ubuntu Server was just acting as a windows file share server.

Obviously, if Samba 4 development goes to plan, then you'll be able to do all that without the Windows PDC.

---

### Post by doublez2 on 2010-10-23
Sweet, thanks.

---

