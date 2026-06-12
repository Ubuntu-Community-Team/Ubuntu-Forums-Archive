---
title: "samba4 and bind9 auto updates"
date: 2010-09-02
forum: Server Platforms
---

### Post by anchise on 2010-09-02
I am using samba4 and bind9 (9.7.2rc1) on an ubuntu server 10.04.

Everything works fine, but bind9 ist unable to update DNS entries sent by clients.

I followed the tutorial [http://wiki.samba.org/index.php/Samba4/HOWTO#Step_10_Configure_kerberos_DNS_dynamic_updates](http://wiki.samba.org/index.php/Samba4/HOWTO#Step_10_Configure_kerberos_DNS_dynamic_updates) but it doesn't work for me.

It doesn't look like a file permission problem:

```
-rw-r--r-- 1 root root /usr/local/samba/private/dns.keytab
-rw-r--r-- 1 root root /usr/local/samba/private/dns_update_list
-rw-r--r-- 1 root root /usr/local/samba/private/named.conf
-rw-r--r-- 1 root root /usr/local/samba/private/named.conf.update
-rw-r--r-- 1 root root /usr/local/samba/private/dns.keytab
-rw-rw-rw- 1 root root /usr/local/samba/private/dns/mydomain.local.zone
```I also linked the keytab to /etc/krb5,keytab

Wenn a client tries to update its DNS entry, the following happens:

syslog:
```
Sep 2 17:22:21 samba named[15405]: client 192.168.1.299#58058: update 'mydomain.local/IN' denied
```samba.log:
```
../dsdb/dns/dns_update.c:249:dnsupdate_nameupdate_done() 
../dsdb/dns/dns_update.c:249: Failed DNS update - NT_STATUS_IO_TIMEOUT
```With google I found a lot of posts of users with similar problems, but only one solution so far ([http://lists.samba.org/archive/samba/2010-May/156032.html](http://lists.samba.org/archive/samba/2010-May/156032.html)) and this solution gives me a TKEY error.

Does anybody see what's going wrong here (not with the tkey, but with the updates)?

Thanks in advance

anchise

---

### Post by bmullan on 2011-03-31
> **anchise said:**
> I am using samba4 and bind9 (9.7.2rc1) on an ubuntu server 10.04.

Everything works fine, but bind9 ist unable to update DNS entries sent by clients.

I followed the tutorial [http://wiki.samba.org/index.php/Samba4/HOWTO#Step_10_Configure_kerberos_DNS_dynamic_updates](http://wiki.samba.org/index.php/Samba4/HOWTO#Step_10_Configure_kerberos_DNS_dynamic_updates) but it doesn't work for me.

It doesn't look like a file permission problem:

```
-rw-r--r-- 1 root root /usr/local/samba/private/dns.keytab
-rw-r--r-- 1 root root /usr/local/samba/private/dns_update_list
-rw-r--r-- 1 root root /usr/local/samba/private/named.conf
-rw-r--r-- 1 root root /usr/local/samba/private/named.conf.update
-rw-r--r-- 1 root root /usr/local/samba/private/dns.keytab
-rw-rw-rw- 1 root root /usr/local/samba/private/dns/mydomain.local.zone
```I also linked the keytab to /etc/krb5,keytab

Wenn a client tries to update its DNS entry, the following happens:

syslog:
```
Sep 2 17:22:21 samba named[15405]: client 192.168.1.299#58058: update 'mydomain.local/IN' denied
```samba.log:
```
../dsdb/dns/dns_update.c:249:dnsupdate_nameupdate_done() 
../dsdb/dns/dns_update.c:249: Failed DNS update - NT_STATUS_IO_TIMEOUT
```With google I found a lot of posts of users with similar problems, but only one solution so far ([http://lists.samba.org/archive/samba/2010-May/156032.html](http://lists.samba.org/archive/samba/2010-May/156032.html)) and this solution gives me a TKEY error.

Does anybody see what's going wrong here (not with the tkey, but with the updates)?

Thanks in advance

anchise

You said your Syslog showed:
Sep 2 17:22:21 samba named[15405]: client 192.168.1.***[COLOR="Red"]299[/COLOR]***#58058: update 'mydomain.local/IN' denied

What kind of an address is 192.169.1.299 ?

---

### Post by SeijiSensei on 2011-03-31
Did you give permission to that IP address or its subnet with "allow-update" in named.conf?

---

