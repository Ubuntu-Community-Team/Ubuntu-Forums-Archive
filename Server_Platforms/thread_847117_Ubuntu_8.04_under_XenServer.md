---
title: "Ubuntu 8.04 under XenServer"
date: 2008-07-02
forum: Server Platforms
---

### Post by G.Hagedorn on 2008-07-02
We are running servers as VM machines under a XenServer 4.1 host (the Citrix XenExpress distribution). We are happy with Xen, but although Citrix does support a wide array of Linux systems (including SUSE, Debian, Red Hat, Oracle, etc.), they do not support Ubuntu. For the paravirtualization, Xen requires a modified Kernel of the hosted Linux system.

Debian 4 is running fine, but we would really like to use Ubuntu. Is there any way for Linux beginners to achieve this? Thanks!

---

### Post by windependence on 2008-07-02
Yes. VMware server. It's free (as in beer).

-Tim

---

### Post by G.Hagedorn on 2008-07-02
Even if we can use VMWare instead, we would have to migrate and test all the other machines to VMWare then. Ubuntu and Xen ("free as in Opensource") just don't match?

---

### Post by JGJones on 2009-04-09
This is probably a bit late for you since you posted this almost a year ago BUT...just in case :)

[http://community.citrix.com/blogs/citrite/anilma/2008/07/02/Installing+Ubuntu+on+XenServer](http://community.citrix.com/blogs/citrite/anilma/2008/07/02/Installing+Ubuntu+on+XenServer)

Today XenServer is on version 5.0 and is free which I use so at this point I have an issue with attaching the console to XenCenter and installing the deb files, but otherwise it is running in PV mode.

---

### Post by windependence on 2009-04-10
You may want to reconsider using Xen as it looks like it will become another Micro$oft casualty by proxy through Citrix. Citrix has always been in bed with Redmond and when they bought Xen I figured it was probably the end. Looks like my thoughts may be coming true:

[http://boycottnovell.com/2008/06/04/xen-with-hyper-v/](http://boycottnovell.com/2008/06/04/xen-with-hyper-v/)

-Tim

---

