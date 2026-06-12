---
title: "Slapd won't start when TLS enabled."
date: 2011-03-01
forum: Server Platforms
---

### Post by mnbbrown on 2011-03-01
When starting slapd after generating the certificate/key for TLS i recieve the following error:

```


Starting OpenLDAP: slapd - failed.
The operation failed but no output was produced. For hints on what went
wrong please refer to the system's logfiles (e.g. /var/log/syslog) or
try running the daemon in Debug mode like via "slapd -d 16383" (warning:
this will create copious output).

Below, you can find the command line options used by this script to 
run slapd. Do not forget to specify those options if you
want to look to debugging output:
  slapd -h 'ldap:/// ldapi:///' -g openldap -u openldap -F /etc/ldap/slapd.d/


```

I had a look in syslog and it was a follows:

```

Mar  2 09:15:24 server slapd[6661]: @(#) $OpenLDAP: slapd 2.4.21 (Aug 10 2010 1$
**Mar  2 09:15:24 server slapd[6661]: main: TLS init def ctx failed: -1**
Mar  2 09:15:24 server slapd[6661]: slapd stopped.
Mar  2 09:15:24 server slapd[6661]: connections_destroy: nothing to destroy.

```

I then ran strace slapd and believe I have found the problem:
```


open("/etc/ssl/certs/cacert.pem", O_RDONLY) = 10
fstat64(10, {st_mode=S_IFREG|0644, st_size=1383, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb773e000
read(10, "-----BEGIN CERTIFICATE-----\nMIID"..., 8192) = 1383
read(10, "", 4096)                      = 0
close(10)                               = 0
munmap(0xb773e000, 4096)                = 0
brk(0x21d28000)                         = 0x21d28000
open("/etc/ssl/private/ldap-key.pem", O_RDONLY|O_LARGEFILE) = 10
fstat64(10, {st_mode=S_IFREG|0646, st_size=891, ...}) = 0
read(10, "-----BEGIN RSA PRIVATE KEY-----\n"..., 891) = 891
close(10)                               = 0
**open("/etc/ssl/ldap-cert.pem", O_RDONLY|O_LARGEFILE) = -1 EACCES (Permission denied)**
time(NULL)           


```

It opens the CA key and the ldap key successfully but when it goes to open the ldap-cert the permission is denied..

Any idea why this could be happening?

Thanks Matthew

---

### Post by headvampyre@hotmail.co.uk on 2011-03-02
Hi, ive encountered this issue before - i never managed to fix it, but, have you added the user openldap to the group openssl, and allowed the the user and group read access to the file?

---

