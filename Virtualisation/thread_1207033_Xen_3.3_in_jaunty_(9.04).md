---
title: "Xen 3.3 in jaunty (9.04)"
date: 2009-07-07
forum: Virtualisation
---

### Post by laprice on 2009-07-07
I'm trying to setup xen from packages in jaunty but it seems that there is no xen enabled kernel in the jaunty repos.

I have the following packages installed.

```

ii  libxen3                                    3.3.0-1ubuntu9.3                          library interface for Xen, a Virtual Machine
ii  libxen3-dev                                3.3.0-1ubuntu9.3                          headers for Xen, a Virtual Machine Monitor
ii  python-xen-3.3                             3.3.0-1ubuntu9.3                          python bindings for Xen, a Virtual Machine M
ii  ubuntu-xen-desktop                         0.0.1-2ubuntu10                           Xen software for running on desktops
ii  ubuntu-xen-server                          0.0.1-2ubuntu10                           Xen software for running on servers
ii  xen-docs-3.3                               3.3.0-1ubuntu9.3                          documentation for XEN, a Virtual Machine Mon
ii  xen-hypervisor-3.3                         3.3.0-1ubuntu9.3                          The Xen Hypervisor for i386 and amd64.
ii  xen-shell                                  1.9-1                                     Console based Xen administration utility
ii  xen-tools                                  3.9-6                                     Tools to manage Debian XEN virtual servers
ii  xen-utils-3.3                              3.3.0-1ubuntu9.3                          XEN administrative tools
ii  xenwatch                                   0.5.4-1ubuntu1                            Virtualization utilities, mostly for Xen


```

When I attempt to start xend I get 

```
/etc/init.d/xend start
grep: /proc/xen/capabilities: No such file or directory

```

Any of the xm tools give me a stack trace ending with ```
xen.lowlevel.xc.Error: (1, 'Internal error', 'Could not obtain handle on privileged command interface (2 = No such file or directory)')
```

Looking around on google gives me some vague advice on grabbing a debian kernel, but nothing definite.

This seems like a packaging bug to me, if we have the xen-3.3 packages it should be accompanied by a kernel capable of accomodating that. I thought I would ask here before posting on launchpad. Or attempting to build my own kernel.

---

### Post by pivert on 2009-07-17
Hi,

If you are running a xen dom0 enabled kernel, you should be able to mount it :

mount -t xenfs none /proc/xen

Regards,

---

### Post by bodhi.zazen on 2009-07-17
As far as I know (I have not looked recently) Xen dom0 is not supported in Ubutnu 9.04, you need to go with 8.04 or compile a custom kernel.

See if this page helps, it seems to imply there is support for Xen in 9.04

[https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen)

---

### Post by tazan008 on 2009-08-03
Hi,
I got same problem. I followed steps in [https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen) to install Xen in my Ubuntu laptop. However when i tried to restart the services: 
funzi@funzi-laptop:/etc/xen$ sudo /etc/init.d/xend restart
i got the problem: grep: /proc/xen/capabilities: No such file or directory

I googled a lot but i'm still stuck here. Thanks a lot for helps.

---

