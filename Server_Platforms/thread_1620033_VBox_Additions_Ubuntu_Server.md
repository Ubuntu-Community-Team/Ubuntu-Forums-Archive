---
title: "VBox Additions Ubuntu Server"
date: 2010-11-12
forum: Server Platforms
---

### Post by bluethundr on 2010-11-12
I am attempting to get copy-paste into the terminal working in ubuntu server 10 with VirtualBox additions which works under a VM. 


This did the trick in a fedora client VM:

```

yum -y update kernel 
2. Next is install kernel-devel, kernel-headers, dkms, gcc serta gcc-c++. The command is

yum -y install kernel-devel kernel-headers dkms gcc gcc-c++
3. Now reboot your Guest system

4. Now its time to install the VBoxGuestAddition. Click Device | CD/DVD Device | VboxGuestAddition.iso

```

I was wondering what packages corresponded under ubuntu so that I can get this working there. 

thanks

---

### Post by CharlesA on 2010-11-12
You just need to mount the Guest additions iso and run VBoxLinuxAdditions-*.run.

I don't think they'll install since the server install doesn't have a GUI, but you can always try.

---

