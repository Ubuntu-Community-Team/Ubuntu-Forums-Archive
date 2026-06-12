---
title: "Ubuntu on ESXi 5.1"
date: 2015-01-22
forum: Virtualisation
---

### Post by george-openshaw89 on 2015-01-22
Hi,

i am having a problem with ESXi. I am using Ubuntu server 14.04.

I have created 3 vms and as soon as the OS had finished installing on the 3rd vm. The 2nd vm lost its connection to the internet. Now the 1st and 3rd vms are able to ping the gateway and 8.8.8.8, but the 2nd vm is unable to ping the gateway. The 2nd vm can ping the other 2 vms but no other device on the lan. vm1 is a dns server and i can also successfully nslookup google.com and vm3.

thanks

---

### Post by newbie-user on 2015-01-22
IP address conflict?

---

### Post by george-openshaw89 on 2015-01-23
That was my first thought. Nothing else is using that IP address, ive scanned the network

---

### Post by george-openshaw89 on 2015-01-23
Ok, now i have just rebooted vm3 and it has lost its dhcp assigned ip. So vm1 can be rebooted and keeps its network connection. vm2 & 3 are now unable to ping anything on the network other than the ESXi host, vm1 and localhost.
I know its not an issue with DHCP on my network as other devices are working fine. Also vm2 has a statically assigned IP address that was working before.
All the vm's are on the same vswitch and traffic goes out of vmnic0.

---

