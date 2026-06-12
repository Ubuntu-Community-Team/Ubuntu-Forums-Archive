---
title: "Seeking advice on server virtualization"
date: 2008-06-18
forum: Server Platforms
---

### Post by satimis on 2008-06-18
Hi folks,


Server virtualization.


What will be the best planning, strategy, etc. on server virtualization?  Google found me tons of article sufficient for me reading a month.  Can any folk shed me some light on;

- whether the host should not run any server or application on it except VMware/Xen/Virtualbox/qemn etc. there ?

- if there is only one fixed IP/public IP can it satisfy all servers running on the virtural box?  OR multiple fixed IP/public IP are needed?

- Which servers can't be co-exist

- Network arrangement.

- Can I run Vyatta on the same box
[http://www.vyatta.com/](http://www.vyatta.com/)


Pointer would be appreciated.  TIA


B.R.
satimis

---

### Post by firecat53 on 2008-06-19
My only piece of advice is ..... don't use a windows host .... especially Vista!!! I had nothing but problems trying to virtualize my home server on Vista host, using both Vmware and Virtualbox.

Oh, and make sure you have plenty of RAM. 

Scott

---

### Post by satimis on 2008-06-19
> **firecat53 said:**
> My only piece of advice is ..... don't use a windows host .... especially Vista!!! I had nothing but problems trying to virtualize my home server on Vista host, using both Vmware and Virtualbox.

Hi Scott,


Thanks for your advice.  Vista is resource hog.


What I expect to know/clarify;

- Whether we should not run anything on the host other than VMware/Xen/VirturalBox, etc.


- Can I run a workstation as host?  Because I don't install X packages on server.  I do headless installation.


> 
Oh, and make sure you have plenty of RAM. 
I have >4G RAM on board.


B.R.
satimis

---

### Post by gtdaqua on 2008-06-19
Keep the host as minimum as possible. Do not install anything other virtualization-server-software. You can max on performance this way. You technically "CAN" run other software but you might end up sacrificing performance. 

I have an AMD Opteron Dual-core running Hardy server and VMware server running Win2k3 as a guest. 2GB is now almost utilized because I am running Zenoss NMS on the host. Win2k3 is running other apps as well. So I will try to keep the host running on a bare minimum kernel and apps.

Your memory is above 4GB, so go for a 64bit OS instead of 32-bit and PAE stuff. Remember, the base OS has to be solid and should not require frequent restarts. So in any case, Windows as your base is no good. Its bad. Hardy 64-bit or Debian Etch or CentOS should be your ideal choice.

You can run on workstations, but make sure the hardware is good enough. Most server processors are specifically designed to support virtualization - Intel VT, AMD-V etc. It would be better if you used these.

Once you have virtualization installed, don't stop there! Tweak it to get maximum performance. Try as much as possible to run all VMs on physical RAM. Swapping too much will negatively impact the performance of the guest VMs. Adjust your "swappiness" of your host to prioritize and use physical RAM.

---

### Post by satimis on 2008-06-19
> **gtdaqua said:**
> Keep the host as minimum as possible. Do not install anything other virtualization-server-software. You can max on performance this way. You technically "CAN" run other software but you might end up sacrificing performance. 

I have an AMD Opteron Dual-core running Hardy server and VMware server running Win2k3 as a guest. 2GB is now almost utilized because I am running Zenoss NMS on the host. Win2k3 is running other apps as well. So I will try to keep the host running on a bare minimum kernel and apps.

Your memory is above 4GB, so go for a 64bit OS instead of 32-bit and PAE stuff. Remember, the base OS has to be solid and should not require frequent restarts. So in any case, Windows as your base is no good. Its bad. Hardy 64-bit or Debian Etch or CentOS should be your ideal choice.

You can run on workstations, but make sure the hardware is good enough. Most server processors are specifically designed to support virtualization - Intel VT, AMD-V etc. It would be better if you used these.

Once you have virtualization installed, don't stop there! Tweak it to get maximum performance. Try as much as possible to run all VMs on physical RAM. Swapping too much will negatively impact the performance of the guest VMs. Adjust your "swappiness" of your host to prioritize and use physical RAM.
Hi gtdaqua,


Thanks for your advice.


All PCs here are running 64bit OS and I don't have Windows here.  


What I'm prepared to set up is;

- A 32/64 bit workstation as host for running Xen server (I have a VMWare box here.  I'm planning to test Xen, never run it).  I'll config/install the servers on Xen via the workstation.  As all servers here are running headless.

- Servers to be installed on the virtual box : Mail server, Web server, File server/NAS at start.

- I'll install Vyatta on the virtual box as well, for testing only.  I don't think I need it to cater only 3 servers.


Have you had experience on vserver?  I'm interested to test it.  I'll install in on CentOS running on the same virtual box later.


TIA


B.R.
satimis

---

### Post by gtdaqua on 2008-06-19
satimis, you shouldnt have problems installing vyatta. it seems it supports running on a virtual environment. its a good thing to run such appliances as a vm because they can quickly start up in case of a reboot.

---

### Post by satimis on 2008-06-19
> **gtdaqua said:**
> satimis, you shouldnt have problems installing vyatta. it seems it supports running on a virtual environment. its a good thing to run such appliances as a vm because they can quickly start up in case of a reboot.
Thanks


satimis

---

