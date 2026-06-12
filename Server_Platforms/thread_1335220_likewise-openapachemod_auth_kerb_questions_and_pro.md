---
title: "likewise-open/apache/mod_auth_kerb questions and problem"
date: 2009-11-23
forum: Server Platforms
---

### Post by RoboJ1M on 2009-11-23
Hi,

I have an old server on which we have installed Ubuntu Server 8.04 (9.04 and 9.10 screw up the LILO and GRUB2 instllations respectively, can't use those)

We want to host Bazaar, SVN and Samba services on there and integrate the machines into our Active Directory.

I followed this guide on how to setup kerberos using likewise open:

[https://help.ubuntu.com/8.04/serverguide/C/likewise-open.html](https://help.ubuntu.com/8.04/serverguide/C/likewise-open.html)

That works, I can login to the server using DOMAIN\USER accounts

I then followed this guide on how to install and configure mod_auth_kerb:

[http://grolmsnet.de/kerbtut](http://grolmsnet.de/kerbtut)

But I fail at step 6c, testing the kerberos keytab file with the error:

```
administrator@vmserver:~$ kinit -k -t /usr/local/apache/conf/http_vmserver.krb5keytab
kinit(v5): Cannot resolve network address for KDC in realm  while getting initial credentials
```

in fact, kinit -k fails all on its own without that file with the same error.

DNS appears to work:

```
administrator@vmserver:~$ host spurprimary
spurprimary.win2kdomain has address 192.168.27.64
spurprimary.win2kdomain has address 192.168.56.1
administrator@vmserver:~$ host 192.168.27.64
64.27.168.192.in-addr.arpa domain name pointer spurprimary.win2kdomain.
administrator@vmserver:~$ host vmserver
vmserver.win2kdomain has address 192.168.27.89
administrator@vmserver:~$ host 192.168.27.89
89.27.168.192.in-addr.arpa domain name pointer vmserver.win2kdomain.
```

If there is a better place to be asking this question, please let me know!

Here's my (auto generated, but I added my kdc) krb5.conf:

```
administrator@vmserver:~$ cat /etc/krb5.conf
[logging]
default=FILE:/var/log/krb5.log
[libdefaults]
        default_realm = WIN2KDOMAIN
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
        default_tgs_enctypes = RC4-HMAC DES-CBC-MD5 DES-CBC-CRC
        default_tkt_enctypes = RC4-HMAC DES-CBC-MD5 DES-CBC-CRC
        preferred_enctypes = RC4-HMAC DES-CBC-MD5 DES-CBC-CRC
        dns_lookup_kdc = true

# The following krb5.conf variables are only for MIT Kerberos.

# The following encryption type specification will be used by MIT Kerberos
# if uncommented.  In general, the defaults in the MIT Kerberos code are
# correct and overriding these specifications only serves to disable new
# encryption types as they are added, creating interoperability problems.

#       default_tgs_enctypes = aes256-cts arcfour-hmac-md5 des3-hmac-sha1 des-cbc-crc des-cbc-md5
#       default_tkt_enctypes = aes256-cts arcfour-hmac-md5 des3-hmac-sha1 des-cbc-crc des-cbc-md5
#       permitted_enctypes = aes256-cts arcfour-hmac-md5 des3-hmac-sha1 des-cbc-crc des-cbc-md5

# The following libdefaults parameters are only for Heimdal Kerberos.

[realms]
        WIN2KDOMAIN = {
                kdc = spurprimary.win2kdomain:88
                auth_to_local = RULE:[1:$0\$1](^WIN2KDOMAIN\\.*)s/^WIN2KDOMAIN/WIN2KDOMAIN/
                auth_to_local = DEFAULT
        }
        ATHENA.MIT.EDU = {
                kdc = kerberos.mit.edu:88
                kdc = kerberos-1.mit.edu:88
                kdc = kerberos-2.mit.edu:88
                admin_server = kerberos.mit.edu
                default_domain = mit.edu
        }
        MEDIA-LAB.MIT.EDU = {
                kdc = kerberos.media.mit.edu
                admin_server = kerberos.media.mit.edu
        }
        ZONE.MIT.EDU = {
                kdc = casio.mit.edu
                kdc = seiko.mit.edu
                admin_server = casio.mit.edu
        }
        MOOF.MIT.EDU = {
                kdc = three-headed-dogcow.mit.edu:88
                kdc = three-headed-dogcow-1.mit.edu:88
                admin_server = three-headed-dogcow.mit.edu
        }
        CSAIL.MIT.EDU = {
                kdc = kerberos-1.csail.mit.edu
                kdc = kerberos-2.csail.mit.edu
                admin_server = kerberos.csail.mit.edu
                default_domain = csail.mit.edu
                krb524_server = krb524.csail.mit.edu
        }
        IHTFP.ORG = {
                kdc = kerberos.ihtfp.org
                admin_server = kerberos.ihtfp.org
        }
        GNU.ORG = {
                kdc = kerberos.gnu.org
                kdc = kerberos-2.gnu.org
                kdc = kerberos-3.gnu.org
                admin_server = kerberos.gnu.org
        }
        1TS.ORG = {
                kdc = kerberos.1ts.org
                admin_server = kerberos.1ts.org
        }
        GRATUITOUS.ORG = {
                kdc = kerberos.gratuitous.org
                admin_server = kerberos.gratuitous.org
        }
        DOOMCOM.ORG = {
                kdc = kerberos.doomcom.org
                admin_server = kerberos.doomcom.org
        }
        ANDREW.CMU.EDU = {
                kdc = vice28.fs.andrew.cmu.edu
                kdc = vice2.fs.andrew.cmu.edu
                kdc = vice11.fs.andrew.cmu.edu
                kdc = vice12.fs.andrew.cmu.edu
                admin_server = vice28.fs.andrew.cmu.edu
                default_domain = andrew.cmu.edu
        }
        CS.CMU.EDU = {
                kdc = kerberos.cs.cmu.edu
                kdc = kerberos-2.srv.cs.cmu.edu
                admin_server = kerberos.cs.cmu.edu
        }
        DEMENTIA.ORG = {
                kdc = kerberos.dementia.org
                kdc = kerberos2.dementia.org
                admin_server = kerberos.dementia.org
        }
        stanford.edu = {
                kdc = krb5auth1.stanford.edu
                kdc = krb5auth2.stanford.edu
                kdc = krb5auth3.stanford.edu
                admin_server = krb5-admin.stanford.edu
                default_domain = stanford.edu
        }

[domain_realm]
        .mit.edu = ATHENA.MIT.EDU
        mit.edu = ATHENA.MIT.EDU
        .media.mit.edu = MEDIA-LAB.MIT.EDU
        media.mit.edu = MEDIA-LAB.MIT.EDU
        .csail.mit.edu = CSAIL.MIT.EDU
        csail.mit.edu = CSAIL.MIT.EDU
        .whoi.edu = ATHENA.MIT.EDU
        whoi.edu = ATHENA.MIT.EDU
        .stanford.edu = stanford.edu
        spurprimary.win2kdomain = SPURPRIMARY.WIN2KDOMAIN
        .spurprimary.win2kdomain = SPURPRIMARY.WIN2KDOMAIN
[login]
        krb4_convert = true
        krb4_get_tickets = false
[appdefaults]
        pam = {
   mappings = WIN2KDOMAIN\\(.*) $1@WIN2KDOMAIN
   forwardable = true
   validate = true
        }
        httpd = {
   mappings = WIN2KDOMAIN\\(.*) $1@WIN2KDOMAIN
   reverse_mappings = (.*)@WIN2KDOMAIN WIN2KDOMAIN\$1
        }
administrator@vmserver:~$

```

resolv.conf:

```
administrator@vmserver:~$ cat /etc/resolv.conf
search win2kdomain
nameserver 192.168.27.64

```

/etc/hosts:

```
administrator@vmserver:~$ cat /etc/hosts
#127.0.0.1      localhost
#127.0.1.1      vmserver.win2kdomain    vmserver
127.0.0.1 vmserver.win2kdomain vmserver localhost
192.168.27.64 spurprimary.win2kdomain spurprimary
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

Regards,

James.

---

### Post by RoboJ1M on 2009-12-07
Solved by likewise support: use likewise's own mods in the /opt/likewise/lib folder.

---

