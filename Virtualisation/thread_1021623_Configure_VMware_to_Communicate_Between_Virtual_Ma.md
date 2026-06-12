---
title: "Configure VMware to Communicate Between Virtual Machines"
date: 2008-12-25
forum: Virtualisation
---

### Post by rmoore on 2008-12-25
All:
     I have three virtual machines that I would like to communicate with each other to create a honeynet.  I have my honeywall with three network interfaces.  Eth0 is outbound to the Internet conected to VMnet1.  Eth1 is bridged to Eth0 and connected to VMnet3, and Eth2 is connected to VMnet4.  My honeypot has a single interface connectd to VMnet3.  Finally, I have a machine used for management of my honeywall connected to VMnet4.  

     What I'm not sure about is how to configure the different VMnets.  Running the vmware configuration script, it requires the end-user to choose from NAT, Host-only, or bridged when adding VMnets.  I assume that VMnet1 is bridged.  But, I'm not real sure what VMnet3 and VMnet4 should be.  Experimentation has failed.

    Thanks for the advice.

---

### Post by dcstar on 2008-12-25
> **rmoore said:**
> 
........
What I'm not sure about is how to configure the different VMnets.  Running the vmware configuration script, it requires the end-user to choose from NAT, Host-only, or bridged when adding VMnets.  I assume that VMnet1 is bridged.  But, I'm not real sure what VMnet3 and VMnet4 should be.  Experimentation has failed.

    Thanks for the advice.

VMWare does not "Communicate Between Virtual Machines", the VMs communicate with whatever using the various virtual network interfaces. You choose what particular type of network interface to use with each VM.

---

### Post by bodhi.zazen on 2008-12-26
I am not understanding what you want exactly in terms of networking options.  In general you can use NAT, bridged, or host only networking.

With your description I am guessing you want a bridged network, so use the vmnet interface with all your guests.

---

