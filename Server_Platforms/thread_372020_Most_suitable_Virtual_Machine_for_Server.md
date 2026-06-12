---
title: "Most suitable Virtual Machine for Server"
date: 2007-02-27
forum: Server Platforms
---

### Post by nalmeth on 2007-02-27
I'm looking for a spot of advice on installing a Virtual Machine.
I want to whet my feet in the server arena, and as safely as possible!! :KS
From what I understand, running the server in a Virtual Machine is the safest way to go.

I tried setting up VMWare Player on Ubuntu, but was asked for a serial number at the end.
This is the first time in maybe 2 years I have been asked such a thing, and I'm kind of put off by VMWare now.

Reading here: [http://en.wikipedia.org/wiki/Comparison_of_virtual_machines](http://en.wikipedia.org/wiki/Comparison_of_virtual_machines)
I was pleased to find there are GPL'd Virtual Machines that seem quite capable. 

I think I've narrowed my choices down to Xen, Virtual Box, and Qemu. 

Apparenly Xen requires a NAT to deliver networking:
> Device Drivers: Not required with the exception of the networking drivers where a NAT is required. A modified guest kernel or special hardware level abstraction is required for guest OSs.Is this non-trivial to setup? Also Xen uses something called [Paravirtualization, modifying the guest OS to run faster in virtualization]("http://en.wikipedia.org/wiki/Xen#Paravirtualization.2C_requiring_porting_of_guest_systems"). Is this something that requires significant work and attention from me, or is it automated?

VirtualBox looks good, maybe easier to setup, but apparently is just a step slower than Xen. Not supporting SMP for guest, but this is probably not a game breaker at this point. Also, only GPL for evaluation version? What gives?

Qemu is unclear about device drivers, but I have used it before to test liveCDs. Also a step slower than Xen. Also no SMP for guest OS. [This benchmark test]("http://www.linux-gamers.net/modules/smartsection/item.php?itemid=56") said:
> Qemu is little bit faster in writing and reading files from/to the virtual harddisk, but the speed of the simulated network communication is very slow.So, is Xen worth the trouble? Is Qemu up to the task of running a Server? Or just I just go with VirtualBox?

---

### Post by bernied on 2007-02-27
I know it wasn't really one of your options, but you can install vmware-server for free. You have to register with vmware, but it doesn't cost anything. And it does work very well. Yes you do need a serial number, but if you register they will give you one. If you are paranoid, you don't even have to give them real information, as long as you give them something in each of the required fields, and a valid email address.

If you install vmware you can install anything you like from cd or even run a live-cd (and you don't even have to burn the cd, just get the .iso image and tell vmware to treat it like it was a drive). So put a ubuntu-server install on there if you want.

---

### Post by jason_vaughan on 2008-02-18
Personally, I think it depends on what you are trying to do.  I'm XEN certified, and I can say its fairly superior to some of the other platforms out there.  The only drawback is the free version of the server is limited to 4 VE's, but unless you have some heavy duty hardware then you probably can't run more than 4 anyways.  XEN allows for full paravirtualization of the OS kernel and you can host both windows AND linux OS's with many of them having paravirtualized driver support.

I'm just testing QEMU, but personally i think that's better for having your virtualized desktop.  I'm dumping my windows workstation to work within the Ubuntu OS environment, so I'm using QEMU to start with on that.

XEN is an easy install.  If you have VT chip then you are set, just download the iso, burn it and boot to it.  You may need a driver disk if you are using a weird raid card or networking device that isn't recognized, but its VERY stable.  I have multiple production servers running on some XEN servers and I've never had XEN fail.

Best of luck.


Jason Vaughan
[www.ntehosting.com](www.ntehosting.com) 
an Alert Systems Inc. Company
[www.alert-systems.net](www.alert-systems.net)
916-290-8606

- Virtualization, Hosting and Consulting

---

### Post by rickyjones on 2008-02-18
I personally recommend VMWare Server - the free version - installs pretty easily on Linux and Windows alike. I've had a lot of good luck with it and I do a lot of work with virtual servers as a testing environment.

-Richard

---

