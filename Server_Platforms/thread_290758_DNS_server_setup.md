---
title: "DNS server setup"
date: 2006-11-01
forum: Server Platforms
---

### Post by Bachstelze on 2006-11-01
So I installed and configured BIND 9 on Dapper following [this howto](http://ubuntuforums.org/showthread.php?t=236093) and I get the same error than the one mentioned on post #4 so obviously it won't work...

Any ideas ?

---

### Post by bmillsap on 2006-11-01
I'm not an expert, but I have it working on my install.  Did you configure the named.conf.options file with your ISPs DNS under "forwarders"?  My issues were all with setting up DHCP updates for my interal network, I think just using BIND as a caching DNS worked more or less out of the box for me, possibly only with this one change ("forwarders"), I can't remember for sure.

---

### Post by Bachstelze on 2006-11-01
Well actually what I want to do is to reach each machine on my network with myhost.mydomain.org and that's where it doesn't work. Forwarders are OK since I can ping the outside world using my DNS.

---

### Post by bmillsap on 2006-11-01
Sorry, I must have read the wrong post in the thread you referenced.  Do you use static or dynamic IPs for your machines?  Maybe post your named.conf.local and whatever db. files are referenced there.

---

### Post by Bachstelze on 2006-11-01
I use static, here are the files, as you can see, it's a no-ip.org domain name but I can't see any reason why it wouldn't work :


**named.conf.local**

```

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

# This is the zone definition. replace example.com with your domain name
zone "fkraiem.no-ip.org" {
        type master;
        file "/etc/bind/zones/fkraiem.no-ip.org.db";
        };

# This is the zone definition for reverse DNS. replace 0.168.192 with your netw$
zone "1.168.192.in-addr.arpa" {
     type master;
     file "/etc/bind/zones/rev.1.168.192.in-addr.arpa";
};
```


**fkraiem.no-ip.org.db**

```

// replace example.com with your domain name. do not forget the . after the domain name!
// Also, replace ns1 with the name of your DNS server
fkraiem.no-ip.org.      IN      SOA     mika.fkraiem.no-ip.org. admin.fkraiem.no-ip.org. (
// Do not modify the following lines!
                                                        2006081401
                                                        28800
                                                        3600
                                                        604800
                                                        38400
 )

// Replace the following line as necessary:
// ns1 = DNS Server name
// mta = mail server name
// example.com = domain name
fkraiem.no-ip.org.      IN      NS              mika.fkraiem.no-ip.org.
fkraiem.no-ip.org.      IN      MX     10       mika.fkraiem.no-ip.org.

// Replace the IP address with the right IP addresses.
www              IN      A       192.168.1.2
home             IN      A       192.168.1.2
ftp              IN      A       192.168.1.2
miu              IN      A       192.168.1.2
mika             IN      A       192.168.1.3

```



**rev.1.168.192.in-addr.arpa**

```

//replace example.com with yoour domain name, ns1 with your DNS server name.
// The number before IN PTR example.com is the machine address of the DNS server. in my case, it's 1, as my IP address is 192.168.0.1.
@ IN SOA mika.fkraiem.no-ip.org. admin.fkraiem.no-ip.org. (
                        2006081401;
                        28800;
                        604800;
                        604800;
                        86400
)

                     IN    NS     mika.fkraiem.no-ip.org.
3                    IN    PTR    fkraiem.no-ip.org

```

---

### Post by bmillsap on 2006-11-01
One thing I notice, in my db file, the form of my first active line is:

(domain)      IN SOA (domain) (nameserver)

where you don't have the domain and nameserver at the end, you have the nameserver and something else (I think).  Also, I in fact do NOT have a period after the first (domain) in the line above, but I do after the second (domain) and (nameserver).  I think I copied that form from another sample file I found somewhere, don't know if it's right, but it is working.

---

### Post by Bachstelze on 2006-11-01
Same thing...

---

### Post by bmillsap on 2006-11-01
My db lines for my static machines don't have "IN A", they just have "A", like:

ubuntu1      A     192.168.1.107

---

### Post by Bachstelze on 2006-11-01
Nope, stil "unknown host". The funny thing is, when I use my DNS in /etc/resolv.conf I also get unknown host on ping fkraiem.no-ip.org while I don't when I use my ISPs.

---

### Post by bmillsap on 2006-11-01
Are you sure you're doing the lookups on your local DNS, and not your ISPs DNS?  

Here's my entire db file down to and including my first static machine:

$ORIGIN .
$TTL 604800     ; 1 week
mshomebem.com           IN SOA  mshomebem.com. ubuntu1.mshomebem.com. (
                                23         ; serial
                                604800     ; refresh (1 week)
                                86400      ; retry (1 day)
                                2419200    ; expire (4 weeks)
                                604800     ; minimum (1 week)
                                )
                        NS      ubuntu1.mshomebem.com.
$ORIGIN mshomebem.com.
gateway1                A       192.168.1.100

I don't think I added the $ORIGIN statements, I think BIND did that at some point, maybe when I started it talking to DHCP3, I'm not sure.

---

### Post by Bachstelze on 2006-11-01
Still "unknown host" :/ Could you please paste all your config files ?

---

### Post by bmillsap on 2006-11-01
Here's my named.conf.local:

include "/etc/bind/zones.rfc1918";
include "/etc/bind/rndc.key";

controls {
        inet 127.0.0.1 port 953
        allow { 127.0.0.1; 192.168.1.107; } keys {"rndc-key";
};
};

zone "mshomebem.com" {
        type master;
        check-names ignore;
        file "/etc/bind/db.network";
        allow-update {key "rndc-key";};
        notify yes;
};

zone "1.168.192.in-addr.arpa" {
        type master;
        check-names ignore;
        file "/etc/bind/db.1921681";
        allow-update {key "rndc-key";};
        notify yes;
};

Here's named.conf.options:
options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you might need to uncomment the query-source
        // directive below.  Previous versions of BIND always asked
        // questions using port 53, but BIND 8.1 and later use an unprivileged
        // port by default.

        query-source address * port 53;

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

        forwarders {
                192.168.0.1;
        };

        auth-nxdomain no;    # conform to RFC1035

};

---

### Post by bmillsap on 2006-11-01
Here's db.network referenced in name.conf.local.  Note that some of this (and some of the config entries above) are for DHCP updating of dynamic clients.

$ORIGIN .
$TTL 604800     ; 1 week
mshomebem.com           IN SOA  mshomebem.com. ubuntu1.mshomebem.com. (
                                23         ; serial
                                604800     ; refresh (1 week)
                                86400      ; retry (1 day)
                                2419200    ; expire (4 weeks)
                                604800     ; minimum (1 week)
                                )
                        NS      ubuntu1.mshomebem.com.
$ORIGIN mshomebem.com.
gateway1                A       192.168.1.100
nas-00-63-83            A       192.168.1.105
$TTL 10800      ; 3 hours
TIVO_24000008074BF68    A       192.168.1.117
                        TXT     "0088a2ebf770a3a666c25267dfe0ed8058"
$TTL 604800     ; 1 week
ubuntu1                 A       192.168.1.107

---

### Post by bmillsap on 2006-11-01
Here's the reverse lookup file.  I think this is everything that's changed from defaults:

$ORIGIN .
$TTL 604800     ; 1 week
1.168.192.in-addr.arpa  IN SOA  mshomebem.com. ubuntu1.mshomebem.com. (
                                16         ; serial
                                604800     ; refresh (1 week)
                                86400      ; retry (1 day)
                                2419200    ; expire (4 weeks)
                                604800     ; minimum (1 week)
                                )
                        NS      localhost.
$ORIGIN 1.168.192.in-addr.arpa.
100                     PTR     gateway1
105                     PTR     nas-00-63-83
107                     PTR     ubuntu1
$TTL 10800      ; 3 hours
117                     PTR     TIVO_24000008074BF68.mshomebem.com.

---

### Post by Bachstelze on 2006-11-01
Still not working, I guess that's just because of the no-ip domain...

---

