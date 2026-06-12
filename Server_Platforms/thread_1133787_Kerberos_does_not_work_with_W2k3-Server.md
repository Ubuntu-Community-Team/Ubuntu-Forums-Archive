---
title: "Kerberos does not work with W2k3-Server"
date: 2009-04-23
forum: Server Platforms
---

### Post by Diamonds on 2009-04-23
Hello

I have installed Ubuntu server 8.04 LTS with samba, Kerberos and winbind. Now i would like to join a W2k3 ADS domain. But it does not work.

Ping and nslookup is working fine (svr-01 and svr-01.pamatech.local).

Hier a list of my work:
Installed packages: krb5-user libpam-krb5 winbind smbclient


/etc/krb5.conf
```
[logging]
    default = FILE:/var/log/krb5.log

[libdefaults]
    ticket_lifetime = 24000
    clock_skew = 300
    default_realm = PAMATECH.LOCAL

[realms]
    PAMATECH.LOCAL = {
        kdc = svr-01:88
        admin_server = svr-01:464
        default_domain = PAMATECH.LOCAL
    }

[domain_realm]
    .pamatech.local = PAMATECH.LOCAL
    pamatech.local = PAMATECH.LOCAL

```Getting ticket
kinit [EMAIL="Administrator@pamatech.local"]Administrator@pamatech.local[/EMAIL]
"Cannot resolve network address for KDC in realm PAMATECH.LOCAL while getting initial credentials"

Why do I get this message? I searched a long time but I did not find a answer. Could someone help me to solve this probleme?

Thanks Diamonds

---

### Post by wlraider70 on 2009-06-17
I have the same error.

---

### Post by deejross on 2009-08-10
I too have this problem and I count 6 other threads just like this one with no answers. What's up with the lack of help from the community these days?

Anyways, I was following [Ubuntu's Help Page]("https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto"), which is garbage. It uses the OLD method for authenticating against an AD server (NTLM).

I ended up using [another guide]("http://wiki.randompage.org/index.php/DistOS:Linux:Debian:Samba") to set this up. But when you follow that guide, you will still have the same problem with kinit.

To fix that problem, you simply need to add the domain controller's ip and fully qualified domain name to your /etc/hosts file. So for example:
```
10.0.0.1   dc1.example.com
```

Hope that helps!

---

