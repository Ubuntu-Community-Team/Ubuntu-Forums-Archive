---
title: "Windows installed on KVM license"
date: 2019-06-11
forum: Virtualisation
---

### Post by webmiester on 2019-06-11
Hi guys,

I remember that windows has this thing that if we activate it on a specific motherboard, we wont be able to transfer the license to any other computer anymore because it remembers the bios where it was activated on, right?.  In the case of a  Virtual Machine, does it have some sort of virtual bios?  Can we replicate this virtual bios exactly into another computer?  If I make another instance of this VM, will it have the same virtual bios or will its virtual bios be different?  If I delete a VM on a device and make a new one with exactly the same specs, can I have its BIOS the same too?  Just consider the implications... I install windows on VM and activate it... then it gets compromised, so I delete it and make a new VM on the same computer and install windows again... will it still activate?

Thanks.

---

### Post by kc1di on 2019-06-11
I believe that windows now offfers an individual license instead of a per device license.  I have not used that my self (I don't run windows) but [this page ]("https://community.spiceworks.com/how_to/146354-license-windows-10-for-use-in-virtualization-environment-including-multitenant-and-cloud-hosting-use-rights")may be of help.

---

### Post by webmiester on 2019-06-11
Thanks.  My bigger concern is how to preserve the data and the system when Microsoft no longer supports windows 10.  Its my current problem with a windows 2003 server we have.  It's not possible to reinstall it somewhere else anymore, and we can't transfer the main software we are using to a different system. Its one reason why my new system runs on Ubuntu.  But I still need windows 10 for some users.  Even if we are allowed to own one copy, and we run only one copy, we won't be able to activate it anymore if we transfer it to a different hardware once support for it is abandoned.

---

### Post by kc1di on 2019-06-11
That is one of the great reasons to go open source and dump windows, JMHO.  You can bit the bullet now or wait until your forced to :)

---

