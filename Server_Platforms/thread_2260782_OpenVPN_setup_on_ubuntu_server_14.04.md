---
title: "OpenVPN setup on ubuntu server 14.04"
date: 2015-01-14
forum: Server Platforms
---

### Post by darkapec on 2015-01-14
I am new to openvpn and have read numerous tutorials online about initial setup and configuration. Hopefully someone here can be of a little more assistance. 

Here is the setup
```



# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
# This is my outside network 
auto eth0
iface eth0 inet static
        address 70.88.120.***
        gateway 70.88.120.***
        netmask 255.255.255.0
        dns-nameservers 75.75.75.75


#This is my local internal network
auto eth1
iface eth1 inet static
        address 192.168.1.6
        network 192.168.1.0
        netmask 255.255.255.0
        broadcast 192.168.1.255
        dns-nameservers 192.168.1.2

```

My openvpn clients will connect using the outside network static ip. 

My questions are 
1. Is the internal (eth1) required?
2. How can the clients access the internal network on eth1 if they are connecting on eth0? 
3. I currently have openvpn assigning the default ip's 10.8.0.1/24 is this correct?

Them primary mission is to allow outside vpn clients to be able to access a samba server on ip 192.168.1.5

Any help is much appreciated

Thanks

---

### Post by darkod on 2015-01-14
1. If your primary mission is access to 192.168.1.5, then eth1 is required. A vpn client will connect to your vpn server on eth0, but without eth1 it can only reach the vpn server and nothing else.

2. You need a few things for vpn client to access another machine in the LAN:
- You need to allow traffic between tun0 and eth1 in your firewall (if you don't have firewall running on the machine configure one ASAP, you can't have a public IP machine without firewall, it's asking for trouble)
- You need to configure ubuntu to allow packets forwarding between interfaces. You do that in /etc/sysctl.conf. You need to enable the net.ipv4.ip_forward=1 option. Remove the # sign in front if there is one and reboot the server.
- You need to tell your vpn server to push a route to clients in server.conf. This is so that clients know to send traffic to 192.168.1.5 through the vpn. To allow the whole 192.168.1.x subnet in server.conf make an entry like:
```
push "route 192.168.1.0 255.255.255.0"
```

Save and close the file and restart the openvpn service. Depending on the client OS you might need to run the vpn client as administrator (for win7 for example), otherwise the route will not be configured properly.

3. Using the default vpn subnet of 10.8.0.x is OK, but if in the future you want one of the clients to connect to a second vpn the second vpn server can't use the same subnet. Have that in mind.

Also, your selection of subnet for the LAN of 192.168.1.x is a very bad choice. Many home routers and even business routers use as default 192.168.1.x subnet. If you have any client with that local LAN, it can't work correctly with your vpn and again 192.168.1.x on the other end. Especially since you want clients to reach 192.168.1.5. Depending whether your setup is already in production, I would strongly suggest to change the server local LAN subnet to something like 10.1.1.x or 10.10.1.x. Basically use any 10.x.x.x that you want. Just not 192.168.1.x.

Let us know how it goes.

---

### Post by darkapec on 2015-01-14
I will update the server config as you suggested. The current vpn is not in production... however the 192.168.1.5 server is. All of the clients have a 192.168.1.XXX network so I will probably need to change the production network before I can go any further (huge task, over 200 devices on the network many with static ips, dont look at me the previous IT guy did it lol). So far there had been no reason to change it, but if it is required to get the vpn to work correctly I will get started. 

Thank you for your response, glad I was able to find someone here with an understanding of openvpn.

---

### Post by darkod on 2015-01-14
Wow... I mean you can always "risk" it, and hope no client will show up with local ip in the same subnet. Or if clients are all from another office all you need is to check which subnet that office uses.

Otherwise, the logic is clear. Imagine tomorrow a client home router uses 192.168.1.x and the client has ip 192.168.1.100. When he tries to open 192.168.1.5 how will the local router know whether to look for that machine on its local subnet, or send it over the vpn?

There might be a workaround for this situations but honestly I have never looked for one. I just try to follow the basic vpn rule that the remote networks can't have same subnets. Whenever it's up to me of course... :)

PS. The good news in bad might be that if LAN clients are dhcp like they usually are, you only need to change the dhcp range. Don't forget to modify any static addresses, like the server, main router, printers, etc. But at the end, it might be just a few devices as opposed to 200+.

---

### Post by darkapec on 2015-01-14
Yes a majority will be easily changed by modifying the dhcp scope. The problem with that is all of the VoIP phones have been statically configured within the 192.168.1.XXX addresses, guess now is a good time to get them all moved to a VLAN... its funny how one little request from the boss turns into a weekend nightmare. Now you can see why the previous IT guy is not around any more ;)

---

### Post by darkapec on 2015-01-25
Just finished redoing the entire address scheme for the network. 

Darkod i cannot thank you enough the new address pool fixed openvpn. It actually fixed the openvpn install that I tried to setup months ago on our pfsense network appliance. 

Openvpn was very easy to setup once the network was configured correctly.

Thanks again darkod

---

