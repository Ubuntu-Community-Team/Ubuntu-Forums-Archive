---
title: "Samba PDC as windows repository"
date: 2007-07-19
forum: Server Platforms
---

### Post by Subnet on 2007-07-19
Hi everyone!

I'm considering setting up a Samba PDC to help out with patch management. On top of using this machine as a PDC, I'm also wanting it to be a Windows update repository since these machines cannot have all of the latest updates installed on them until they are verified by our vendor. Does anyone know if this is possible? Or does anyone know of any great patch management software that will allow me to push out updates to Windows XP machines?

Thanks,
Subnet

---

### Post by elst on 2007-07-21
Microsoft provide a free system for managing patches to Windows clients on a network called WSUS:

[http://technet.microsoft.com/en-us/wsus/default.aspx]("http://technet.microsoft.com/en-us/wsus/default.aspx")

IIRC, the only cost is that it needs to be hosted on Windows 2003 Server. This is definitely a case where avoiding the MS solution would cause more work than it saves.

---

