---
title: "Kerberos V5 Server; ubuntu package isn't creating /var/lib/krb5kdc/principal"
date: 2022-11-27
forum: Server Platforms
---

### Post by Surfrock66 on 2022-11-27
I have an existing openldap server on Ubuntu Server 22.04 and am trying to set up a kerberos server with it, following this guide: [https://ubuntu.com/server/docs/service-kerberos-with-openldap-backend](https://ubuntu.com/server/docs/service-kerberos-with-openldap-backend)

The accounts are created and tested, they work fine (I reference them by cn, but they have a uid; I just created them in apache directory studio first).  I've done "dpkg-reconfigure krb5-config" and edited /etc/krb5.conf to add my server and realm.  One thing not in that doc but that I've seen elsewhere is to create a section "[domain_realm]" and add my domain to it, which I've done but it hasn't helped.  I created a logging section, which requires modifying the systemd services to allow writing to /var/log/kerberos, but that's fine.  I then run the "kdb5_ldap_util" command as listed, and after entering the passwords it appears to complete successfully.  I do the stash for the kdc-service and kadmin-service passwords, that completes successfully.  I create the kadm.acl file, that is fine, then when I try to start the service, I get this in krb5kdc.log:

```
    krb5kdc[712216](Error): Cannot find master key record in database - while fetching master keys list for realm SUBDOMAIN.DOMAIN.COM
```

If I then run "kadmin.local" I get the following:

```
    Authenticating as principal root/admin@SUBDOMAIN.DOMAIN.COM with password.
    kadmin.local: Cannot find master key record in database while initializing kadmin.local interface
```

As it turns out, the file /var/lib/krb5kdc/principal never gets created.  Here is console output:

```
root:/var/lib/krb5kdc# kdb5_util create -r SUBDOMAIN.DOMAIN.COM
Loading random data
Initializing database '/var/lib/krb5kdc/principal' for realm 'SUBDOMAIN.DOMAIN.COM',
master key name 'K/M@SUBDOMAIN.DOMAIN.COM'
You will be prompted for the database Master Password.
It is important that you NOT FORGET this password.
Enter KDC database master key: 
Re-enter KDC database master key to verify: 
root:/var/lib/krb5kdc# ls
total 0
```

I'm not sure what else to troubleshoot here, but at this point I'm stuck and any guidance would be appreciated.  Config files below, with domain and subdomain changed:

/etc/krb5.conf:

```
    [libdefaults]
            default_realm = SUBDOMAIN.DOMAIN.COM
    
    # The following krb5.conf variables are only for MIT Kerberos.
            kdc_timesync = 1
            ccache_type = 4
            forwardable = true
            proxiable = true
    
    # The following encryption type specification will be used by MIT Kerberos
    # if uncommented.  In general, the defaults in the MIT Kerberos code are
    # correct and overriding these specifications only serves to disable new
    # encryption types as they are added, creating interoperability problems.
    #
    # The only time when you might need to uncomment these lines and change
    # the enctypes is if you have local software that will break on ticket
    # caches containing ticket encryption types it doesn't know about (such as
    # old versions of Sun Java).
    
    #       default_tgs_enctypes = des3-hmac-sha1
    #       default_tkt_enctypes = des3-hmac-sha1
    #       permitted_enctypes = des3-hmac-sha1
    
    # The following libdefaults parameters are only for Heimdal Kerberos.
            fcc-mit-ticketflags = true
    
    [logging]
            kdc = FILE:/var/log/kerberos/krb5kdc.log
            admin_server = FILE:/var/log/kerberos/kadmin.log
            default = FILE:/var/log/kerberos/krb5lib.log
    
    [realms]
            SUBDOMAIN.DOMAIN.COM = {
                    kdc = hostname.subdomain.domain.com
                    admin_server = hostname.subdomain.domain.com
                    default_domain = subdomain.domain.com
                    database_module = openldap_ldapconf
            }
    
    [domain_realm]
            .subdomain.domain.com = SUBDOMAIN.DOMAIN.COM
            subdomain.domain.com = SUBDOMAIN.DOMAIN.COM
    
    [dbdefaults]
            ldap_kerberos_container_dn = cn=krbContainer,dc=subdomain,dc=domain,dc=com
    
    [dbmodules]
            openldap_ldapconf = {
                    db_library = kldap
    
                    # if either of these is false, then the ldap_kdc_dn needs to
                    # have write access
                    disable_last_success = true
                    disable_lockout  = true
    
                    # this object needs to have read rights on
                    # the realm container, principal container and realm sub-trees
                    ldap_kdc_dn = "cn=kdc-service,ou=accounts,dc=subdomain,dc=domain,dc=com"
    
                    # this object needs to have read and write rights on
                    # the realm container, principal container and realm sub-trees
                    ldap_kadmind_dn = "cn=kadmin-service,ou=accounts,dc=subdomain,dc=domain,dc=com"
    
                    ldap_service_password_file = /etc/krb5kdc/service.keyfile
                    ldap_servers = ldapi:///
                    ldap_conns_per_server = 5
            }
```

/etc/krb5kdc/kadm5.acl:

```
    */admin@SUBDOMAIN.DOMAIN.COM *
```

/etc/krb5kdc/kdc.conf:

```
    [kdcdefaults]
        kdc_ports = 750,88
    
    [realms]
        SUBDOMAIN.DOMAIN.COM = {
            database_name = /var/lib/krb5kdc/principal
            admin_keytab = FILE:/etc/krb5kdc/kadm5.keytab
            acl_file = /etc/krb5kdc/kadm5.acl
            key_stash_file = /etc/krb5kdc/stash
            kdc_ports = 750,88
            max_life = 10h 0m 0s
            max_renewable_life = 7d 0h 0m 0s
            master_key_type = des3-hmac-sha1
            #supported_enctypes = aes256-cts:normal aes128-cts:normal
            default_principal_flags = +preauth
        }


```

---

