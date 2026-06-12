---
title: "DHCP server help please"
date: 2012-02-19
forum: Server Platforms
---

### Post by Ninjin25 on 2012-02-19
Hello,    I have recently inherited a network and need to add a new DHCP statement, but in the logs I am getting unknown network segment.       This network is kind large and has many VLANs and many different subnets. Each VLAN is setup to be associated with a MAC address and has a 255.255.255.252 subnet mask.   This particular new device is going to be 172.17.20.70/30.  So the VLAN that I created on the core switch is VLAN 268, 172.17.20.69 255.255.255.252 and it is a routing VLAN. This scheme matches the other working VLANs. Here is what the dhcp.conf entry looks like:       subnet 172.17.20.68 netmask 255.255.255.252 {     range 172.17.20.70;     option domain-name-servers ns1.xxxx.com, ns2.xxxxx.com;    option domain-name ;xxx.com;     option routers 172.17.20.69;     default-lease-time 43200;     default-lease-time 86400;     authoritative;   }      This matches all the other existing and working DHCP entries. I get a entry in the syslog that specifically states &quot;unknown network segment&quot;.   Well I know that this is pretty much telling me that this is an unknown network, even though there are dozens more entries like the one above like this working one:     subnet 172.17.20.64 netmask 255.255.255.252 {     range 172.17.20.66;     option domain-name-servers ns1.xxxxxx.com, ns2.xxxxx.com;   option domain-name xxxxxx.com;     option routers 172.17.20.65;     default-lease-time 43200;     default-lease-time 86400;     authoritative;   }      I really am at a loss at this time, I have done everything that I know. I'm not sure where else I can look on the DHCP server to see what is going on. The other other thing I can think of is I have  bond0,eth0, and eth1  bond0 and eth0 share the same IP address. eth1 reports as being down and doesn't have an IP address. I wouldn't think that this would be an issue since I have well over 100 addresses being assigned out by this same server.  Any thoughts or help will be much appreciative.

---

### Post by Iowan on 2012-02-19
Quite a wall of words...
I'm probably missing something (like VLAN's) - or just don't understand that DHCP server (which one is it?), but shouldn't the **range** statement have more than one address?

---

### Post by Ninjin25 on 2012-02-19
Wow sorry about that, don't know what happened to the formatting of that post, but lets try again.

This network is actually a lab to test network equipment in. I made the range only have 1 address because of the 255.255.255.252 subnet mask. I can only have 2 usable addresses, the gateway and the actual IP address. I have tried larger subnet masks. What I haven't done, but going to start working on in a moment is the following:

1. Try something other than 172.17.20.x, such as 172.17.21.x/24
2. Try another device, or switch the VLAN MAC associations with a working device.

So here is the topology:


[Router]----Layer 3 switch(core)----L2 switch---item I'm wanting to add
                           |
                  Layer 2 switch----DHCP server.

Now I know it would be better to simply this. But, DHCP works for about 70 devices which was added by the previous admin. Many of these devices are using a 255.255.255.252 subnet mask.

So this is what I have

On my switch this is what I have for this particular device. Do keep in mind that I have many more VLAN just like this one that works.

VLAN 268=172.17.20.69/255.255.255.252
VLAN 268 has a mac association with ----:1d:15:f9(which is the device in question)
All correct ports are participating members, and this is a routing VLAN

*My DHCP Configuration*, top one is the exiting working one, the bottom one in bold is mine:


subnet 172.17.20.64 netmask 255.255.255.252 {
  range 172.17.20.66;
  option domain-name-servers ns1.prosupportlab.com, ns2.prosupportlab.com;
  option domain-name "prosupportlab.com";
  option routers 172.17.20.65;
  default-lease-time 43200;
  default-lease-time 86400;
  authoritative;
}

[B]subnet 172.17.20.68 netmask 255.255.255.252 {
  range 172.17.20.70;
  option domain-name-servers ns1.xxxxb.com, ns2.xxxx.com;
  option domain-name "xxxx.com";
  option routers 172.17.20.69
  default-lease-time 43200;
  default-lease-time 86400;
  authoritative;
}[/B]

*Error seen in logs*:

Feb 19 16:18:27 ns1 dhcpd: DHCPDISCOVER from -----:15:f9 via 172.17.20.69: unknown network segment

So from what I can tell the device I am trying to get connected is being seen by the DHCP server via appropriate routing; the server just doesn't know how to respond. Not sure if I need to do anything else to tell the server that this network segment isn't ummm unknown.

---

### Post by Iowan on 2012-02-19
The formatting helps! :D
I understand your subnetting, now... well, sorta.
I'm grasping a bit, but I presume it's just a typo that there's no semicolon after **option routers 172.17.20.69**?

---

### Post by Ninjin25 on 2012-02-19
That was an error in my dhcpd.conf file which I have since fixed; unfortunately no go still.

I removed the  VLAN 268 and created a new one in a different subnet this time 172.17.200.0/24. Then created a new DHCP pool that I have since deleted so I can not give the config of it.

I probably messed up on the config, long day, very tired, and extremely frustrated lol. But, that didn't even get logged so idk.

I am still in contact with the previous admin, I am just going to call him tomorrow before I lose any more hair on this one.

If anyone can think of anything that I can check, please let me know.

---

