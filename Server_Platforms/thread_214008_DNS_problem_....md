---
title: "DNS problem ..."
date: 2006-07-12
forum: Server Platforms
---

### Post by dbee on 2006-07-12
So, all my mails are going into the spam boxes of hotmail, yahoo, and gmail.
It seems that my reverse dns records aren't configured properly...

Can someone take a look at it here pls ? ...dns really isn't my speciality...

> 

 //My named.conf file ... on hostname india.eccindustries.info ... 72.232.183.2
// Boot file for englishteachingkorea name server

include "/etc/rndc.key";

controls {
       inet 127.0.0.1 port 953
               allow { 127.0.0.1; } keys { "rndckey"; };
};

options {
        directory "/var/named";
        query-source address * port 53;
        listen-on-v6 { none; };
                listen-on { 72.232.183.2; 127.0.0.1; };
};

zone "englishteachingkorea.com" in {
        type master;
        notify yes;
        file "zone/englishteachingkorea.com";
        allow-transfer {
                193.218.105.149; 195.234.42.1;
        };
};

zone "eccindustries.info" in {
        type master;
        notify yes;
        file "zone/eccindustries.info";
        allow-transfer {
                193.218.105.149; 195.234.42.1;
        };
};

zone "presumae.com" in {
        type master;
        notify yes;
        file "zone/presumae.com";
        allow-transfer {
                193.218.105.149; 195.234.42.1;
        };
};

My zone files ... 

[root@india zone]# cat 72.232.183
$TTL 86400
@     IN     SOA    india.eccindustries.info.     admin.eccindustries.info. (
                    2006042502 ; serial
                    8H       ; refresh after 6 hours
                    2H       ; retry after 1 hour
                    4W       ; expire after 1 week
                    1D )     ; minimum TTL of 1 day
;
; Name server
;
     IN     NS      india.eccindustries.info.
;
; Pointer Address
;
2    IN     PTR     india.eccindustries.info.


[root@india zone]# cat eccindustries.info
$ORIGIN eccindustries.info.
$TTL 3D
@       IN      SOA     india.eccindustries.info. admin.eccindustries.info. (
                2006042504
                8H
                2H
                4W
                1D )
;
; Name servers
;
            IN     NS     ns1.eccindustries.info.
;
; Mail server
;
            IN     MX     10     mail.eccindustries.info.
;
; Addresses for canonical names
;
india        IN     A       72.232.183.2
             IN     A       72.232.183.2
ns1          IN     A       72.232.183.2
server       IN     A       72.232.183.2
;
; Aliases
;
ftp          IN     CNAME   server
mail         IN     CNAME   server
www          IN     CNAME   server
;
; Secondary servers
;
@       IN    NS   ns0.xname.org.
@       IN    NS   ns1.xname.org.

[root@india zone]# cat englishteachingkorea.com
$ORIGIN englishteachingkorea.com.
$TTL 3D
@       IN      SOA     india.eccindustries.info. admin.india.eccindustries.info. (
                2006042504
                8H
                2H
                4W
                1D )
;
; Name servers
;
             IN     NS     ns1.eccindustries.info.
;
; Mail server
;
             IN     MX     10     mail.eccindustries.info.
;
; Addresses for canonical names
;
india        IN     A       72.232.183.2
             IN     A       72.232.183.2
ns1          IN     A       72.232.183.2
server       IN     A       72.232.183.2
;
; Aliases
;
ftp          IN     CNAME   server
mail         IN     CNAME   server
www          IN     CNAME   server
;
; Secondary servers
;
@             IN    NS   ns0.xname.org.
@             IN    NS   ns1.xname.org.


---

### Post by tonym on 2006-07-12
You don't appear to have an entry in your named.conf pointing to your reverse lookup zone.  Doing a reverse lookup on your IP address gives 2.183.232.72.reverse.layeredtech.com.

This may be the problem.  I'm interested in how you know this is the problem with Hotmail etc.  I have problems also even though my DNS is OK (I think!).

---

### Post by dbee on 2006-07-12
Hi tonym,

Yes, sorry, I left a little bit out .... 

zone "dara-teacher.info" in {
        type master;
        notify yes;
        file "zone/dara-teacher.info";
        allow-transfer {
                193.218.105.149; 195.234.42.1;
        };
};

zone "183.232.72.in-addr.arpa" in {
        type master;
        file "zone/72.232.183";
};

zone "0.0.127.in-addr.arpa" in {
        type master;
        file "zone/127.0.0";
};

zone "." in {
        type hint;
        file "root.hints";
};


... I have that in my named.conf as well...

As for the email issue. I'm fairly sure that hotmail and others spam email which isn't verifiable on a reverse lookup. Maybe there are some other issues too, with ip addresses classified as spam machines. But I need to fix this reverse dns issue first ...

---

