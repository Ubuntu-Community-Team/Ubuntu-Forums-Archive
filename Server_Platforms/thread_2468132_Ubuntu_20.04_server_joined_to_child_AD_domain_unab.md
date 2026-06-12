---
title: "Ubuntu 20.04 server joined to child AD domain unable to auth users from parent domain"
date: 2021-10-19
forum: Server Platforms
---

### Post by joeagored on 2021-10-19
I have an Ubuntu 20.04 server that I have successfully joined to my domain using realm, US.EXAMPLE.COM.
 
The way our AD is structured is that all machines are joined to the  child domain for their region and all users are setup in the parent  domain, EXAMPLE.COM. With full trust, etc, of course.

 
I can successfully look up users in the US.EXAMPLE.COM domain with id  or getent passwd, but cannot look up any users in the parent  EXAMPLE.COM domain.

 
I can successfully kinit to the parent domain.

 
I have tried adding capaths to the krb5.conf as well as adding the parent domain to the sssd.conf file like this:

 [domain/EXAMPLE.com]
inherit_from = US.EXAMPLE.com
id_provider = ad
debug_level = 7
krb5_validate = False

 The closest I seem to get is an error message saying the server isn't found in the parent domain's Kerberous DB.
[INDENT] Client 'host/SERVER01@US.EXAMPLE.COM' not found in Kerberos database

 [/INDENT]
Surely there is a way to use the existing trust to let the machine  joined to the child domain authenticate users from the parent domain?  I have done this successfully in this domain before with a RedHat server using FQDN, but I am trying to get away from RedHat and move to Ubuntu and the same configuration tricks were unable to let the Ubuntu server lookup or authenticate users from the parent domain even with FQDNs.

---

