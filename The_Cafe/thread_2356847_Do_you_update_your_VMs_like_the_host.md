---
title: "Do you update your VMs like the host ?"
date: 2017-03-27
forum: The Cafe
---

### Post by linuxyogi on 2017-03-27
Hi,
I just finished installing openSUSE inside Virtualbox with Ubuntu 17.04 as the host. The first thing I am doing now is update openSUSE but thats a lot of updates specially when combined with host's updates. 

So my question is do you guys update your VMs as soon as updates appear like you do with your host ?

---

### Post by speedwell68 on 2017-03-27
The only VM I have is Windows 7 and I just let it get on with it when it fancies.  Which is frustrating as when I next come to use the VM it takes ages to start as it is still updating itself.

---

### Post by linuxyogi on 2017-03-27
Initially I had allocated 1 GB of Ram to the VM... By default openSUSE offers only KDE and Gnome and it was painfully slow. I had to add another 1 GB and install lxde. Now its fast than before.

---

### Post by ajgreeny on 2017-03-27
I treat all my VMs as if the were normal hard-metal installed OSs and update them when updates appear.

As I use VMs for other DE versions of the same *ubuntu version as my main OS I copy the /var/cache/apt/archives folder of my host into a cache folder in my host's home fo0lder, then I update my host, and use that cache folder for my VMs by using symbolic links from host to /var/cache/apt/archives in the guest.

The only one I can't update is an old WinXP, no longer supported, of course, but which I need to keep to get updated maps etc for my TomTom GPS satnav device. I make sure the antivirus on that is kept updated and I also have a totally clean snapshot in case it does ever get corrupted by virus or malware.

---

### Post by sp40140 on 2017-03-27
I do, and suggest that you do as well. Unless you have internet connectivity / limited data issues. VMs are like any other computers and should be treated as such. I have 16.10 host and three different distros + win7. I never update win7, I have disabled the updates. But the others, they are kept up with updates.
BTW, I use VMWare Player. I found it to be much better than VirtualBox.

---

### Post by wildmanne39 on 2017-03-29
Yes, I update my vm's the same as I do physical installs.

---

