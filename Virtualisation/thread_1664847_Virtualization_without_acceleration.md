---
title: "Virtualization without acceleration"
date: 2011-01-11
forum: Virtualisation
---

### Post by TrickerZ on 2011-01-11
I'm trying to create a node controller on a bunch of Pentium D servers which have no virtualization support.  The rest of my cloud works fine since I was able to use an i7 laptop to test as a NC.  There is very little documentation on how to do this.  I tried installing Xen 4.0.1 as shown here: [https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen) but it seems like Xen now requires virtualization support in the processor as well.  Whenever I try to load Xen as specified in that article, I get a black screen and nothing after the kernel tries to load.  I can load the kernel normally (without the multiboot line) and it runs, but xm list gives me an error:

> ERROR Internal error: Could not obtain handle on privileged command interface (2 = No such file or directory)
Traceback (most recent call last):
  File "/usr/sbin/xm", line 5, in <module>
    from xen.xm import main
  File "/usr/lib/python2.6/dist-packages/xen/xm/main.py", line 61, in <module>
    xc = xen.lowlevel.xc.xc()
xen.lowlevel.xc.Error: (1, 'Internal error', 'Could not obtain handle on privileged command interface (2 = No such file or directory)')


Nothing shows up in the xend.log when I run it and if I try to start eucalyptus-nc, I get:

> libvir: error : no connection driver available for xen:///
libvirt error: no connection driver available for xen:/// (code=5)
error: failed to connect to hypervisor
in the euca_test_nc.log file and it exits

Has anyone had success getting Xen to run without virtualization support in the processor?

---

