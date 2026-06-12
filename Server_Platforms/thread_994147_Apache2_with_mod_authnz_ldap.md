---
title: "Apache2 with mod_authnz_ldap"
date: 2008-11-26
forum: Server Platforms
---

### Post by MarkHowells on 2008-11-26
Hi,

First up I'm no ldap expert, so if this is a dumb question I apologize (please point me at a good starting point ... :)

I'm trying to use an LDAP server that generates one-time passwords. There's little in the way of technical docs for it but I do have the following example command that gives good results.

```
ldapsearch -v -x -h 10.0.0.247 -p 10389 -b 'ou=wikid' -D 'uid=lduser,domain=010000000247' -W '(objectclass=*)'
```

I'm trying to set up an htaccess that will auth a user against the server and I'm struggling big-time.

What I have tried do far is (using a user called lduser and a OTP)

.htaccess
```
AuthName "LDAP"
AuthLDAPUrl ldap://10.0.0.247:10389/ou=wikid?uid
AuthLDAPBindDN domain=010000000247
AuthBasicProvider ldap
AuthType basic
AuthBasicAuthoritative off
AuthzLDAPAuthoritative on
require valid-user

```
which results in the following in the apache error_log (I do supply the right user/pass combo...).

```
[Wed Nov 26 18:28:46 2008] [warn] [client 10.0.0.85] [5208] auth_ldap authenticate: user lduser authentication failed; URI /ldaptest [LDAP: ldap_simple_bind_s() failed][Invalid credentials]
[Wed Nov 26 18:28:46 2008] [error] [client 10.0.0.85] user lduser: authentication failure for "/ldaptest": Password Mismatch

```

and .htaccess
```
AuthName "LDAP"
AuthLDAPUrl ldap://10.0.0.247:10389/ou=wikid?uid??domain=010000000247
AuthBasicProvider ldap
AuthType basic
AuthBasicAuthoritative off
AuthzLDAPAuthoritative on
require valid-user

``` 
which results in an entry in error_log ```
[Wed Nov 26 18:14:35 2008] [warn] [client 10.0.0.85] [5168] auth_ldap authenticate: user lduser authentication failed; URI /ldaptest [User not found][No such object]
[Wed Nov 26 18:14:35 2008] [crit] [client 10.0.0.85] configuration error:  couldn't check user.  No user file?: /ldaptest

```

I obviously don't quite get the use of the 'domain' attribute (I mean I know what it does, but not its' relevance to the URL I need to use). Any ideas and advice would be appreciated. 

Many thanks

Mark

---

### Post by Titan8990 on 2008-11-26
No expert but when I used openLDAP users had to be defined in this format:


CN=username,DN=mydomain,DN=com

---

### Post by MarkHowells on 2008-11-26
> **Titan8990 said:**
> No expert but when I used openLDAP users had to be defined in this format:


CN=username,DN=mydomain,DN=com

It's an unfortunate choice of attributes, but 'domain' in this environment means authorization domain not inet domain...

I'll experiment with using dn tho (I haven't tried yet...)

Thx Mark

---

### Post by Titan8990 on 2008-11-26
Also, if your LDAP server is a Active Directory domain controller you will always have to specify an organization unit:


CN=username,OU=Users,DN=mydomain,DN=com

---

