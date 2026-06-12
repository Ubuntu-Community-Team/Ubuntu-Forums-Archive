---
title: "Install &amp; Run VMware Server on CLI Server"
date: 2006-10-17
forum: Server Platforms
---

### Post by doogy2004 on 2006-10-17
Does anyone know what you packages are required for VMware Server to run on a Command Line Only Server?  Is the install different from the gui install requirements?

---

### Post by Chayak on 2006-10-18
This really a question to post on the VMware support boards.  The experts are there.  To give you a bit of info, yes you can, but you still have to have the X server installed as VMware depends on some of its resources.  You don't have to actually start the X server.  I know of a number of people who have done this, but again post on the VMware board for specifics

---

### Post by doogy2004 on 2006-11-03
i found the packages needed.

build-essential
linux-headers-`uname -r`
xlibs-dev
xinetd

---

