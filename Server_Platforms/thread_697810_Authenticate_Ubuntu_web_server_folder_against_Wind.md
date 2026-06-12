---
title: "Authenticate Ubuntu web server folder against Windows server AD"
date: 2008-02-15
forum: Server Platforms
---

### Post by dboot on 2008-02-15
I'm moving my website from Windows 2003 (with Exchange, IIS, and AD) to a Debian 4 server. Currently, the website on Windows requires AD authentication in one folder (and everything within) so there's a public portion and a private portion. It was very easy to set up and I want to keep it as simple as possible. 

When I move the website to linux, how do I continue to authenticate a directory against AD on the Windows server?

Thanks!

---

### Post by kevinatkins on 2008-02-15
Hi,

I've done something similar using  Apache, albeit with Apache running on the windows 2003 server - I can't remember exactly, so I'll look it out in the next day or so. It involved using LDAP...

In the meantime, this link might help -

[http://www.debianhelp.co.uk/apachead.htm](http://www.debianhelp.co.uk/apachead.htm)

---

### Post by dboot on 2008-02-26
Thanks for the link! I figured it out following your direction combined with [this link]("http://www.jejik.com/articles/2007/06/apache_and_subversion_authentication_with_microsoft_active_directory/").

To simplify, you need to have several mods installed:
```
$ ls -al /etc/apache2/mods-enabled
alias.load -> ../mods-available/alias.load
auth_basic.load -> ../mods-available/auth_basic.load
authnz_ldap.load -> /etc/apache2/mods-available/authnz_ldap.load
authz_default.load -> ../mods-available/authz_default.load
authz_user.load -> ../mods-available/authz_user.load
ldap.load -> ../mods-available/ldap.load
```

I did this with the command "a2enmod mod_name" (a2enmod ldap, a2enmod authnz_ldap, etc.).

Next you have to edit /etc/ldap/ldap.conf by adding this line:
```
REFERRALS       off
```

Then add the following to your current server setup in /etc/apache2/sites-available/default:

```
	# Authenticates against the Windows Active Directory on adserver.example.com
	<Location "/dir1">
	        AuthBasicProvider ldap
	        AuthType Basic
	        AuthzLDAPAuthoritative off
	        AuthName "Secure Directory"
	        AuthLDAPURL "ldap://adserver.example.com:389/DC=example,DC=com?sAMAccountName?sub?(objectClass=*)" NONE
	        AuthLDAPBindDN "user@example.com"
	        AuthLDAPBindPassword userpassword

	        require valid-user
	</Location>
```

This made webserver.example.com/dir1 authenticate with my AD on adserver.example.com. And, of course, still allowing anyone to access all other directories on webserver.example.com.

---

