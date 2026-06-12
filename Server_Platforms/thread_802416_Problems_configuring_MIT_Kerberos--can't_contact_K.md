---
title: "Problems configuring MIT Kerberos--can't contact KDC"
date: 2008-05-21
forum: Server Platforms
---

### Post by joehill on 2008-05-21
Hi,

I'm trying to set up a kerberos 5 (MIT's krb5) server and I'm having problems getting it to find my KDC.

I can "sudo kadmin.local" and add principals and all that, but I can't locate the KDC with kadmin or kinit.  I get this error when I do "kinit":

> kinit(v5): Cannot contact any KDC for realm 'EXAMPLE.COM' while getting initial credentials

"kadmin" gives me this:

> kadmin: Cannot contact any KDC for requested realm while initializing kadmin interface

I've followed a number of how-to guides on line but I can't find any answers to what I'm seeing.  It's probably a simple configuration problem.

Here are my main configuration files:

/etc/krb5.conf:

```

[libdefaults]
default_realm = EXAMPLE.COM

[realms]
EXAMPLE.COM = {
  kdc = example.com
  admin_server = example.com
}

[domain_realm]
example.com = EXAMPLE.COM
.example.com = EXAMPLE.COM

[login]
krb4_convert = false
krb4_get_tickets = false


```

And here's my /etc/krb5kdc/kdc.conf:
```

[kdcdefaults]
    kdc_ports = 750,88

[realms]
EXAMPLE.COM = {
        database_name = /var/lib/krb5kdc/principal
        admin_keytab = FILE:/etc/krb5kdc/kadm5.keytab
        acl_file = /etc/krb5kdc/kadm5.acl
        key_stash_file = /etc/krb5kdc/stash
        kdc_ports = 750,88
        max_life = 10h 0m 0s
        max_renewable_life = 7d 0h 0m 0s
        master_key_type = des3-hmac-sha1
        supported_enctypes = des3-hmac-sha1:normal des-cbc-crc:normal des:normal des:v4 des:norealm des:onlyrealm des:afs3
        default_principal_flags = +preauth
    }

```

---

### Post by joehill on 2008-05-28
D'oh, the problem was that the ports I needed were hidden behind the router.  I had assumed that since I was just working through the local host it wouldn't need it, but it turns out you need to associate a real network address with the realm name and to make sure those ports are available.  so in /etc/hosts, I had to have this line:

128.151.45.10 example.com

(Actually, since I was away from the router at the time, I had to use the local address at first--192.168.1.3--which works as long as you're not accessing it over the Internet.  You just can't use 127.0.0.1 or any other loopback interface--that doesn't work.)

---

