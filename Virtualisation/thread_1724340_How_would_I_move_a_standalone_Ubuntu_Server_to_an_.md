---
title: "How would I move a standalone Ubuntu Server to an virtual server (ESXi)"
date: 2011-04-08
forum: Virtualisation
---

### Post by alexlaban on 2011-04-08
I need to move an ubuntu server to a virtual server and everything on it with users, etc. The most logical way would be to move the entire HDD to an virtual disk on VMWare ESXi but how would I do that? Exporting all data, all userdata, configurations, etc seems like an unnecessary hassle. Could anyone guide me in the right direction?

---

### Post by CharlesA on 2011-04-08
Clone it using something like Clonezilla, and restore it onto a virtual drive in ESXi.

---

### Post by falko on 2011-04-08
You can do this with VMware Converter: [http://www.vmware.com/products/converter/](http://www.vmware.com/products/converter/)

Also see [http://www.howtoforge.com/vmware_converter_windows_linux](http://www.howtoforge.com/vmware_converter_windows_linux)

---

