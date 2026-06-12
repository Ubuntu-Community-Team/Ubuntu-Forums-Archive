---
title: "Kerberos - create database"
date: 2008-02-14
forum: Server Platforms
---

### Post by fishwolf on 2008-02-14
I have ubunto server ver. 6.06 TLS

I'm tring to installa kerberos service.

I cannot create the database

root@azienda01:/etc/krb5kdc# kdb5_util create -s
Loading random data
Initializing database '/etc/krb5kdc/principal' for realm 'AZIENDA.IT',
master key name 'K/M@AZIENDA.IT'
You will be prompted for the database Master Password.
It is important that you NOT FORGET this password.
Enter KDC database master key:MYPASSWORD
Re-enter KDC database master key to verify:MYPASSWORD
kdb5_util: No matching key in entry having a permitted enctype while initializing the Kerberos admin interface

kdc.conf:
[kdcdefaults]
    kdc_ports = 750,88

[realms]
    AZIENDA.IT = {
        database_name = /etc/krb5kdc/principal
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

krb5.con:
[libdefaults]
        default_realm = AZIENDA.IT
#
# For Windows 2000 compatibility
#
        default_tgs_enctypes = des-cbc-crc des-cbc-md5
        default-tkt-enctypes = des-cbc-crc des-cbc-md5
        permitted_enctypes = des-cbc-crc des-cbc-md5
        krb4_config = /etc/krb.conf
        krb4_realms = /etc/krb.realms
        kdc_timesync = 1
        ccache_type = 4
        forwardable = true
        proxiable = true
#
# The following libdefaults parameters are only for Himdal Kerberos.
#
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

[realms]
        AZIENDA.IT = {
                kdc = kdc.azienda.it
                admin_server = kdc.azienda.it
        }

[domain_realm]
        .azienda.it = AZIENDA.IT

[login]
        krb4_convert = true
        krb4_get_tickets = true


Help me, please.

Thanks

---

### Post by faithful on 2008-02-22
In kdc.conf change the line supported_enctypes to:
supported_enctypes =  des-cbc-crc:normal des-cbc-md5:normal des:normal des:v4 des:norealm des:onlyrealm des:afs3

---

