---
title: "[SOLVED] C headers"
date: 2008-06-12
forum: Virtualisation
---

### Post by Linaxeyourwindows on 2008-06-12
I have unbuntu server running in vmware and have been trying to install the vmware tools.

I can get through the process okay. but when it gets to the part where it wants the C headers for the kernel I do not have them.

How can I get the kernel source package?

---

### Post by Joeb454 on 2008-06-12
For the C headers etc. run ```
sudo apt-get install build-essential
``` Take off "sudo" if you're logged in as root (which I doubt)

---

### Post by Linaxeyourwindows on 2008-06-12
I actually am logged in as root i kept forgetting to use sudo all the time

I have the headers and I told the installer to look in:
/usr/src/linux-headers-2.6.24-16-server/include

I think i must update VMWare its telling me:
"The directory of kernel headers (Version @@VMWare@@ UTS_Release) does not match your running kernel (2.6.24-16-server)..."


I am using putty now, got tired of crtl+alt to release my mouse

Thank you btw

---

### Post by Linaxeyourwindows on 2008-06-12
Updating vmware solved the problem. The install even found the C header dir itseld. 

Thank you for your help.

---

### Post by Joeb454 on 2008-06-12
No problem :) You can mark your thread as solved from "Thread Tools" at the top of this page :)

---

