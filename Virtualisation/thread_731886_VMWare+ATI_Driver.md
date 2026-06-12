---
title: "VMWare+ATI Driver"
date: 2008-03-22
forum: Virtualisation
---

### Post by Dhaun on 2008-03-22
Hello, 

I'm trying to install the newest ATI Drivers on my Ubuntu 7.10 guest. When I'm following the official ATI guide it says there is no ATI card.
Do I need to do some special settings in vmware in order to allow my radeon 1950 work on the guest?
If there's a guide for this, could you please link me to it? 

Thank you :)

---

### Post by Bachstelze on 2008-03-22
VMware is a full virtualization platform, which means that what your guest system "sees" is virtual hardware created by it, *not* your actual, physical hardware. So it doesn't make any sense to install the ATi drivers on a VMware guest.

Moved to the Virtualization forum.

---

### Post by Dhaun on 2008-03-22
Dammit ! Does that mean I can't get Compiz working on my ubuntu guest? :confused:

---

### Post by Bachstelze on 2008-03-22
> **Dhaun said:**
> Dammit ! Does that mean I can't get Compiz working on my ubuntu guest? :confused:

Yes, there is no 3D support in VMware yet. It's a work in progress though, and I've heard it's available as a beta in VMware Workstation, but that one you have to pay for.

---

### Post by Dhaun on 2008-03-22
So dual-boot or buying the vmware beta is the only option for now?
How about Parallels Workstation?

Thanks for your answers :)

---

