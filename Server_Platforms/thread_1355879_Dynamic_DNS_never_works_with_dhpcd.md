---
title: "Dynamic DNS never works with dhpcd"
date: 2009-12-15
forum: Server Platforms
---

### Post by jimmah6786 on 2009-12-15
I have been trying to get my DHCP server to update my DNS with the client hostnames dynamically. After several days of googling and even following by the letter some of the examples, my DNS does not resolve local DNS names. In the BIND9 logs, there are some security denied updating record non-sense, and I have no idea why. Also if you have any recommendations or considerations please let me know. This set up is for a SOHO and the domain specified is not the actual for privacy purposes. Here is my configs...

**/etc/bind/named.conf**
```

logging{
        channel simple_log {
                file "/var/log/named/bind.log";
                severity info;
                print-category yes;
                print-severity yes;
                print-time yes;
                };
        channel warning_log {
                file "/var/log/named/bind.log";
                severity warning;
                print-category yes;
                print-severity yes;
                print-time yes;
                };
        channel notice_log {
                file "/var/log/named/bind.log";
                severity notice;
                print-category yes;
                print-severity yes;
                print-time yes;
                };
        category default {
                simple_log;
                };
};


controls {
        inet 192.168.10.1 port 953 allow { 192.168.10.1; } keys { "rndc-key"; };
        };

include "/etc/bind/rndc.key";

```

**/etc/bind/named.conf.local**
```

zone "ourhouse.iscool." {
  type master;
  file "/etc/bind/zones/ourhouse.iscool.db";
  allow-update { key "rndc-key"; };
  notify yes;

};

zone "10.168.192.in-addr.arpa." {
   type master;
   file "/etc/bind/zones/rev.10.168.192.in-addr.arpa";
   allow-update { key "rndc-key"; };
   notify yes;
};


include "/etc/bind/rndc.key";

acl local {
        127.0.0.0/8;
        192.168.10.0/24;
        };

```

**/etc/bind/named.conf.options**
```

options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

        // forwarders {
        //      0.0.0.0;
        // };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
        forwarders {
                208.67.220.220;
                208.67.222.222;
                };

        recursion yes;

        allow-recursion {
                127.0.0.1;
                192.168.10.0/24;
                };

        allow-query {
        127.0.0.1;
        192.168.10.0/24;
        };

        topology {
                192.168.10.1;
                };
};

```

Here are the zones:

**/etc/bind/zones/ourhouse.iscool.db**
```
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ns.ourhouse.iscool. root.ourhouse.iscool. (
                        9
                        604800
                        86400
                        2419200
                        604800 )
;
ourhouse.iscool.        IN      NS      ns.ourhouse.iscool.
ourhouse.iscool.        IN      A       192.168.10.1
ourhouse.iscool.        IN      AAAA    ::1
homerouter.ourhouse.iscool.     IN      A       192.168.10.1
ns.ourhouse.iscool.     IN      A       192.168.10.1

```

**/etc/bind/zones/rev.10.168.192.in-addr.arpa**
```

;
; BIND reverse data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ns.ourhouse.iscool. root.ourhouse.iscool. (
                        3
                        604800
                        86400
                        2419200
                        604800 )
;
@       IN      NS      ns.
1.10.168.192.in-addr.arpa.      IN      PTR     ns.ourhouse.iscool.

```


/etc/dhcp3/dhcpd.conf
```

allow unknown-clients;
# for DNS
authoritative;
server-identifier server;
ddns-updates on;
ddns-update-style interim;
ddns-domainname "ourhouse.net.";
ddns-rev-domainname "in-addr.arpa.";
allow client-updates;

#DNS key
include "/etc/bind/rndc.key";

# communication zone
zone ourhouse.iscool. {
        primary 192.168.10.1;
        key "rndc-key";
        }



# Local Subnet
subnet 192.168.10.0 netmask 255.255.255.0 {
        allow client-updates;
        allow unknown-clients;
        ddns-updates on;
        option domain-name "ourhouse.iscool.";
        option domain-name-servers 192.168.10.1;
        option broadcast-address 192.168.10.255;
        option subnet-mask 255.255.255.0;
        option routers 192.168.10.1;
        option ip-forwarding off;
        default-lease-time 600;
        max-lease-time 7200;
        range 192.168.10.100 192.168.10.200;
        # zones
        zone 10.168.192.in-addr.arpa. {
                primary 192.168.10.1;
                key "rndc-key";
                }
        zone ourhouse.iscool. {
                primary 192.168.10.1;
                key "rndc-key";
}
}


```

---

### Post by munky99999 on 2009-12-15
It should be possible to reserve your dhcp ip at the dhcp server for those assets you want associated with DNS.

Then keep the DNS -Bind settings the properly setup way.


That way Bind host records point to 192.168.10.10 or whatever. Then have your dhcp server dynamically reserve 192.168.10.10 for that specific server.

---

### Post by Zeosa on 2009-12-16
Be sure that the user dhcpd is running as has read access to /etc/bind/rndc.key (add the dhcpd user to the bind group and set rndc.key to be group readable)

---

### Post by jimmah6786 on 2009-12-16
> **Zeosa said:**
> Be sure that the user dhcpd is running as has read access to /etc/bind/rndc.key (add the dhcpd user to the bind group and set rndc.key to be group readable)

Thanks Zeosa, I added it using usermod. However I noticed that in the daemon.log there are a ton of 
```
"Unable to add forward map from <hostname> to <ip address>:timed out 
```

---

### Post by jimmah6786 on 2009-12-17
Okay I keep getting the Unable to add a forward map" error messages.

I have read several forums and have tried the following:

-Ensuring firewall allows communication
-ensuring dhcpd user is a member of bind group
-ensuring permissions of the rndc.key file are correct
-encsuring that apparmor is not hindering this process

Any ideas?

Thanks all!

---

### Post by jimmah6786 on 2009-12-17
The logs are filled with the following

```
Dec 17 10:29:42 homerouter dhcpd: Unable to add forward map from someonecpu.ourhouse.iscool to 192.168.10.117: timed out
Dec 17 10:29:42 homerouter dhcpd: server: host unknown.
Dec 17 10:29:42 homerouter dhcpd: dhcp.c(3997): non-null pointer

```

Heres my /etc/group
```

dhcpd:x:114:
bind:x:115:dhcpd

```

---

### Post by Zeosa on 2009-12-17
I know you said that you've made sure apparmor isn't interfering, how did you do it? If you havn't yet, try stopping apparmor altogether just to be sure. 

Can you post the permissions of /etc/bind/zones (ls -lad)

---

### Post by jimmah6786 on 2009-12-18
> **Zeosa said:**
> I know you said that you've made sure apparmor isn't interfering, how did you do it? If you havn't yet, try stopping apparmor altogether just to be sure. 

Can you post the permissions of /etc/bind/zones (ls -lad)


ls -lad
```

ls -lad
drwxr-sr-x 2 root bind 4096 2009-12-17 23:48 .


```

apparmor for dhcpd3
```

 /etc/bind/ rw,
  /etc/bind/** rw,


```

---

### Post by jimmah6786 on 2009-12-18
Okay all thanks to Zeosa, 

I was missing the correct permissions for the zones file. So what I did was a 

```
sudo chmod 664 /etc/bind/zones/*
```

Which now allows the forward maps to append the zone db files.


Thanks

Zeosa! You ROck!

New issue is the reverse-map is filled with really long ip address
```

192.168.10.192.168.10.116

```
as if it is adding it twice?

---

