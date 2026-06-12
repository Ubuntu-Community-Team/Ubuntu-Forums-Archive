---
title: "ip for lamp running on esxi"
date: 2010-05-28
forum: Virtualisation
---

### Post by karmic-koala on 2010-05-28
I am new to HyperVisors. I installed ESXi on a Dell Poweredge 2950 server today. The network people were able to bind the server's mac address to a static IP. We don't have DHCP on our subnet yet so had to supply these details manually to ESXi.

Since then I've installed a copy of Ubuntu Server (virtual machine) using vSphere. Whilst installing I had the option to connect to VM Network which is what I did because I do not have more static IPs.

During installation I get prompted by virtual machine there ain't no network interface and post installation ifconfig confirms the machine's got no IP.

Any ideas on how can I get this virtual machine and others connected to the internet?

---

### Post by BobVila on 2010-05-28
> **karmic-koala said:**
> I am new to HyperVisors. I installed ESXi on a Dell Poweredge 2950 server today. The network people were able to bind the server's mac address to a static IP. We don't have DHCP on our subnet yet so had to supply these details manually to ESXi.

Since then I've installed a copy of Ubuntu Server (virtual machine) using vSphere. Whilst installing I had the option to connect to VM Network which is what I did because I do not have more static IPs.

During installation I get prompted by virtual machine there ain't no network interface and post installation ifconfig confirms the machine's got no IP.

Any ideas on how can I get this virtual machine and others connected to the internet?
Did you add a NIC when you created the VM in the vSphere client? If not, shut the vm down and add one. If you did, you should be able to see the mac address of the interface in the machine settings. 

When you say that ifconfig said you didn't have an IP, did it show eth0, or just the loopback?

If it showed eth0, you need to manually set the IP and related settings, given that you don't have a DHCP server to hand those out. (Ubuntu machines come with DHCP configured by default).

---

### Post by karmic-koala on 2010-05-28
No, it did not have an eth0 just the loopback (lo). I tried doing it two ways, first I tried creating a vm from scratch in vSphere, which only had a lo, then I used viconverter to convert and upload an existing virtual machine (originally created in vmplayer, was connected okay). 

None of these seem to work. And once I create NIC's will they be able to bridge to ESXi and get 172.x address(or similar)? At the moment I don't have any free IPs, not until Monday anyway.

---

### Post by BobVila on 2010-05-28
> **karmic-koala said:**
> No, it did not have an eth0 just the loopback (lo). I tried doing it two ways, first I tried creating a vm from scratch in vSphere, which only had a lo, then I used viconverter to convert and upload an existing virtual machine (originally created in vmplayer, was connected okay). 

None of these seem to work. And once I create NIC's will they be able to bridge to ESXi and get 172.x address(or similar)? At the moment I don't have any free IPs, not until Monday anyway.

Hmm... sounds like you've got the vm misconfigured within the vsphere client. Even if it can't connect, you should still see the device...

---

### Post by karmic-koala on 2010-05-29
Well, its working now. Here's how I got it working.

Previously my NIC was configured as VMXNET2, the guest I was running did not support that type and I had to reconfigure it to VMXNET3 for my guest to be able to detect it.

Although I have it manually configured to a static IP I still wonder if its possible to have a bridge like functionality where guests share hypervisor's IP. It not always possible to have dedicated IP's for every virtual host.

---

