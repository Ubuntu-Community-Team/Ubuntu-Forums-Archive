---
title: "Apache 1.3 with LDAP authentication"
date: 2007-08-16
forum: Server Platforms
---

### Post by eradan on 2007-08-16
Hello, 

I'm trying to authenticate a web resource published by and Apache1.3 server against my LDAP server. Accordingly to: [http://mod-ldap.sourceforge.net/#tutorial](http://mod-ldap.sourceforge.net/#tutorial)
this is the snippet of my code:

        <Location /mylocation/>
                AuthName "LDAP Authentication"
                AuthType Basic
                LDAPAuth On
                LDAPServer "ldap://delfi.elabor.net:389/"
                ##LDAPBindName cn=manager,dc=elabor,dc=net
                ##LDAPBindPass secret
                LDAPuseridAttr uid
                LDAPBase ou=People,dc=elabor,dc=net
                Require valid-user
        </Location>

I don't need to use LDAPBind Name and Pass because my module doesn't need authentication, but even if I add them, any time I try I have this error on /var/log/apache/error.log:

[Thu Aug 16 10:20:18 2007] [error] access to /mylocation/ failed for 227.143.11.22, reason: ldap bind failed

I thought my apache user (www-data) cannot contact LDAP but I tried this:

su - www-data
ldapsearch -x

and evertything works fine.

Any ideas?
Many Thanks.
Ivan

---

### Post by chombourger on 2007-12-09
It seems that this mod uses LDAPv2 protocol and you may have configured slapd for v3 only (check for allow bind_v2 in /etc/ldap/slapd.conf)

---

### Post by chombourger on 2007-12-09
Also added "LDAPSearchMode subtree" in Location block

Apache is now connecting properly to my LDAP server and finding users but still getting an "authentication failed"

---

