---
title: "Automount vmware shared folder as /home"
date: 2010-12-16
forum: Virtualisation
---

### Post by stevebond001 on 2010-12-16
Hi
I am currently running a physical version of Ubuntu 10.10 with a separate partition mounted as /home.  This allows me to upgrade the version of Ubuntu without overwriting my home folder (when I reinstall I just mount the /home partition as part of the normal setup).
What I am trying to do now is virtualise my Ubuntu PC but leave the original /home partition as a physical device.  I have installed a virtual build of 10.10 within VMware and have shared my /home partition with the virtual machine (which it can see OK).  What I want to do now is automount  the shared /home partition as /home within my virtual build so it will see the files and configs, etc.  This greatly helps when I reinstall applications after an Ubuntu release (as the program configs, etc are located in the user home mount. 

The shared physical home folder is currently mounted at /mnt/hgfs/Home/steve and I can browse to all the necessary files, folders, etc.  But this is not yet mounted as /home.

Can anyone please tell me how I can automount this physical partition as my home folder within my virtualised build?

Many thanks in advance

---

### Post by stevebond001 on 2010-12-17
Anyone please??

---

### Post by dcstar on 2010-12-27
> **stevebond001 said:**
> Hi
I am currently running a physical version of Ubuntu 10.10 with a separate partition mounted as /home.  This allows me to upgrade the version of Ubuntu without overwriting my home folder (when I reinstall I just mount the /home partition as part of the normal setup).
What I am trying to do now is virtualise my Ubuntu PC but leave the original /home partition as a physical device.  I have installed a virtual build of 10.10 within VMware and have shared my /home partition with the virtual machine (which it can see OK).  What I want to do now is automount  the shared /home partition as /home within my virtual build so it will see the files and configs, etc.  This greatly helps when I reinstall applications after an Ubuntu release (as the program configs, etc are located in the user home mount. 

The shared physical home folder is currently mounted at /mnt/hgfs/Home/steve and I can browse to all the necessary files, folders, etc.  But this is not yet mounted as /home.

Can anyone please tell me how I can automount this physical partition as my home folder within my virtualised build?

Many thanks in advance

You should not - under any circumstances - "share" the system folders of a host system with a VM.

The host system assumes it has **exclusive** control of it's system folders, and you cannot run two systems at the same time with both of them designed to function on this assumption.

---

