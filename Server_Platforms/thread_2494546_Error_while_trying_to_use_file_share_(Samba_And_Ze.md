---
title: "Error while trying to use file share (Samba And Zentyal AD)"
date: 2024-01-19
forum: Server Platforms
---

### Post by rafaeltrevisan on 2024-01-19
Hi, i've setup a simple samba using this config:

[global]
        password server = eco.lan
        realm = ECO.LAN
        security = ADS
        server role = standalone server
        template shell = /bin/bash
        winbind use default domain = Yes
        workgroup = ECO
        idmap config * : range = 16777216-33554431
        idmap config * : backend = tdb

I am able to login as guest in the share when its enable.
But the same is not true when i try to log in using a domain account:

```
[2024/01/19 21:49:24.194818,  1] ../../source3/librpc/crypto/gse.c:665(gse_get_server_auth_token)
  gss_accept_sec_context failed with [ Miscellaneous failure (see text): Failed to find cifs/arquivos.ec.eco.br@ECO.LAN(kvno 8) in keytab MEMORY:cifs_srv_keytab (arcfour-hmac-md5)]
[2024/01/19 21:49:24.194882,  1] ../../auth/gensec/spnego.c:1242(gensec_spnego_server_negTokenInit_step)
  gensec_spnego_server_negTokenInit_step: gse_krb5: parsing NEG_TOKEN_INIT content failed (next[(null)]): NT_STATUS_LOGON_FAILURE
[2024/01/19 21:49:24.194915,  3] ../../source3/smbd/smb2_server.c:3954(smbd_smb2_request_error_ex)
  smbd_smb2_request_error_ex: smbd_smb2_request_error_ex: idx[1] status[NT_STATUS_LOGON_FAILURE] || at ../../source3/smbd/smb2_sesssetup.c:147
[2024/01/19 21:49:24.195665,  3] ../../source3/smbd/server_exit.c:239(exit_server_common)

```


When trying to log in from localhost to samba, i get this: (I think it's working ok)

```
smbclient -L localhost  -U test@eco.lan
Password for [test@eco.lan]:


        Sharename       Type      Comment
        ---------       ----      -------
        ITOps           Disk      ITOps
        IPC$            IPC       IPC Service (Samba 4.15.13-Ubuntu)

```

The log above seems to be a issue with kerberos(?) but i dont really understand how winbind samba and kerberos really worker together.

My AD/LDAP is a Zentyal Server and i can list users and groups with wbinfo.

---

### Post by MAFoElffen on 2024-01-20
Are you running Zentyal or Ubuntu Server?

Please post the contents of your /etc/krb5.conf file within CODE Tags.

---

### Post by rafaeltrevisan on 2024-01-20
Hi, sorry for the lack of information.

I'm running a Ubuntu Server 22.04, using Zentyal as the AD provider/Password server

cat /etc/krb5.conf:

```

[libdefaults]        
        default_realm = ECO.LAN
        dns_lookup_realm = true
        dns_lookup_kdc = true


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


[realms]
        ATHENA.MIT.EDU = {
                kdc = kerberos.mit.edu
                kdc = kerberos-1.mit.edu
                kdc = kerberos-2.mit.edu:88
                admin_server = kerberos.mit.edu
                default_domain = mit.edu
        }
        ZONE.MIT.EDU = {
                kdc = casio.mit.edu
                kdc = seiko.mit.edu
                admin_server = casio.mit.edu
        }
        CSAIL.MIT.EDU = {
                admin_server = kerberos.csail.mit.edu
                default_domain = csail.mit.edu
        }
        IHTFP.ORG = {
                kdc = kerberos.ihtfp.org
                admin_server = kerberos.ihtfp.org
        }
        1TS.ORG = {
                kdc = kerberos.1ts.org
                admin_server = kerberos.1ts.org
        }
        ANDREW.CMU.EDU = {
                admin_server = kerberos.andrew.cmu.edu
                default_domain = andrew.cmu.edu
        }
        CS.CMU.EDU = {
                kdc = kerberos-1.srv.cs.cmu.edu
                kdc = kerberos-2.srv.cs.cmu.edu
                kdc = kerberos-3.srv.cs.cmu.edu
                admin_server = kerberos.cs.cmu.edu
        }
        DEMENTIA.ORG = {
                kdc = kerberos.dementix.org
                kdc = kerberos2.dementix.org
                admin_server = kerberos.dementix.org
        }
        stanford.edu = {
                kdc = krb5auth1.stanford.edu
                kdc = krb5auth2.stanford.edu
                kdc = krb5auth3.stanford.edu
                master_kdc = krb5auth1.stanford.edu
                admin_server = krb5-admin.stanford.edu
                default_domain = stanford.edu
        }
        UTORONTO.CA = {
                kdc = kerberos1.utoronto.ca
                kdc = kerberos2.utoronto.ca
                kdc = kerberos3.utoronto.ca
                admin_server = kerberos1.utoronto.ca
                default_domain = utoronto.ca
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
        .slac.stanford.edu = SLAC.STANFORD.EDU
        .toronto.edu = UTORONTO.CA
        .utoronto.ca = UTORONTO.CA

```

---

### Post by MAFoElffen on 2024-01-21
I don't see where it is point to "your" Kerberos server(s)

It should have something like this, but modified to your own:
```

realms]
        EXAMPLE.COM = {
                kdc = kdc01.example.com
                kdc = kdc02.example.com
                admin_server = kdc01.example.com
                default_domain = example.com
                database_module = openldap_ldapconf
        }

```
And after getting your ticket with kinit, do "klist -f" to check your Kerberos ticket, right?

---

### Post by rafaeltrevisan on 2024-01-21
I've joined the domain using winbind, do i still need Kerberos?, i have an old samba (Ubuntu server) in the environment, that has Kerberos but the config is the same, no realms configured on it

---

### Post by MAFoElffen on 2024-01-22
If then, does your user have a samba password set? And where in your Samba conf file does t say security is handled by pam?

---

### Post by rafaeltrevisan on 2024-01-22
Well, now i've tried to use kerberos and got a ticket

> Valid starting       Expires              Service principal
01/22/2024 13:04:10  01/22/2024 23:04:10  krbtgt/ECO.LAN@ECO.LAN

But failed to do kadmin:

> server@samba-new:~# kadmin -p eco.lan
Authenticating as principal eco.lan with password.
kadmin: Missing parameters in krb5.conf required for kadmin client while initializing kadmin interface


  
Added this domain to krb5.conf
      > 
eco.lan = {
                kdc = eco.lan   
                default_domain = eco.lan
                database_module = openldap_ldapconf
        }


---

### Post by TheFu on 2024-01-22
Are the client OSes MS-Windows?  If not, why use samba at all?

---

### Post by rafaeltrevisan on 2024-01-22
Yes, the clients are Windows, it's a common shared folder.

---

