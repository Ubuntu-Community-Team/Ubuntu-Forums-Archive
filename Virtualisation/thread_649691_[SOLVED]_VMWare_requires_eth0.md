---
title: "[SOLVED] VMWare requires eth0"
date: 2007-12-25
forum: Virtualisation
---

### Post by Spr0k3t on 2007-12-25
okay, I've got a weird one here.  I've got VMWare server configured and working correctly on my system.  However, every time I install an updated package, install new applications, remove packages/components I have to go back through vmware-config-network.pl.  The reason seems to stem from the requirement of eth0 during the install process through the synaptic package manager.

Is there any way to change the requirement of eth0 to something else, like ath0 (what I have)?

---

### Post by Shazaam on 2007-12-26
Running Dapper with VMware installed from the repo's here......
AFAIK the host is not required to have eth0 installed. VMware uses "virtual" ethernet cards for communication between the host and the guest so your physical "eth0" or "auth0" should be separate from the vm. The guest WILL need a virtual eth0 and/or eth1. I run VMware Player using "nat" networking so your config might be different. I also do not have a physical ethernet card installed on my system as I use dialup. Here are the relevant .vmx entries on my system...

Ubuntu host; Mepis guest:

# First network interface card
ethernet0.present = "TRUE"
ethernet0.virtualDev = "e1000"
ethernet0.connectionType = "nat"
ethernet0.addressType = "generated"
ethernet0.generatedAddressOffset = "0"

Ubuntu host; WinXP guest:

# First network interface card
ethernet0.present = "TRUE"
ethernet0.virtualDev = "vlance"
ethernet0.connectionType = "nat"
ethernet0.addressType = "generated"
ethernet0.generatedAddressOffset = "0"

WinXP host; Ubuntu guest:

# First network interface card
ethernet0.present = "TRUE"
ethernet0.virtualDev = "e1000"
ethernet0.connectionType = "nat"
ethernet0.addressType = "generated"
ethernet0.generatedAddressOffset = "0"

WinXP host; Win98 guest:

# First network interface card
ethernet0.present = "TRUE"
ethernet0.virtualDev = "vlance"
ethernet0.connectionType = "nat"
ethernet0.addressType = "generated"
ethernet0.generatedAddressOffset = "0"

I can and do run Synaptic updates/install software on ALL of the guests/hosts with zero problems. The Win98 guest has VMware tools installed so I can drag and drop files between XP and 98.
Hopefully this post will help you resolve your problem.

---

### Post by Spr0k3t on 2007-12-27
Perhaps I didn't give enough information.

Host: Ubuntu 64
Guest: any

I performed a --purge of vmware and did a reinstall so I can see what's happening and what steps it took for me to recreate the problem.

After the --purge I did a reinstall after a clean boot with no extra apps running outside of a standard Gutsy install (with updates).  The install goes smooth, but the application will not run, exits without errors.  Searching online I found I have to run the vmware-config-network.pl script so I can change the configuration from eth0 (default) to anything else.  From here, vmware console works locally without any problems... until I reboot or go through an update/upgrade.

On reboot, I get notified there are updates available for vmware.  The software will launch, but when I try to open a guest session I always get the same error message.  See thumbnail.

So I go back through the vmware-config-network.pl and get the following:
```
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                   failed
Unable to stop services for VMware Server

Execution aborted.
```

When I try to performan an apt-get upgrade, I get the following:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up vmware-server (1.0.4-1gutsy2) ...
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

Do you want networking for your virtual machines? (yes/no/help) [yes] 

Configuring a bridged network for vmnet0.

Your computer has multiple ethernet network interfaces available: ath0, eth2, 
eth3, vmnet1, vmnet8. Which one do you want to bridge to vmnet0? [eth0] 

The ethernet device "eth0" was not detected on your system.  Available ethernet
devices detected on your system include ath0, eth2, eth3, vmnet1, vmnet8.  Are 
you sure you want to use this device? (yes/no) [no] 

Invalid default answer!
Execution aborted.

dpkg: error processing vmware-server (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Now then... I'm a bit more confused now by your post, so I hope this information will help with finding a solution to my issue.

---

### Post by Spr0k3t on 2008-01-09
This is related to the [Bug# 112492](https://bugs.launchpad.net/ubuntu/+source/app-install-data-commercial/+bug/112492).

Here's the temporary fix:[quote=trogdoor]I successfully installed vmware in apt by replacing all instances of "eth0" in /usr/bin/vmware-config-network.pl with "eth1"[/quote] Essentially replacing "eth0" with the interface you want to use.

---

### Post by Shazaam on 2008-01-09
Sorry it seems that I was a little confused by your first post so I guess we are even. :)
It looks like you have it all squared away.

---

