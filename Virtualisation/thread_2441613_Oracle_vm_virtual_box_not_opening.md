---
title: "Oracle vm virtual box not opening"
date: 2020-04-25
forum: Virtualisation
---

### Post by AnupamMitra on 2020-04-25
My OS was Ubuntu 19.10 64 bit. Today this has been upgraded to Ubuntu 20.04. Thereafter, when I tried to open the Oracle VM Virtual Box, which was active with earlier OS 19.10, it failed with a following message.

```

RTR3InitEx failed with rc=-1912 (rc=-1912)

The VirtualBox kernel modules do not match this version of VirtualBox. The installation of VirtualBox was apparently not successful. Executing '/sbin/vboxconfig'

may correct this. Make sure that you are not mixing builds of VirtualBox from different sources.

where: supR3HardenedMainInitRuntime what: 4 VERR_VM_DRIVER_VERSION_MISMATCH (-1912) - The installed support driver doesn't match the version of the user. 

```

Kindly advise how to overcome the problem.

---

### Post by ajgreeny on 2020-04-25
This looks like a Virtualbox version problem.
How do you install VBox; from the Ubuntu repos or direct from Oracle's own repos?
Do you know which version you were using and also what is now installed?

---

### Post by AnupamMitra on 2020-04-25
> **ajgreeny said:**
> This looks like a Virtualbox version problem.
How do you install VBox; from the Ubuntu repos or direct from Oracle's own repos?
Do you know which version you were using and also what is now installed?

Thanks ajgreeny. After creating thread, I could remember that I had faced a similar situation while my OS was upgraded to 18.04. Therefore, I installed Oracle Virtual Box from Ubuntu repository afresh, installed VirtualBox Guest Additions and Extension Pack too. But the installation of Extension Pack couldn't be done properly and it was fixed for a long time. Therefore, I closed the Terminal. Now VirtualBox is working but I couldn't succeed to install Extension Pack.

---

### Post by AnupamMitra on 2020-04-25
I tried to install extension pack afresh, but it is fixed again. The position is given below.

```

anupam@anupam-ubuntu:~$ sudo apt install virtualbox-ext-pack
[sudo] password for anupam: 
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is heWaiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is heWaiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is heWaiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is heWaiting for cache lock: Could n

```

I presume that there is a mismatch of version of virtual box and extension pack despite downloading from Ubuntu repos. 

Awaiting for your advise.

---

### Post by ajgreeny on 2020-04-25
Without knowing the versions of each that you are using it's difficult to know what is wrong but I suspect still a version conflict.

I have used the Oracle VBox repos for a long time now so I'm using VBox 6.1.6 with the Guest Additions from the site at [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads).

There are instructions for adding the VBox repos in the section ***Debian-based Linux distributions*** at [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by AnupamMitra on 2020-04-25
> **ajgreeny said:**
> Without knowing the versions of each that you are using it's difficult to know what is wrong but I suspect still a version conflict.

I have used the Oracle VBox repos for a long time now so I'm using VBox 6.1.6 with the Guest Additions from the site at [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads).

There are instructions for adding the VBox repos in the section ***Debian-based Linux distributions*** at [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

Thanks for your patience and support. Yes, you are correct, there was a version conflict. Present version of VB is 6.1.6r137129. However, at last I could find the matching Extension Pack. This was embedded in the Guest Addition itself. Simply a mouse click in the VNC (Virtualbox > File > Preference > Extension) settled the issue. :D

---

