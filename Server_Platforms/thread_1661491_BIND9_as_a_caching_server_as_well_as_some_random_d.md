---
title: "BIND9 as a caching server as well as some random domains"
date: 2011-01-06
forum: Server Platforms
---

### Post by iiz on 2011-01-06
I have installed BIND9 and it is currently functioning fine as a caching server. I would like it to remain this way but i would also like to include some custom domain resolutions for example:

test.com -> 10.0.1.11
server.com -> 10.0.1.12

I can't quite figure out how to get this done, I have tried adding zones for each:

```

zone "test.com" IN {
        type master;
        file "/etc/bind/db.test.com";
};

```


/etc/bind/db.test.com
```

;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     test.com. admin.test.com. (
                              1         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
test    IN      A       10.0.1.11

```

I have a a whole bunch of locally hosted sites that I would like to use dns for. I was hoping for an easier way to accomplished this like just adding a list of resolutions like the db.root file has, I also tried adding them there on the off chance it would work.

Thank you,

Nick

---

### Post by aceofspades686 on 2011-01-07
Something I would like to stress before you go into this, if you only have one or two computers you want to be able to see the websites from, its much simpler to just add the url to the hosts file.

That said, I just recently set up something similar to what you want for my home network.  While I don't have an specific advice to give you, I determined most of what I needed to do from [http://howtoforge.com/installing-an-ubuntu8.04-dns-server-with-bind-p4](http://howtoforge.com/installing-an-ubuntu8.04-dns-server-with-bind-p4) particularly steps 11 and 12.

---

### Post by iiz on 2011-01-07
> **aceofspades686 said:**
> Something I would like to stress before you go into this, if you only have one or two computers you want to be able to see the websites from, its much simpler to just add the url to the hosts file.

That said, I just recently set up something similar to what you want for my home network.  While I don't have an specific advice to give you, I determined most of what I needed to do from [http://howtoforge.com/installing-an-ubuntu8.04-dns-server-with-bind-p4](http://howtoforge.com/installing-an-ubuntu8.04-dns-server-with-bind-p4) particularly steps 11 and 12.

Thank you for the reply!

Tried this and it didn't quite work as I had wanted it to.

This is the tm.local.db file. when attempting to access test.com it does not work, which is apparent without trying to access it. The only things that work are the subdomains of tm.local. My goal was to have a list of random domains and not use the zone "." so for example only be authoritative for test.com and not google.com.

```

$TTL 1500
@  IN SOA server1.tm.local. root (
                             2007062703        ;serial
                             28800             ;refresh
                             3600              ;retry
                             604800            ;expire
                             38400 )           ;minimum 25 minutes
tm.local.      IN      NS      server1.tm.local.
server1        IN      A       192.168.0.100
webserver1     IN      A       192.168.0.103
webserver2     IN      A       192.168.0.104
loadb1         IN      A       192.168.0.101
loadb2         IN      A       192.168.0.102
test.com        IN      A       10.0.1.11
tm.local.      IN      MX      10    server1.tm.local.

```

Also right now I use host files to handle those routes, but it's really difficult to keep up with updating them all since we have a lot of machines on our network. It should have been setup to a non-existent TLDs like .loc rather than using real TLDs like .com.

Thank

nick

---

### Post by iiz on 2011-01-07
[Erased] Double posted, sorry.

---

### Post by aceofspades686 on 2011-01-07
Well, I'm still sort of new to DNS configuration, but maybe this will be of some help.  These are my configuration files (the pertinent ones) that allow me to connect to subdomains of eclair.acenet (all on my same server at 192.168.1.100) from anywhere within my internal network.

named.conf.local:
```
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "eclair.acenet" {
        type master;
        file "/etc/bind/db.eclair.acenet";
};
```

db.eclair.acenet:
```

$TTL    604800
@       IN      SOA     ns1.eclair.acenet   root.eclair.acenet (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns1
ns1     IN      A       192.168.1.100
torrent IN      A       192.168.1.100
main    IN      A       192.168.1.100
kana    IN      A       192.168.1.100
```

I seem to remember something about anytime changes are made the serial number needs to be incremented, but unfortunately I can't seem to find that any more.  Hopefully if this doesn't help someone with a bit more DNS experience can step in.

---

### Post by iiz on 2011-01-10
aceofspades686 Thanks for posting you configuration, I was playing with it for a while.

I do not think what I want to do is possible. BIND simply doesn't seem like it supports a random list of A records for different single domains and subdomains. I have a sneaking suspicion that it may work with a different type setting in the zone declaration, but I do not have the time to do trial and error testing :(.

So what I have settled on is the following, which I still have no idea how to do.

I would like to setup one subdomain, beta.example.com, to point to 10.0.1.11 the remaining subdomains should route normally so [www.example.com](www.example.com) should catch a WAN IP as should ftp.example.com.

I have tried many ways using the zone db files, but unfortunately I cannot seem to get this to work either. I know it is possible there is no way one of the top open source DNS server doesn't support such configuration.


Thank you for the help,

Nick

---

### Post by Ed_Ziffel on 2011-01-10
I also am new to this but am having all the same issues with getting my server to do the same things. Found a really good article at [http://www.aboutdebian.com/dns.htm](http://www.aboutdebian.com/dns.htm).  

[http://www.aboutdebian.com/dns.htm]("http://www.aboutdebian.com/dns.htm")

It also pointed to me to a couple of 300 page plus books on the subject.

---

### Post by iiz on 2011-01-10
> **Ed_Ziffel said:**
> I also am new to this but am having all the same issues with getting my server to do the same things. Found a really good article at [http://www.aboutdebian.com/dns.htm](http://www.aboutdebian.com/dns.htm).  

[http://www.aboutdebian.com/dns.htm]("http://www.aboutdebian.com/dns.htm")

It also pointed to me to a couple of 300 page plus books on the subject.

Thank you, i'll have a look at this tomorrow.

---

