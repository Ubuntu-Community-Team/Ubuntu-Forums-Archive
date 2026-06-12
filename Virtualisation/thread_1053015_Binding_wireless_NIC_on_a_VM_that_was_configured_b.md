---
title: "Binding wireless NIC on a VM that was configured bridged to another NIC"
date: 2009-01-28
forum: Virtualisation
---

### Post by gatorguy on 2009-01-28
I am running Ubuntu 8.10 on my laptop and installed VMWare Server v2. I created a VM (virtual machine) and installed Windows XP on that machine. I configured the VM as a bridged to the Ethernet adapter on my laptop. Everything works fine when going through the Ethernet adapter. I took the laptop offsite and connected my Linksys wireless adapter to the laptop and connected to the internet without a problem via a WIFI connection and then started up my virtual machine. The virtual machine shows no network connection. I plug in a network cable into the ethernet port and everything works again. It appears that the VM is binding only to the ethernet port and doesn't recognize the wireless adapter. I looked at the VM configuration parameters for that particular VM and see several references for "ethernet0 & ethernet1". Not sure how to get the VM to bind to that USB NIC. Anyone see this before? I did search on these forums and online prior to posting but wasn't able to find any similar issues.

Thanks in advance for any feedback,
Gatorguy - aka Dan

---

### Post by gatorguy on 2009-01-28
I was able to find the following online post that fixed the issue I was having.It refers to an older version of both Ubuntu and VMWare but still worked.

Hope this helps someone else.
Gatorguy - Dan


*******************************************************************
[http://forums.fedoraforum.org/showthread.php?t=179832](http://forums.fedoraforum.org/showthread.php?t=179832)

Using VMware Server 1.0.x:

1) Install the network card in the host PC
2) Ensure that the network card works in your Fedora installation. ie: It should show up as "eth1", assuming your first network card is "eth0".
3) As root, run "vmware-config.pl". Warning This will stop your Virtual Machines if they are running.
4) Follow the prompts until it asks you about Networking. In the section below, I am adding a second bridged interface on the vmnet2 network:
Code:

You have already setup networking.

Would you like to skip networking setup and keep your old settings as they are?
(yes/no) [no] no

Do you want networking for your virtual machines? (yes/no/help) [yes] yes

Would you prefer to modify your existing networking configuration using the
wizard or the editor? (wizard/editor/help) [wizard] editor

The following virtual networks have been defined:

. vmnet0 is bridged to eth0
. vmnet1 is a host-only network on private subnet 172.16.1.0.
. vmnet8 is a NAT network on private subnet 172.16.117.0.

Do you wish to make any changes to the current virtual networks settings?
(yes/no) [no] yes

Which virtual network do you wish to configure? (0-99) 2

What type of virtual network do you wish to set vmnet2?
(bridged,hostonly,nat,none) [none] bridged

Configuring a bridged network for vmnet2.

The following virtual networks have been defined:

. vmnet0 is bridged to eth0
. vmnet1 is a host-only network on private subnet 172.16.1.0.
. vmnet2 is bridged to eth1
. vmnet8 is a NAT network on private subnet 172.16.117.0.

Do you wish to make additional changes to the current virtual networks
settings? (yes/no) [yes] no

5) Answer the rest of the questions to finish setting up VMware.
6) You can now add a second virtual Ethernet card to the VM via VMware Server Console, and bind that Virtual Ethernet adapter to a "Custom" network, specifying the network you added (vmnet2 in the example above).

Hope that helps. I haven't played around enough with the VMware Server 2.0 Beta to tell you how it works in the new version.

---

