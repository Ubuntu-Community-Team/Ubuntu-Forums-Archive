---
title: "Can't figure out mod_auth_kerb issue"
date: 2017-12-14
forum: Server Platforms
---

### Post by onegative on 2017-12-14
Hi,

I have a apache2 web server that had a functional kerberos authentication setup. Originally, I was using /etc/krb5.keytab for authentication from apache2. 
I have sssd on this system and I am able to ssh to it using domain credentials. I think sssd updated and the OS authentication broke. 

I rejoined it to the windows domains and have ssh working again but that broke my apache authentication. After looking into it I figured that apache should use its own keytab.

I started by creating a keytab on windows using this command:

```
ktpass -princ HTTP/testkrb.mydomain.example@MYDOMAIN.EXAMPLE -mapuser svc.inet.dev.krb@MYDOMAIN.EXAMPLE -crypto AES256-SHA1 -ptype KRB5_NT_PRINCIPAL -pass mypassword -out C:\temp\testkrb.keytab
```

This worked fine. I copied it to my server and changed the permissions so it's readable by www-data.

The svc.inet.dev.krb service account also has the SPN for the site:

```
PS C:\Windows\system32> setspn -L svc.inet.dev.krb
Registered ServicePrincipalNames for CN=SVC.INET.DEV.KRB,OU=Service Accounts,OU=Admin,DC=MYDOMAIN=DC=EXAMPLE:
        HTTP/testkrb.mydomain.example
```

I have what I think is a functional krb5.conf configuration:

```
[libdefaults]
        default_realm = MYDOMAIN.EXAMPLE
        clockskew = 300
        ticket_lifetime =       1d
        forwardable = true
        proxiable = true
        dns_lookup_realm = true
        dns_lookup_kdc = true


        default_tkt_enctypes = aes256-cts-hmac-sha1-96 aes128-cts-hmac-sha1-96 rc4-hmac
        default_tgs_enctypes = aes256-cts-hmac-sha1-96 aes128-cts-hmac-sha1-96 rc4-hmac
        permitted_enctypes = aes256-cts-hmac-sha1-96 aes128-cts-hmac-sha1-96 rc4-hmac


[realms]
        MYDOMAIN.EXAMPLE = {
                kdc = MYDOMAINDC0001.MYDOMAIN.EXAMPLE
                kdc = MYDOMAINDC0002.MYDOMAIN.EXAMPLE
                admin_server = MYDOMAINDC0001.MYDOMAIN.EXAMPLE
                default_domain = MYDOMAIN.EXAMPLE
        }

[domain_realm]
        .kerberos.server = MYDOMAIN.EXAMPLE
        .mydomain.example = MYDOMAIN.EXAMPLE
        mydomain.example = MYDOMAIN.EXAMPLE
        mydomain     = MYDOMAIN.EXAMPLE

[appdefaults]
        pam = {
        ticket_lifetime = 1d
        renew_lifetime = 1d
        forwardable = true
        proxiable = false
        retain_after_close = false
        minimum_uid = 0
        debug = false
        }
[logging]
        default = FILE:/var/log/krb5libs.log
        kdc = FILE:/var/log/kdc.log
        admin_server            = FILE:/var/log/kadmind.log
```


If I do klist -k /etc/apache2/testkrb.keytab I have these two records:

```
Keytab name: FILE:/etc/apache2/testkrb.keytab
KVNO Principal
---- --------------------------------------------------------------------------
   3 HTTP/testkrb.mydomain.example@MYDOMAIN.EXAMPLE
   4 HOST/testkrb.mydomain.example@MYDOMAIN.EXAMPLE
```

And if I do: 
```
kvno HTTP/testkrb.mydomain.example
HTTP/testkrb.mydomain.example@MYDOMAIN.EXAMPLE: kvno = 3
```

So it seems to work and the KVNO are the same.

My authentication configuration in apache is this:

```
AuthType Kerberos
AuthName "Kerberos Testing"
KrbAuthRealms mydomain.example
KrbServiceName HTTP/testkrb.mydomain.example@MYDOMAIN.EXAMPLE
Krb5Keytab /etc/apache2/testkrb.keytab
KrbMethodNegotiate On
KrbMethodK5Passwd On
Require valid-user
```

For some reason, I can't get this to work. Here's an example of a client coming in with Internet Explorer with the logs set to debug:

```
[Thu Dec 14 10:39:28.145228 2017] [authz_core:debug] [pid 28913] mod_authz_core.c(809): [client 123.123.123.123:4708] AH01626: authorization result of Require valid-user : denied (no authenticated user yet)
[Thu Dec 14 10:39:28.145297 2017] [authz_core:debug] [pid 28913] mod_authz_core.c(809): [client 123.123.123.123:4708] AH01626: authorization result of <RequireAny>: denied (no authenticated user yet)
[Thu Dec 14 10:39:28.145321 2017] [auth_kerb:debug] [pid 28913] src/mod_auth_kerb.c(1971): [client 123.123.123.123:4708] kerb_authenticate_user entered with user (NULL) and auth_type Kerberos
[Thu Dec 14 10:39:28.145346 2017] [auth_kerb:debug] [pid 28913] src/mod_auth_kerb.c(1299): [client 123.123.123.123:4708] Acquiring creds for HTTP/testkrb.mydomain.example
[Thu Dec 14 10:39:28.146767 2017] [auth_kerb:debug] [pid 28913] src/mod_auth_kerb.c(1722): [client 123.123.123.123:4708] Verifying client data using KRB5 GSS-API with our SPNEGO lib
[Thu Dec 14 10:39:28.146908 2017] [auth_kerb:debug] [pid 28913] src/mod_auth_kerb.c(1738): [client 123.123.123.123:4708] Client didn't delegate us their credential
[Thu Dec 14 10:39:28.146927 2017] [auth_kerb:debug] [pid 28913] src/mod_auth_kerb.c(1757): [client 123.123.123.123:4708] GSS-API token of length 9 bytes will be sent back
[Thu Dec 14 10:39:28.146936 2017] [auth_kerb:debug] [pid 28913] src/mod_auth_kerb.c(1159): [client 123.123.123.123:4708] GSS-API major_status:000d0000, minor_status:96c73a2d
[Thu Dec 14 10:39:28.146944 2017] [auth_kerb:error] [pid 28913] [client 123.123.123.123:4708] gss_accept_sec_context() failed: Unspecified GSS failure.  Minor code may provide more information (, No key table entry found for HTTP/testkrb.mydomain.example@MYDOMAIN.EXAMPLE)
```

It shouldn't ask for a password but it does and then even if the password is right, it doesn't work.
  
I can only find 3 reference to minor_status:96c73a2d on google and they don't fix my issue.

I've been trying so many things, I am out of ideas. Anyone sees anything wrong here?

Thanks

---

