---
title: "Problem with login to machine using second kerberos server"
date: 2015-02-24
forum: Server Platforms
---

### Post by marcin23 on 2015-02-24
Hi all, 

I've problem with loging to Ubuntu machine connected to AD using kerberos. I've 2 domain controllers, in krb5.conf I had one as kdc, admin_server. When I add second one (domain controller too) in line under 1st, this works because OS connecting to first DC. When I change name of first DC - I cannot login using AD credentials to Ubuntu - why, if I've second kdc? 

One hint is that, when I copy 2nd kdc server above, I can log into OS using AD credentials. Ubuntu cannot automatically use running kdc server from file?

This is my /etc/krb5.conf file:  (primary controller - PDC, secondary - SDC)
```

[logging]
    default = FILE:/var/log/krb5.log

[libdefaults]
    default_realm = EXAMPLE.COM
    kdc_timesync = 1
    ccache_type = 4
    forwardable = true
    proxiable = true

[realms]
    EXAMPLE.COM = {
        kdc = pdc.example.com
        kdc = sdc.example.com
        admin_server = pdc.example.com
        default_domain = EXAMPLE.COM
    }

[domain_realm]
    .example.com = EXAMPLE.COM
    example.com = EXAMPLE.COM

```
This work great, but if I change pdc.example.com to pdctesttest.example.com - I cannot login using AD credentials. After this change, when I copy sdc.example.com above pdctesttest.example.com - works fine. Can I edit file or something and when first KDC will be not rensposible, Ubuntu will try to autenthicate with second one?

---

### Post by marcin23 on 2015-02-24
Ok i found the solution - when I leave PDC, SDC names as default and add in /etc/hosts file not accesible IP for PDC, it works. Maybe kerberos must have valid name of computer in config, when it is not accesible kerberos checks another KDC from config file.
BTW I found another mistake in my system - in NTP I have only one server (PDC) :)

---

