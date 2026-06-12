---
title: "Headless Virtualbox-OSE Hardy?"
date: 2008-04-15
forum: Virtualisation
---

### Post by wolfchri on 2008-04-15
Hello,

is there a way to have virtualbox running on a remote machine, like vmware-server? Obviously, virtualbox wants a RDP client in this case somewhere, while the RDP functionality is not impleneted in the OSE version - which in turn means that Virtualbox OSE can not be used on headless machines, right? :confused:


Is there a way to get the virtual machine running in any other way? 

And even with RDP on the binary version, can I close the RDP session on my remote RDP client without shutting down my virtual machine server? 

Me thinks somehow that Virtualbox is not really meant for server purposes, right? Seems quite limited to me? 

Can you recommend any other virtualization solution that does not require a VT CPU, such as KVM? VMWare-Server is not really free, I doo not like to need a serial number and regisitration, I would like to use an open source software.

---

### Post by mrsteveman1 on 2008-04-15
VMware server is free to use and parts are open source, so unless you were planning on modifying the program it doesn't matter if its truly free software or not. If it works better, use it.

And it does work pretty well, I've used it on a number of headless servers to virtualize a lot of different OS.


Most everything else either requires VT in the processor, or doesn't work very well, if at all, on headless servers.

---

### Post by wyomingguy on 2008-04-29
Actually, VirtualBox does servers really well.  The free version would function great as a headless (no GUI) server.  I have setup the non-free version as a headless machine and it runs great.

If I simply transfer the VMs that I have created to another server running the OpenSource version (must be same release version), then I can boot them up and RDP into them just like any other server.

Note:  The "Virtual" RDP server that comes with the non-free version simply allows you to RDP in to each VM console by host-ip: port.  You must assign a unique port to each of your VMs.  The VRDP Server feature is helpful for running the setup from boot, but once the VM is installed, you do not need it.

---

### Post by wolfchri on 2008-05-01
Hello guy from Wyoming, 

that is what I also found out - I even got one step further as I symlinked all .vurtualbox directories to the same directory on my fileserver. So I dont even need to copy the VM images anymore.

I prepare the VM with the OSE version locally, and then start it from my main server. 

The Ubuntu JEOS server is very useful for this as you get a real slick and slim VM from it. I have currently only one running on my main server, but want to expand to 3 (blog, test environment, ET-QW server)

Of course, one should NOT access a running VM at the same time from another VirtualBox interface, that gives a huge mess :lolflag:

However, VirtualBox for Hardy is sill not out, had to do install all the linux-headers and build-essentual stuff.

---

