---
title: "Unable to intall GuestAdditions and use shared folder"
date: 2015-12-21
forum: Virtualisation
---

### Post by Bello_Dalhatu on 2015-12-21
I have installed Ubuntu server Version 14.04.3 on as a guest on windows 8.1  upgraded to windows 10 using oracle Virtual-box 5.10 . I have updated the guest os as usual, and installed
and mounted the file virtualBoxGuestAddition.iso  file at my home directory. When I run the installer for the Linux version , I get the following errors 
[LIST=1]
[*]The headers for the current running kernel were not found. If the following module compilations fails, this could be the reason 
[*]Building the share module fails.(Look at /var/log/vboxadd-install .log to find out what went wrong). 
[/LIST]

---

### Post by ian-weisser on 2015-12-21
Did you install the kernel headers package? It is not included by default.

Example:
```
$ uname -r
**4.2.0-19-generic**         ## Currently running kernel

$ apt-cache search 4.2.0-19-generic
linux-cloud-tools-4.2.0-19-generic - Linux kernel version specific cloud tools for version 4.2.0-19
**linux-headers-4.2.0-19-generic** - Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
linux-image-4.2.0-19-generic - Linux kernel image for version 4.2.0 on 64 bit x86 SMP
linux-image-extra-4.2.0-19-generic - Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
linux-signed-image-4.2.0-19-generic - Signed kernel image generic
linux-tools-4.2.0-19-generic - Linux kernel version specific tools for version 4.2.0-19
```

If I wanted the kernel headers, I would install the linux-headers-4.2.0-19-generic package.

---

### Post by SeijiSensei on 2015-12-21
If you take the route of installing VB from Oracle's repository as [described here](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions), it will automatically download dkms, gcc and company, and the kernel headers so it can compile the kernel module.  It will also update them if necessary when a new VB release is pushed out.

---

### Post by Tadaen_Sylvermane on 2015-12-21
I have also found it required to install the dkms package as well before guest additions will install properly. However guest additions are based on having an X11 environment. They don't seem to work from what I've seen on a terminal only server installation. For that you will likely need to setup a shared folder on the host and mount it.

---

### Post by Bello_Dalhatu on 2015-12-22
Thank you

---

### Post by Bello_Dalhatu on 2015-12-22
Thank you. But wen I installed the the linux-headers-4.2.0-19-generic package, two error messages were reported as follows:
1.  Error! (dkms apport) : binary for vboxguest 4.3.10 not found
2. Errors : Bad return status for module build on kernal 4.2.0-19-generic(x86-64).

---

### Post by SeijiSensei on 2015-12-22
> **Tadaen_Sylvermane said:**
> I have also found it required to install the dkms package as well before guest additions will install properly. However guest additions are based on having an X11 environment. They don't seem to work from what I've seen on a terminal only server installation. For that you will likely need to setup a shared folder on the host and mount it.

You can install X on the server, then log into that machine with "ssh -X" and run applications on it that display on your local workstation. Or you could install a complete desktop package onto the server.  Or you could install a regular desktop version of Ubuntu so all the X paraphernalia are there.  Little actually differentiates the server from the desktop version other than the absence of a GUI and pre-installed server applications like Apache and MySQL.  If you need them, you can quickly add them with apt-get after the initial configuration is finished.

---

### Post by Bello_Dalhatu on 2015-12-23
Thank you. But how do I set up share folder on the host and mount it?

---

### Post by Bello_Dalhatu on 2016-01-02
Thank you. Your suggestions have been very useful.

---

