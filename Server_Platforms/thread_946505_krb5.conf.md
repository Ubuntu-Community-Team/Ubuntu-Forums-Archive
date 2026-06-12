---
title: "krb5.conf"
date: 2008-10-13
forum: Server Platforms
---

### Post by vegas588 on 2008-10-13
Having difficulty configuring the krb5.conf file for AD/Samba authentication. I am following the steps in this article as a guide: [http://www.ccs.neu.edu/home/battista/articles/winbind/index.html](http://www.ccs.neu.edu/home/battista/articles/winbind/index.html)

Below is the output of my krb5.conf file. Let me explain a few things first because it looks terribly messy to me. By default, krb5.conf has many entries in it already and I did not delete them or modify them. I did however add what I believe are the correct entries for my domain, but it is probably not correct. My domain is a bit confusing in its naming structure because the Pre-Windowss 2000 name is MY_DOMAIN and the domain name is MYDOMAIN.COM. In other words, the NetBIOS name has an underscore in it. My opinion is that I should delete all of the domain names except mine to clean this up. Is there anything else I need to add?

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
        default_tgs_enctypes = RC4-HMAC DES-CBC-MD5 DES-CBC-CRC
        default_tkt_enctypes = RC4-HMAC DES-CBC-MD5 DES-CBC-CRC
        preferred_enctypes = RC4-HMAC DES-CBC-MD5 DES-CBC-CRC
        dns_lookup_kdc = true

# The following krb5.conf variables are only for MIT Kerberos.

# The following encryption type specification will be used by MIT Kerberos
# if uncommented.  In general, the defaults in the MIT Kerberos code are
# correct and overriding these specifications only serves to disable new
# encryption types as they are added, creating interoperability problems.

#       default_tgs_enctypes = aes256-cts arcfour-hmac-md5 des3-hmac-sha1 des-c
#       default_tkt_enctypes = aes256-cts arcfour-hmac-md5 des3-hmac-sha1 des-c
#       permitted_enctypes = aes256-cts arcfour-hmac-md5 des3-hmac-sha1 des-cbc

# The following libdefaults parameters are only for Heimdal Kerberos.

[realms]
        MYDOMAIN.COM = {
                auth_to_local = RULE:[1:$0\$1](^MYDOMAIN\.COM\\.*)s/^STANT
                auth_to_local = DEFAULT
                kdc = 192.168.110.71
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


[login]
        krb4_convert = true
        krb4_get_tickets = false
[appdefaults]
        pam = {
   mappings = MY_DOMAIN\\(.*) $1@MYDOMAIN.COM
   forwardable = true
validate = true
        }
        httpd = {
   mappings = MY_DOMAIN\\(.*) $1@MYDOMAIN.COM
   reverse_mappings = (.*)@MYDOMAIN\.COM MY_DOMAIN\$1
        }

---

### Post by vegas588 on 2008-10-13
I figured it out. The problem I was having was related to the smb.conf settings and not the krb5.conf settings.

---

