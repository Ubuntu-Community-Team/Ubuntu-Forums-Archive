---
title: "Bind9 DNS Server - can anyone suggest why mine isn't working?"
date: 2012-12-04
forum: Server Platforms
---

### Post by Toriku on 2012-12-04
I read that a DNS server can be used on a LAN network to point to internal servers for people on the network, and is also useful for rerouting employees who try to access websites that aren't conducive to a work environment;

 For now I'm trying to set up a simple DNS to point to two servers on the LAN and then point the rest of the traffic to my ISPs DNS and GoogleDNS... However, when I run nslookup, I get an error, and attempting to set my computers DNS to the DNS server kills my internet connection with DNS failure errors.

```

** server can't find mydomain.com.myDNS.com: SERVFAIL
```

 I am also unclear if I need to have purchased a domain to point to the DNS, but I understood that DNS was a great way to play with as many domains as you liked without having to purchase them all, which appealed to me.

 Can anyone suggest why my DNS isn't working? Thanks.

---

### Post by Rakeshvijayan on 2012-12-04
> **Toriku said:**
> 
 However, when I run nslookup, I get an error, and attempting to set my computers DNS to the DNS server kills my internet connection with DNS failure errors.



 Can anyone suggest why my DNS isn't working? Thanks.

Dont worry man I will help you to resolve this issue .before that will you elaborate configuration setting that you are don on the DNS  server .ok I will share my setting to you dear 
sudo vi /etc/bind/named.conf.option
> 
options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See [http://www.kb.cert.org/vuls/id/800113](http://www.kb.cert.org/vuls/id/800113)

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

         forwarders {
                10.0.0.0;
         };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};



first you need to copy the file db.127 on bind folder to db.yoursite.com and edit like below
your site name must be in db.yoursite.com like this .This is the forward look up zone location 
sudo nano /etc/bind/db.yoursite.com
> 
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     servername.yoursite.com. root.yoursite.com. (
                              5         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.yoursite.com. //NAME SERVER 
@       IN      A       *.*.*.*
@       IN      AAAA    ::1
ns      IN      A        *.*.*.*
ns1     IN      A        *.*.*.* //ns1 is the webserver 
ns8     IN      A        *.*.*.*
rivaus  IN      A        *.*.*.*
www     IN      CNAME   ns1
 This is reverse zone location 
first you need to copy the file db.127 on bind folder to db.you ip first part eg: db.101 then edit db.101

> 
;
; BIND reverse data file for local loopback interface
;.
$TTL    604800
@       IN      SOA     ns.yoursite.com. root.yoursite.com. (
                              4         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.
100     IN      PTR     ns.yoursite.cm
200     IN      PTR     ns1.yoursite.cm
8       IN      PTR     ns8.yoursite.cm
77      IN      PTR     rivaus.yoursite.cm

you need to edit resolve.conf file on your server 

Thanks this may help .

---

### Post by Toriku on 2012-12-04
thankyou for the help, does the "db.yoursite.com" need to refer to a domain I have paid to register? Or can I just put in a domain for the local network?

---

### Post by Toriku on 2012-12-05
I am now getting the "9(NOAUTH)" error...

---

### Post by Rakeshvijayan on 2012-12-06
> **Toriku said:**
> thankyou for the help, does the "db.yoursite.com" need to refer to a domain I have paid to register? Or can I just put in a domain for the local network?

Shure you can put this in your local network.if you want to access site from outside world you must have register website name on registrar  and you must have public ip configure to your server .
There is mistake on my above answer  you have do some thing on named.conf.local file

there you must enter the forward and reverse lookup zone location I forget to post there .if you want I will do it for you 

Thanks

---

### Post by Toriku on 2012-12-06
named.conf:

> include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.default-zones";

logging {
        channel custom {
                file "/var/log/named";
                print-time yes;                 #  timestamps
                print-category yes;
        };


named.conf.local:

> 
zone "office.lan" {
        type master;
        file "/etc/bind/db.office.lan";
};

zone "1.168.192.in-addr.arpa" {
        type master;
        notify no;
        file "/etc/bind/db.192";
};




named.conf.options:
> options {
        directory "/var/cache/bind";
        forwarders {
                8.8.8.8;        //Google
                8.8.4.4;        //Google
        };
        //=====================================================================$
        // If BIND logs error messages about the root key being expired,
        // you will need to update your keys.  See [https://www.isc.org/bind-keys](https://www.isc.org/bind-keys)
        //=====================================================================$
        dnssec-validation auto;

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
}



zones/office.lan.db:
> 
$ORIGIN .
$TTL 86400      ; 1 day
office.lan. IN SOA computer2.office.lan. me.office.lan. (
    2008080901 ; serial
    8H ; refresh
    4H ; retry
    4W ; expire
    1D ; minimum
)
; NS indicates that ubuntu is the name server on home.lan
; MX indicates that ubuntu is (also) the mail server on home.lan
office.lan. IN NS computer2.home.lan.
office.lan. IN MX 10 computer2.home.lan.

$ORIGIN office.lan.

; Set the address for localhost.office.lan
localhost    IN A 127.0.0.1

; Set the hostnames in alphabetical order
computer1        IN A 192.168.1.84
computer2        IN A 192.168.1.65
computer3        IN A 192.168.1.74



zones/rev.0.168.192.in-addr.arpa:
> 
; IP Address-to-Host DNS Pointers for the 192.168.0 subnet
@ IN SOA computer2.office.lan. joseph.office.lan. (
    2008080901 ; serial
    8H ; refresh
    4H ; retry
    4W ; expire
    1D ; minimum
)
; define the authoritative name server
           IN NS computer2.office.lan.
; our hosts, in numeric order
84         IN PTR computer1.office.lan.
65         IN PTR computer2.office.lan.
74         IN PTR computer3.office.lan.



might have missed a file out, but these are the files I have been fiddling with a lot, can you spot where I may have gone wrong? Thanks

---

### Post by Rakeshvijayan on 2012-12-06
> zone "office.lan" {
        type master;
        file "/etc/bind/db.office.lan";
};

zone "1.168.192.in-addr.arpa" {
        type master;
        notify no;
        file "/etc/bind/db.192";
};here you using file location is not same as you taken (file "/etc/bind/db.office.lan";)

in you zone entry is not correct .....may you took the path /etc/bind/zones/db.office.lan .....
any way please forget all things and follow the offical pages of ubuntu guide 
[https://help.ubuntu.com/12.04/serverguide/dns-configuration.html](https://help.ubuntu.com/12.04/serverguide/dns-configuration.html) dont make any other folder like zones ect .first you need to learn whole things then you can do so .if you do so  you need to change paths on bind files .for better setting first you need to configure your ip address in terminal 
location : sudo nano /etc/network/interface 
AND 
you need to edit the resolve.conf sudo nano /etc/resolve.conf
type : search yoursite.com. (dont forget to insert dot after the name)
            nameserver yourserver ipaddress


use your isp given ipaddress in named.conf

---

### Post by Toriku on 2012-12-06
thankyou, Rakeshvijayan, I will try that now, I'll let you know how it goes

---

### Post by Toriku on 2012-12-06
so far not great... I got as far as the forward zone file, put in

> sudo service bind9 restart

and I got the following error:

> 
rndc: connect failed: 127.0.0.1#953: connection refused		[ OK ]
 * Starting domain name service... bind9			[fail]


I'll try again on a clear installation tomorrow...

---

### Post by Rakeshvijayan on 2012-12-07
What is your current status ......?

---

### Post by Toriku on 2012-12-12
current status is that I've got it working!
I have the caching server set up, and a primary nameserver, it appears to be working atm! Thankyou for your help!

---

