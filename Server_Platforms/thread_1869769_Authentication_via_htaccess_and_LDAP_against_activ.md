---
title: "Authentication via htaccess and LDAP against active directory"
date: 2011-10-26
forum: Server Platforms
---

### Post by Panchorizo on 2011-10-26
Hi

I'm running apache 2.2 on ubuntu 10.04 and on the other side a MS Small Business Server with an Active Directory. 
I want to grant access to a website only to members of the Active Directory, so I try to use the mod_authnz_ldap module of apache.
So I use this:
```

Alias /new "/var/www/newportal"
<Directory /var/www/newportal>
  Options -Indexes -FollowSymLinks
  AllowOverride None
  Order deny,allow
  Deny from All
  Allow From 192.168
  AuthType Basic
  AuthName "Please use your Windows login"
  AuthBasicProvider ldap
  AuthLDAPURL ldap://sbs-server.example.local:389/ou=MyBusiness,ou=Users,ou=SBSUsers,dc=sbs-server,dc=example,dc=local?sAMAccountName?sub?
  AuthLDAPBindDN cn=Apacheldap,ou=MyBusiness,ou=Users,ou=SBSUsers,dc=sbs-server,dc=example,dc=local
  AuthLDAPBindPassword 1234
  AuthzLDAPAuthoritative off
  Require valid-user
</Directory>

```

But logging in won't work (login window appears). Apache throws this error:
```

[Wed Oct 26 12:06:44 2011] [warn] [client 192.168.0.XX] [25152] auth_ldap authenticate: user XXXXX authentication failed; URI /new **[LDAP: ldap_simple_bind_s() failed]**[Invalid credentials]
[Wed Oct 26 12:06:44 2011] [error] [client 192.168.0.XX] user XXXXX: authentication failure for "/new": Password Mismatch

```
It seems LDAP won't bind. The credentials are correct and the user "Apacheldap" has permission to search the directory.

Does anyone have an idea?

---

### Post by luvshines on 2011-10-27
Don't know if this helps or not, maybe just a sanity check. Validate ldapsearch from the machine using same creds:```
ldapsearch -x -H ldap://sbs-server.example.local:389 -D cn=Apacheldap,ou=MyBusiness,ou=Users,ou=SBSUsers,dc=sbs-server,dc=example,dc=local -w 1234 -b ou=MyBusiness,ou=Users,ou=SBSUsers,dc=sbs-server,dc=example,dc=local -s sub 'sAMAccountName'
```

---

### Post by Panchorizo on 2011-10-31
This is the outcome:
```

ldap_bind: Invalid credentials (49)
	additional info: 80090308: LdapErr: DSID-0C090334, comment: AcceptSecurityContext error, data 525, vece

```
Still says the same thing: Invalid credentials.
I'm still trying to figure our what the second line means. I'll google it...

---

### Post by Panchorizo on 2011-10-31
Okay, it seems that a connection to the Active Directory can be established. Also "data 525" means "User Not Found". The user (and password) are 100% correct. I tried with the user "Admin", too, which MUST exist. Still the user was not found. I'm running out of options...

---

### Post by luvshines on 2011-11-02
> **Panchorizo said:**
> Okay, it seems that a connection to the Active Directory can be established. Also "data 525" means "User Not Found". The user (and password) are 100% correct. I tried with the user "Admin", too, which MUST exist. Still the user was not found. I'm running out of options...

Is the DC serving the domain 'sbs-server.example.local'

Maybe you can also try [ with administrator user/password]```

## Enter the password when it prompts for
ldapsearch -x -H ldap://sbs-server.example.local:389 -D administrator@sbs-server.example.local -W -b "" -s base 'defaultNamingContext'
```

---

