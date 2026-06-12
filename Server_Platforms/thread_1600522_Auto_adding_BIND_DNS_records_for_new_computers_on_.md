---
title: "Auto adding BIND DNS records for new computers on a Win 2k3 AD"
date: 2010-10-19
forum: Server Platforms
---

### Post by Instantkarma! on 2010-10-19
Hello all,

We have a BIND9 DNS server running with working support for dynamic DNS.
LDAP and Kerberos SRV records are up and running and so far dynamic DNS is running smoothly.

Our Domain controller and Active directory host is a W2k3 server. 
I know that with Windows DNS, once you added a new computer in the Domain the DNS records would automatically update with the data of the freshly added computer.

I would like to implement this on our current BIND ubuntu server as well. As soon as a new computer gets added to the windows AD, Bind should copy that records in its DNS.

I have the allow-update paramter on for the W2k3 server in named.conf, but so far to no avail. The messages and deamon.log files dont show any errors.
Do i have to set up anything else in order to make BIND update from a Windows AD?

Thanks in advanc,e

-Instantkarma

---

### Post by HermanAB on 2010-10-19
Howdy,

Dynamic DNS is a huge security hole that Microsoft added to the version of BIND 8 that they took from BSD for Active Directory.

Implement it at your peril.

---

### Post by Instantkarma! on 2010-10-19
@Herman

Thanks for your reply.
I realize DDNS is a possible security hole. Hence, we only allowed our main DC to send the updates to the zone.

Here are the zone options in named.conf by the way (with the examples actually being our companies domain name of course):

[I]zone "example.org" {
        type master;
        file "/etc/bind/zones/example.org.db";
        allow-transfer { IP of peer; };
        allow-update { IP of domain controller; };
        };[/I]


Plus, the SRV records in the zone file itself:

[I]_ldap._tcp.example.org.         38400   IN      SRV     0       100     389     dc.example.org.
_kpasswd._tcp.example.org.        38400   IN      SRV     0       100     464     dc.example.org.
_kerberos._tcp.example.org.      38400   IN      SRV     0       100     88      dc.example.org.
_gc._tcp.example.org.             38400   IN      SRV     0       100     3268    dc.example.org.

_kpasswd._udp.example.org.        38400   IN      SRV     0       100     464     dc.example.org.
_kerberos._udp.example.org.       38400   IN      SRV     0       100     88      dc.example.org.[/I]

---

### Post by HermanAB on 2010-10-19
Well, you would have to somehow get the data from Windows, create the necessary scripts and then restart BIND - not a nice thing to do.

If I need to serve Windows desktops with AD, then I use a Win 2003 server running in a virtual machine on VMware.  Once working, I make a tarball of the VM and when it screws up after a few months, I untar the backup.

---

### Post by SeijiSensei on 2010-10-19
You have two options I can think of.  Either make the BIND9 server a slave of the AD server, or use the "forward" directive in your zone file to send all requests for your domain to the AD server for resolution.

Slave
```
zone "example.com" {
     type slave;
     masters { ad.server.ip.addr; };
};
```

Forward
```
zone "example.com" {
     type forward;
     forward-only;
     forwarders { ad.server.ip.addr; };
};
```

You'll want to do the same for the in-addr.arpa reverse domain.

If you want the BIND9 host to be a redundant backup to the AD server, making it a slave is the best approach.  Forwarding won't work if the AD server is offline.

If you make the BIND9 host a slave, make sure you include its IP address in an "IN NS" nameserver record on the AD host.  That tells it to send updates to the slave(s) when the domain information changes.

---

