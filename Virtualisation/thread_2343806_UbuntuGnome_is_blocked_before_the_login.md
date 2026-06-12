---
title: "UbuntuGnome is blocked before the login"
date: 2016-11-19
forum: Virtualisation
---

### Post by cialu on 2016-11-19
Hi all.
I have a problem with a user on the it forum.

UbuntuGnome 14.04.5 is blocked before the login on this message:

```

*starting crash report submission daemon

 vboxdrv.sh Starting VirtualBox services vboxdrv.sh Building VirtualBox kernel modules 


```

Also trying to boot with old kernels give the same issue.
Any idea to solve it?

Thanks in advance.

---

### Post by ajgreeny on 2016-11-19
In view of the error you see I assume this is a VM of Ubuntu-gnome therefore I have moved thread to **Virtualisation** which is more appropriate for the problem and should be a better fit.

---

### Post by cialu on 2016-11-21
> **ajgreeny said:**
> In view of the error you see I assume this is a VM of Ubuntu-gnome therefore I have moved thread to **Virtualisation** which is more appropriate for the problem and should be a better fit.

UbuntuGnome 14.04.5 is the host machine.
Ubuntu 16.04 is the guest machine.

The issue is at 'host' machine start-up, I don't know if it's related to Virtualisation.

---

### Post by ajgreeny on 2016-11-21
What version of VBox are you using and have you added yourself as user to the vboxusers group on your host?

Have you installed the **dkms** package in your host which may be needed to build the kernel modules?

---

