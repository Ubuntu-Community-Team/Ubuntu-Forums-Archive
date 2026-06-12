---
title: "DDNS not working in local zone"
date: 2013-08-15
forum: Server Platforms
---

### Post by SeaKing on 2013-08-15
Hey guys,

I'm currently trying to setup my local ddns with bind9 but it seems to be harder than I thought.

There are two major problems at the moment, first: I only can resolv static entries properly like:
```
seaking@seaking-nb01:~$ host nas
nas.home.sk.org has address 192.168.50.2
```
but dynamic ones (like my laptop) do not work:
```
seaking@seaking-nb01:~$ host seaking-nb01
Host seaking-nb01 not found: 3(NXDOMAIN)
```

The secon one is bind itself, it writes messages like this to syslog:
```

Aug 15 17:55:11 router named[6013]: error (host unreachable) resolving 'seaking-nb01/A/IN': 208.67.222.222#53
Aug 15 18:56:20 router named[6013]: error (host unreachable) resolving './NS/IN': 8.8.8.8#53
Aug 15 19:02:21 router named[6013]: error (host unreachable) resolving './NS/IN': 208.67.222.222#53
Aug 15 19:07:17 router named[6013]: error (host unreachable) resolving './NS/IN': 8.8.8.8#53
Aug 15 19:15:14 router named[6013]: managed-keys-zone ./IN: No DNSKEY RRSIGs found for '.': success
Aug 15 19:15:14 router named[6013]: managed-keys-zone ./IN: No DNSKEY RRSIGs found for 'dlv.isc.org': success

```

my configs:

dhcpd.conf
```
authoritative;
log-facility local7;

#ddns-update-style interim;


#subnet 192.168.1.0 netmask 255.255.255.0 {
#  range 192.168.1.2 192.168.1.3;
#}

subnet 192.168.50.0 netmask 255.255.255.0 {

  range 192.168.50.20 192.168.50.150;
  option subnet-mask 255.255.255.0;
  option domain-name-servers 192.168.50.1;
  option domain-name "home.sk.org";
  option routers 192.168.50.1;
  option broadcast-address 192.168.50.255;
  option netbios-name-servers 192.168.50.1;
  default-lease-time 3600;
  max-lease-time 7200;
  ################DDNS Part###################
  ddns-domainname "home.sk.org";
  ddns-updates on;
  ddns-update-style interim;
  allow client-updates;
  update-static-leases off;
  one-lease-per-client on;


  key DDNS_UPDATE_VLAN50 {
     algorithm HMAC-SHA512;
     secret "key==";
  };

  zone home.sk.org. {
    primary 192.168.50.1;
    key DDNS_UPDATE_VLAN50;
  }

  zone 50.168.192.in-addr.arpa. {
    primary 192.168.50.1;
    key DDNS_UPDATE_VLAN50;
  }
  #############static hosts###################

  host nas {
        hardware ethernet aa:bb:cc:dd:ee:ff;
        fixed-address 192.168.50.2;
  }

  host printer {
        hardware ethernet bb:cc:dd:ee:ff:aa;
        fixed-address 192.168.50.3;
  }


}


```

named.conf.options:
```
options {
        directory "/var/cache/bind";

        forwarders {
                192.168.50.1;   // my Router
                208.67.222.222; //OpenDNS Primary
                208.67.222.220; //OpenDNS Secondary
                8.8.8.8;        //google DNS Primary
                8.8.4.4;        //google DNS Secondary
        };

        auth-nxdomain no;    # conform to RFC1035

        listen-on-v6 { none; };

        listen-on{
                192.168.50.1;
                127.0.0.1;
        //      192.168.60.1;
        };

        recursion yes;

        query-source address * port 53;

        dnssec-enable no;
        dnssec-validation no;
}
```

named.conf.local
```
key DDNS_UPDATE_VLAN50 {
        algorithm HMAC-SHA512;
        secret "key==";
};

acl "home.sk.lan" { 192.168.50.0/24; 127.0.0.1; };

controls {
  inet 127.0.0.1 port 953

  allow { 127.0.0.1; 192.168.50.1; }
  keys { DDNS_UPDATE_VLAN50;};

};

zone "home.sk.org" {
     type master;
     notify no;
     file "/var/cache/bind/db.home.sk.org";
     allow-update { key DDNS_UPDATE_VLAN50; };
};

zone "50.168.192.in-addr.arpa" {
     type master;
     notify no;
     file "/var/cache/bind/db.192.168.50";
     allow-update { key DDNS_UPDATE_VLAN50; };
};

```

my zone files:
```
root@router:/var/cache/bind# ls -la
insgesamt 16
drwxrwxr-x 2 root bind 4096 Aug 15 19:15 .
drwxr-xr-x 9 root root 4096 Aug 14 17:57 ..
lrwxrwxrwx 1 root bind   36 Aug 13 19:29 db.192.168.50 -> /etc/bind/zones/vlan50/db.192.168.50
lrwxrwxrwx 1 root bind   39 Aug 13 19:29 db.home.sk.org -> /etc/bind/zones/vlan50/db.home.sk.org
```

my dhclient.conf tells the clients to sent their hostname and the zone content is pretty standard with two static and working entries for nas and printer.

---

