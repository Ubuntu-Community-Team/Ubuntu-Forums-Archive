---
title: "virtualbox cannot start after upgrade to 3.0.2"
date: 2009-07-12
forum: Virtualisation
---

### Post by starfry on 2009-07-12
Hello, I have just upgraded vb 2.2 to 3.0.2. It won't start, reporting errors:


Could not load the settings file '/home/myusr/.VirtualBox/VirtualBox.xml'.
Cannot convert settings from version '1.7-linux'.
The source version is not supported.


Result Code: 
0x80004005
Component: 
VirtualBox
Interface: 
IVirtualBox {2d3b9ea7-25f5-4f07-a8e1-7dd7e0dcf667}

If I move ~/.VirtualBox out of the way it starts ok. However I can't do this as I have loads of VMs already existant. 

Any pointers how to fix this greatly appreciated...

*update* default apt-get actually downgrades!!! I didn't notice that. I now have 302 installed and all is well :)

---

