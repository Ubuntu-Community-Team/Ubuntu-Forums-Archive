---
title: "Ubuntu 12.04 and virtualbox problems"
date: 2012-05-09
forum: Virtualisation
---

### Post by Nerdishman on 2012-05-09
when i start virtualbox (from the terminal) it says
WARNING: The character device /dev/vboxdrv does not exist.Please install the virtualbox-ose-dkms package and the appropriate headers, most likely linux-headers-generic.

You will not be able to start VMs until this problem is fixed.

i installed virtualbox-ose-dkms and linux-headers-generic and it still says that.

I am using Ubuntu 12.04 and linux version 3.3.0-030300-generic (from uname -r)

can anyone help me?

---

### Post by nothingspecial on 2012-05-10
*Thread moved to **Virtualization**.*

---

### Post by speedwlk on 2012-05-11
If you have installed the 32-bit Ubuntu 12.04, please note that it now provides the pae kernel. So you might need linux-headers-generic-pae instead of linux-headers-generic.

If you are running 64bit Ubuntu, then I have no idea about your problem.



EDIT: Sorry, I did not notice that you have already mentioned the output of "uname -r". Your kernel is not the pae-kernel.

---

