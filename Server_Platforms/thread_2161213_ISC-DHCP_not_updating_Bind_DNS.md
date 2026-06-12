---
title: "ISC-DHCP not updating Bind DNS"
date: 2013-07-09
forum: Server Platforms
---

### Post by Zosimus on 2013-07-09
Hi I've been working all day a on a problem that I'm unfortunately unable to solve. I'm currently running a ubuntu server and with Bind DNS and ISC DHCP server.

I'm trying to configure yhem so that the DHCP automatically updates the bind dns records.

I've looked at the log and all my client recieve the proper ip configuration from the dhcp server however,it seems that it's unable to "pass the information" to bind dns.

This is the kind of error that I have in the syslog:

> 
Jul  9 12:59:48 FS02 dhcpd: Unable to add forward map from Steph-A-Soucy.webtelecom.local. to 10.9.1.69: timed out
 Jul  9 13:07:15 FS02 dhcpd: Unable to add forward map from BSP00260BB036C8.webtelecom.local. to 10.9.1.71: timed out
 Jul  9 13:11:04 FS02 dhcpd: Unable to add forward map from Steph-A-Soucy.webtelecom.local. to 10.9.1.69: timed out
 Jul  9 13:11:22 FS02 dhcpd: Unable to add forward map from Steph-A-Soucy.webtelecom.local. to 10.9.1.69: timed out
 Jul  9 13:12:40 FS02 dhcpd: Unable to add forward map from Steph-A-Soucy.webtelecom.local. to 10.9.1.69: timed out
 Jul  9 13:15:58 FS02 dhcpd: Unable to add forward map from Steph-A-Soucy.webtelecom.local. to 10.9.1.69: timed out
 Jul  9 13:29:08 FS02 dhcpd: unable to add reverse map from 64.1.9.10.in-rev.arpa. to POSTENODEUS1.adsum.local: timed out


This is my dhcpd.conf file

```

key rndc-key { algorithm hmac-md5; secret "8IGWFWpVOkQZcVj0rYtKNg=="; }
default-lease-time 600;
max-lease-time 7200;


zone webtelecom.local. {
        primary 127.0.0.1;
        key rndc-key;
        }


zone 1.9.10.in-addr.arpa. {
    primary 127.0.0.1;
        key rndc-key; 
        }


log-facility local7;


# Default subnet
subnet 10.9.1.0 netmask 255.255.255.0 {
    authoritative;
    ignore client-updates;
    allow unknown-clients;
    ddns-updates on;
        ddns-update-style interim;
        use-host-decl-names on;
    range 10.9.1.50 10.9.1.254;
    option subnet-mask 255.255.255.0;
    option routers 10.9.1.1;
    option domain-name-servers 10.9.1.20;
    option domain-name "webtelecom.local";
    ddns-domainname "webtelecom.local.";
    ddns-rev-domainname "in-rev.arpa.";

    }


# PC de Robin
host PC07 {
    hardware ethernet 00:1c:c0:66:c9:f7;
    fixed-address 10.9.1.60;
    }
# Acomba-Jacques
host Acomba-Jacques {
    hardware ethernet 00:0c:29:ed:89:03;
    fixed-address 10.9.1.61;
    }
# Acomba-Fred
host Acomba-Fred {
    hardware ethernet 00:0c:29:bc:5c:88;
    fixed-address 10.9.1.62;
    }
# Acomba-Marie
host Acomba-Marie {
    hardware ethernet 00:0c:29:0f:ad:ed;
    fixed-address 10.9.1.63;
    }
# Switch Lynksys
host BSP00260BB036C8 {
    hardware ethernet 00:26:0b:b0:36:c8;
    fixed-address 10.9.1.2;
    }
                           

```

And this is my named.conf.local

```


key "rndc-key" {
        algorithm hmac-md5;
        secret "8IGWFWpVOkQZcVj0rYtKNg==";
};


zone "webtelecom.local" {
    type master;
    file "/var/lib/bind/webtelecom.local.hosts";
    allow-update { key rndc-key; };
    };


zone "1.9.10.in-addr.arpa" {
    type master;
    file "/var/lib/bind/10.9.1.rev";
    allow-update { key rndc-key; };
    };



```

I've also made sure that the bind user and group have full read/write/execute in var/lib/bind and etc/bind folders (althoug it dosen't seem to be an access right problem from the logs)

I have to add the following : bind works fine for the root zone my clients are able to resolve google.com and stuff like that it seems that this problem is with my local zone. 

Don't be afraid to ask if you need more info to diagnose the problem 

Anybody experienced similar problem and knows how to fix it ? I'm desperate !

---

### Post by Zosimus on 2013-07-10
Update:
I managed to fix my "time out" errors (there were a bunch of errors in my host files) I repaired them but now I'm having another issue, all my files seems "clean" but nothing is showing up in the logs (as if the dhcp was not trying to push the information to the DNS.)

Any idea ?

---

