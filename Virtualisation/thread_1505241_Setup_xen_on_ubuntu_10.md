---
title: "Setup xen on ubuntu 10"
date: 2010-06-08
forum: Virtualisation
---

### Post by endless83 on 2010-06-08
Hi, I'm new to ubuntu. would like to know how can i setup xen virtualization for ubuntu 10?

---

### Post by TheFu on 2010-06-09
It is not as easy as it was in previous releases. There is no 'apt-get install' method any more since Canonical decided the reduce Xen support in favor of KVM for virtualization. A link that may help is [http://bderzhavets.wordpress.com/2010/04/24/set-up-ubuntu-10-04-server-pv-domu-at-xen-4-0-dom0-pvops-2-6-32-10-kernel-dom0-on-top-of-ubuntu-10-04-server/](http://bderzhavets.wordpress.com/2010/04/24/set-up-ubuntu-10-04-server-pv-domu-at-xen-4-0-dom0-pvops-2-6-32-10-kernel-dom0-on-top-of-ubuntu-10-04-server/)

You may want to check the Xen web site too. [http://www.xen.org/](http://www.xen.org/)  I think you'll be compiling your own kernels.

---

### Post by endless83 on 2010-06-09
I see. That was the reason why i fail to setup xen based the previous ubuntu version method. Would give a try based on the link which you provided. Thanks for your help.

---

