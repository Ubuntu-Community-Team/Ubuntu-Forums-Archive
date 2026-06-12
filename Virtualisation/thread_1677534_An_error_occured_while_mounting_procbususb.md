---
title: "An error occured while mounting /proc/bus/usb"
date: 2011-01-28
forum: Virtualisation
---

### Post by cccc on 2011-01-28
hi

I've Ubuntu 10.10 32-bit and I've installed vmware-view-client_4.0.1-235010_i386.deb from:   

[http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=12454&prodSeriesId=3719101&swItem=vc-81719-1&prodNameId=3719106&swEnvOID=4030&swLang=13&taskId=135&mode=4&idx=0](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=12454&prodSeriesId=3719101&swItem=vc-81719-1&prodNameId=3719106&swEnvOID=4030&swLang=13&taskId=135&mode=4&idx=0)

The setup has added the following entry to /etc/fstab:```

none    /proc/bus/usb   usbfs   listgid=1001,listmode=0664,busgid=1001,busmode=0775,devgid=1001,devmode=0664    0       0

```and this line is needed for the usb support through the vmware client.

Now during Ubuntu startup I get this error message:

**[COLOR="Red"]"An error occured while mounting /proc/bus/usb" [/COLOR]** 

and the startup process stops.

---

