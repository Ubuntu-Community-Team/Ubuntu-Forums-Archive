---
title: "Problem with BIND9, can't resolve a local name with the browser"
date: 2018-09-20
forum: Server Platforms
---

### Post by othin2 on 2018-09-20
Hi all, i have a server debian 9 with bind 9 in slave, is correctly running but only one thing is wrong, if i ping (on the server) the example.domainname.local.. the ping is ok and resolve the name but if i go on my browser (chromium,firefox ecc) i can't resolve the name [http://example.domainname.local](http://example.domainname.local), if in my "resolv.conf" i use the ip of my master, all is ok...


i don't find any error on the logs


the sync from the master to slave i think is ok 
My config files are:


**names.conf**
```
// This is the primary configuration file for the BIND DNS server named.//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the 
// structure of BIND configuration files in Debian, *BEFORE* you customize 
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local




include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.default-zones";

```

**names.conf.options**

```

acl goodclients {
        192.168.100.0/24;
        192.168.148.0/22;
        localhost;
        localnets;
};


options {


directory "/var/cache/bind";


        recursion yes;
        allow-query { goodclients; };


        forwarders {
                1.1.1.1;
                1.0.0.1;
        };


        forward only;
    
    dnssec-enable yes;
    dnssec-validation auto;
        dnssec-lookaside auto;


        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };


};




logging {
    channel default_file {
        file "/var/log/bind/default.log" versions 3 size 5m;
        severity dynamic;
        print-time yes;
    };
    channel general_file {
        file "/var/log/bind/general.log" versions 3 size 5m;
        severity dynamic;
        print-time yes;
    };
    channel database_file {
        file "/var/log/bind/database.log" versions 3 size 5m;
        severity dynamic;
        print-time yes;
    };
    channel security_file {
        file "/var/log/bind/security.log" versions 3 size 5m;
        severity dynamic;
        print-time yes;
    };
    channel config_file {
        file "/var/log/bind/config.log" versions 3 size 5m;
        severity dynamic;
        print-time yes;
    };
    channel resolver_file {
        file "/var/log/bind/resolver.log" versions 3 size 5m;
        severity dynamic;
        print-time yes;
    };
    channel xfer-in_file {
        file "/var/log/bind/xfer-in.log" versions 3 size 5m;
        severity dynamic;
        print-time yes;
    };
    channel xfer-out_file {
        file "/var/log/bind/xfer-out.log" versions 3 size 5m;
        severity dynamic;
        print-time yes;
    };
    channel notify_file {
        file "/var/log/bind/notify.log" versions 3 size 5m;
        severity dynamic;
        print-time yes;
    };
    channel client_file {
        file "/var/log/bind/client.log" versions 3 size 5m;
        severity dynamic;
        print-time yes;
    };
    channel unmatched_file {
        file "/var/log/bind/unmatched.log" versions 3 size 5m;
        severity dynamic;
        print-time yes;
    };
    channel queries_file {
        file "/var/log/bind/queries.log" versions 3 size 5m;
        severity dynamic;
        print-time yes;
    };
    channel network_file {
        file "/var/log/bind/network.log" versions 3 size 5m;
        severity dynamic;
        print-time yes;
    };
    channel update_file {
        file "/var/log/bind/update.log" versions 3 size 5m;
        severity dynamic;
        print-time yes;
    };
    channel dispatch_file {
        file "/var/log/bind/dispatch.log" versions 3 size 5m;
        severity dynamic;
        print-time yes;
    };
    channel dnssec_file {
        file "/var/log/bind/dnssec.log" versions 3 size 5m;
        severity dynamic;
        print-time yes;
    };
    channel lame-servers_file {
        file "/var/log/bind/lame-servers.log" versions 3 size 5m;
        severity dynamic;
        print-time yes;
    };


    category default { default_file; };
    category general { general_file; };
    category database { database_file; };
    category security { security_file; };
    category config { config_file; };
    category resolver { resolver_file; };
    category xfer-in { xfer-in_file; };
    category xfer-out { xfer-out_file; };
    category notify { notify_file; };
    category client { client_file; };
    category unmatched { unmatched_file; };
    category queries { queries_file; };
    category network { network_file; };
    category update { update_file; };
    category dispatch { dispatch_file; };
    category dnssec { dnssec_file; };
    category lame-servers { lame-servers_file; };
};

```

**name.conf.local**

```

 type slave; 
 masters { [IPMASTER]; };
 file "/var/cache/bind/db.domain.local";
};


zone "100.168.192.in-addr.arpa" {
             type slave;
             file "/var/cache/bind/db.192";
             masters { [IPMASTER]; };
        };


// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

```

**name.conf.default-zones**

```

// prime the server with knowledge of the root servers
zone "." {
    type hint;
    file "/etc/bind/db.root";
};


// be authoritative for the localhost forward and reverse zones, and for
// broadcast zones as per RFC 1912


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


#zone "255.in-addr.arpa" {
#    type master;
#    file "/etc/bind/db.255";
#};

```

My permission for the files in /etc/bind/ are:

```
-rw-r--r--   1 root root 3,9K set 12 11:27 bind.keys
-rw-r--r--   1 root root  237 set 12 10:46 db.0
-rw-r--r--   1 root root  271 set 12 10:46 db.127
-rw-r--r--   1 root root  237 set 12 10:47 db.255
-rw-r--r--   1 root root  353 gen 15  2018 db.empty
-rw-r--r--   1 root root  270 set 12 10:46 db.local
-rw-r--r--   1 root root 3,0K set 12 10:48 db.root
-rw-r--r--   1 root root 3,1K gen 15  2018 db.root.dpkg-dist
-rw-r--r--   1 root bind  463 set 20 15:17 named.conf
-rw-r--r--   1 root bind  494 set 20 15:05 named.conf.default-zones
-rw-r--r--   1 root bind  444 set 14 10:08 named.conf.local
-rw-r--r--   1 root bind  165 gen 15  2018 named.conf.local.dpkg-dist
-rw-r--r--   1 root bind 3,6K set 20 15:35 named.conf.options
-rw-r--r--   1 root root 1,3K gen 15  2018 zones.rfc1918

```
permission in /var/cache/bind/ are:

```
-rw-r--r--  1 bind bind  293 set 20 16:16 db.192
-rw-r--r--  1 bind bind 8,1K set 20 16:04 db.domain.local
-rw-r--r--  1 bind bind    0 set 14 10:05 db-eiJocqnH
-rw-r--r--  1 bind bind 2,0K set 20 15:58 managed-keys.bind
-rw-r--r--  1 bind bind  512 set 20 15:58 managed-keys.bind.jnl

```


if anyone can help would be great XD
Thanks all

---

