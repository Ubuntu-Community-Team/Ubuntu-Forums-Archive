---
title: "DHCP and Bind and windows Domain Issues!"
date: 2006-10-20
forum: Server Platforms
---

### Post by twistedtwig on 2006-10-20
Hey all,

Ok so there was a post a little while ago where i was working though some of these issues([Click here]("http://ubuntuforums.org/showthread.php?t=274694")).  Since then i have completely removed bind and reinstalled it to make sure there wasnt any rubbish in there and have a clean slate.

so i have the main server running dapper. with a dhcp server and it (trying) updating bind with new users ips etc.  I have recently got a trail version of windows server 2003 and installed that on the network.  The domain controller is on and i have most of the machines within that domain now.

The issue is............ when a computer has joined the windows domain it will not get resolved, the forward mapping does not happen.  But if i remove it from the windows domain and just have it in a workgroup it all works perfectly.  here are my conf files:

dhcpd.conf
> 
authoritative;

ddns-updates on;
ddns-rev-domainname "in-addr.arpa.";
ddns-update-style interim;
allow client-updates;

max-lease-time 172800;
default-lease-time 43200;
one-lease-per-client on;

subnet 192.168.10.0 netmask 255.255.255.0 {
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.10.255;

option domain-name "ponywars.local";
option domain-name-servers 192.168.10.1;
option routers 192.168.10.1;

range 192.168.10.101 192.168.10.200;
}

key "rndc-key" {
        algorithm hmac-md5;
        secret "0AznrocTmZQTLwyjlhkR/g==";
};

zone ponywars.local. {
        primary 127.0.0.1;
        key rndc-key;
}

zone 10.168.192.in-addr.arpa. {
        primary 127.0.0.1;
        key rndc-key;
}

host WIGGLY {
        hardware ethernet 00:09:5B:06:0F:30;
        fixed-address 192.168.10.99;
}

host BOBBY {
        hardware ethernet 00:08:54:44:75:10;
        fixed-address 192.168.10.100;      
}        


bind folder permissions:
> 
root@betty:/etc# ls -l | grep bind
drwxr-sr-x   3 root   bind      4096 2006-10-20 22:15 bind


bind file permissions
> 
-rwxr-xr-x 1 root root  237 2006-09-07 17:21 db.0
-rwxr-xr-x 1 root root  271 2006-09-07 17:21 db.127
-rwxr-xr-x 1 root root  237 2006-09-07 17:21 db.255
-rwxr-xr-x 1 root root  353 2006-09-07 17:21 db.empty
-rwxr-xr-x 1 root root  256 2006-09-07 17:21 db.local
-rwxr-xr-x 1 root root 1507 2006-09-07 17:21 db.root
-rwxr-xr-x 1 root bind 2273 2006-10-20 20:53 named.conf
-rwxr-xr-x 1 root bind  329 2006-10-20 21:19 named.conf.local
-rwxr-xr-x 1 root bind  697 2006-10-20 20:34 named.conf.options
-rwxr-xr-x 1 bind bind   77 2006-10-20 20:12 rndc.key
drwxrwxr-x 2 root bind 4096 2006-10-20 21:54 zones
-rwxr-xr-x 1 root root 1317 2006-09-07 17:21 zones.rfc1918


excert from named.conf (key changed)
> 
include "/etc/bind/named.conf.options";
logging {

        channel update_debug {
                file "/var/log/update-debug.log";
                severity debug 3;
                print-category yes;
                print-severity yes;
                print-time     yes;
        };

        channel security_info {
                file "/var/log/named-auth.info";
                severity info;
                print-category yes;
                print-severity yes;
                print-time     yes;
        };

        category update { update_debug; };
        category security { security_info; };
};

key "rndc-key" {
        algorithm hmac-md5;
        secret "happykey";
};

// prime the server with knowledge of the root servers
zone "." {
        type hint;
        file "/etc/bind/db.root";
};

zone "localhost" {
        type master;
        file "/etc/bind/db.local";
};

zone "127.in-addr.arpa" {
        type master;
        file "/etc/bind/db.127";
};

zone "0.in-addr.arpa" {
        type master;
        file "/etc/bind/db.0";
};

zone "255.in-addr.arpa" {
        type master;
        file "/etc/bind/db.255";
};
include "/etc/bind/named.conf.local";
 

named.conf.local
> 
zone "ponywars.local" {
      type master;
      file "/etc/bind/zones/ponywars.local.db";
      notify yes;
      allow-update { key rndc-key; };
        };

zone "10.168.192.in-addr.arpa" {
      type master;
      file "/etc/bind/zones/rev.10.168.192.in-addr.arpa";
      notify yes;
      allow-update { key rndc-key; };
};


named.conf.options
> 
forwarders {
                194.74.65.69;
                194.72.9.38;
        };


zones files:
> 
-rw-r--r-- 1 root root  520 2006-10-20 21:54 ponywars.local.db
-rw-r--r-- 1 root root  819 2006-10-20 21:32 ponywars.local.db.jnl
-rw-r--r-- 1 root root  491 2006-10-20 21:51 rev.10.168.192.in-addr.arpa
-rwxr-xr-x 1 root bind 3755 2006-10-20 21:44 rev.10.168.192.in-addr.arpa.jnl


ponywars.local.db
> 
$ORIGIN .
$TTL 86400      ; 1 day
ponywars.local          IN SOA  betty.ponywars.local. jon.ponywars.local. (
                                2006081402 ; serial
                                28800      ; refresh (8 hours)
                                3600       ; retry (1 hour)
                                604800     ; expire (1 week)
                                38400      ; minimum (10 hours 40 minutes)
                                )
                        NS      betty.ponywars.local.
                        MX      10 betty.ponywars.local.
$ORIGIN ponywars.local.
betty                   A       192.168.10.1
$TTL 250        ; 4 minutes 10 seconds
felix                   A       192.168.10.194
                        TXT     "312260eea3db5eeb7fb08722fb0ff1eed7"
$TTL 86400      ; 1 day
www                     A       192.168.10.1


NOTE: it seems to have altered this to have the "ORIGIN" bit in it.  also the felix is when i was not in the domain (i think)

rev.10.168.192.in-addr.arpa
> 
$ORIGIN .
$TTL 86400      ; 1 day
10.168.192.in-addr.arpa IN SOA  betty.ponywars.local. jon.ponywars.local. (
                                2006081412 ; serial
                                28800      ; refresh (8 hours)
                                604800     ; retry (1 week)
                                604800     ; expire (1 week)
                                86400      ; minimum (1 day)
                                )
                        NS      betty.ponywars.local.
$ORIGIN 10.168.192.in-addr.arpa.
1                       PTR     ponywars.local
$TTL 250        ; 4 minutes 10 seconds
100                     PTR     bobby.ponywarshome.local.
194                     PTR     felix.ponywarshome.local.
99                      PTR     wiggly.ponywarshome.local.


NOTE: it is still putting it as ponywarshome.local which was the old name i was using on bind, it is also the name of the windows domain controller.  so i changed it to remove confusion.  there could be somewhere i have missed changing this but i do not know where.

resolv.conf
> search ponywars.local
nameserver 127.0.0.1
nameserver 194.74.65.69


dump of daemon.log after networking, bind and dhcp were restarted:
> Oct 20 22:21:48 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Oct 20 22:21:48 localhost dhclient: DHCPACK from 192.168.1.1
Oct 20 22:21:48 localhost dhclient: bound to 81.129.104.242 -- renewal in 30 seconds.
Oct 20 22:21:48 localhost named[31942]: *** POKED TIMER ***
Oct 20 22:21:48 localhost named[31942]: shutting down: flushing changes
Oct 20 22:21:48 localhost named[31942]: stopping command channel on 127.0.0.1#953
Oct 20 22:21:48 localhost named[31942]: stopping command channel on ::1#953
Oct 20 22:21:48 localhost named[31942]: no longer listening on 127.0.0.1#53
Oct 20 22:21:48 localhost named[31942]: no longer listening on 81.129.104.242#53
Oct 20 22:21:48 localhost named[31942]: no longer listening on 192.168.10.1#53
Oct 20 22:21:48 localhost named[31942]: exiting
Oct 20 22:21:51 localhost named[416]: starting BIND 9.3.2 -u bind
Oct 20 22:21:51 localhost named[416]: found 4 CPUs, using 4 worker threads
Oct 20 22:21:51 localhost named[416]: loading configuration from '/etc/bind/named.conf'
Oct 20 22:21:51 localhost named[416]: listening on IPv4 interface lo, 127.0.0.1#53
Oct 20 22:21:51 localhost named[416]: binding TCP socket: address in use
Oct 20 22:21:51 localhost named[416]: listening on IPv4 interface eth0, 81.129.104.242#53
Oct 20 22:21:51 localhost named[416]: binding TCP socket: address in use
Oct 20 22:21:51 localhost named[416]: listening on IPv4 interface eth1, 192.168.10.1#53
Oct 20 22:21:51 localhost named[416]: binding TCP socket: address in use
Oct 20 22:21:51 localhost named[416]: command channel listening on 127.0.0.1#953
Oct 20 22:21:51 localhost named[416]: command channel listening on ::1#953
Oct 20 22:21:51 localhost named[416]: zone 0.in-addr.arpa/IN: loaded serial 1
Oct 20 22:21:51 localhost named[416]: zone 127.in-addr.arpa/IN: loaded serial 1
Oct 20 22:21:51 localhost named[416]: zone 10.168.192.in-addr.arpa/IN: loaded serial 2006081412
Oct 20 22:21:51 localhost named[416]: zone 255.in-addr.arpa/IN: loaded serial 1
Oct 20 22:21:51 localhost named[416]: zone ponywars.local/IN: loaded serial 2006081402
Oct 20 22:21:51 localhost named[416]: zone localhost/IN: loaded serial 1
Oct 20 22:21:51 localhost named[416]: running
Oct 20 22:21:57 localhost dhcpd: Internet Systems Consortium DHCP Server V3.0.3
Oct 20 22:21:57 localhost dhcpd: Copyright 2004-2005 Internet Systems Consortium.
Oct 20 22:21:57 localhost dhcpd: All rights reserved.
Oct 20 22:21:57 localhost dhcpd: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Oct 20 22:21:59 localhost dhcpd: Internet Systems Consortium DHCP Server V3.0.3
Oct 20 22:21:59 localhost dhcpd: Copyright 2004-2005 Internet Systems Consortium.
Oct 20 22:21:59 localhost dhcpd: All rights reserved.
Oct 20 22:21:59 localhost dhcpd: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Oct 20 22:21:59 localhost dhcpd: Wrote 0 deleted host decls to leases file.
Oct 20 22:21:59 localhost dhcpd: Wrote 0 new dynamic host decls to leases file.
Oct 20 22:21:59 localhost dhcpd: Wrote 9 leases to leases file.
Oct 20 22:21:59 localhost dhcpd: bogus UDP packet length: 43938
Oct 20 22:22:18 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Oct 20 22:22:18 localhost dhclient: DHCPACK from 192.168.1.1
Oct 20 22:22:18 localhost dhclient: bound to 81.129.104.242 -- renewal in 31 seconds.


dump from daemon.log when did release renew on felix (windows xp machine)
> 
Oct 20 22:23:06 localhost dhcpd: DHCPRELEASE of 192.168.10.194 from 00:d0:59:34:17:7c (felix) via eth1 (found)
Oct 20 22:23:12 localhost dhcpd: DHCPDISCOVER from 00:d0:59:34:17:7c via eth1
Oct 20 22:23:13 localhost dhcpd: DHCPOFFER on 192.168.10.194 to 00:d0:59:34:17:7c (felix) via eth1
Oct 20 22:23:13 localhost named[416]: /etc/bind/zones/rev.10.168.192.in-addr.arpa.jnl: open: permission denied
Oct 20 22:23:13 localhost dhcpd: unable to add reverse map from 194.10.168.192.in-addr.arpa. to felix.ponywarshome.local: timed out
Oct 20 22:23:13 localhost dhcpd: DHCPREQUEST for 192.168.10.194 (192.168.10.1) from 00:d0:59:34:17:7c (felix) via eth1
Oct 20 22:23:13 localhost dhcpd: DHCPACK on 192.168.10.194 to 00:d0:59:34:17:7c (felix) via eth1


i am not sure why i am getting permission errors on the reverse map, and not even getting a forward mapping result or error.

dump from update log file created from logging within named.conf
> 
20-Oct-2006 22:23:13.003 update: info: client 127.0.0.1#32922: updating zone '10.168.192.in-addr.arpa/IN': deleting rrset at '194.10.168.192.in-addr.arpa' PTR
20-Oct-2006 22:23:13.004 update: info: client 127.0.0.1#32922: updating zone '10.168.192.in-addr.arpa/IN': adding an RR at '194.10.168.192.in-addr.arpa' PTR
20-Oct-2006 22:23:13.005 update: info: client 127.0.0.1#32922: updating zone '10.168.192.in-addr.arpa/IN': error: journal open failed: unexpected error


i think this error is the same as the daemon.log file due to permissions.

to be completely honest i am so stuck and confused now i dont know where to turn.

ALL local machines on the network (every machine except betty the ubuntu box) can ping each other by name.  i get "unkown host" from her.  ALL machines can see the net correctly.

This is a complete mistery to me.  When i reinstalled it i hoped i would have solved it but to no avail.  I hope someone has seen this sort of thing before or can see the problem

Thank you

Twiggy

p.s... just looked at it.. sorry for writting my life story :p

---

### Post by elst on 2006-10-21
I'm not going to try to quote the original post in this reply :).

Windows clients automatically appear in DNS because they use dynamic DNS by default - IIRC the computer records in AD aren't actually connected to, or dependent on, DNS records. So my guess is that your problem lies with your DHCP/dynamic DNS setup.

---

### Post by twistedtwig on 2006-10-21
ok,

well thats good to know, thanks :)

so i need to track down where the issue(s) are with bind and dhcp... any suggestions on error finding please?

---

### Post by elst on 2006-10-21
I think that the key clue is here, with attempts to update the reverse zone file failing:

> 
Oct 20 22:23:13 localhost named[416]: /etc/bind/zones/rev.10.168.192.in-addr.arpa.jnl: open: permission denied
Oct 20 22:23:13 localhost dhcpd: unable to add reverse map from 194.10.168.192.in-addr.arpa. to felix.ponywarshome.local: timed out


As a matter of course I'd run named-checkconfig to test the syntax of your named.conf file for errors. 

Unfortunately, I haven't configured dynamic DNS on Linux, so I'm not sure exactly how the zone files are supposed to be updated in this configuration. At work we let a Windows DNS server handle the Windows network, and configured the main Linux DNS server as a slave for the zones that the Windows server manages.

You could also disable dynamic updates and just manually add the Windows hosts to your DNS zones - the effect is the same as having DDNS register them.

Hope that helps

---

### Post by twistedtwig on 2006-10-22
hi,

i have tried "named-checkconfig" but i get this error

bash: named-checkconfig: command not found

i can run named-checkzone on both zone files and it comes back with OK.  hadnt heard of these commands till this morning.

> 
named-checkzone -dj 10.168.192.in-addr.arpa rev.10.168.192.in-addr.arp
loading "10.168.192.in-addr.arpa" from "rev.10.168.192.in-addr.arpa" class "IN"
zone 10.168.192.in-addr.arpa/IN: loaded serial 2006081412
OK

still trying to hunt down the permission denied error, but thanks for the help :D

---

### Post by twistedtwig on 2006-10-22
ok, so when i removed the computer from the windows domain it all worked perfectly

> 
Oct 22 10:18:26 localhost dhcpd: DHCPRELEASE of 192.168.10.194 from 00:d0:59:34:17:7c (felix) via eth1 (found)
Oct 22 10:18:28 localhost dhcpd: DHCPDISCOVER from 00:d0:59:34:17:7c via eth1
Oct 22 10:18:28 localhost dhcpd: DHCPOFFER on 192.168.10.194 to 00:d0:59:34:17:7c (felix) via eth1
Oct 22 10:18:28 localhost dhcpd: Added new forward map from felix.ponywars.local to 192.168.10.194
Oct 22 10:18:28 localhost dhcpd: added reverse map from 194.10.168.192.in-addr.arpa. to felix.ponywars.local
Oct 22 10:18:28 localhost dhcpd: DHCPREQUEST for 192.168.10.194 (192.168.10.1) from 00:d0:59:34:17:7c (felix) via eth1
Oct 22 10:18:28 localhost dhcpd: DHCPACK on 192.168.10.194 to 00:d0:59:34:17:7c (felix) via eth1


but when i add the same computer back into the domain i get

> 
Oct 22 10:36:38 localhost dhcpd: removed reverse map on 194.10.168.192.in-addr.arpa.
Oct 22 10:36:38 localhost dhcpd: DHCPRELEASE of 192.168.10.194 from 00:d0:59:34:17:7c (felix) via eth1 (found)
Oct 22 10:36:45 localhost dhcpd: DHCPDISCOVER from 00:d0:59:34:17:7c via eth1
Oct 22 10:36:46 localhost dhcpd: DHCPOFFER on 192.168.10.194 to 00:d0:59:34:17:7c (felix) via eth1
Oct 22 10:36:46 localhost dhcpd: added reverse map from 194.10.168.192.in-addr.arpa. to felix.ponywarshome.local
Oct 22 10:36:46 localhost dhcpd: DHCPREQUEST for 192.168.10.194 (192.168.10.1) from 00:d0:59:34:17:7c (felix) via eth1
Oct 22 10:36:46 localhost dhcpd: DHCPACK on 192.168.10.194 to 00:d0:59:34:17:7c (felix) via eth1


there is no obvious error to me here.  BUT the linux dns zone is "ponywars.local" NOT ponywarshome.local, which is the windows domain.  when i do a ipconfig/all on that machine when its in the domain i get something which i think could be interesting.

the Primary DNS Suffix is ponywarshome.local
DNS suffex search list has both ponywarshome.local and ponywars.local (in that order)

the connection-specific dns suffex is ponywars.local

i dont think this has anythign to do with it but i see this error in the daemon.log file often

> 

Oct 22 10:35:56 localhost dhclient: bound to 81.129.104.242 -- renewal in 28 seconds.
Oct 22 10:36:06 localhost named[4273]: dumping master file: /etc/bind/tmp-EEWsXFijPF: open: permission denied


and this seems very odd to me its not quite as often as the last error but still there some times

> 
Oct 22 10:08:42 localhost named[891]: unexpected RCODE (SERVFAIL) resolving '225.40.184.140.in-addr.arpa/PTR/IN': 194.72.9.38#53
Oct 22 10:08:43 localhost named[891]: unexpected RCODE (SERVFAIL) resolving '225.40.184.140.in-addr.arpa/PTR/IN': 194.74.65.69#53
Oct 22 10:08:44 localhost named[891]: lame server resolving '225.40.184.140.in-addr.arpa' (in '40.184.140.in-addr.arpa'?): 140.184.1.1#53
Oct 22 10:08:56 localhost named[891]: unexpected RCODE (SERVFAIL) resolving '52.79.95.211.in-addr.arpa/PTR/IN': 194.72.9.38#53
Oct 22 10:08:57 localhost named[891]: unexpected RCODE (SERVFAIL) resolving '52.79.95.211.in-addr.arpa/PTR/IN': 194.74.65.69#53
Oct 22 10:08:59 localhost named[891]: lame server resolving '52.79.95.211.in-addr.arpa' (in '79.95.211.in-addr.arpa'?): 211.95.1.97#53


oh the joys of debuging :p

Twiggy

---

### Post by twistedtwig on 2006-10-22
it would seem the lame-server is a failed dns server somewhere else on the net and not a lot i can do about it. :(

going to look into the master file issue

---

### Post by twistedtwig on 2006-10-22
the master issues seem to be back to permission issues.

i am not sure i have the folder permissions / bind + named permissions sorted correctly.. would some one have a look at these name files and see if they make sense please?

/etc grepped for bind
> 
drwxrwxr-x   3 root   bind      4096 2006-10-22 11:20 bind


> 
root@betty:/etc/bind# ls -l
total 48
-rwxrwxr-x 1 root root  237 2006-09-07 17:21 db.0
-rwxrwxr-x 1 root root  271 2006-09-07 17:21 db.127
-rwxrwxr-x 1 root root  237 2006-09-07 17:21 db.255
-rwxrwxr-x 1 root root  353 2006-09-07 17:21 db.empty
-rwxrwxr-x 1 root root  256 2006-09-07 17:21 db.local
-rwxrwxr-x 1 root root 1507 2006-09-07 17:21 db.root
-rwxrwxr-x 1 root bind 2273 2006-10-20 20:53 named.conf
-rwxrwxr-x 1 root bind  329 2006-10-22 11:20 named.conf.local
-rwxrwxr-x 1 root bind  697 2006-10-20 20:34 named.conf.options
-rwxrwxr-x 1 bind bind   77 2006-10-20 20:12 rndc.key
drwxrwxr-x 2 bind bind 4096 2006-10-22 11:15 zones
-rwxrwxr-x 1 root root 1317 2006-09-07 17:21 zones.rfc1918


> root@betty:/etc/bind/zones# ls -l
total 8
-rwxrwxr-x 1 bind bind 400 2006-10-22 11:15 ponywars.local.db
-rwxrwxr-x 1 bind bind 544 2006-10-22 11:15 rev.10.168.192.in-addr.arpa


when i tried to release renew on felix it didnt through any errors in the daemon.log file but when i had named -g -p 53 running (not honestly sure what that means but i found it in another forum and seems to give nice output) it says

> 22-Oct-2006 11:21:11.747 client 127.0.0.1#32956: updating zone '10.168.192.in-addr.arpa/IN': deleting rrset at '194.10.168.192.in-addr.arpa' PTR
22-Oct-2006 11:21:11.747 journal file /etc/bind/zones/rev.10.168.192.in-addr.arpa.jnl does not exist, creating it
22-Oct-2006 11:21:11.748 /etc/bind/zones/rev.10.168.192.in-addr.arpa.jnl: create: permission denied
22-Oct-2006 11:21:11.748 client 127.0.0.1#32956: updating zone '10.168.192.in-addr.arpa/IN': error: journal open failed: unexpected error
22-Oct-2006 11:21:48.006 client 127.0.0.1#32956: updating zone '10.168.192.in-addr.arpa/IN': deleting rrset at '194.10.168.192.in-addr.arpa' PTR
22-Oct-2006 11:21:48.007 client 127.0.0.1#32956: updating zone '10.168.192.in-addr.arpa/IN': adding an RR at '194.10.168.192.in-addr.arpa' PTR


from what i understand that means it couldnt create / open the reverse mapping jnl file.  but again no mention of the forward mapping.

daemon.log
> 
Oct 22 10:29:03 localhost dhcpd: if felix.ponywars.local IN TXT "312260eea3db5eeb7fb08722fb0ff1eed7" rrset exists and felix.ponywars.local IN A 192.168.10.194 rrset exists delete felix.ponywars.local IN A 192.168.10.194: success.
Oct 22 10:29:03 localhost dhcpd: if felix.ponywars.local IN A rrset doesn't exist delete felix.ponywars.local IN TXT "312260eea3db5eeb7fb08722fb0ff1eed7": success.
Oct 22 10:29:03 localhost dhcpd: removed reverse map on 194.10.168.192.in-addr.arpa.
Oct 22 10:29:03 localhost dhcpd: DHCPRELEASE of 192.168.10.194 from 00:d0:59:34:17:7c (felix) via eth1 (found)
Oct 22 10:29:07 localhost dhcpd: DHCPDISCOVER from 00:d0:59:34:17:7c via eth1
Oct 22 10:29:08 localhost dhcpd: DHCPOFFER on 192.168.10.194 to 00:d0:59:34:17:7c (felix) via eth1
Oct 22 10:29:08 localhost dhcpd: added reverse map from 194.10.168.192.in-addr.arpa. to felix.ponywarshome.local
Oct 22 10:29:08 localhost dhcpd: DHCPREQUEST for 192.168.10.194 (192.168.10.1) from 00:d0:59:34:17:7c (felix) via eth1
Oct 22 10:29:08 localhost dhcpd: DHCPACK on 192.168.10.194 to 00:d0:59:34:17:7c (felix) via eth1


this is so confusing :s

---

### Post by twistedtwig on 2006-10-22
okie dokie,

so bind:bind permissions on folders and files is a bad thing it seems.  i am assuming that dhcp needs permissions which is "root" so root:bind seems to work better.  it will now create the jnl file for reverse look up but nothing for forward look ups still.

so i tested it by removing computer from the domain and ALL worked ACE! then re adding it and it adds the reverse but i get a mailformed transaction

> Oct 22 12:34:16 localhost named[7750]: malformed transaction: /etc/bind/zones/ponywars.local.db.jnl last serial 2006081412 != transaction first serial 2006081409
Oct 22 12:34:16 localhost dhcpd: if felix.ponywars.local IN TXT "312260eea3db5eeb7fb08722fb0ff1eed7" rrset exists and felix.ponywars.local IN A 192.168.10.194 rrset exists delete felix.ponywars.local IN A 192.168.10.194: timed out.
Oct 22 12:34:16 localhost dhcpd: DHCPRELEASE of 192.168.10.194 from 00:d0:59:34:17:7c (felix) via eth1 (found)
Oct 22 12:34:27 localhost dhcpd: DHCPDISCOVER from 00:d0:59:34:17:7c via eth1
Oct 22 12:34:28 localhost dhcpd: DHCPOFFER on 192.168.10.194 to 00:d0:59:34:17:7c (felix) via eth1
Oct 22 12:34:28 localhost dhcpd: added reverse map from 194.10.168.192.in-addr.arpa. to felix.ponywarshome.local
Oct 22 12:34:28 localhost dhcpd: DHCPREQUEST for 192.168.10.194 (192.168.10.1) from 00:d0:59:34:17:7c (felix) via eth1
Oct 22 12:34:28 localhost dhcpd: DHCPACK on 192.168.10.194 to 00:d0:59:34:17:7c (felix) via eth1


---

### Post by elst on 2006-10-22
> 
Oct 22 12:34:16 localhost named[7750]: malformed transaction: /etc/bind/zones/ponywars.local.db.jnl last serial 2006081412 != transaction first serial 2006081409


Try deciding a new serial number like 2006102201, updating all of the zone masters to that to make them consistent, and then reloading. BIND uses the serial numbers to compare the versions of zone data.

FWIW, the syntax checker is "named-checkconf", rather than named-checkconfig, as I had misremembered.

---

### Post by twistedtwig on 2006-10-22
cool, thx for the info.  changes the serial numbers.  didnt realise thats what they did.  have run the named0checkconf command and i think i undestand the output

> 
root@betty:/etc/bind/zones# named-checkconf rev.10.168.192.in-addr.arpa
rev.10.168.192.in-addr.arpa:1: unknown option '$ORIGIN'
rev.10.168.192.in-addr.arpa:2: unknown option '1'
rev.10.168.192.in-addr.arpa:4: unknown option 'serial'
rev.10.168.192.in-addr.arpa:5: unknown option 'refresh'
rev.10.168.192.in-addr.arpa:6: unknown option 'retry'
rev.10.168.192.in-addr.arpa:7: unknown option 'expire'
rev.10.168.192.in-addr.arpa:8: unknown option 'minimum'
rev.10.168.192.in-addr.arpa:13: unknown option '4'
rev.10.168.192.in-addr.arpa:15: unknown option '6'
rev.10.168.192.in-addr.arpa:17: unknown option '4'
rev.10.168.192.in-addr.arpa:20: unexpected token near end of file
root@betty:/etc/bind/zones# named-checkconf rev.10.168.192.in-addr.arpa
rev.10.168.192.in-addr.arpa:1: unknown option '$ORIGIN'
rev.10.168.192.in-addr.arpa:2: unknown option '1'
rev.10.168.192.in-addr.arpa:4: unknown option 'serial'
rev.10.168.192.in-addr.arpa:5: unknown option 'refresh'
rev.10.168.192.in-addr.arpa:6: unknown option 'retry'
rev.10.168.192.in-addr.arpa:7: unknown option 'expire'
rev.10.168.192.in-addr.arpa:8: unknown option 'minimum'
rev.10.168.192.in-addr.arpa:13: unknown option '4'
rev.10.168.192.in-addr.arpa:15: unknown option '6'
rev.10.168.192.in-addr.arpa:17: unknown option '4'
rev.10.168.192.in-addr.arpa:20: unexpected token near end of file
root@betty:/etc/bind/zones# named-checkconf ponywars.local.db
ponywars.local.db:1: unknown option '$ORIGIN'
ponywars.local.db:2: unknown option '1'
ponywars.local.db:4: unknown option 'serial'
ponywars.local.db:5: unknown option 'refresh'
ponywars.local.db:6: unknown option 'retry'
ponywars.local.db:7: unknown option 'expire'
ponywars.local.db:8: unknown option 'minimum'
ponywars.local.db:14: unknown option '6'
ponywars.local.db:17: unknown option '1'
ponywars.local.db:19: unexpected token near end of file


the origin was put in by bind or dhcp (well the server did it not me).  the rest (apart from the unexpexted token) are all after ";" which i believe to be commentors so all text after them are ignored on that line.

is this right? 

thx :)

---

### Post by elst on 2006-10-22
The "named-checkconf" utility checks a named.conf for errors, and "named-checkzone" checks zone files.

To test the zone files:

named-checkzone <zone name> <file>

To test /etc/named.conf you just type: 

named-checkconf

---

### Post by twistedtwig on 2006-10-23
doh!

ran that against the named.conf and named.conf.local, it gave no output, well only bind version:
> 
root@betty:/etc/bind# named-checkconf -vzj named.conf
9.3.2


reading the man file i thought it returned zero or one depending on success or not.

---

### Post by elst on 2006-10-23
Those are exit codes which you can test for by scripts. The utility displays errors, so it will show nothing if the config file is valid.

---

### Post by twistedtwig on 2006-10-23
ahh ok.. thanks :)

---

### Post by hitochigae on 2007-04-04
I realize it's a belated and inconsistent answer, but hopefully it will be of use to anyone else searching for the same thing.

The issue with windows domain members not being resolved is caused by the difference in FQDNs between workgroup and domain members.
In tcpdump output one can see, that when a workgroup member talks to the DHCP server, it says, among other things, 

> 22:56:07.815575 IP (tos 0x0, ttl 128, id 0, offset 0, flags [none], proto: UDP (17), length: 334) 0.0.0.0.bootpc > 255.255.255.255.bootps: [udp sum ok] BOOTP
/DHCP, Request from 00:01:6c:b5:1b:69 (oui Unknown), length: 306, xid:0xf30b9d49, flags: [none] (0x0000)
          Client Ethernet Address: 00:01:6c:b5:1b:69 (oui Unknown)
          Vendor-rfc1048:
            DHCP:REQUEST
            CID:[ether]00:01:6c:b5:1b:69
            RQ:host.lan.local
            HN:"host"
            **FQDN:"Host."**
            VC:"MSFT 5.0"
            PR:SM+DN+DG+NS+WNS+WNT+WSC+RD+SR+T249+VO

However, the domain member will ask for 
> 
            **FQDN:"Host.lan.local."**

In that case dhcpd will only add a reverse map, leaving - by default - to  update the forward zone to the cilent itself.
Man page :) to the isc-dhcpd says one has to "ignore client-updates;" and also to switch "use-host-decl-names on;" (if you want the dhcpd to add the maps, of course)

Real description is in the isc-dhcpd man page, section "THE INTERIM DNS UPDATE SCHEME".

Damn, it's late. :D

---

### Post by djdvant on 2008-04-24
After much hair pulling over several months I finally got to the problem.  My DNS and DHCP files were OK and always had been.

I finally tracked down an kernel audit message


kernel:  audit(1209076817.081:16): type=1503 operation="inode_create" requested_mask="w::" denied_mask="w::" name="/etc/bind/xxxxx.com.hosts.jnl" pid=16561 profile="/usr/sbin/named" namespace="default"

So I had a look in:
/etc/apparmor.d/usr.sbin.named

and changed this line:
  /etc/bind/** r,

to this:
  /etc/bind/** rw,

End of problems

---

