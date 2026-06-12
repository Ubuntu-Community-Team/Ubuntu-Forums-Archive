---
title: "virtual machine blocks printer"
date: 2008-12-09
forum: Virtualisation
---

### Post by horacle on 2008-12-09
hello, after reading the tutorials about turning on the usb ports in virtualbox, installing the printer in the guest (xp) was a no brainer, but then the printer stoped working in linux and the machines around while the virtual machine is running; after turning off the virtual machine, some printing jobs resume, some has to be cancelled and started again. Did I miss anything?

---

### Post by HermanAB on 2008-12-09
I would not install a full printer subsystem in a VM, since it will fight with the host as you found.  If the host is running CUPS already, then you can print from a Windows guest by 'discovering' and connecting to the host print system, or by manually entering the IP address of the host and name of the printer.

Linux makes all printers look like Postscript printers, so you can simply select an Apple Laser Writer driver in Windows and it should work fine irrespective of what kind of printer you actually have.

Hope that helps!

Herman

---

### Post by dragos_iliescu_2005 on 2008-12-09
If you will need your printer to be available from Linux, disable the printer from virtual machine

---

### Post by Therion on 2008-12-09
The device can only be accessed from one OS at a time.  Enable the printer in your guest OS when you need it, then disable it when you no longer need it in the guest OS, or shut down the guest OS altogether.  Once you do, control of the device will return to the Host OS.

---

### Post by horacle on 2008-12-10
thank you to all who answered.
what about a shared printer in another machine? I tryed that before destroying one of my testing boxes last night; I was able to see the printer installed in the other fedora/xp box, but each time I tryed to print a test page nothing happened, and I dont know whats going on because right now I cant print from ubuntu either.

Thanks again :)

---

### Post by Dedoimedo on 2008-12-10
A shared printer should work, provided networking is setup correctly, including forwarding and firewall rules.
Dedoimedo

---

