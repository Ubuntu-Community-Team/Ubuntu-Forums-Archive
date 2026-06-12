---
title: "Bind9 DNS with multidomain multiMX issues"
date: 2010-04-10
forum: Server Platforms
---

### Post by nyu2007 on 2010-04-10
Dear All,

I setup an DNS Bind9 with 3 domains and host mail zimbra for 3 domain on it.

Hostname: zmail.micro.net

Three domain

A.COM
B.COM
C.COM

db.a.com
```
$ORIGIN .
$TTL 604800
a.com.      IN      SOA     zmail.micro.net.        admin.micro.net$
                        070725  ;
                        604800  ;
                        86400   ;
                        2419200 ;
                        604800 )
;
        IN      NS      zmail.micro.net.
        IN      MX      10      mail.a.com.
zmail.micro.net IN      A       192.168.0.1
$ORIGIN a.com.
```


```
$ORIGIN .
$TTL 604800
b.com.      IN      SOA     zmail.micro.net.        admin.micro.net$
                        070725  ;
                        604800  ;
                        86400   ;
                        2419200 ;
                        604800 )
;
        IN      NS      zmail.micro.net.
        IN      MX      10      mail.b.com.
zmail.micro.net IN      A       192.168.0.1
$ORIGIN b.com.
```


```
$ORIGIN .
$TTL 604800
c.com.      IN      SOA     zmail.micro.net.        admin.micro.net$
                        070725  ;
                        604800  ;
                        86400   ;
                        2419200 ;
                        604800 )
;
        IN      NS      zmail.micro.net.
        IN      MX      10      mail.c.com.
zmail.micro.net IN      A       192.168.0.1
$ORIGIN c.com.
```

I can nslookup to zmail.micro.com, dig mx record of 3 domain.
But when I send mail it said **host or domain name not found. name service error name=zmail.micro.net type=a: host not found try again**

I known that is Bind9 issue. What happen with my DNS Server???

Regards,
NyU

---

### Post by Bachstelze on 2010-04-10
You can't define an A record for zmail.micro.net. in a zone file for a.com.. Does the micro.net. domain belong to you?

---

### Post by nyu2007 on 2010-04-10
Thanks Bachstelze,

Yes. and this is system for testing. Could you help me, pls?

Regards,
NyU

---

### Post by Bachstelze on 2010-04-10
Then you need to create another zone file for domain micro.net., ant your A record for zmail.micro.net. will go there.

---

### Post by Skidbladnir on 2010-04-10
And "admin.micro.net" is invalid.  It HAS to end with a period.  Otherwise, it interprets it as admin.micro.net.a.com.  It's why "www IN A blah" works; Full domains HAVE to have a period at the end.

---

