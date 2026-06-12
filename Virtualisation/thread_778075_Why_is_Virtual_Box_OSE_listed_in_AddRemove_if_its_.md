---
title: "Why is Virtual Box OSE listed in Add/Remove if its broken?"
date: 2008-05-01
forum: Virtualisation
---

### Post by diablo75 on 2008-05-01
Here's my beef:

Fresh 8.04 install, and have never attempted to install Virtual Box yet.  After installing Virtual Box OSE via Add/Remove, I was given an error upon starting my newly created virtual machine that said I needed to install the "virtualbox-ose-modules-2.6.24-16-generic" package via synaptic (to be more accurate, it suggested the above package as an e.g., not an explicit instruction.  The last time this happened, I installed the 386 version, and it ended up calling for the 386 Linux kernels to be installed, which caused ubuntu to crash unless manually picking the generic kernel from grub).  Strike one, in my book.

After installing the virtualbox-ose-modules-2.6.24-16-generic package, and attempting to restart my virtual machine, I am given a new error:
> 
The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..

Now, before anybody tells me how to fix this, I need to ask (for the newbies sake), why on earth is Virtual Box included with the Add/Remove applet if it can't install Virtual Box correctly on a fresh system?  I mean, the very first error mentioned above shows me that IT DIDN'T EVEN INSTALL ALL OF IT'S DEPENDENCIES right off the bat.  I mean.... wow, that alone just seems beyond ridiculous these days.
](*,)

---

### Post by cor2y on 2008-05-02
I hear you, for the past 2 previous versions of ubuntu  i have never gotten Virualbox OSE to work correctly when installed, the furthest i have ever gotten after an install was the window to select the virtual machine then it wouldn't launch it. I won't say i have given up on it but considering the closed version just requires a deb and a simple quick reinstall if you update ubuntu. Its hard to recommend or even consider the OSE version.

---

### Post by Fratm on 2008-05-02
I have had no problems with virtual box, but I also did not use the add/remove tool to add it.. I followed directions found in this post : [http://ubuntuforums.org/showthread.php?t=776372](http://ubuntuforums.org/showthread.php?t=776372) (The directions are in a reply) and they worked flawlessly. 

The install was so smooth that I would recommend it to anyone who needs this functionality.

-Steve

---

### Post by tech9 on 2008-05-02
you could also try installing the tar.gz file from virtual box main site...

cd /path to install

./virtual box install

---

### Post by drsox1899 on 2008-05-02
BREAKING NEWS !!!!


New version of Virtual Box now released :

[https://cds.sun.com/is-bin/INTERSHOP...-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP...-F@CDS-CDS_SMI)

Version 1.6

Supports Ubuntu 8.04 !!

---

