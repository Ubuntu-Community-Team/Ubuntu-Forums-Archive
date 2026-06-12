---
title: "krb5kdc ignores database_name in kdc.conf"
date: 2013-02-06
forum: Security
---

### Post by DaveQB on 2013-02-06
Hi all,

Not sure if this is the right forum. And not 100% sure this is a bug or not, hence the post and not a bug report on launchpad. I am not too familiar with Kerberos to know so I will just state what I have found.


Setting a realm in the "/etc/krb5kdc/kdc.conf" like so:

```

[kdcdefaults]
    kdc_ports = 750,88

[realms]
    think.vpc = {
        database_name = /var/lib/krb5kdc/think.vpc
        admin_keytab = FILE:/etc/krb5kdc/kadm5.keytab
        acl_file = /etc/krb5kdc/kadm5.acl
        key_stash_file = /etc/krb5kdc/stash
        kdc_ports = 750,88
        max_life = 10h 0m 0s
        max_renewable_life = 7d 0h 0m 0s
        master_key_type = des3-hmac-sha1
        supported_enctypes = aes256-cts:normal arcfour-hmac:normal des3-hmac-sha1:normal des-cbc-crc:normal des:normal des:v4 des:norealm des:onlyrealm des:afs3
        default_principal_flags = +preauth
    }


```

For what I can tell, this is basically what comes in the package looking at:
```

dpkg -L krb5-kdc | grep example
/usr/share/doc/krb5-kdc/examples
/usr/share/doc/krb5-kdc/examples/kdc.conf

```


Then setting this realm as the default in:

/etc/krb5.conf:

```

[libdefaults]
        default_realm = THINK.VPC

# The following krb5.conf variables are only for MIT Kerberos.
        krb4_config = /etc/krb.conf
        krb4_realms = /etc/krb.realms

```
I have trimmed that to just the pertinent bit.
This is bascially the same as what comes in the package.

```

dpkg -L krb5-config | grep template
/usr/share/kerberos-configs/krb5.conf.template

```

So now, with my database_name set to /var/lib/krb5kdc/think.vpc I try and launch krb5kdc with no arguments:

```

krb5kdc 
krb5kdc: cannot initialize realm THINK.VPC - see log file for details

```

If I tell it the database location...

```

krb5kdc  -d  /var/lib/krb5kdc/think.vpc
ps aux|grep kd[c]
root     18863  0.0  0.0  43124   568 ?        Ss   16:56   0:00 krb5kdc -d /var/lib/krb5kdc/think.vpc

```

Same issue with kadmin.local

```

kadmin.local -q 'listprincs'
Authenticating as principal root/admin@THINK.VPC with password.
kadmin.local: No such file or directory while initializing kadmin.local interface


kadmin.local -d /var/lib/krb5kdc/think.vpc -q 'listprincs'
Authenticating as principal root/admin@THINK.VPC with password.
K/M@THINK.VPC
kadmin/admin@THINK.VPC
kadmin/changepw@THINK.VPC
kadmin/mgt-master01-ap-southeast-2b.think.edu.au@THINK.VPC
krbtgt/THINK.VPC@THINK.VPC

```


Checking what files we read during start up though...

```

strace -e trace=file krb5kdc 2>&1 | grep '/etc/'
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
stat("/etc/krb5kdc/kdc.conf", {st_mode=S_IFREG|0644, st_size=605, ...}) = 0
open("/etc/krb5kdc/kdc.conf", O_RDONLY) = 3
stat("/etc/krb5.conf", {st_mode=S_IFREG|0644, st_size=1729, ...}) = 0
open("/etc/krb5.conf", O_RDONLY)        = 3
stat("/usr/etc/krb5.conf", 0x7fffd10cf580) = -1 ENOENT (No such file or directory)
access("/etc/krb5kdc/kdc.conf", R_OK)   = 0
access("/etc/krb5.conf", R_OK)          = 0
stat("/usr/etc/krb5.conf", 0x7fffd10cf490) = -1 ENOENT (No such file or directory)
access("/etc/krb5kdc/kdc.conf", R_OK)   = 0
access("/etc/krb5.conf", R_OK)          = 0
stat("/usr/etc/krb5.conf", 0x7fffd10cf410) = -1 ENOENT (No such file or directory)
access("/etc/krb5kdc/kdc.conf", R_OK)   = 0
access("/etc/krb5.conf", R_OK)          = 0
stat("/usr/etc/krb5.conf", 0x7fffd10cf350) = -1 ENOENT (No such file or directory)
open("/etc/krb5kdc/principal", O_RDONLY) = -1 ENOENT (No such file or directory)

```

I notice here that we are hitting:
"/etc/krb5kdc/principal"

So if I move my database to that location....


```

/etc/krb5kdc# for i in  /var/lib/krb5kdc/think* ; do cp $i $(basename $i|sed 's/think\.vpc/principal/g') ; done
/etc/krb5kdc# ls
dump  kadm5.acl  kdc.conf  principal  principal.kadm5  principal.kadm5.lock  principal.ok  stash

```

All starts and works fine

```

strace -e trace=file krb5kdc 2>&1 | grep '/etc/'
...
open("/etc/krb5kdc/principal", O_RDONLY) = 4
open("/etc/krb5kdc/principal.ok", O_RDWR) = 4
access("/etc/krb5kdc/kdc.conf", R_OK)   = 0
...

```

And kadmin.local works too without needing to be told where to look.

```

kadmin.local  -q 'listprincs'
Authenticating as principal root/admin@THINK.VPC with password.
K/M@THINK.VPC
kadmin/admin@THINK.VPC
kadmin/changepw@THINK.VPC
kadmin/mgt-master01-ap-southeast-2b.think.edu.au@THINK.VPC
krbtgt/THINK.VPC@THINK.VPC

```


Am I missing something? It feels like the binary is hardcoded where to go and ignores any configs about where to go for the database.

Happy to be proven wrong.

Thanks.

---

