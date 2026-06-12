---
title: "[SOLVED] Xen Server Express Edition with/versus Ubuntu"
date: 2008-10-29
forum: Virtualisation
---

### Post by stephanvaningen on 2008-10-29
I would like to install a server with Ubuntu & Xen, But if I then search for installation instructions I always get 12-pages of commands to copy/paste with a lot of if-then's and version-dependencies.

There is an easy installation CD of Xen, the ' Xen server express edition', it's a boot-CD with some Linux distro (stripped-down debian-based?).

My question is: is it worthwhile to try getting the same result with an Ubuntu-server installation-with-Xen or would that not give me more advantages then just using the (very-very-)easy installation of just booting the xen-express and installing using that Linux?

---

### Post by cyberwisdom on 2008-11-01
The Citrix XenServer Express edition is a fully tuned OS to run the XEN hypervisor.

It would actually take a lot of work to get an OS that is so tweaked and stripped from all extras as similar as the XenServer Express edition.

I use XenServer Express edition with Xen Center which is the management GUI frontend.  I really like it and have gotten even better performance over VMware ESX.  To get better performance you do however need to have XenTools installed in Windows or Linux.  In Linux you also need to be using the Xen optimized Kernel.

Also, you get a lot of pre-built templates for installing other Linux OS's without needing the ISO to do the install.

There are some cons.  Express edition has a 4GB RAM limit, can't use a SAN backend, and is missing some of the High Availability features, such as XenMotion, that are found  in the Enterprise edition.

---

### Post by stephanvaningen on 2008-11-03
Thanks, it makes me realize that I better stick to the red hat into the XenServer Express. 

You say you use XenCenter - as far as I understand from Citrix it is only available in Windows, right? I tried Convirt to connect to my virtualized server, but I didn't succeed in connecting :-/ [see other thread]("http://ubuntuforums.org/showthread.php?p=6094501") for that...

---

