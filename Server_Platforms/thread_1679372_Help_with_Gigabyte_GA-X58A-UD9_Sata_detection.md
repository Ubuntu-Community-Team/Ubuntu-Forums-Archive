---
title: "Help with Gigabyte GA-X58A-UD9 Sata detection"
date: 2011-01-31
forum: Server Platforms
---

### Post by tnine on 2011-01-31
Hi guys,
  We're attempting to use server 10.10 to build a workstation from this board.

[http://www.gigabyte.com/products/product-page.aspx?pid=3434#ov](http://www.gigabyte.com/products/product-page.aspx?pid=3434#ov)

However we're having a lot of issues with drive detection.  The installation disk doesn't detect the drives, and I've made sure the FRAID module is disabled in the BIOS.  All the SATA modules are set to IDE mod, so I'm not sure why it can't detect the drives.  Windows 7 can detect the drives, so I'm pretty sure it's not a hardware failure issue.  

We really don't want to have to install windows just to run an Ubuntu Server over the top of it in VMware Workstation.  What can I do to help debug the issue?  I've never encountered this with Ubuntu before, it's always just worked!

Thanks,
Todd

---

### Post by Vegan on 2011-01-31
Try setting the drives to ACPI

---

### Post by tnine on 2011-02-01
Hi Vegan,
  Unfortunately we already tried that.  When we do that, it can detect the hard drives, however the install process cannot find a driver to use the DVD drive.  I'm not quite sure why we're getting this error, since it can obviously read the drive to start the install process.

---

