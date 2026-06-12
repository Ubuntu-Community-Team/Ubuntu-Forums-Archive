---
title: "DHCP can't update reverse DNS"
date: 2011-07-19
forum: Server Platforms
---

### Post by mcarrara on 2011-07-19
I am setting up dynamic DNS (DDNS).  DNS has been working for two years without a issue.  My DHCP server can update the forward zone, but not the reverse.  I found some references to issues with AppArmour so I turned it off, but I still have the issue.  Here is part of the syslog output:

Jul 19 13:38:54 morgan dhcpd: Added new forward map from tech-Coordinator.gilman.k12.wi.us. to 172.20.4.205
Jul 19 13:38:54 morgan dhcpd: unable to add reverse map from 205.4.20.172.in-addr.arpa. to tech-Coordinator.gilman.k12.wi.us.: not authorized
Jul 19 13:38:54 morgan dhcpd: DHCPREQUEST for 172.20.4.205 from 00:24:8c:01:08:c8 via eth0
Jul 19 13:38:54 morgan dhcpd: DHCPACK on 172.20.4.205 to 00:24:8c:01:08:c8 (tech-Coordinator) via eth0.

Here is the zone declaration part of named.conf:

zone "gilman.k12.wi.us" {
    type master;
    file "/var/lib/bind/gilman.k12.wi.us.hosts";
    allow-update {
        key dhcpupdate2;
        };
           };

zone "20.172.in-addr.arpa" {
    type master;
    file "/var/lib/bind/db.reverse";
    allow-update {
        key dhcpupdate2;
        };
    };

I've been looking at this all day.  Did I miss something simple?

Mark

---

### Post by jmoorse on 2011-07-19
Does reverse DNS normally work?  Are you handing out addresses in a /16 block for this zone?  I am curious if your rev-zone shouldn't be 4.20.172.in-addr.arpa

Edit: can you post applicable rev-dns portion of dhcpd.conf

---

### Post by mcarrara on 2011-07-20
Reverse lookup works for the static IP addresses I have hand entered.  We have four subnets for security.  The 172.20.0.0 network is for network devices, 172.20.2.0 is for wireless guest access, 172.20.3.0 is for students and 172.20.4.0 is for staff.

dhcpd.conf (the other subnets are configed the same way)

zone gilman.k12.wi.us. {
    primary 172.20.0.6;
    key dhcpupdate2;
    }

zone in-addr.arpa. {
    primary 172.20.0.6;
    key dhcpupdate2;
    }

subnet 172.20.0.0 netmask 255.255.255.0 {
    allow client-updates;
    option netbios-name-servers 172.20.0.95;
    option domain-name-servers 172.20.0.6;
    option domain-name "gilman.k12.wi.us";
    option broadcast-address 172.20.0.255;
    option subnet-mask 255.255.255.0;
    option routers 172.20.0.100;
    ddns-updates on;
    ddns-rev-domainname "in-addr.arpa.";
    max-lease-time 25900;
    default-lease-time 25900;
    authoritative;
    range 172.20.0.150 172.20.0.199;
    }

---

### Post by wineman on 2011-07-20
the reason it isn't 'authorising' (as the syslog says) is that you need to have a shared key that both bind (or your dns system) and dhcp-server (or your dhcp server) can share so that they can verify that they are asking each other to update each other.

basically, you need to create an RNDC key and a assign that RNDC key updateable access from your pc. here is how to do it:
1) create your RNDC key by using the dnssec-keygen command. you'll need to specify a name or the RNDC key. the command is:
$ dnssec-keygen <name> -K <path to your bind/named config directory>

2) In your named.conf file, add the following lines:
# Start
controls {
        inet 127.0.0.1 allow { localhost; } keys { rndc-key; };
};
# Change /etc/bind to the path of your named/bind directory
include "/etc/bind/rndc.key";

....
# In your zone config part of the named.conf, add these lines:
# (change 'rndc-key' to the name that you set your RNDC key to
notify yes;
allow-update { 127.0.0.1; key "rndc-key"; };
# The journal file is a temporary high-update file that you can update your DNS name of your client as you obtain a DHCP address
journal "pri/<domain name without spaces>.jnl";
# End

3) in your dhcpd.conf file, you need to put these lines in there: (preferably near to the top)
# Start
# Change ubuntu to your server name
server-identifier           ubuntu;
ddns-updates                on;
ddns-update-style           interim;
# Change ubudhcp to your DNS Domain Name
ddns-domainname             "ubudhcp.";
ddns-rev-domainname         "in-addr.arpa.";
ignore                      client-updates;
# Change '/etc/bind' to the path to the config file of 
# the DNS(bind/powerdns/pdns or whatever) server
include                     "/etc/bind/rndc.key";
# End

4) restart your services: (im assuming you're using dhcp3-server and bind9)
$ service dhcp3-server restart
$ service bind9 restart

5) renew your ip address on your clients and then you should be getting a dynamic dns address system going :)

HTH

---

