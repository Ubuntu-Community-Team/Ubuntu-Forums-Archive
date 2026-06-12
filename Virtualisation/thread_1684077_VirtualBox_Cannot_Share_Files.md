---
title: "VirtualBox: Cannot Share Files"
date: 2011-02-08
forum: Virtualisation
---

### Post by kd4hey on 2011-02-08
I am running Ubuntu 10.10 for my host OS.

I set-up VirtualBox OSE with Win 7 Ultimate 64 Bit as my Guest OS.

My system is a dual-Boot on a 750GB HD, 50GB for Win7, 80GB for Ubuntu & the remaining 600GB or so for my data.  I set-up the data partition as a shared file in VirtualBox, but the virtual Win7 doesn't see any shared file.

I followed the manual instructions & attampted to map a network HD as I would with a standard Win7 install,  but it can't find my shared file.

Any Ideas?

---

### Post by Cheesehead on 2011-02-08
You set shared folders from the VB Manager on the Host OS, *not* from within the guest OS.

1) Shut down (not just save state) the Guest OS.
2) Open the VB Manager, select the (turned-off) Guest OS, click Shared Folders.
3) Navigate to the shared folder...which must be on the Host filesystem.
4) When you restart the Guest, look in My Computer..the Share should be automatically mounted as a network drive.

---

### Post by kd4hey on 2011-02-08
> **Cheesehead said:**
> You set shared folders from the VB Manager on the Host OS, *not* from within the guest OS.

1) Shut down (not just save state) the Guest OS.
2) Open the VB Manager, select the (turned-off) Guest OS, click Shared Folders.
3) Navigate to the shared folder...which must be on the Host filesystem.
4) When you restart the Guest, look in My Computer..the Share should be automatically mounted as a network drive.

I agree it SHOULD be there, but it isn't.  The VB manual also told me to try to map it like a network HD, that failed too.

I even deleted the mapped shared folder (with the guest OS shutdown) & set it up again, all to no avail.  It just doesn't show up on my guest OS (Win7).

---

### Post by kd4hey on 2011-02-08
Well I stumbled onto it.

I WAS running VirtualBox OSE (V2.3) & went to the VB site & downloaded VB 4.0.  Once I installed it (un-installed OSE 1st) it then told me I needed Guest Add-ons.  Once I installed Guest Add-ons, the Shared file appeared as expected.

Thanks for the reply.

---

