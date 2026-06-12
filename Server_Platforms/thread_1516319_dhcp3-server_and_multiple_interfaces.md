---
title: "dhcp3-server and multiple interfaces"
date: 2010-06-23
forum: Server Platforms
---

### Post by fdelval on 2010-06-23
Hello


I have a dhcp3-server in a box with 2 interfaces, which are both connected to a switch with all the other computers and a router which also servers dhcp.

The idea is:

Can i  config the DHCP so it can serve both 192.168.1 and 192.168.2 ip's, based on clases, while its connected???

If the server is down, the router will handle all the requests.

---

### Post by jbrown96 on 2010-06-23
You will probably have to give static declarations to all your hosts to identify which subnet you want them on. I don't really understand why you want different subnets; there's no advantage and it's likely to break things.
You will have to create entries like this: ```
host tomato {
     hardware ethernet 00:0C:41:F5:B4:32;
     fixed-address 10.0.0.2;
}
``` for all your hosts and set the address appropriately. 
Switches really aren't designed to run separate subnets. You will have to set the address space for your dhcp server to be 192.168.0.0/16. However, any undefined clients can get unspecified addresses, likely outside the subnets you want.

Without being able to run some type of heartbeat code on the router to see if your server is down, there's no way to have the failover system you want. You can only have one DHCP server on a network or else your clients will not be able to get valid leases. 

Personally, I wouldn't recommend operating different subnets.

---

### Post by fdelval on 2010-06-24
> **jbrown96 said:**
> 

Without being able to run some type of heartbeat code on the router to see if your server is down, there's no way to have the failover system you want. You can only have one DHCP server on a network or else your clients will not be able to get valid leases. 

Personally, I wouldn't recommend operating different subnets.


weird thing is, if i set up my server to serve only in the 192.168.2 (dont forget the other router serves 192.168.1), things go as spected, and every client gets 192.168.2

Bad things start when i set up the server to assing 192.168.2 to some fixed mac's, and 192.168.1 by default, thats when the clients get whatever ip...

also if i disconnect the router, it works well... and i have the authoritative policy set...

---

### Post by jbrown96 on 2010-06-25
I'm not totally sure what you mean. It would be more helpful if you posted your dhcpd.conf

---

