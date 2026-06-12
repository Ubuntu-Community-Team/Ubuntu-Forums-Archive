---
title: "Dell Precision T3400 Ubuntu 9.04 kvm_intel not found"
date: 2009-06-19
forum: Server Platforms
---

### Post by Highway on 2009-06-19
Hi,
I am setting up a Dell Precision T3400 with Intel Quad processor as a server for virtual machines.

I downloaded Ubuntu 9.04 server x86 and installed it fine. 
I chose Minimal virtual host installation, and just chose ubuntu core, openssh server, and virtual machine in the install options.

I have enabled Virtualisation in the bios as per other threads.
However, when i boot up the machine, i get the message:

FATAL: module kvm_intel not found.

Everything else seems fine, and the machine brings me to a login prompt.  However, the keyboard is not responding.  I've tried it in all the usb ports, front and back, and it won't work.  I don't know if this is related to the kvm_intel module or a separate issue. 

Can anyone help me with this?  

I was also wondering if i can put the x64 version of ubuntu on this machine.

Thanks,
Highway.

---

### Post by Highway on 2009-06-19
Hi,
I just downloaded and tried the 64bit version of 9.04 server, and that is exactly the same issue.

Highway.

---

### Post by Highway on 2009-06-20
Ok, making progress.

I reinstalled again, but this time chose Mimimal installation mode, instead of minimal install for virtualisation (or whatever they are called).

The install went fine.  At the package selection, i didn't choose virtualisation host. 
 
After install was complete, i was able to log in fine.  No errors during boot up.  I installed the metapackage ubuntu-virt-server which installs a load of stuff needed (apparently) to use ubuntu as a host for virtual machines.  This installed fine, as did the kvm_intel module, and I installed an updated kernel.

Rebooted, and everything is fine. 

I guess the behaviour described in the previous messages i posted must indicate a bug.  I'll log a bug report about it anyway.

Highway.

---

