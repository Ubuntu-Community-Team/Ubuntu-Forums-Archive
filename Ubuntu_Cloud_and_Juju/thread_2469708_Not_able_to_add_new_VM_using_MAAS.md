---
title: "Not able to add new VM using MAAS"
date: 2021-12-07
forum: Ubuntu Cloud and Juju
---

### Post by dangerzonen on 2021-12-07
Hi all, 
I have installed MAAS server on my VM. I'm using KVM and virt-manager. The setup as follows

Host(Centos7)---KVM(libvirt)---Guest VM(Maas)

network (NAT) 192.168.122.0/24

I'm able to install maas and able to launch the dashboard.  Set the DNS, key, enable DHCP on subnet 192.168.122.0/24 (pool .50-.55)

Then, I create new VM using virt-manager to test and get the ip and boot from MAAS with the setting below

-Network Boot PXE
-OS Type Generic
-1024MB/1/15GB memory,cpu,storage
-Network selection -- NAT 192.168.122.0/24

When boot the VM, it able to get the IP from MAAS i.e. 192.168.122.50-192.168.122.55 but the VM process will stop at user login 'maas-enlisting-node login:' I have wait for 30min and nothing happen. From MAAS dashboard also No new machine added.... I checked MAAS DHCP used, 192.168.122.52 is assigned with status below.

IP Address                 Type                 Interface   Usage   Owner
192.168.122.52 	Observed 		Unknown 	DNS 	   MAAS 

I have tested few times with same behavior...the new vm will stop at login 'maas-enlisting-node login:'

I even create new maas server and still the same. I really need some advise and help on this matter.

Thank you

---

### Post by dangerzonen on 2021-12-07
Updated
1. After I increase the memory, VM able to be added and commissioned.

---

