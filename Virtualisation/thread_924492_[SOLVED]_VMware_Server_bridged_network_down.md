---
title: "[SOLVED] VMware Server bridged network down"
date: 2008-09-19
forum: Virtualisation
---

### Post by Xkutzy on 2008-09-19
I'm trying to start a Windows2000 virtual machine in VMware server. The machine starts but I get the following error.

"The network bridge on device vmnet0 is temporarily down because the bridged ethernet interface is down"

The background is that I installed VMware server a month or so ago using the instructions in the sticky. I created the virtual machine using VMware converter and installed it no problem. It worked fine for several weeks. Earlier this week my PC went down with a memory controller fault. I replaced the motherboard and all seems to be working fine now. (Network is on the motherboard). The next time I tried to start the virtual machine, there was an error message saying that something had moved (I can't remember what) and offering the choice to keep existing or create new. I chose Keep as I didn't think anything had changed. I then got the above error message and the network is not available to my virtual machine. The network works fine for the host. I have tried running vmware-config.pl and accepting the defaults but that hasn't fixed the problem.

Any suggestions as to how to fix this would be much appreciated.

---

### Post by Xkutzy on 2008-09-19
OK. I did a bit more googling and have managed to fix it. Here's what I did.

When running vmware-config.pl previously I had seen that the bridged network connection was mapped to eth0. I ran ifconfig to display the current network configuration. eth0 was missing, and in its place was eth1. I suspect that this happened when I replaced the motherboard which had the network interface on it. I guess that as the MAC address no longer matched the existing config, a new ethernet port eth1 was created. So next I re-ran vmware-config.pl and changed the network using the editor option, mapping the bridged network to eth1 instead of eth0.

I hope that helps if anyone else has a similar problem.

---

### Post by SecretCode on 2008-09-22
Do you have an option in the virtual network settings for "Automatically choose an available physical network adapter to bridge to VMnet0"? If you have that checked this problem should be avoided in future.

---

### Post by Xkutzy on 2008-09-22
Thanks for the suggestion but I cannot find an option to automatically choose an available physical network adapter in the version of Vmware Server that I am running (1.06). Where should I be looking? Perhaps it is only available in a leter version of a different VMWare product?

---

### Post by SecretCode on 2008-09-24
That's the version I have, except my host (currently) is windows. 

Select Host > Virtual network settings, or open the Virtual Network Editor any way you prefer. Go to the 'Automatic bridging' tab. The first (and only) checkbox is the one you need.

---

### Post by Xkutzy on 2008-09-24
That option does not appear to exist in the Linux host version. I have looked in the server console settings, the host settings and the virtual machine settings and I cannot find the checkbox you describe. I guess this must be a difference between the Windows and Linux versions. Thanks for the sugestion though.

---

### Post by pacice on 2008-09-26
I had the same problem, My motherboard failed and once repaired, no bridged networking.
I ran vmware-config.pl, and used the editor to change the settings for network link 0, from eth0 to eth1.
All seemsto be working now.

Thanks for the advise.

Pacice

---

### Post by untill on 2009-01-19
Ah, had exactly that problem, and the suggested solution solved it. Thanks! :cool:

---

### Post by adhika_rexuss on 2009-04-14
> **Xkutzy said:**
> OK. I did a bit more googling and have managed to fix it. Here's what I did.

When running vmware-config.pl previously I had seen that the bridged network connection was mapped to eth0. I ran ifconfig to display the current network configuration. eth0 was missing, and in its place was eth1. I suspect that this happened when I replaced the motherboard which had the network interface on it. I guess that as the MAC address no longer matched the existing config, a new ethernet port eth1 was created. So next I re-ran vmware-config.pl and changed the network using the editor option, mapping the bridged network to eth1 instead of eth0.

I hope that helps if anyone else has a similar problem.

Hi Xkutzy, 

I'm having the same problem where my Bridged Network is not working. I'm using VMware 1.09 which is the latest version in 1.xx. I configure the Bridge Network to use the wlan0 which is my wireless network. Do you think I should change it to eth0 to get my Bridge Network working?

I always use wireless network, because I don't have any ethernet cable here. Would it be ok if the cable is unplugged but I'm using the eth0 for the Bridged Network interface?

Thank you,
Adhika

---

### Post by Xkutzy on 2009-04-15
Hi Adhika,

I can't tell if using eth0 will solve your problem.  Since you are using wireless wlan0 may well be correct. I suggest you try running ifconfig in a terminal to work out which device you are actually using to connect to the net and use that one in VMware.

Xkutzy

---

