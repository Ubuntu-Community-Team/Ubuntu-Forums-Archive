---
title: "Apache 2.2 LDAP"
date: 2007-07-20
forum: Server Platforms
---

### Post by skyguy85 on 2007-07-20
I have been trying to connect the apache server up to a MS Active Directory server with no success. I have recently discovered though that there are new updates to the way Apache handles LDAP authentication but these don't seem to be implemented in Ubuntu yet and I can't seem to get it to work on my own.

Apache now uses a mod_authnz_ldap instead of the old mod_auth_ldap. This new method doesn't seem to want to work on the latest version of ubuntu though. Is there a module to install that I have likely missed. I thought it was pretty standard and included in apache.

Can someone please help me out with some instructions and maybe an example of how to get this to work. Thanks.

---

### Post by MMoudry on 2007-07-23
Hi,
I've only managed ever to get the LDAP working on Apache 2.2.4. Since the Ubuntu package is 2.2.3 I am not sure if it will work as well (it might). The SSL-AD connection gives a segfault so you'll have to use a normal ldap:// instead of ldaps://

Here is an extract from my httpd.conf:

# LDAP Config
LDAPSharedCacheSize 200000
LDAPCacheEntries 1024
LDAPCacheTTL 600
LDAPOpCacheEntries 1024
LDAPOpCacheTTL 600

# Subversion Location
<Location /yoururilocation/>
	AuthzLDAPAuthoritative off
 
	# LDAP Authentication parameters
	AuthBasicProvider ldap
	AuthType Basic
	AuthLDAPBindDN LdapUsernameToUseToConnect
	AuthLDAPBindPassword LdapPasswordToUseToConnect
	AuthLDAPURL ldap://server/OU=orgunit,dc=yourcompany,dc=com?sAMAccountName?sub?(objectClass=User)
	AuthName "MyURITitle"

	# only authenticated users may access the repository
	Require valid-user
</Location>

There, Let me know if you have any more questions,

MM

---

