---
title: "Specify SCSI driver"
date: 2006-10-03
forum: Server Platforms
---

### Post by Peter Hopfgartner on 2006-10-03
Hello,

I'm having some problems with a Adaptec aic7890 controller. Therefore I would like the machine to boot with the aic7xxx_old driver instead of aic7xxx. How can I do this?

Regards,

Peter

---

### Post by Peter Hopfgartner on 2006-10-04
Ok, I added the module to /etc/mkinitramfs/modules and run mkinitramfs -o /boot/...

When I do it with the server images, the machine fails to boot. It tries to uncompress the ram disc and hangs there (I had this problem already during Dapper testing with server kernels), with standard kernels it works fine.

---

