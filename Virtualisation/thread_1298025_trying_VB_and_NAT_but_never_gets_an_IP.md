---
title: "trying VB and NAT but never gets an IP"
date: 2009-10-22
forum: Virtualisation
---

### Post by sdowney717 on 2009-10-22
ubuntu host and XP guest
I downloaded the latest VB 3 and got usb figured out. BUT this networking just never works. My ethernet adapter in the guest is the pcnet fast iii and it is installed properly, got the drivers from AMD and XP guest says it is working. 

How do i get the Internet to work on the XP guest?
I have been playing around with bridged, NAT etc... but hitting an impenetrable wall right now.

---

### Post by chipper_farley on 2009-10-22
I always use the bridged ethernet setting.  This will make your VM appear like just another machine on the network.  You'll need to shutdown your VM and change the setting for the network to bridged adapter.  Setup Windows to use DHCP if you have a dhcp server on your network and you should get an IP address and be ready to go.  If not, just assign the IP manually (making sure not to use one already in use of course) and again,  you should be good to go.

---

### Post by sdowney717 on 2009-10-22
well i have tried VBOX and VMWARE and neither one will let me connect anywhere. it feels like ubuntu is blocking them. they never get an ip whether in bridged mode or nat. i tried assigning an ip and it cant see the network or the internet. my router is on DHCP and my network is fine. i have several pc's running various os's.

---

### Post by chipper_farley on 2009-10-26
Maybe you're firewalled somehow on the host?  Are you using IPTables or something?

---

### Post by sdowney717 on 2009-10-26
I eventually got both vbox and vmware to work.
vbox is working with bridged networking, and vmware with nat.
For vbox, i had to set a manual ip.

---

