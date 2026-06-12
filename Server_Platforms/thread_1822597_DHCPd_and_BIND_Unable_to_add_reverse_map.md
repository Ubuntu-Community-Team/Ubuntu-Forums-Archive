---
title: "DHCPd and BIND: Unable to add reverse map"
date: 2011-08-10
forum: Server Platforms
---

### Post by Barry Cent on 2011-08-10
Hello,

I'm currently being faced with an issue with my DHCP and BIND setup, where I'm getting the following messages in my /var/log/syslog file:

```
Aug 10 22:23:35 NetworkServer1 dhcpd: Added new forward map from Joe-7-VM.merlin.local to 192.168.1.217
Aug 10 22:23:35 NetworkServer1 dhcpd: unable to add reverse map from 217.1.168.192.in-addr.arpa. to Joe-7-VM.merlin.local: not authorized
```

Can anyone help me with this please?

/var/log/syslog (more info):
```
Aug 10 22:23:31 NetworkServer1 named[24967]: client 192.168.1.4#36946: signer "dhcp-update-key" approved
Aug 10 22:23:31 NetworkServer1 named[24967]: client 192.168.1.4#36946: updating zone 'merlin.local/IN': deleting an RR at Joe-7-VM.merlin.local A
Aug 10 22:23:31 NetworkServer1 dhcpd: if Joe-7-VM.merlin.local IN TXT "311bbf4fb93ce613841bdfbf61101c0e68" rrset exists and Joe-7-VM.merlin.local IN A 192.168.1.217 rrset exists delete Joe-7-VM.merlin.local IN A 192.168.1.217: success.
Aug 10 22:23:31 NetworkServer1 named[24967]: client 192.168.1.4#38291: signer "dhcp-update-key" approved
Aug 10 22:23:31 NetworkServer1 named[24967]: client 192.168.1.4#38291: updating zone 'merlin.local/IN': deleting an RR at Joe-7-VM.merlin.local TXT
Aug 10 22:23:31 NetworkServer1 dhcpd: if Joe-7-VM.merlin.local IN A rrset doesn't exist delete Joe-7-VM.merlin.local IN TXT "311bbf4fb93ce613841bdfbf61101c0e68": success.
Aug 10 22:23:31 NetworkServer1 dhcpd: DHCPRELEASE of 192.168.1.217 from 00:0c:29:2b:27:59 (Joe-7-VM) via eth0 (found)
Aug 10 22:23:34 NetworkServer1 dhcpd: DHCPDISCOVER from 00:0c:29:2b:27:59 via eth0
Aug 10 22:23:35 NetworkServer1 dhcpd: DHCPOFFER on 192.168.1.217 to 00:0c:29:2b:27:59 (Joe-7-VM) via eth0
Aug 10 22:23:35 NetworkServer1 named[24967]: client 192.168.1.4#38345: signer "dhcp-update-key" approved
Aug 10 22:23:35 NetworkServer1 named[24967]: client 192.168.1.4#38345: updating zone 'merlin.local/IN': adding an RR at 'Joe-7-VM.merlin.local' A
Aug 10 22:23:35 NetworkServer1 named[24967]: client 192.168.1.4#38345: updating zone 'merlin.local/IN': adding an RR at 'Joe-7-VM.merlin.local' TXT
Aug 10 22:23:35 NetworkServer1 dhcpd: Added new forward map from Joe-7-VM.merlin.local to 192.168.1.217
Aug 10 22:23:35 NetworkServer1 dhcpd: unable to add reverse map from 217.1.168.192.in-addr.arpa. to Joe-7-VM.merlin.local: not authorized
Aug 10 22:23:35 NetworkServer1 dhcpd: DHCPREQUEST for 192.168.1.217 (192.168.1.4) from 00:0c:29:2b:27:59 (Joe-7-VM) via eth0
Aug 10 22:23:35 NetworkServer1 dhcpd: DHCPACK on 192.168.1.217 to 00:0c:29:2b:27:59 (Joe-7-VM) via eth0
Aug 10 22:23:35 NetworkServer1 dhcpd: DHCPREQUEST for 192.168.1.102 from 00:21:47:a4:57:31 (Wii) via eth0
Aug 10 22:23:35 NetworkServer1 dhcpd: DHCPACK on 192.168.1.102 to 00:21:47:a4:57:31 (Wii) via eth0
Aug 10 22:23:35 NetworkServer1 named[24967]: error (network unreachable) resolving 'ns1.msft.net/AAAA/IN': 2001:500:2f::f#53
Aug 10 22:23:35 NetworkServer1 named[24967]: error (network unreachable) resolving 'ns2.msft.net/AAAA/IN': 2001:503:231d::2:30#53
```

Here's my dhcpd.conf file:
```
authoritative;
allow client-updates;
allow unknown-clients;
ddns-updates on;
ddns-rev-domainname "in-addr.arpa.";
#
# Sample configuration file for ISC dhcpd for Debian
#
# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as
# configuration file instead of this file.
#
# $Id: dhcpd.conf,v 1.1.1.1 2002/05/21 00:07:44 peloy Exp $
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style interim;


# default-lease-time 600;
default-lease-time 86400;
# max-lease-time 7200;
max-lease-time 172800;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
#authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

# No service will be given on this subnet, but declaring it helps the 
# DHCP server to understand the network topology.

#subnet 10.152.187.0 netmask 255.255.255.0 {
#}

# This is a very basic subnet declaration.

#subnet 10.254.239.0 netmask 255.255.255.224 {
#  range 10.254.239.10 10.254.239.20;
#  option routers rtr-239-0-1.example.org, rtr-239-0-2.example.org;
#}

# This declaration allows BOOTP clients to get dynamic addresses,
# which we don't really recommend.

#subnet 10.254.239.32 netmask 255.255.255.224 {
#  range dynamic-bootp 10.254.239.40 10.254.239.60;
#  option broadcast-address 10.254.239.31;
#  option routers rtr-239-32-1.example.org;
#}

# A slightly different configuration for an internal subnet.
#subnet 10.5.5.0 netmask 255.255.255.224 {
#  range 10.5.5.26 10.5.5.30;
#  option domain-name-servers ns1.internal.example.org;
#  option domain-name "internal.example.org";
#  option routers 10.5.5.1;
#  option broadcast-address 10.5.5.31;
#  default-lease-time 600;
#  max-lease-time 7200;
#}

# Hosts which require special configuration options can be listed in
# host statements.   If no address is specified, the address will be
# allocated dynamically (if possible), but the host-specific information
# will still come from the host declaration.

#host passacaglia {
#  hardware ethernet 0:0:c0:5d:bd:95;
#  filename "vmunix.passacaglia";
#  server-name "toccata.fugue.com";
#}

# Fixed IP addresses can also be specified for hosts.   These addresses
# should not also be listed as being available for dynamic assignment.
# Hosts for which fixed IP addresses have been specified can boot using
# BOOTP or DHCP.   Hosts for which no fixed address is specified can only
# be booted with DHCP, unless there is an address range on the subnet
# to which a BOOTP client is connected which has the dynamic-bootp flag
# set.
#host fantasia {
#  hardware ethernet 08:00:07:26:c0:a5;
#  fixed-address fantasia.fugue.com;
#}

# You can declare a class of clients and then do address allocation
# based on that.   The example below shows a case where all clients
# in a certain class get addresses on the 10.17.224/24 subnet, and all
# other clients get addresses on the 10.0.29/24 subnet.

#class "foo" {
#  match if substring (option vendor-class-identifier, 0, 4) = "SUNW";
#}

#shared-network 224-29 {
#  subnet 10.17.224.0 netmask 255.255.255.0 {
#    option routers rtr-224.example.org;
#  }
#  subnet 10.0.29.0 netmask 255.255.255.0 {
#    option routers rtr-29.example.org;
#  }
#  pool {
#    allow members of "foo";
#    range 10.17.224.10 10.17.224.250;
#  }
#  pool {
#    deny members of "foo";
#    range 10.0.29.10 10.0.29.230;
#  }
#}
# lan
subnet 192.168.1.0 netmask 255.255.255.0 {
	option domain-name-servers 192.168.1.4 , 192.168.1.20;
	option domain-name "merlin.local";
	option subnet-mask 255.255.255.0;
	option routers 192.168.1.1;
	authoritative;
	allow client-updates;
	allow unknown-clients;
	ddns-updates on;
	ddns-domainname "merlin.local";
	ddns-rev-domainname "in-addr.arpa.";
	range 192.168.1.100 192.168.1.254;
	}

key dhcp-update-key. {
	algorithm hmac-md5;
	secret r61jqGc7BBjPX3rX9CDkEg==;
	}

key dhcpupdate {
	algorithm hmac-md5;
	secret gyGeJuRk3GdbX3kPhd7JDA==;
	}

zone merlin.local. {
	primary 192.168.1.4;
	key dhcp-update-key.;
	}

zone in-addr.arpa. {
	primary 192.168.1.4;
	key dhcpupdate;
	}

```

Here's my namd.conf file:
```
// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the 
// structure of BIND configuration files in Debian, *BEFORE* you customize 
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local

include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.default-zones";
key dhcp-update-key. {
	algorithm hmac-md5;
	secret "r61jqGc7BBjPX3rX9CDkEg==";
	};
key dhcpupdate {
	algorithm hmac-md5;
	secret "gyGeJuRk3GdbX3kPhd7JDA==";
	};
```

Please let me know if you need any other info.

Many thanks,

Joe

EDIT: By the way, I spent some time researching this issue, and none of the solutions which I have found seemed to have made a difference to my error message that I receive. I suspect I've set something up wrong though, through lack of experience with BIND!

---

### Post by nyu2007 on 2011-08-11
Hi,

You should be check permission of zones files

---

### Post by Barry Cent on 2011-08-11
> **nyu2007 said:**
> Hi,

You should be check permission of zones files

Hi nyu2007,

Here's an ls from /var/lib/bind:
```
joe@NetworkServer1:~$ ls -lh /var/lib/bind/
total 20K
-rw-r--r-- 1 root root  421 2011-08-10 22:12 192.168.1.rev
-rw-r--r-- 1 root root  410 2011-08-10 23:05 ad.merlin.local.hosts
-rw-r--r-- 1 root root  187 2011-08-10 22:10 dsset-1.168.192.in-addr.arpa.
-rw-r--r-- 1 root root 2.3K 2011-08-10 23:05 merlin.local.hosts
-rw-r--r-- 1 root root 4.0K 2011-08-10 22:59 merlin.local.hosts.jnl

```

And here's /etc/bind:
```
joe@NetworkServer1:~$ ls -lh /etc/bind/
total 52K
-rw-r--r-- 1 bind bind  601 2010-03-22 20:00 bind.keys
-rw-r--r-- 1 root root  237 2010-03-22 20:00 db.0
-rw-r--r-- 1 root root  271 2010-03-22 20:00 db.127
-rw-r--r-- 1 root root  237 2010-03-22 20:00 db.255
-rw-r--r-- 1 root root  353 2010-03-22 20:00 db.empty
-rw-r--r-- 1 root root  270 2010-03-22 20:00 db.local
-rw-r--r-- 1 root root 2.9K 2010-03-22 20:00 db.root
-rw-r--r-- 1 root bind  625 2011-08-10 14:23 named.conf
-rw-r--r-- 1 root bind  490 2010-03-22 20:00 named.conf.default-zones
-rw-r--r-- 1 root bind  675 2011-08-10 22:18 named.conf.local
-rw-r--r-- 1 root bind  574 2011-08-10 21:32 named.conf.options
-rw-r--r-- 1 root bind   77 2011-07-27 23:49 rndc.key
-rw-r--r-- 1 root root 1.3K 2010-03-22 20:00 zones.rfc1918

```

Does anything there look out of place?

Thanks,

Joe

---

### Post by SeijiSensei on 2011-08-12
> **Barry Cent said:**
> Hi nyu2007,

Here's an ls from /var/lib/bind:
```
joe@NetworkServer1:~$ ls -lh /var/lib/bind/
total 20K
-rw-r--r-- 1 root root  421 2011-08-10 22:12 192.168.1.rev
-rw-r--r-- 1 root root  410 2011-08-10 23:05 ad.merlin.local.hosts
-rw-r--r-- 1 root root  187 2011-08-10 22:10 dsset-1.168.192.in-addr.arpa.
-rw-r--r-- 1 root root 2.3K 2011-08-10 23:05 merlin.local.hosts
-rw-r--r-- 1 root root 4.0K 2011-08-10 22:59 merlin.local.hosts.jnl

```


Use chown and chgrp to put these files in the bind group and give the group write permissions.  BIND runs as the unprivileged user "bind" not root.

```

cd /var/lib
sudo chgrp bind bind
sudo chmod g+w bind
cd bind
sudo chgrp bind *
sudo chmod g+w *

```

---

### Post by Barry Cent on 2011-08-12
Hi,

Thank you for your suggestions.

I tried changing the permissions as you suggested, but unfortunately I still have the same messages.

Is this now correct?:

```
joe@NetworkServer1:/var/lib/bind$ ls -lh /var/lib/bind/
total 24K
-rw-rw-r-- 1 root bind  421 2011-08-10 22:12 192.168.1.rev
-rw-rw-r-- 1 bind bind  410 2011-08-12 14:39 ad.merlin.local.hosts
-rw-rw-r-- 1 root bind  187 2011-08-10 22:10 dsset-1.168.192.in-addr.arpa.
-rw-rw-r-- 1 root bind 2.3K 2011-08-10 23:05 merlin.local.hosts
-rw-rw-r-- 1 root bind 4.3K 2011-08-12 14:39 merlin.local.hosts.jnl

```

Any other suggestions?

Thanks,

Joe

---

### Post by SeijiSensei on 2011-08-12
```
Aug 10 22:23:35 NetworkServer1 dhcpd: unable to add reverse map from 217.1.168.192.in-addr.arpa. to Joe-7-VM.merlin.local: not authorized
```

Where is this file?

Joe-7-VM.merlin.local

I don't see it in /var/lib/bind.

---

### Post by Barry Cent on 2011-08-12
> **SeijiSensei said:**
> ```
Aug 10 22:23:35 NetworkServer1 dhcpd: unable to add reverse map from 217.1.168.192.in-addr.arpa. to Joe-7-VM.merlin.local: not authorized
```

Where is this file?

Joe-7-VM.merlin.local

I don't see it in /var/lib/bind.

??

I'm not sure I follow you (or I've completely misunderstood bind's error messages :-))

Surely that line which you have quoted is telling us that it cannot map "217.1.168.192.in-addr.arpa." to the host "Joe-7-VM.merlin.local", as it it is somehow not authorised to create the record in the zone file?

Thanks,

Joe Nyland

---

### Post by Barry Cent on 2011-08-14
SeijiSensei:

Can you expand on why I should be seeing a zone file for the machine "Joe-7-VM.merlin.local" please?

Thanks,

Joe

---

### Post by SeijiSensei on 2011-08-14
Sorry, my mistake.  I misread the error message.  The permissions look right for bind.

Looking at it again, I see that it's the dhcpd daemon that lacks permissions to write the file.  Is it running as a user other than root?  If so, try putting that user into the bind group.

There seem to be a couple of tutorials on this process on the web.  Maybe they can help?

---

### Post by Barry Cent on 2011-08-14
Ok, I thought I'd been going mad! :-)

I agree, it does look like the DHCPd user doesn't have permisssions to update the records for the in-addr.arpa. zone. However I've tried this already. To confirm, "id dhcpd" tells me that it's in the bind group, but it still gives the original message above.

```
joe@NetworkServer1:~$ id dhcpd
uid=105(dhcpd) gid=113(dhcpd) groups=113(dhcpd),107(bind)
```

I've trawled through Google for possible causes to this, but I've not been able to find anything to fix it, hence my thread here. I'm really at a loss as to why this will not allow me to setup DDNS for the reverse zone - my forward zone updates without fail via DDNS :-(.

Have you any other suggestions?

Thanks for your help so far.

Joe

---

### Post by Barry Cent on 2011-08-16
Sorry to bump, but does anyone have an idea how to resolve this issue?

I'm completely at a loss :-(

Thanks,

Joe

---

### Post by devros69 on 2011-12-14
did you ever solve this?  having the same issue.

---

### Post by Barry Cent on 2011-12-15
> **devros69 said:**
> did you ever solve this?  having the same issue.
Unfortunately not devros. I didn't manage to find any more suggestions of things to try to resolve this.

It's frustrating that 99% of the time these kind of problems are just silly mistakes and can be overcome quite easily, but my guess is that this issue is down to a lack of understanding of dynamic DNS updates with BIND and DHCPd - well in my case it is. I'm not implying you don't know what you're doing! :-)

Joe

---

### Post by devros69 on 2011-12-15
I was able to fix my problems.  on the slave in my dhcpd.conf file I had the zones setup wrong.

what I had:

zone xxx.com. {
     primary <ip of slave>;
     key rndc-key;
}

after changing it to:

zone xxx.com. {
     primary <ip of master>;
     key rndc-key;
}

the problem went away.

hope that helps!

-dev

---

### Post by Barry Cent on 2011-12-15
Nice one! - That's very kind of you.

I don't recall investigating that as a possible cause win I looked at the issue last, so it's possible the config you posted could be the solution for me too.

I'll have to give it a go next week, when I have access to my servers!

Thanks,

Joe

---

### Post by Barry Cent on 2012-08-09
I know this is getting a little old now and I am sorry to dig it up, but I thought it was best to share the solution to my problem here, for any users who may have this problem.
Basically, my issue was with the configuration of the forward and reverse zones in Bind: For whatever reason, Bind would not let me update the zone, without providing a DNS key to sign the update. To simplify things, my original zone config in Bind looked like this:

My forward zone:
```

zone "merlin.local" {
    type master;
    file "/var/lib/bind/merlin.local.hosts";
    allow-update {
        192.168.1.0/24;
        };
    allow-query {
        192.168.1.0/24;
        };
    };
```
My reverse zone:
```

zone "1.168.192.in-addr.arpa" {
    type master;
    file "/var/lib/bind/192.168.1.rev";
    allow-update {
        192.168.1.0/24;
        };
    allow-query {
        192.168.1.0/24;
        };
    };

```

Once I replaced this with:
My forward zone:
```

zone "merlin.local" {
    type master;
    file "/var/lib/bind/merlin.local.hosts";
    allow-update { key dhcpupdate; };
    allow-query {
        192.168.1.0/24;
        };
    };

```
My reverse zone:
```

zone "1.168.192.in-addr.arpa" {
    type master;
    file "/var/lib/bind/192.168.1.rev";
        allow-update { key dhcpupdate; };
        allow-query {
        192.168.1.0/24;
        };
    };

```
and checked that DHCPd was configured to use the key "dhcpupdate" to sign updates submitted to Bind, I'm now getting PTR records created when an A record is added to the zone via DHCPd!:
```


dhcpd: Added new forward map from test-vm.merlin.local to 192.168.1.211
named[16545]: client 192.168.1.2#43076: signer "dhcpupdate" approved
named[16545]: client 192.168.1.2#43076: updating zone '1.168.192.in-addr.arpa/IN': deleting rrset at '211.1.168.192.in-addr.arpa' PTR
Server1 named[16545]: client 192.168.1.2#43076: updating zone '1.168.192.in-addr.arpa/IN': adding an RR at '211.1.168.192.in-addr.arpa' PTR
Server1 dhcpd: added reverse map from 211.1.168.192.in-addr.arpa. to test-vm.merlin.local

```
Thanks to all who helped!

---

