---
title: "VMWare Tools on ESXi and Intrepid 8.10"
date: 2008-10-31
forum: Virtualisation
---

### Post by buchan on 2008-10-31
I'm having a problem getting the VMWare tools to compile with 8.10 on ESXi 3.5... here's a quick rundown of what I've installed already etc... 
```
 sudo apt-get install build-essential linux-headers-`uname -r`
```

Next I go to install the VMWare client by copying the tar.gz to /tmp and running the installer, when I run the installer I get the attached message (see pic) 

Basically the vmmemctl (memory management and the vmhgfs modules fail)  I'm not really too concerned with the vmhgfs failing but the memory management failing is not good for running VMs

I'm running the 3.5 build of ESXi if that helps at all.

Anybody out there got a workaround for this??

Thanks

---

### Post by _Poincare on 2008-11-02
I am not able to get vm-tools or open-vm-tools to compile under VMWare Fusion.  When I run ./vmware-install.pl it craps out when trying to compile VSOCK module.  PLEASE HELP!!!!:confused:

---

### Post by The_night on 2008-11-02
I believe this link is relevant. 

[http://communities.vmware.com/thread/177150;jsessionid=91B450BDFDDCCF4985A0FC44F1943167?tstart=0](http://communities.vmware.com/thread/177150;jsessionid=91B450BDFDDCCF4985A0FC44F1943167?tstart=0)

---

### Post by _Poincare on 2008-11-02
> **The_night said:**
> I believe this link is relevant. 

[http://communities.vmware.com/thread/177150;jsessionid=91B450BDFDDCCF4985A0FC44F1943167?tstart=0](http://communities.vmware.com/thread/177150;jsessionid=91B450BDFDDCCF4985A0FC44F1943167?tstart=0)

This link doesn't solve anything. It's just some VMWare douche_bag saying they've got their head in the sand and don't know what the heck it going on.......

---

### Post by mastabog on 2008-11-05
the problems come from the fact that part of the vmtools don't work with 2.4.26+ kernels. i "fixed" the vsock and vmmouse issues on my WS 6.5 by installing the 2.6.24-21 kernel and the newest vmmouse driver from intrepid-propose

[http://ubuntuforums.org/showpost.php?p=6108522&postcount=17]("http://ubuntuforums.org/showpost.php?p=6108522&postcount=17")

If you're ok with not running the latest kernel then i believe the fix should work for your esx as well

---

### Post by _Poincare on 2008-11-09
All I want to do is compile vmtools under the standard UBUNTU 8.10 kernals (or whatever comes when you install 8.10). As I'm not an expert, I don't want to fudge around with "patches" or crap. I don't see why the compile fubars when it gets to VSOCK. Please does anyone know how to compile the vmtools for Ubuntu 8.10. Not 8.04, I am looking for 8.10. The directions in the community docs do not work and that link above is junk.

---

### Post by Rever75 on 2008-11-19
Has this been resolved? I have installed ESX 31 U3 and Ubuntu 8.10 Server. I got part of the vmware-tools to install but not all. I have vmnet but not vmmemctl. I would like to get the memory controller to compile at least.

---

### Post by marcpem on 2008-11-19
I have Ubuntu 8.10 Server JeOS 64-bit on ESXi 3.5.0, 110271. I installed VMware Tools with success, here is my how-to guide:

[http://ubuntuforums.org/showthread.php?t=987631]("http://ubuntuforums.org/showthread.php?t=987631")

But the last thing that I haven’t figured out is that when I turn on Paravirtualization in ESXi for this VM I get the message “This kernel requires an x86-64 CPU, but only detected an i686 CPU.” I did turn on VT on the bios of the host machine. Can anybody help ?

---

### Post by PilotJLR on 2008-11-19
Ubuntu 8.10 is not supported under ESX / ESXi 3.5 U3 or lower. If you really want this to work properly, using ESX U3 and Ubuntu 8.04.1, which is supported.

---

### Post by marcpem on 2008-12-27
Hi PilotJLR,

I followed your advice and installed the 64-bit version of Ubuntu 8.04.1 server edition on VMware ESXi Udate 3 (which is officially supported). Everything works perfectly, the vmware tools install in no time. But as soon as I turn Paravirtualization on I get the same error:

“This kernel requires an x86-64 CPU, but only detected an i686 CPU.”

I did turn on VT on the bios of the host machine. 
Can anybody help ?

---

