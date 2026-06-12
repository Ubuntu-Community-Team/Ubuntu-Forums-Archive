---
title: "Usb on Windows client"
date: 2008-12-24
forum: Virtualisation
---

### Post by any.linux12 on 2008-12-24
HI HI!!!

I have Vmware2.0 and a windows client on a ubuntu host.
When I plug my usb stick and connect it the ubuntu client disconnect it(!?!)

Why that??

---

### Post by inobe on 2008-12-24
not too knowledgeable on vmware for usb device's' but it looks the host and guest are using the same device, i don't think that's recommended !


i use vbox, assuming the device shouldn't be mounted simultaneously 

but idk' just an idea :)

---

### Post by any.linux12 on 2009-01-05
Does someone has vmware with windows xp guest and usb stick working??

---

### Post by any.linux12 on 2009-01-05
does someone has VMware :) or just myself??

---

### Post by bear2 on 2009-02-21
Where I work we are running vmware to host windows2003 servers (xp can make use of this as well) and we use the "anywhereUSB" box to do what you are talking about-- 
see the product info on that box here:
[http://www.digi.com/products/usb/anywhereusb.jsp](http://www.digi.com/products/usb/anywhereusb.jsp)
This hardware solution only seems to work though with one anywhereusb box dedicated to one windows vm.  But it does work reliably.  We have several licensing usb keys that are on the anywhereusb box and the windows vm sees them fine in windows device mgr, etc. This is what we are running in "production".

---

