---
title: "Bind9 Dns Host record for 'domain.com' not 'something.domain.com'"
date: 2008-07-12
forum: Server Platforms
---

### Post by oleskiwt on 2008-07-12
Hello,

I've just set up ubuntu server and got dns running on my domain oleskiw.ca.  I setup the froward zone db.oleskiw.ca:

```

example.ca.      IN      SOA     ns1.example.ca. admin.example.ca. (
        2006081401
        28800
        3600
        604800
        38400
)

example.ca.      IN      NS              ns1.example.ca.
example.ca.      IN      MX     10       mta.example.ca.

www             IN      A       24.xx.29.155
mta             IN      A       24.xx.29.155
frosty          IN      A       24.xx.29.155
ns1             IN      A       24.xx.29.155
ns2             IN      A       24.xx.29.155
ftp             IN      A       24.xx.29.155

```

it works like it should.  ping [www.oleskiw.ca](www.oleskiw.ca) hits 24.xx.29.155.
but I want to create a host record so that ping oleskiw.ca hits 24.xx.29.155.  how do I do this? the zone config file syntax seems like it needs characters to work.  i've done this before in windows server 2003 and 2008

thanks for the help, im sure the solution is easy
-tim

---

### Post by RealPSL on 2008-07-13
Adding the following will put a record for "example.com"

```
@  IN   A 24.xx.29.155
```

You can do the same thing with

```
example.com.  IN   A 24.xx.29.155
```

Obviously you need replace example.com with your registered domain named. More information is available here. 

[http://doc.ubuntu.com/ubuntu/serverguide/C/dns-configuration.html](http://doc.ubuntu.com/ubuntu/serverguide/C/dns-configuration.html)

---

