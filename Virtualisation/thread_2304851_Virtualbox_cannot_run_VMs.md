---
title: "Virtualbox cannot run VMs"
date: 2015-11-30
forum: Virtualisation
---

### Post by chuck945 on 2015-11-30
I've been running several VMs on Virtualbox for years.  An automatic update managed to break all of them.  The version is DISTRIB_DESCRIPTION="Ubuntu 12.04.5 LTS".  The upgrade event was recorded in /var/logs/dkms.log as: 2015-11-26 08:39:17 upgrade virtualbox 4.1.12-dfsg-2ubuntu0.10 4.1.44-dfsg-1+deb7u1ubuntu1.  The VMs have been using VBoxGuestAdditions version is 4.1.12.  

From another Ubuntu 12.04.5 LTS system I tried to install virtualbox using Synaptic Package Manager.  It gave me virtualbox 4.1.12 but when I selected it, an error occurred that the server did not have that available.

My questions are:
1. How to make my VMs function again.
2. Should I upgrade Virtualbox and the VMs to some newer version like 5.0?

Thanks,
Charles

---

### Post by chuck945 on 2015-11-30
The error message given is:
        RTR3Init failed with rc=-1912 (rc=-1912)The VirtualBox kernel modules do not match this version of VirtualBox. The installation of
        VirtualBox was apparently not successful. Executing  '/etc/init.d/vboxdrv setup'may correct this. Make sure that you do not mix the OSE
        version and the PUEL version of VirtualBox.

        where: supR3HardenedMainInitRuntime
        what:  4
        VERR_VM_DRIVER_VERSION_MISMATCH (-1912) - The installed support driver doesn't match the version of the user.

---

### Post by SeijiSensei on 2015-12-01
Try following the error message by running
```
sudo /etc/init.d/vboxdrv setup
```

The problem is that portions of the Linux kernel need to be recompiled to use the new VirtualBox "module."  If that command doesn't work, try running
```
sudo apt-get install dkms
```
then try the first command again.

Personally I use the Oracle repositories as described here: [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions).  They keep up-to-date with new releases and install flawlessly.

You would need to remove the Ubuntu version first with
```
sudo apt-get remove --purge virtualbox virtualbox*
```

---

### Post by chuck945 on 2015-12-05
Thank you!  This worked perfectly.  When I installed the new upgrade it asked for an upgrade to the extension pack as well so it guided me through.
Thanks, SeijiSensi-san.

---

