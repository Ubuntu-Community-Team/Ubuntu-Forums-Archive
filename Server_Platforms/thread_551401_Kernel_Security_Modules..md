---
title: "Kernel Security Modules."
date: 2007-09-15
forum: Server Platforms
---

### Post by HuwSy on 2007-09-15
Is there anything out there that will recompile kernel modules then reset the system whenever the kernel has been updated.  Currently i have the cvs download commands, and build commands in a script that is ran whenever needed, and was thinking of making a slimple script to go into init.d where it checks the kernel version to that last complied against by comparing it to a log file somewhere, then if they differ rebuild the modules and reboot.  I realise this adds a slight security risk in that anythin that manages to add its self to the file could cause chaos, but is there any other problems with this im missing? which run level would it be best to put this at?
Thanks

---

