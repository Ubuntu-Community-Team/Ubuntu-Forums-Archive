---
title: "Ubuntu Server and Static IP"
date: 2016-02-21
forum: Server Platforms
---

### Post by curtis18 on 2016-02-21
Hi guys and gals,

I am using VMware Workstation 12 and I have installed Linux Ubuntu Server 12.4. I am attempting to change the IP from DHCP IP to a Static IP. My plans are to turn this into a Proxy Server using Squid.

I am using NAT settings for the internert connection for the virtual machine.

My IP address (on the guest OS, which I gert from 'ifconfig' is 192.168.124.133, Netmask 255.255.255.0, BCast 192.168.124.255 and the Gateway for my host OS (Windows 10 is 192.168.1.1).

I have tried using the IP Address x.x.x.254 as well, but that doesn't work.

I try to validate the internet connection by typing 'apt-get update' but nothing gets updated as I the network isn't connecting. If I run 'apt-get update' with the DHCP settings, everything updates.

Any questions or any spec queries, please ask.

Many thanks,
Curtis.

---

### Post by SchnappiJedi on 2016-02-21
Use bridged mode for virtual machines in my humble opinion in most situations. If you use NAT mode for virtual machines VMWare/VirtualBox/whatever basically act as a router behind your router. Have you tried bridged mode?

---

### Post by curtis18 on 2016-02-21
Yes I have tried bridged mode, but without the "replicated" box ticked.

---

### Post by SchnappiJedi on 2016-02-21
Try bridged mode again and list full IP address, subnet mask, default gateway (router), and DNS servers of your host computer and of your virtual machine. Command on Windows host computer is "ipconfig /all".

---

### Post by curtis18 on 2016-02-21
Hi, thank you for your reply.

Host:
[ATTACH=CONFIG]267420[/ATTACH]

Guest: (this is my attempt, not the results from ifconfig if it is DHCP)
[ATTACH=CONFIG]267421[/ATTACH]

---

### Post by darkod on 2016-02-21
1. The address also has to be in your router network, for example 192.168.1.10.
2. Delete the network and broadcast parameters, they are not needed and are calculated automatically by the system. They just make the settings more confusing. And in your case they are incorrect because they should be in the 192.168.1.x network too.

After you do that reboot the VM and it should work if the settings are correct in VMware Workstation. You should be able to ssh into the VM on the address you set up, if you have installed the ssh server during installation.

Another thing, why the 12.04 LTS instead of the latest 14.04 LTS?

---

### Post by curtis18 on 2016-02-21
Hola Darkod:) 

I have the following:
[ATTACH=CONFIG]267422[/ATTACH]

Gracies nen.

Edit: The reason for 12.04 is because I am following a tutorial. I am just practising with this at the moment, once it works I will get newest versions and do it again.

---

### Post by darkod on 2016-02-21
OK, that should work if Workstation and VM settings are correct. I haven't used Workstation so I can't comment on that. I use Virtual Box for testing with VMs at home.

---

