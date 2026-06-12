---
title: "Ltsp Client no dhcp"
date: 2012-01-11
forum: Server Platforms
---

### Post by buyit1986 on 2012-01-11
I just setup a Ubuntu desktop with the ltsp add-on and i cant seem to get the thin client to boot i am using vmware and the server has to NICs, one is for internet and the other for booting clients. the internet one works fine but the other one seems connected but the clients say no  dhcp or proxy dhcp received. I just want to know what the default IP address the server sets up when u install it on a running desktop. both machines have the same nic and drivers so i don't know what i am doing wrong the server has 512mb ram 5gb hd set for 2 processor cores. i know the server ram is on the skimpy side but this is just a test so i know what i am doing when i get a real server to set all this up. any and all help would be very appreciated thank you in advance.
If there is any other info you need let me know and i will post it. i want to make sure all this works before i spend big money buying a server.

---

### Post by HugoSerrano on 2012-01-11
Hello.

You got DHCP server running on server?
Do you got Vlans? Does the 2nd server NIC it's on the same Vlan then Thin Clients?

Regards!

---

### Post by buyit1986 on 2012-01-11
i set the vlans to the same and how do icheck to make sure the dhcp is running

---

### Post by HugoSerrano on 2012-01-12
You can connect any computer on same vlan and see if you get an IP.

Else, on server, you can do:
ps -e | grep dhcpd 

But you also need to make sure that you got the dhcpd well configured.

Regards!

---

### Post by buyit1986 on 2012-01-12
ok thankyou ill give it a try ill letu know how it comes out

---

