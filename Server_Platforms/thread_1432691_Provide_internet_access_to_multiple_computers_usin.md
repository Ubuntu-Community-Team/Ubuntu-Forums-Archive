---
title: "Provide internet access to multiple computers using only a hub and 1 Ethernet Port"
date: 2010-03-18
forum: Server Platforms
---

### Post by geoffmcc on 2010-03-18
Ever need to provide access to multiple PC's and did not have a router only a hub. Maybe this isn't original thinking, but then again maybe you didn't think of doing it this way (which i am sure there are many ways to do it)

So I have 2 Ubuntu Servers, 1 Windows Box and a Hub - All 3 with internet access off of single ip and single Ethernet port.

While searching for a backup method today I came across Clonezilla. I was wondering if this was the right thing for me and since I needed to backup my roommates PC for a reformat and install of Windows I decided I would give it a try, but only if it would work. I didn't want the hassle of going into the main part of the house and finding out what cord was what as there is a cable modem connected into a switch (4 static IP's with internet) and one port of the switch hooked to a router) Anyways, didn't work he was on the router I was on the switch)

But this got me thinking. When I setup my server to do this, during one of the setup scripts it said it was setting up Internet access for client machines and that it was assigning them IP addresses threw a DHCP server that it had installed. 

So, I dug up the hub connected the internet cable to hub up link and Server 1 on port 1 Server 2 on port 2 and Windows on port 3

The main server gets the internet provided IP address and routes it to the hub via a virtual interface. Server 2 is configured for DHCP and the windows box, It was set to get info automatically but it didn't fill the DNS info so I had to manually do that (just a heads up) I decided to use OpenDNS Servers (208.67.222.222 & 208.67.220.220) but im sure putting in the gateway IP address would have worked too. 


So, by now if you need this I am sure you are excited and want to get to it. Like i said there are probably other ways of doing it, ways that don't involve you installing clonezilla and DRBL, maybe even just DRBL is needed, maybe one of them installed whats needed as a dependency- all I know is it works, if you know - elaborate so people know, but hey- this way not only do you have internet access on all PC's you can deploy custom images to them as well.

Just follow this Tut, very easy. Even an basic user can do it, I know cause I did it.

[http://www.lightcubesolutions.com/blog/?p=33]("http://www.lightcubesolutions.com/blog/?p=33")

---

### Post by geoffmcc on 2010-03-25
This ended up not working to well for me. When I restart my windows PC it does not want to provide internet anymore on the ip address that i configured [example: 192.168.222.3] when i restart I had to change to [192.168.222.4] and then later on at some point change back.

So that obviously wont due. I ended up doing this:

Gateway Machine: edit /etc/network/interfaces
```

# The virtual network interface
auto eth0:1
iface eth0:1 inet static
   address 192.168.1.1
   netmask 255.255.255.0

ifup eth0:

```

Now you need to add to /etc/rc.local (before exit 0)
```

iptables -A FORWARD -i eth0 -o eth0 -s 192.168.0.0/24 -m conntrack --ctstate NEW -j ACCEPT

```
```

iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT

```
```

iptables -A POSTROUTING -t nat -j MASQUERADE 

```

[ If you are not using a virtual interface (i.e you have 2 network adapters) then you would change the second eth0 in the command above to eth1 (or whatever yours is)]

Now we need to enable routing:
```
sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"
```
and
Edit /etc/sysctl.conf and add these lines: 
```
net.ipv4.conf.default.forwarding=1
net.ipv4.conf.all.forwarding=1
```

Now restart the computer and configure your clients accordingly. 


Sample Config for clients
```
# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.2
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        dns-nameservers 208.67.222.222 208.67.220.220

```

The above example nameservers are for open dns. If you are trying to configure a windows machine you would only need to enter address, netmask, gateway and dns (again use opendns above)

When I setup mine i followed [HTML]https://help.ubuntu.com/community/Internet/ConnectionSharing[/HTML] , however it left me with some questions reguarding iptables and eth0:1 so I rewrote to this post following the steps i took to be more clear for the next person

---

