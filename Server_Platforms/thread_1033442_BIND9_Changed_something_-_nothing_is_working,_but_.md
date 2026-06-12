---
title: "BIND9 Changed something - nothing is working, but it was before"
date: 2009-01-07
forum: Server Platforms
---

### Post by francois.mdlh on 2009-01-07
Maybe I'm missing something silly.

I have BIND9 running on Ubuntu server 8.10, as a caching and primary. please take a look at my conf files. Also, I'm using OpenDNS forwarders.

/etc/bind/named.conf.options:

options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See [http://www.kb.cert.org/vuls/id/800113](http://www.kb.cert.org/vuls/id/800113)

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.
        // Below are the two open-dns server ips

        forwarders {
                208.67.222.222;
                208.67.220.220;
        };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};


/etc/bind/named.conf.local:


//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "example.com" {
        type master;
        file "/etc/bind/db.example.com";
};
zone "0.10.10.in-addr.arpa" {
        type master;
        notify no;
        file "/etc/bind/db.10";
};
logging {
    channel query.log {
        file "/var/log/query.log";
        // Set the severity to dynamic to see all the debug messages.
        severity debug 3;
    };

    category queries { query.log; };
    category config  { query.log; };
    category general { query.log; };

};



/etc/bind/named.conf:


// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the
// structure of BIND configuration files in Debian, *BEFORE* you customize
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local

include "/etc/bind/named.conf.options";

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

zone "255.in-addr.arpa" {
        type master;
        file "/etc/bind/db.255";
};

include "/etc/bind/named.conf.local";


/etc/bind/db.example.com:


;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ns1.example.com. admin.example.com. (
                         20090106002    ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL

@               IN      NS      ns1.example.com.
@               IN      A       10.10.0.11
ns1             IN      A       10.10.0.11

alpha           IN      A       10.10.0.11
gateway         IN      A       10.10.0.1
vaesx01         IN      A       10.10.0.20
vasvr01         IN      A       10.10.0.10
voip            IN      A       10.10.0.200
vpn             IN      A       10.10.0.1

fileserver      IN      CNAME   vasvr01
jira            IN      CNAME   vasvr01
teamcity        IN      CNAME   vasvr01
svn             IN      CNAME   vasvr01
fisheye         IN      CNAME   vasvr01
software-demo   IN      CNAME   vasvr01
www-demo        IN      CNAME   vasvr01
test-images     IN      CNAME   vasvr01
test-services   IN      CNAME   vasvr01
test-viewer     IN      CNAME   vasvr01

blog            IN      CNAME   example.wordpress.com
calendar        IN      CNAME   ghs.google.com
dev             IN      CNAME   ghs.google.com
developers      IN      CNAME   ghs.google.com
docs            IN      CNAME   ghs.google.com

testone         IN      CNAME   ghs.google.com
testexperimens  IN      CNAME   ghs.google.com
intranet        IN      CNAME   ghs.google.com
mail            IN      CNAME   ghs.google.com
exampleweb      IN      CNAME   ghs.google.com
wiki            IN      CNAME   ghs.google.com
www             IN      CNAME   ghs.google.com


/etc/bind/db.10:



;
; BIND reverse data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ns1.example.com. admin.example.com. (
                    20090106002         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL

@               IN      NS      ns1.
1               IN      PTR     ns1.example.com.

10.10.0.11      IN      PTR     alpha.example.com.
10.10.0.1       IN      PTR     gateway.example.com.
10.10.0.20      IN      PTR     vaesx01.example.com.
10.10.0.10      IN      PTR     vasvr01.example.com.
10.10.0.200     IN      PTR     voip.example.com.
10.10.0.1       IN      PTR     vpn.example.com.


/etc/resolv.conf:

domain example.com
search example.com

---

### Post by francois.mdlh on 2009-01-07
Sorry about the rotten formatting of the conf files!

---

### Post by francois.mdlh on 2009-01-07
I did find the following in /var/log/messages evertime I restart BIND:

Jan  7 15:51:48 alpha kernel: [ 1889.214967] type=1503 audit(1231365108.656:6): operation="capable" name="sys_resource" pid=4407 profile="/usr/sbin/named"
Jan  7 15:51:48 alpha kernel: [ 1889.223022] type=1503 audit(1231365108.666:7): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=103 name="/proc/4406/net/if_inet6" pid=4407 profile="/usr/sbin/named"
Jan  7 15:51:48 alpha kernel: [ 1889.250509] type=1503 audit(1231365108.696:8): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=103 name="/proc/4406/net/if_inet6" pid=4407 profile="/usr/sbin/named"

I also did the following to enable logging:

DNS Logging

1. nano /etc/bind/named.conf.local

logging {
channel query.log {
file "/var/log/query.log";
// Set the severity to dynamic to see all the debug messages.
severity debug 3;
};

category queries { query.log; };
};

2. Create and modify permissions on query.log
sudo touch /var/log/query.log
sudo chown bind /var/log/query.log

3. nano /etc/apparmor.d/usr.sbin.named

add
/var/log/query.log w,

4. cat /etc/apparmor.d/usr.sbin.named | sudo apparmor_parser -r

5. sudo /etc/init.d/bind9 restart

6. tail -f /var/log/query.log to view log.

Could this be causing a problem..?

---

### Post by francois.mdlh on 2009-01-07
So after some fiddling i finally have it all working. Correct zone files below:

/etc/bind/db.mydomain.com:

;
; BIND data file for mydomain.com zone
;
$TTL    604800
@               IN      SOA     ns1.mydomain.com. admin.mydomain.com. (
                                      5         ; Serial
                                 604800         ; Refresh
                                86400           ; Retry
                                2419200         ; Expire
                                604800 )        ; Negative Cache TTL
;nameservers

@               IN      NS      ns1.mydomain.com.
@               IN      A       10.10.0.11
ns1             IN      A       10.10.0.11


;mailservers we use google apps

@               MX      40      aspmx2.googlemail.com.
@               MX      50      aspmx3.googlemail.com.
@               MX      10      aspmx.l.google.com.
@               MX      20      alt1.aspmx.l.google.com.
@               MX      30      alt2.aspmx.l.google.com.

;local hosts

alpha           IN      A       10.10.0.11
somesvr         IN      A       10.10.0.10
vpn             IN      A       10.10.0.1

;local services

someservice     IN      CNAME   somesvr.mydomain.com.

;external services

www             IN      CNAME   ghs.google.com.
wiki            IN      CNAME   ghs.google.com.
blog            IN      CNAME   mydomain.wordpress.com.

/etc/bind/db.10: (our network is 10.10.0.0)

;
; BIND reverse data file for mydomain.com zone
;
$TTL    604800
@       IN      SOA     ns1.mydomain.com. admin.mydomain.com. (
                              5         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns1.
11      IN      PTR     ns1.mydomain.com.
11      IN      PTR     alpha.mydomain.com.
10      IN      PTR     somesvr.mydomain.com.
1       IN      PTR     vpn.mydomain.com.

In the reverse zone file, the first entry refers to the host part of the ip address:
10      IN      PTR     somesvr.mydomain.com.

here, 10 refers to the machine IP, 10.10.0.10

---

