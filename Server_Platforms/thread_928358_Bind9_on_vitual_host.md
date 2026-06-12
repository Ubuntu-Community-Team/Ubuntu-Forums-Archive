---
title: "Bind9 on vitual host"
date: 2008-09-23
forum: Server Platforms
---

### Post by amai on 2008-09-23
How do you configure bind on virtual host.
i.e you have 3 sites on the same server ?
I have a static ip address from isp

---

### Post by pdwerryhouse on 2008-09-24
You'll need a zone for each domain, and an A record for each, pointing at the same IP address.

Eg,

/etc/bind/site1.com:
```

@    IN   SOA   site1.com.  root.site1.com. ( 5 604800 8640 2419200 604800)

@    IN   A     10.1.20.1
www  IN   A     10.1.20.1

```

/etc/bind/site2.com:
```

@    IN   SOA   site2.com.  root.site2.com. ( 5 604800 8640 2419200 604800)

@    IN   A     10.1.20.1
www  IN   A     10.1.20.1

```

(and the same once again for the third site). Replace 10.1.20.1 with your own IP address, and don't forget to add zone entries for your files in /etc/bind/named.conf.local

---

### Post by amai on 2008-09-24
OK i went to /etc/bind/site1.com
and it was empty, nothing was in there
so I just need to add the above info (but changing ip address)
Is that correct.

2...
TO add zone entries for my files in /etc/bind/named.conf.local.
how do i do that for three sites.
Just list them one after the other?

Thanks

---

### Post by pdwerryhouse on 2008-09-24
"site1.com" and "site2.com" are example names. Replace them with the real domain names that you will be using.

Then, in named.conf.local, put:

```

zone "site1.com" {
        type master;
        file "/etc/bind/site1.com";
};

zone "site2.com" {
        type master;
        file "/etc/bind/site2.com";
};

```

---

### Post by amai on 2008-09-26
Followed above now I am getting an error message
rndc: connect failed: 127.0.0.1#953: connection refused.

When i do the following command
/etc/init.d/bind9 restart

Have restart still getting the same error.

---

### Post by amai on 2008-09-28
Resolved it was a typo.....

Thanks guys

solution
run command
sudo named -g -p 53

it will tell you the COZ of the error
then just go correct it

---

