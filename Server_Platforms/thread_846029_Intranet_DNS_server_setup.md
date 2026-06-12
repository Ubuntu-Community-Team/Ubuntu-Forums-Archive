---
title: "Intranet DNS server setup"
date: 2008-07-01
forum: Server Platforms
---

### Post by raul_bhatia on 2008-07-01
Hello Linux Gods,
I have a linux machine that I want to use as a server to host applications on. I have installed applications like SugarCRM and Zenoss on this machine and I want other computers in my office to have access to these applications using a domain name. We have a LAN network with static IPs. 

I can access these applications from other computers using the ip address of the server but i want to use names like "abc.example.com". All the other computers are running Windows and I am running Linux Ubuntu 8.04 on the server. Im just looking for a simple setup because I dont have a lot of computers. I tried doing the following (if anyone is familiar with MaraDNS):

I installed MaraDNS and tried to set up an authoritative DNS server. I followed the instructions and configured the mararc file to contain the following four lines:
csv2 = {}
csv2["automech.com."] = "crm.automech.com"
ipv4_bind_addresses = "9.0.0.114"
chroot_dir = "/etc/maradns"

And I configured the zone file crm.automech.com in the etc/maradns directory to contain just the following single line:
crm.% 9.0.0.114 ~

This does not seem to be working. I'm sorry if the question appears outright stupid. But I am completely new to networking as well as Linux. Can someone help me out with MaraDNS or offer another solution to set up the server. I would be very grateful.

Thanks,
Rahul

---

### Post by wlee on 2008-07-01
> **raul_bhatia said:**
> We have a LAN network with static IPs.

. . .

I can access these applications from other computers using the ip address of the server but i want to use names like "abc.example.com".

. . .

This does not seem to be working . . . But I am completely new to networking as well as Linux.

I don't know much about MaraDNS, but a couple of simple questions come to mind based on the amount of information you've provided . . .

[LIST=1]
[*]Are all the clients configured to look to your server for DNS resolution?
[*]Is your server configured to accept incoming traffic on the appropriate ports for DNS queries? I can assume that MaraDNS will configure this on install, but I wouldn't know for sure.
[/LIST]

---

### Post by windependence on 2008-07-02
How many computers are on your LAN?

-Tim

---

### Post by rickyjones on 2008-07-02
> **raul_bhatia said:**
> Hello Linux Gods,
I have a linux machine that I want to use as a server to host applications on. I have installed applications like SugarCRM and Zenoss on this machine and I want other computers in my office to have access to these applications using a domain name. We have a LAN network with static IPs. 

I can access these applications from other computers using the ip address of the server but i want to use names like "abc.example.com". All the other computers are running Windows and I am running Linux Ubuntu 8.04 on the server. Im just looking for a simple setup because I dont have a lot of computers. I tried doing the following (if anyone is familiar with MaraDNS):

I installed MaraDNS and tried to set up an authoritative DNS server. I followed the instructions and configured the mararc file to contain the following four lines:
csv2 = {}
csv2["automech.com."] = "crm.automech.com"
ipv4_bind_addresses = "9.0.0.114"
chroot_dir = "/etc/maradns"

And I configured the zone file crm.automech.com in the etc/maradns directory to contain just the following single line:
crm.% 9.0.0.114 ~

This does not seem to be working. I'm sorry if the question appears outright stupid. But I am completely new to networking as well as Linux. Can someone help me out with MaraDNS or offer another solution to set up the server. I would be very grateful.

Thanks,
Rahul

I have no experience with that DNS Server but I do recommend the BIND9 DNS Server. It is pretty simple to configure using WebMin.

A few questions though that might allow others to help you more on this issue:

1. Are the computers connected to the internet?
2. What are the current DNS server settings?
3. How much experience do you have with configuring server items?

Configuring BIND9 is not that difficult, there are a multitude of how-to's out there and I'd be happy to walk you through it if you'd like. However you have to keep in mind that if the computers are connected to a router and the internet then they currently use an alternative DNS server. Configuring your system as the DNS server will work fine until you forget and power it off, then the other systems will not have a good time.

Just a few things to keep in mind.

Sincerely,
Richard

---

### Post by windependence on 2008-07-02
Most small networks don't need a DNS server. Putting host entries in their host files will be fine. If you have more than say 10 computers you may want to set one up but really, most people don't understand that for DNS lookups you use a public DNS server on the internet. You don't need to set one of these up at all to resolve internet URLs on your home LAN, just set your primary and secondary DNS servers to a good fast DNS server and you are good to go. Almost no one needs to set up bind9 on their home network, it isn't necessary.

-Tim

---

### Post by rickyjones on 2008-07-02
> **windependence said:**
> Most small networks don't need a DNS server. Putting host entries in their host files will be fine. If you have more than say 10 computers you may want to set one up but really, most people don't understand that for DNS lookups you use a public DNS server on the internet. You don't need to set one of these up at all to resolve internet URLs on your home LAN, just set your primary and secondary DNS servers to a good fast DNS server and you are good to go. Almost no one needs to set up bind9 on their home network, it isn't necessary.

-Tim

It sounds like he is doing this at his work, not home. He is trying to make it easier for others to access some intranet sites. Editing the hosts file on each PC would work as well but that introduces more of an overhead than you usually get with a simple DNS server.

Otherwise you are correct - no need to setup your own DNS server just for internet use. For my home network I point clients to OpenDNS because it seems faster than my own ISPs servers!

-Richard

---

### Post by mrpeenut24 on 2008-07-02
Not necessarily more overhead.  You still have to configure every PC on the network to use your DNS, and if the server goes down for whatever reason, then nobody can access the internet.  It's usually *much* easier to just edit the hosts files.

---

### Post by koenn on 2008-07-02
> **mrpeenut24 said:**
> Not necessarily more overhead.  You still have to configure every PC on the network to use your DNS, ....
No, you do that automatically, through dhcp.

There happens to be an excellent solution for this sort of situations ; dns masq. 
what it does :
1- it's a dhcp server so you don't have to do manual network configuration. You can use the dhcp to set the DNS servers for the LAN hosts, easily.

2- it acts as a dns server for the LAN by using its own /etc/hosts file as zone file, so you have the ease of editing /etc/hosts combined with only having to do it on one host.

3- if forwards non-LAN queries to an external DNS server, by thefault the one mentioned in it's own /etc/resolv.conf. So your DNS needs for internet access are covered automatically

4- it resolves names/addresses for hosts that got their address through dhcp (provided they're configured to send their name in the dhcp phase) so on the LAN, al your (dhcp-)hosts are accessible by name.

---

