---
title: "join a machine ( samba) to active directory )"
date: 2017-11-22
forum: Server Platforms
---

### Post by rakai on 2017-11-22
hello

i'm new user of ubuntu and i'm trying to configure o squid proxy, i want  adding my machin ubuntu to active directory using samba and winbind, i  guet the error: 

gss_init_sec_context failed with [ Miscellaneous failure (see text): Server (krbtgt/LOCAL@MIS.LOCAL) unknown]
kinit succeeded but ads_sasl_spnego_gensec_bind(KRB5) failed: An internal error occurred.
Failed to join domain: failed to connect to AD: An internal error occurred.

this is my files configurations:

krb5.conf: 

```
   
 [logging]

 default = FILE:/var/log/krb5libs.log
 kdc = FILE:/var/log/krb5kdc.log
 admin_server = FILE:/var/log/kadmind.log

[libdefaults]

 default_realm = MIS.LOCAL
 dns_lookup_realm = true
 dns_lookup_kdc = true
 ticket_lifetime = 24h
 forwardable = true

[realms]

 MIS.LOCAL = {
  kdc = 10.40.200.10:88
  admin_server = 10.40.200.10:749
 }

[domain_realm]

 .mis.local = MIS.LOCAL
 mis.local = MIS.LOCAL





                                      




  
```

smb.conf :

```
   [global]

   workgroup = MIS0
   password server = *
   realm =MIS.LOCAL
   encrypt passwords = yes
   winbind enum groups = yes
   winbind enum users = yes
   winbind use default domain = yes
   security = ADS
   debuglevel = 2
   wins support = no
   idmap uid = 10000-20000
   idmap gid = 10000-20000
   template shell = /bin/false
   winbind offline logon = false                                                               


     
```

THANK YOU

---

### Post by howefield on 2017-11-22
Duplicate thread closed.

---

