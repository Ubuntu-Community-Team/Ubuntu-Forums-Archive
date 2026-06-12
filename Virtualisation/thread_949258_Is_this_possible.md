---
title: "Is this possible?"
date: 2008-10-16
forum: Virtualisation
---

### Post by sci-fi guy on 2008-10-16
Is there any VM environment that allows the virtual machines to be booted directly from grub without first booting the host OS? (A system in which all the host OS does is manage settings on the VMs.)

---

### Post by Thelasko on 2008-10-16
I'm not sure if I completely understand the question, but I think your are referring to something like [VMware ESX Server.]("http://en.wikipedia.org/wiki/VMware_ESX")  ESX basically is the host OS.

Also, with some hacking, you can boot a hard disk partition in Virtualbox.  Therefore, you could run the same OS as a virtual machine or normally.  This is risky though...

---

### Post by sci-fi guy on 2008-10-16
Are their any open-source equivalents to ESX Server?

---

### Post by das7002 on 2008-10-16
Yes kinda, I suggest Virtualbox as Thelasko did if you want there are 2 verions opensource and non-opensoruce the only true differece is that opensource does not support USB other than that they are the same

Hope that helps

---

