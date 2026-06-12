---
title: "Slave DHCP not updating DNS"
date: 2011-10-06
forum: Server Platforms
---

### Post by MezzFA0 on 2011-10-06
Hi all,

I've been going around in circles trying to set up two DHCP/DNS servers that will work in the event one of them fails.

On machine 1, I installed Bind9 and DHCP for a fake local zone called test.local

I then got DHCP to auto update the DNS entries using rndc.key and everything was great.

To save some work as this was a VM I cloned the machine and adjusted the necessary so that Machine 2 has different IPs, hostnames etc.

Independently both machines work fine.

So then I went about changing the config on machine 2 to be the slave of machine 1.

When shutting down machine 1 DHCP and DNS lookups work fine but DNS updates are refused as such any new machines that turn up never get added to the DNS tables.

Also due to how DHCP is split 50/50 between both machines, if one PC uses Machine 2 for DHCP I get the same errors where DNS is not updated.

I followed an old guide from here [http://ubuntuforums.org/showthread.php?t=267974](http://ubuntuforums.org/showthread.php?t=267974) and amended it slightly to take into account apparmor on Ubu Server 10.04.3

my /var/log/daemon.log on machine 2 is full of the following errors:

machine 2 named[567]: client 10.44.6.20#48912: signer "rndc-key" denied
machine 2 named[567]: client 10.44.6.20#48912: update forwarding 'test.local/IN' denied

The keys are the same on both servers with the same permissions (they are clones).

On machine 1 dhcpd.conf for DNS updates is as follows:
```
include "/etc/dhcp3/rndc.key";

zone test.local {
  primary 10.44.6.10; # Machine 1 IP
  key rndc-key;
}
```

Machine 2:

```
include "/etc/dhcp3/rndc.key";

zone test.local {
  primary 10.44.6.20; # Machine 2 IP
  key rndc-key;
}
```

named.conf.local on machine 1 is:

```
include "/etc/bind/rndc.key";

zone "test.local" {
  type master;
  file "/var/lib/bind/test.local.db"; //Apparmor requires DDNS zones here 
  allow-update { key "rndc-key"; };
  allow-transfer { 10.44.6.20; }; //Transfers to slave server
};
```

same file on machine 2:

```
include "/etc/bind/rndc.key";

zone "test.local" {
  type slave;
  file "/var/lib/bind/test.local.db";
  masters { 10.44.6.10; };
};
```

Any input would be greatly appreciated as I've been stuck on various guides, man pages and copious amounts of Google for nearly 2 weeks so I'm obviously fundamentally misunderstanding something.

Apologies for the length of this post, I can post full files for everything involved but I think thats more than anyone wants to read.

---

