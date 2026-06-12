---
title: "Vmware workstation 7 install fails on Ubuntu 9.10"
date: 2010-02-11
forum: Virtualisation
---

### Post by thednick on 2010-02-11
I am trying to install vmware workstation 7.0.1-227600 on ubuntu 9.10 karmic koala and I am facing a strange problem. The installation fails with no reason.  

```

$sudo ./vmware-workstation-full-7.0.1-227600.x86_64.bundle --console
Extracting VMware Installer...done.
You must accept the VMware VIX API End User License Agreement to
continue.  Press Enter to proceed.

Do you agree? [yes/no]: yes

Path to Eclipse directory for use with Integrated Virtual Debugger
(optional): 

Do you wish to install the Eclipse C/C++ Debugging plugin? (Requires
Eclipse 3.4.0 or higher and must be properly pre-configured.  See
documentation for details) [no]: 

Insufficient file descriptors can cause virtual machines to crash when
using snapshots.  The installer has detected that your hard limit for
open files is 1024, which is lower than VMware Workstation may
require.  Please enter a new limit [4096]: 

The product is ready to be installed.  Press Enter to begin
installation or Ctrl-C to cancel.

Rolling back VMware Tools for FreeBSD 8.1.4
    Deconfiguring...
[##########                                                            ]  15%All configuration information is about to be removed. Do you wish to
keep your configuration files? [yes]: 

Uninstalling VMware Installer 1.1
    Deconfiguring...
[######################################################################] 100%
Installation was unsuccessful.


``````

$ uname -r
2.6.31-19-generic

```Any ideas? Notice that I have installed the same version of vmware on debian testing without any problem.

---

### Post by thednick on 2010-02-11
OK solved. The installer was corrupt. I used the original file and it worked.

---

### Post by fjgaude on 2010-02-11
Thanks for telling us... that was good to know.

---

### Post by ragip on 2011-07-22
> **thednick said:**
> OK solved. The installer was corrupt. I used the original file and it worked.
my installer is not corrupt but receiving the same error message on ubuntu 11.04. any ideas?

---

### Post by fjgaude on 2011-07-22
My only suggestion would be to make sure you have the latest versions of everything from VMware. Their stuff is solid.

---

