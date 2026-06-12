---
title: "How install guest OS on container"
date: 2008-08-19
forum: Virtualisation
---

### Post by satimis on 2008-08-19
Hi folks,


Ubuntu8.04 desktop i686 - host
OpenVZ - Virtual server


I have installed OpenVZ on Ubuntu.  It is now running.  Container can be created.  But I haven't figured out how to install guest OS from its CD installer on the container.


Please shed me some light.  Pointer would be appreciated.  TIA


B.R.
satimis

---

### Post by gurtaj on 2008-09-14
Containers do not work in that way. What you have in each container (what would be similar to a virtual machine) is a user space environment where you can install and run applications.

The container is created based on a template of certain distribution. Anyway, all you can have in a container is a GNU/Linux environment.

---

### Post by satimis on 2008-09-14
> **gurtaj said:**
> Containers do not work in that way. What you have in each container (what would be similar to a virtual machine) is a user space environment where you can install and run applications.

The container is created based on a template of certain distribution. Anyway, all you can have in a container is a GNU/Linux environment.
Hi gurtaj,


Thanks for your advice.


So if I need a container running another Linux distro I must create another container on the corresponding template?


B.R.
Stephen

---

### Post by dejitarob on 2008-09-29
Yes, you must create a container with the corresponding template. You can make your own template or use one of the many that are available at [http://wiki.openvz.org/Download/template/precreated](http://wiki.openvz.org/Download/template/precreated)

Also, I recently posted a [how to for OpenVZ]("http://ubuntuforums.org/showthread.php?t=929106") that may help you.

---

### Post by satimis on 2008-09-29
> **dejitarob said:**
> Yes, you must create a container with the corresponding template. You can make your own template or use one of the many that are available at [http://wiki.openvz.org/Download/template/precreated](http://wiki.openvz.org/Download/template/precreated)

Also, I recently posted a [how to for OpenVZ]("http://ubuntuforums.org/showthread.php?t=929106") that may help you.
Noted with thanks


satimis

---

