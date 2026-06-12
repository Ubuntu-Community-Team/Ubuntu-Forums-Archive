---
title: "Authenticate to Active Directory"
date: 2010-01-13
forum: Server Platforms
---

### Post by richcoosa19 on 2010-01-13
Ubuntu LTS 8.04 Hardy 32 bit
 Server version: Apache/2.2.8 (Ubuntu)

I am wanting to use Apache2::AuthenNTLM authentication module for Apache in our Local corporate network.  Are both LDAP and Kerberos 5 required for this to work properly?  The authentication module works perfectly for the most part out of the box. The problem is some authentication requests seem to take longer and from time to time make the applications I am running VERY slow.  I am thinking in this direction due to my Apache logs:

Bad/Missing NTLM/Basic Authorization Header for (blah blah blah file)

and this post referring to the issue being winbind related:
[http://sivel.net/2007/05/sso-apache-ad-1/#comment-1375]("http://sivel.net/2007/05/sso-apache-ad-1/#comment-1375")

Any thoughts / suggestions?  I really do not want to have to setup LDAP and Kerberos just for this authentication, but if this is the fix then so be it....

:roll:

---

### Post by R.Bucky on 2010-01-15
I am not sure if this is what you are looking for. But, I joined my Ubuntu 9.10 to my AD domain last week using likewise-open. Works beautifully.
[http://buckycomputing.net/blog/how-to-join-ubuntu-to-microsoft-active-directory-domain-using-likewise-open/]("http://buckycomputing.net/blog/how-to-join-ubuntu-to-microsoft-active-directory-domain-using-likewise-open/")

---

### Post by samosamo on 2010-01-16
I also suggest Likewise Open

---

### Post by TwoWordz on 2010-03-11
Likewise has nothing to do with apache authentication. 

What you are looking for is mod_authn_ldap.

Here is an example for apache:

```
<Location "/">
        AuthBasicProvider ldap
        AuthType Basic
        AuthzLDAPAuthoritative on
        AuthName "Subversion server"
        AuthLDAPURL "ldap://192.168.1.15:3268/DC=example,DC=local?sAMAccountName?sub?(objectClass=*)" NONE
        AuthLDAPBindDN "ldapauth@example.local"
        AuthLDAPBindPassword secret
        require ldap-group CN=A_Group,OU=People,OU=Security Groups,OU=MyBusiness,DC=example,DC=local
</Location>
```

This is a redhat configuration, IIRC the port is 389 on ubuntu because it doesn't use the same ldap module. You will have to do some homework here...

TW

---

### Post by koenn on 2010-03-11
similar thread here
[http://ubuntuforums.org/showthread.php?p=8950765#post8950765](http://ubuntuforums.org/showthread.php?p=8950765#post8950765)

---

