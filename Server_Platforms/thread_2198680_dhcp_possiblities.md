---
title: "dhcp possiblities"
date: 2014-01-10
forum: Server Platforms
---

### Post by Rakesh_vijayan on 2014-01-10
Let me know my friends is it possible to block a particular system with mac address in dhcp server  is possible.I configured dhcp with static lease .If not what do I need to block particular system with the server ?



Thanks

---

### Post by tfrue on 2014-01-10
You should be able to configure this option from your router. I don't know a lot about IP tables in Linux, but I'm sure a Google search for IP tables in Linux would give you a plethora of options.

Good Luck,
Chris

---

### Post by Rakesh_vijayan on 2014-01-10
Thanks for the replay 

I select the ubuntu box as a dhcp becuse I use pfsense as a routing system that configured in a small system . that system takes more load if the dhcp server is on . that was my decission to create dhcp server box if it possible to controle the client system by the ubuntu box is better  ,


Thanks

---

### Post by Rakesh_vijayan on 2014-01-13
Let me Know my friends were I can find the leased system in dhcp . which monitoring tool is yours prefference 


Thanks

---

### Post by Doug S on 2014-01-13
You can block by mac address on your LAN with this iptables command (substitute for the proper mac address):```
sudo iptables -A INPUT -i eth0 -m mac --mac-source 6C:BE:E9:A7:F1:07 -j DROP
```Depending on how you issue your IP addresses with your DHCP server, you might be able to block the undesired system by exclusion. For example, if you were to issue IP addresses based on MAC address.

The leases file is typically at: /var/lib/dhcp/dhcpd.leases

I do not know about monitoring tools.

---

### Post by Rakesh_vijayan on 2014-01-16
Thanks for the  path information > The leases file is typically at: /var/lib/dhcp/dhcpd.leases and given iptables rule not work for me  your suggestion is correct when I  googled .but its not work for me  any Idea will appreciate for block the dhcp client request with Iptables 

Thanks  all the reders of the post

[ATTACH=CONFIG]249528[/ATTACH]



I tried it with port also nothing is happen to me . client still get the ip address and he is in the same ip when restart network

---

### Post by SeijiSensei on 2014-01-16
If you are using isc-dhcp-server to provide DHCP services, you can block machines from getting an address based on the machine's MAC address by adding entries to dhcpd.conf like this:

```

host badboy {
    hardware ethernet 00:11:22:33:44:55:66;
    deny booting;
}

```

Of course, that won't prevent an intelligent user from setting up a static IP on her machine.  To actually block by MAC address you need an iptables rule of the type Doug suggested.

---

### Post by Doug S on 2014-01-16
Your screen shot shows that your iptables rule has dropped 51 packets. So it appears to be working.

---

### Post by Rakesh_vijayan on 2014-01-17
> **Doug S said:**
> Your screen shot shows that your iptables rule has dropped 51 packets. So it appears to be working.


that I under stand Doug but the client system able to  ip resolving and able to browse in internet . ```
SeijiSensei suggetion is work form me in case of dhcp lease 
host badboy {
    hardware ethernet 00:11:22:33:44:55:66;
    deny booting;
}
``` let me know Doug  why the client system still get access ......

---

