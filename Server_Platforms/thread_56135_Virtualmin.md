---
title: "Virtualmin"
date: 2005-08-11
forum: Server Platforms
---

### Post by CrustyDOD on 2005-08-11
Hey

Trying to get Virtualmin to work but hmm i get this error:
> The Network Configuration module is not supported on your operating system. Virtualmin needs this module to manage virtual network interfaces.
Did some googling and all i could find out is that some linux distros doesn't support this... Is this also the case for Ubuntu? If not, where can i get Network Configuration module?

Or am i missing something here... :roll:

---

### Post by DJ_Max on 2005-08-12
I would guess it's a configuration problem with your kernel. It's not really dependent on any distro, rather the kernel. I'm using Virtualmin on a Debian server, and it runs fine. I'm not sure what you have to enable in your kernel. You may wanna ask on the Webmin forums. You will probably have to make yourself a custom kernel.

---

### Post by grasomega on 2006-01-26
In Webmin Configuration, Operating Systems and Environment, select Debian Linux System everywhere possible. It should work now.

---

