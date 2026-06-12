---
title: "Eucalyptus: node controller and xen"
date: 2009-05-08
forum: Virtualisation
---

### Post by jinzishuai on 2009-05-08
Hi there,

After reading  the documentation on eucalyptus on Jaunty, I am a bit puzzled that there is no mention on setting up xen on the node-controller, where the xen virtual machine will be running. 
Let me ask this: is it correct that I have to first install the xen kernel on the node controller before any VM can be deployed? Unfortunately Jaunty does not support xen kernel...

Thank you very much.

Shi

---

### Post by dendrobates on 2009-05-08
The Ubuntu version of Eucalyptus uses KVM as the hypervisor.  It is possible to setup Eucalyptus to use Xen, but you would have to do it manually.

--Rick

---

### Post by geppetto on 2009-06-26
Read [http://www.infohit.net/blog/post/running-xen-on-ubuntu-intrepid-and-jaunty.html:](http://www.infohit.net/blog/post/running-xen-on-ubuntu-intrepid-and-jaunty.html:) it works.

---

