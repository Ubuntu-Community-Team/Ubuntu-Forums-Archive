---
title: "Where does apache mod_ldap look for certs"
date: 2014-11-25
forum: Server Platforms
---

### Post by citaliano on 2014-11-25
Hello,


I've done countless Google searches and haven't been able to solve this, so I figured I'd bring it here. I am trying to get mod_ldap authentication working in apache2 on ubuntu 14.04 for one specific web page. I am able to get it to work on the non secure ldap port, 389. When I try it on port 636, I get the "Can't Contact Ldap Server" error which basically means it couldn't verify the certificate. It should be noted that I can get the connection to work on 636 if I set the LDAPVerifyServerCert directive to off. This setting is obviously not desirable.


Anyway, here is my apache config :

```
<VirtualHost *:80>
        ServerName www.example.com
        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/html
        <Directory /var/www/html>
                AuthLDAPUrl ldaps://exampleldap.com:636/OU=Accounts,dc=example,dc=com?cn
                LDAPTrustedClientCert CERT_BASE64 /etc/ssl/certs/ca-certificates.crt
                require valid-user


                Options -Indexes -FollowSymLinks
                AuthType Basic
                AuthName "Please Enter Your Credentials"
                AuthBasicProvider ldap
                AuthLDAPBindDN cn=proxyAccount,ou=Accounts,dc=example,dc=com
                AuthLDAPBindPassword password
        </Directory>
</VirtualHost>
```

And with this config, I get a lot of this in the apache2 error log :

```
ldap_simple_bind() failed with server down (try 1)
```

I have verified that the cert in /etc/ssl/certs/ca-certificates.crt works by performing an ldapsearch using all of the same parameters. I had obtained the certificate with the following command:

```
openssl s_client -connect exampleldap.com:636 -showcerts
```
There must be a specific place that mod_ldap looks for the certificates or perhaps a different directive to let apache know where the cert is, I just can't figure it out. Any help or suggestions are much appreciated.

---

