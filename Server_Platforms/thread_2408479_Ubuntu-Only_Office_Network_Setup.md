---
title: "Ubuntu-Only Office Network Setup"
date: 2018-12-19
forum: Server Platforms
---

### Post by bumcheekcity on 2018-12-19
I'm at a very early stage of working on a project to migrate a small office setup from a Windows based environment to a Linux one. The proposal is to move to Google Hosted Apps for our email, calendar, storage (via Google Drive), docs and spreadsheets. Other needed applications will be an in-house programmed app, migrating our existing programs and software one at a time as we program more functionality. 

I'm experienced in Windows network administration and Linux webserver administration, but not in Linux network design. 

Currently the office runs a standard Windows server network with AD, DNS on one server and various app/web servers (both Linux and Windows) serving a variety of stuff. The office has a completely ordinary router running to connect to the internet, running the DHCP although that functionality can of course be turned off and a hard-coded IP set if needed. 

My intention for the setup is to have a number of physical boxes running virtual machines, obviously providing hardware redundancy. I was anticipating a basic DHCP setup of:

10.0.0.1 - Router (connected to external internet)
10.0.1.x - Physical Machines running server VMs
10.0.2.x - DHCP Servers
10.0.3.x - DNS Servers
10.0.4.x - Web Servers
10.0.x.x - Other Servers as necessary (Git, Puppet, Zabbix, etc.)
10.1.x.x - Desktops, Laptops (pool which clients will connect to)

I've got Virtualbox running on a private network - obviously this won't be able to connect externally but I'm not worried about that at the moment. I have a DHCP server running and two DNS servers. I plan on hardcoding all the server IP addresses in dhcpd.conf as a host{} entry, and this is working. My current dhcpd.conf looks like this:

```
ddns-update-style none;
option domain-name "andach.local";
option domain-name-servers vp-dns1.andach.local, vp-dns2.andach.local;
default-lease-time 600;
max-lease-time 7200;
authoritative;

subnet 10.1.0.0 netmask 255.0.0.0 {
  range 10.1.0.1 10.1.255.255;
  option routers 10.0.0.1;
  option broadcast-address 10.255.255.255;
}

host vp-dns1.andach.local {
  hardware ethernet xx:xx:xx:xx:xx:xx;
  fixed-address 1.0.3.1;
}

//More host declarations as needed...
```

There's a number of questions about both coding and best practise that I have:

[LIST]
[*]I'm confused about the declaration of routers and broadcast address, and I'm not exactly clear what they are - should I be setting these? 
[*]Is is reasonable best practise to hard-code all my server IPs based on MAC Address? 
[*]My second DHCP server I planned to be setup exactly the same as the first, just lacking the "authoritative" statement. That should mean that if the power gets cut to the VMM holding the primary DHCP server, the second one should take over transparently and with no impact to end users. Is that right? 
[*]I'm unsure where to put the firewall, as I'm aware that currently, I don't have that in the plan. Would it be appropriate to configure the router to simply reject all incoming requests on all ports? I don't need the webservers accessible from outside the company but might need so in future - I'm not sure on options here. Obviously each internal server will have a firewall configured to reject all traffic except port 22 and any necessary ports for the service it runs. 
[*]The only systems with hardcoded IP addresses are the DHCP server(s), the VMMs and the Router. Everything else is DHCP. Can/should I use DHCP to assign IPs to the VMMs and the Router? 
[/LIST]

Thanks in advance,

---

### Post by TheFu on 2018-12-19
It is your network. You are responsible, not me. Do what you think is best. Nobody else is in your situation.

No to using dhcp for servers or network devices. Only use DHCP for end-user stuff, not infrastructure. Use DHCP reservations for devices that don't have a keyboard and for specific desktops that need firewall rules.

I'd setup subnets based on required access, not a single purpose.

You need multiple firewalls, not just 1.

I'd begin by making a list of services required. Off the top of my head:
* NTP
* Backup (fully encrypted)
* Authentication/authorization
* Network monitoring, Alarming
* File/Print
* DNS
* DHCP
* VPN
* outbound web proxy
* Accounting (fully encrypted)
* HR (fully encrypted)

That would get me to these subnets:
* Desktops (VoIP on different vlan)
* Internal Services
* External Services
* Guest Network (all wifi devices)
* Storage network / Admin access

But only you can decide what is best for your network.

One last thing, no way would I use virtualbox in a production environment. Look to KVM.

---

### Post by bumcheekcity on 2018-12-19
Thanks for the advice - no, I'm not planning on using VirtualBox in production, just doing it for testing at the moment. 

If I were to split up subnets to something like:

10.1.x x - Desktops
10.2.x.x - Internal Services
10.3.x.x - External Services 
(etc)

How would I work out which subnet to assign a client to, and ensure that the desktops could all access the internal services, but the Guest/Wifi network couldn't?

Edit: From reading, I think I need a separate NIC for each separate subnet. Apply a different IP address to each NIC accordingly, then within the dhcpd.conf file, specify a shared-network{} directive, then multiple subnet{}s within that network, each of which having a separate gateway. The Wifi subnet to be outside of the shared-network{} element.

Edit2: Use the 'class' command to identify what subnet to put stuff into:

```
class "foo" {
match if substring (option vendor-class-identifier, 0, 4) = "SUNW";
}

shared-network 224-29 {
subnet 10.17.224.0 netmask 255.255.255.0 {
option routers rtr-224.example.org;
}
subnet 10.0.29.0 netmask 255.255.255.0 {
option routers rtr-29.example.org;
}
pool {
allow members of "foo";
range 10.17.224.10 10.17.224.250;
}
pool {
deny members of "foo";
range 10.0.29.10 10.0.29.230;
}
}
```

---

