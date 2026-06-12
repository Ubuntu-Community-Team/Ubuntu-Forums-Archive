---
title: "Virtualbox Install Problem"
date: 2013-03-11
forum: Virtualisation
---

### Post by c5vetter on 2013-03-11
Okay, attempted to install Virtualbox and get the following error:

The character device /dev/vboxdrv does not exist. Please install the virtual-box-ose-dkms package and appropriate headers, most likely linux-headers-generic

So, what does this mean and how do I do what it is telling me to do!?

---

### Post by ibjsb4 on 2013-03-12
Have you installed the **dkms** and **build-essential** package from the software center?

Also are you installing from the vBox site or the software center.  I ask just because the site just seems to work better for me.

---

### Post by QIII on 2013-03-12
Also install linux-headers-generic  ;)

+1 to installing from VirtualBox.org.  Download the .deb appropriate for your architecture.  Also download and install the extension pack.

Best wishes!

---

### Post by c5vetter on 2013-03-12
Initially tried to install via software center and got the error, so then decided to install via terminal command line - sudo apt-get install virtualbox and then got the same error; will try the suggestions

---

### Post by El Tito on 2013-03-12
I agree with @ibjsb4: 
```
sudo apt-get install dkms
```
"Ubuntu/Debian users might want to install the **dkms** package to ensure that the VirtualBox host kernel modules (*vboxdrv*, *vboxnetflt* and *vboxnetadp*) are properly updated if the linux kernel version changes during the next apt-get upgrade".
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by SeijiSensei on 2013-03-12
By far the best and more reliable method is to add the VB repository by adding a line to /etc/apt/sources.list as described in the "Debian-based" section of the downloads page on the VB site.  Once you have this configured, updates to VirtualBox will be managed just like all other upgrades.

You can just download the .deb, but adding the repository is a better solution in the long run.

---

### Post by varunendra on 2013-03-12
*Thread moved to **Virtualisation**.*
----------------------

+1 to what others suggested, plus - make sure you are a member of **vboxusers** group -
```
groups
```
If the above command does not show "vboxusers" among other group names, add yourself to the group -
```
sudo adduser <your user id> vboxusers
```
..then run the **groups** command again to double-check.

---

