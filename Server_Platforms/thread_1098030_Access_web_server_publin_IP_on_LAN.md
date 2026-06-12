---
title: "Access web server publin IP on LAN"
date: 2009-03-16
forum: Server Platforms
---

### Post by pwebguy on 2009-03-16
I have two web servers on my office network, and am installing another server for local backups. The web servers are connected to a switch provided by the ISP, and I have no access to change the settings.

Is there a way to configure or set up the web servers so that they have a local IP address on our LAN as well as the public IP address so that I can do backup work across my LAN?

I thought of maybe utilizing a router, connecting the web servers to it as well as the backup server, but then how to configure the local IP's also?

I want to adhere to best practices so any advice would help.

---

### Post by kanikilu on 2009-03-16
I would think the servers will need 2 NIC's on them to be able to assign more than 1 IP address. Then just set /etc/network/interfaces so that eth0 uses the external address and eth1 uses the internal address (for example).

---

### Post by hyper_ch on 2009-03-17
is it a switch or router/modem?

---

### Post by pwebguy on 2009-03-17
It's a cisco switch provided by our ISP. There are no configurations available that I know of.

---

### Post by hyper_ch on 2009-03-18
so you got multiple public ip addresses?

---

### Post by BkkBonanza on 2009-03-18
You can assign more than 1 ip address by using virtual interfaces. You don't need another nic to do that. You end up with interfaces like eth0:1 that can have their own ip. I googled for you and found this  below but there are many places to read about it.

[http://handsonhowto.com/virt.html](http://handsonhowto.com/virt.html)

How you solve your problem depends  alot on the exact topology of your network. A switch alone isn't going to get your servers connected to the web so your isp must have something else in the config now. Typically you have a router on the public end that routes web requests to the servers on your lan. If your servers are actually part of your isp's lan then you would probably need a router of your own to bridge from their lan to yours. Then you put your servers on your lan and they get a local ip on your lan. Your router then filters and forwards http requests to your servers but they only have one (local) ip in that case. To really know the right answer more needs to be known about how you connect to the net via isp.

---

### Post by windependence on 2009-03-18
> **BkkBonaza said:**
> You can assign more than 1 ip address by using virtual interfaces. You don't need another nic to do that. You end up with interfaces like eth0:1 that can have their own ip. I googled for you and found this  below but there are many places to read about it.

[http://handsonhowto.com/virt.html](http://handsonhowto.com/virt.html)

How you solve your problem depends  alot on the exact topology of your network. A switch alone isn't going to get your servers connected to the web so your isp must have something else in the config now. Typically you have a router on the public end that routes web requests to the servers on your lan. If your servers are actually part of your isp's lan then you would probably need a router of your own to bridge from their lan to yours. Then you put your servers on your lan and they get a local ip on your lan. Your router then filters and forwards http requests to your servers but they only have one (local) ip in that case. To really know the right answer more needs to be known about how you connect to the net via isp.

This will work just fine if you assign a virtual IP to the NIC so that it has both IPs. Do not try to put in a second NIC and assign it an internal IP because while it will work, you will have ARP errors galore since the packets may travel through either interface.

If you do assign a virtual internal IP to the NIC, you should adjust your hosts file on your internal machines to reslove the box name to the internal IP, otherwise you may have DNS issues.

-Tim

---

### Post by pwebguy on 2009-03-18
The ISP provides a modem, router and the switch. I have 5 public IP addresses to work with now and will be expanding soon so I wanted to get this backup configuration solved before it grew too big;

Our small company has grown a lot over the past several years, and we made the decision to move from multiple leased servers and coloco's to hosting our own servers, so while I have plenty of server admin experience I am still learning a lot on the job. No complaints, though :^)

Virtual interface looks like it will solve the problem, thanks for the link. Now that I know what to search for, I'll do some googling and some testing.

Thanks!

---

