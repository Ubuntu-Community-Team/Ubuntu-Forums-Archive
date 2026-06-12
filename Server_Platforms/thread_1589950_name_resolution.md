---
title: "name resolution"
date: 2010-10-07
forum: Server Platforms
---

### Post by bibble235 on 2010-10-07
Hi,

I have an internal network with a server which has a static IP address. I have set the hostname as suggested in the Perfect Setup. 

However internally I cannot resolve my hostname except for on the actual machine and this is of course because I have added it to the hosts file.

I there a way to resolve this host name on my own internal network. Externally this all works fine it is just on the internal network. 

For the PC's this can be resolved by adding it to each PC's host file however my mobile (nokia C5) does not have this facility.

Thanks,
Iain

---

### Post by kreggz on 2010-10-07
You need to setup a Bind9 server OR if you have a good router like a Cisco 800 series and upwards you can set that up as a DNS server.

[https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)

---

### Post by bibble235 on 2010-10-07
Thanks for your response,

I have set up my server using the instructions and all works well except,

The router (TD-W8960N v1) does not give the server as the default DNS. I have to go to each PC and set it. 

I have set the DNS on the router to be the machine with BIND9 and I am forwarding traffic to the original DNS. All is working welling accept for this manual step of putting in the DNS on the individual PCs which connect to the router.

Thanks,
Iain

---

### Post by BkkBonanza on 2010-10-07
Usually your router's DHCP would hand out the DNS address with it's leases. If you're not configured for DHCP then you would setup DNS manually as well as IPs for each machine..

Using Bind9 to handle local LAN DNS is like using a sledgehammer to fix the furniture. Typically DHCP on good routers can take care of local DNS for hostnames as well. You should check if there is options for DNS as part of the DHCP services. If not then dnsmasq is a much lighter and easier solution for local DNS.

Sometimes you just need to add the setting for the DHCP client to "send hostname" so that the DHCP server receives each system's hostname to add to it's DNS function.

---

### Post by CharlesA on 2010-10-07
> **BkkBonanza said:**
> Using Bind9 to handle local LAN DNS is like using a sledgehammer to fix the furniture. Typically DHCP on good routers can take care of local DNS for hostnames as well. You should check if there is options for DNS as part of the DHCP services. If not then dnsmasq is a much lighter and easier solution for local DNS.

+1. I've used BIND to do local DNS, but dnsmasq is so much easier to configure and deal with.

---

### Post by bibble235 on 2010-10-07
My router does understand DHCP hostnames and will resolve these correctly for machines which are non statics. I cannot make the static IP address in the server be resolve correctly, that was the original problem.

So at the moment I am having to choose between 

a) puting all traffic via the server and manually configuring the DNS on each machine

b) going back to no BIND9 and changing my mobile when I get home to the local IP and back to the external hostname when I leave home.

---

### Post by Morbius1 on 2010-10-07
> My router does understand DHCP hostnames and will resolve these  correctly for machines which are non statics. I cannot make the static  IP address in the server be resolve correctly, that was the original  problem.
This discussion is out of my league but when you say it cannot resolve hostnames for machines that have static ip addresses how are you setting up the static ip address?

Internally within the OS of the server?

Or using the "DHCP Static IP Lease" function of the router?

Or all of the above.

---

### Post by bibble235 on 2010-10-07
Using the set up from Perfect setup.

[http://howtoforge.net/perfect-server-ubuntu-9.10-ispconfig-3-p3](http://howtoforge.net/perfect-server-ubuntu-9.10-ispconfig-3-p3)

Although I am not using ispconfig.

For me I see the problem as the router does not know how to resolved myserver.domain.com internally because the machine is not DHCP and therefore the router is not aware of its name. Whereas all of the other machines are DHCP and therefore do share their name with the router.

There is an option to put in the mac address and IP but this does not seem to work either. The router just goes to the internet and resolves my server to the external IP. To resolve this before buying a mobile I changed all PCs to have the myserver.domain.com in their individual hosts file. However for my mobile there is no hosts file so I thought I would try and resolve it "more correctly" 

Iain

---

### Post by BkkBonanza on 2010-10-08
Ideally you would have all machines use DHCP but the servers tagged as "Static Lease". This forces the DHCP server always give the same IP to those machines but still have the same management functions for DNS and names. Usually you can add static leases by entering the MAC address to attach the server's IP to.

---

### Post by bibble235 on 2010-10-08
Cannot thank people enough for patient,

Note internally the system recognizes the hostname but not the hostname + domain.

i.e. ping myserver returns internal IP, ping myserver.mydomain.co.nz returns the external IP with nothing in the clients host file.

---

### Post by BkkBonanza on 2010-10-08
I hate to sound like a broken record but... this is also often a feature of DHCP. I don't know what options DHCP has on yours. With dnsmasq that I use it allows setting a domain name that can be combined with the hostnames provided by each machine. Check if there is a "network domain" setting in your DHCP.

---

### Post by bibble235 on 2010-10-11
Well just in case people wanted to know the outcome. 

I could not resolve the issue where I use a static IP on my Ubuntu server and DHCP on my router. This is probably a restriction of the router as there is nowhere to enter a domain name in the router configuration and it does not pick this up when configured as a known MAC address in the router.

Thanks all for your patient.

---

