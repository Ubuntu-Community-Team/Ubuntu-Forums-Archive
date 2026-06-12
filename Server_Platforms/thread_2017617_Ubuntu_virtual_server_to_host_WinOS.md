---
title: "Ubuntu virtual server to host WinOS"
date: 2012-07-05
forum: Server Platforms
---

### Post by vladinet on 2012-07-05
Hi all!

I have such a question, may be somewhere here it was resolved, but I couldn't find this.

I have server machine with high-level hardware. I Want to launch virtual machine with running Windows OS to be installed there. And I have client machines with low performance that should connect and use this server virtual WinOS as clients viewing GUI.

I know how implement this solution using VMWare software in Windows platform, but is there any solution for Ubuntu platform?

Grate thanks for answers!

---

### Post by papibe on 2012-07-05
Hi vladinet. Welcome to the forums!

[VMWare]("https://help.ubuntu.com/community/VMware") is available for Ubuntu. I personally use Virtualbox. Both are on the repositories.

Does your server has a GUI or is it just text mode?

Regards.

---

### Post by CharlesA on 2012-07-05
Are you trying to install Windows Server onto a Linux host? That is possible and that is also the only way you could get something like a terminal server using Windows.

The other option might be something like LISP:
[http://www.ltsp.org/](http://www.ltsp.org/)

---

