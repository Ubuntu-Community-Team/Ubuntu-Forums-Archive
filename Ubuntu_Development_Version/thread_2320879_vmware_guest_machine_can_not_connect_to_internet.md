---
title: "vmware guest machine can not connect to internet"
date: 2016-04-18
forum: Ubuntu Development Version
---

### Post by erkanea on 2016-04-18
Hello,
I am using xubuntu 16.04 fully updated and latest version of VMWare Workstaion 12. My guest OS's can not connect to internet if I use NAT networking. I tested this with different versions of guest Windows's and even an ubuntu guest. 
vmnet8 ip on xubuntu host is 192.168.88.1 and guests are getting ip of 192.168.88.128, gateways are 192.168.88.2. I can not ping the gateway from the guests.
Is this something known?

---

### Post by QDR06VV9 on 2016-04-18
> **erkanea said:**
> Hello,
I am using xubuntu 16.04 fully updated and latest version of VMWare Workstaion 12. My guest OS's can not connect to internet if I use NAT networking. I tested this with different versions of guest Windows's and even an ubuntu guest. 
vmnet8 ip on xubuntu host is 192.168.88.1 and guests are getting ip of 192.168.88.128, gateways are 192.168.88.2. I can not ping the gateway from the guests.
Is this something known?
I too was going through something quite similar a few months ago..anyway long story short.
 I found that by manually setting the IP address on both the workstation and the client has allowed me to connect to the internet.  I need to do some further testing but it seems like the DHCP server is not issuing an IP address on the guest machine.
Oh and BTW, I use Bridged connections
DHCP for host yes.  For guest No.
EDIT: the NAT (vmnet8) subnet is 192.168.10.x, so your VM needs an IP address in this range with subnet mask 255.255.255.0 and the default gateway as well as the DNS-Server address set to 192.168.10.2.

Hope this is helpful regards.

---

### Post by erkanea on 2016-04-20
i noticed that the dhcp service is assigning wrong ip address for gateway. in my case vmnet8 on host (ubuntu) has 192.168.88.2 and guest's gateway is 192.168.88.1 and guest can not ping the gateway.

---

