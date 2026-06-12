---
title: "Trouble with Bind DNS server"
date: 2008-05-04
forum: Server Platforms
---

### Post by lusis89 on 2008-05-04
Hello,
I'm trying to set up a primary (authoritative) dns server for a domain I own, the domain is cuttr.info, and i want my nameserver to be ns1.lusenti.com. The domain cuttr.info is already delegated to ns1.lusenti.com and to a secondary (backup) server ns2.afraid.org.

The problem is that when I query my dns server at ns1.lusenti.com for any cuttr.info (from a command-line using dig) this is the answer:
> 
dig @lusenti.com any cuttr.info

; <<>> DiG 9.4.2 <<>> @lusenti.com any cuttr.info
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: **REFUSED**, id: 18128
;; flags: qr rd; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0
;; WARNING: recursion requested but not available

;; QUESTION SECTION:
;cuttr.info.                    IN      ANY

;; Query time: 118 msec
;; SERVER: 92.243.11.142#53(92.243.11.142)
;; WHEN: Sun May  4 14:20:16 2008
;; MSG SIZE  rcvd: 28


DnsStuff reports "Broken dns server: Reports that it refuses to respond!" at [http://www.dnsstuff.com/tools/traversal.ch?domain=cuttr.info&type=A]("http://www.dnsstuff.com/tools/traversal.ch?domain=cuttr.info&type=A")  ([http://www.dnsstuff.com/tools/traversal.ch?domain=cuttr.info&type=A&token=1450e83b5a6f545b2a120a852d787019](http://www.dnsstuff.com/tools/traversal.ch?domain=cuttr.info&type=A&token=1450e83b5a6f545b2a120a852d787019)).

This is my  /etc/bind/named.conf
```

acl afraid {
        ns2.afraid.org;
        };
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

*include "/etc/bind/named.conf.local";*

key rndc-key {
        algorithm hmac-md5;
        secret "9qKaCYYiij50qfvS5qGIvg==";
        };

```

/etc/bind/named.conf.local is
```

zone "cuttr.info" {
        type master;
        file "/etc/bind/zones/cuttr.info.db";
        };

```

/etc/bind/zones/cuttr.info.db is
```

cuttr.info.      IN      SOA     ns1.lusenti.com. simone.lusenti.com. (
                                                        2006081401
                                                        28800
                                                        3600
                                                        604800
                                                        38400
 )

cuttr.info.       IN      NS              ns1.lusenti.com.
cuttr.info.       IN      MX     10       92.243.11.142.

www              IN      A       92.243.11.142
ns1              IN      A       92.243.11.142

```

What's wrong:confused:?

Thanks

---

### Post by Webdemic on 2008-05-06
Are you behind a firewall? If so, ensure that the necessary ports are open. Are you hosting your own domain names? In my case, I had to register my DNS servers with godaddy.com (the company I purchased my domain name from) for it to work.

Also, I assume you have tried "sudo /etc/init.d/bind9 start" to make sure everything is running?

---

### Post by lusis89 on 2008-05-06
> **Webdemic said:**
> Are you behind a firewall? If so, ensure that the necessary ports are open. Are you hosting your own domain names? In my case, I had to register my DNS servers with godaddy.com (the company I purchased my domain name from) for it to work.

Also, I assume you have tried "sudo /etc/init.d/bind9 start" to make sure everything is running?

Thanks for the reply,
My server is a vps at gandi.net, ther is no firewall.
I have registered my domain names with godaddy (either cuttr.info and lusenti.com), delegated cuttr.info to ns1.lusenti.com, ns2.afraid.org and added ns1.lusenti.com (that I want to be my nameserver) to "Host Summary" in the Domain control center as described in an official FAQ.

I've followed some how-to but without success.
Now I'm using webmin to manage bind; I have also tried to remove (--purge) and reinstall bind9... but nothing changed...

Thanks

---

### Post by Paulparkers on 2008-05-06
Please check your Virtual host, might be it can be wrong. wheather it's correct please reastart your network once and after restarting your network restart the named.conf configurations and than check your firewall....
=================================================================
Paul Parker

New York Immigration Lawyer Marina Shepelsky, located in Brooklyn, assists clients from the New York metro area and across the United States in all immigration and naturalization matters [http://www.e-us-visa.com](http://www.e-us-visa.com)

---

### Post by lusis89 on 2008-05-06
> **Paulparkers said:**
> Please check your Virtual host, might be it can be wrong. wheather it's correct please reastart your network once and after restarting your network restart the named.conf configurations and than check your firewall....


What has to do VirtualHost with bind:confused:?

---

