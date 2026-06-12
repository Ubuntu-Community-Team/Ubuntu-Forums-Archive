---
title: "Setting up edgy as a kerberos KDC"
date: 2007-04-10
forum: Server Platforms
---

### Post by glenn1 on 2007-04-10
Well I haven't posted here before but I'm at my wit's end with this particular problem. I've done so much googling and reading of man pages in the last few days but I just cannot figure out why this isn't working.

I am trying to set up a machine as a kerberos KDC. I am using the 6.10 server edition ubuntu release. Here is a simplified view of the configuration I have done in relation to kerberos. **Note:** wherever you see 'myhost' or 'mydomain', a real domain has been placed in the config, and it is valid in DNS for both forward and reverse lookups, etc. I'm just trying to simplify things for the purpose of this post.

[list]
[*] Installed the packages **krb5-kdc** and **krb5-admin-server** (plus dependencies).
[*] Ran krb5_newrealm to create my realm

[*] My /etc/krb5.conf looks like this:
```

[libdefaults]   
        default_realm = MYDOMAIN.COM
        krb4_config = /etc/krb.conf
        krb4_realms = /etc/krb.realms
        kdc_timesync = 1
        ccache_type = 4
        forwardable = true
        proxiable = true
        v4_instance_resolve = false
        v4_name_convert = {
                host = {
                        rcmd = host
                        ftp = ftp
                }
                plain = {
                        something = something-else
                }
        }
        fcc-mit-ticketflags = true

[realms]
        MYDOMAIN.COM = {
                kdc = myhost.mydomain.com
                admin_server = myhost.mydomain.com
        }

[domain_realm]
        .mydomain.com = MYDOMAIN.COM
        mydomain.com = MYDOMAIN.COM

[login]
        krb4_convert = true
        krb4_get_tickets = false

[logging]
    kdc = FILE:/var/log/krb5kdc.log
    admin_server = FILE:/var/log/kadmin.log
    default = FILE:/var/log/krb5lib.log

```


[*] My /etc/krb5kdc/kdc.conf looks like this:

```

[kdcdefaults]
    kdc_ports = 750,88

[realms]
    MYDOMAIN.COM = {
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

[/list]

**/etc/init.d/krb5-kdc restart** and the KDC starts successfully. **/var/log/krb5kdc.log** shows:

```

Apr 10 20:07:22 myhost krb5kdc[3763](info): setting up network...
Apr 10 20:07:22 myhost krb5kdc[3763](info): skipping unrecognized local address family 17
Apr 10 20:07:22 myhost krb5kdc[3763](info): listening on fd 7: udp 10.0.1.10.88
Apr 10 20:07:22 myhost krb5kdc[3763](info): listening on fd 8: udp 10.0.1.10.750
Apr 10 20:07:22 myhost krb5kdc[3763](info): listening on fd 9: udp fe80::20d:61ff:fe2d:a627%eth0.88
Apr 10 20:07:22 myhost krb5kdc[3763](info): listening on fd 10: udp fe80::20d:61ff:fe2d:a627%eth0.750
Apr 10 20:07:22 myhost krb5kdc[3763](info): set up 4 sockets
Apr 10 20:07:22 myhost krb5kdc[3764](info): commencing operation

```

and **ps ax | grep krb** shows:

```

3764 ?        Ss     0:00 /usr/sbin/krb5kdc -4none

```

So the KDC is running and, as far as I can see, configured properly. But when I type **kinit** (on the same machine that is running the KDC...) it just says:

```

kinit(v5): Cannot contact any KDC for requested realm while getting initial credentials

```

I've also created myself a principal in the database with kadmin.local: ```
kadmin.local -q "addprinc glenn/admin@MYDOMAIN.COM"
``` but if I run **kinit -V glenn/admin@MYDOMAIN.COM** i still get exactly the same message about being unable to contact a KDC. I've tried putting SRV records in DNS for _kerberos._udp and _kerberos-master._udp pointing to the KDC host but that didn't help either. I still can't even get kinit to run, on the host where the KDC is running.

Any ideas?? All suggestions will be appreciated!

---

### Post by glenn1 on 2007-04-11
Even if anyone has successfully set up a KDC on their Ubuntu system, if you could describe the process you followed that would still be helpful so I can see if I have missed something!

I'm very new to Kerberos and this is my first attempt at setting up a KDC.

---

### Post by glenn1 on 2007-04-11
I think I have resolved this problem. Believe it or not i had to **remove** these lines from the [realms] section of my krb5.conf:

```

MYDOMAIN.COM = {
                kdc = myhost.mydomain.com
                admin_server = myhost.mydomain.com
        }

```

Since removing the location of the KDC from the config file, I assume kinit is now getting it from the DNS instead, and this is working.

I really have no idea why this is the case. The KDC FQDN in the config file was exactly the same as the one in DNS.

---

### Post by moonkey on 2007-06-03
Hi, i ran into the same problem and i commeted the line begining with 127.0.1.1 in /etc/hosts in order to solve this.
Don't know if this is correct but it's working now.

---

