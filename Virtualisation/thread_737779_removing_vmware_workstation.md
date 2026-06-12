---
title: "removing vmware workstation"
date: 2008-03-27
forum: Virtualisation
---

### Post by Matt26 on 2008-03-27
can anyone direct me to instructions on how to properly uninstall vmware workstation 6.0.2 build-59824 setup on ubuntu 7.10?  thanks.

---

### Post by bkozora on 2008-03-28
wow, I need precisely the same thing... post back if you find anything, as will I

---

### Post by bkozora on 2008-03-28
vmware-uninstall.pl from a terminal, worked for me with 6

[http://www.vmware.com/support/ws5/doc/ws_install_uninstall_linux_host.html]("http://www.vmware.com/support/ws5/doc/ws_install_uninstall_linux_host.html")

---

### Post by speedbaron on 2010-11-09
For VMWare workstation 7.1.2
+++++++++++++++++++++

The vmware-uninstall* scripts have been deprecated.  Instead, please use
the vmware-installer.

Long form:
      vmware-installer --uninstall-product PRODUCT
Short form:
      vmware-installer -u PRODUCT

Where PRODUCT is one of vmware-workstation, vmware-player, or vmware-vix.

For a list of which products are installed, you may run:
      vmware-installer --list-products
or:
      vmware-installer -l

++++++++++++++++++

In my case, I used:
sudo vmware-installer -u vmware-workstation

---

