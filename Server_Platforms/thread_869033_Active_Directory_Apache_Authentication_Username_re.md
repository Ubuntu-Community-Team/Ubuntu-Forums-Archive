---
title: "Active Directory Apache Authentication Username rewrite"
date: 2008-07-24
forum: Server Platforms
---

### Post by jamessnell on 2008-07-24
Please **HELP**! :)

Howdy, I've got my apache2 server (on 8.04) configured to authenticate users with my Win2K3 Active Directory server.

Currently, connecting users provide their Active Directory username only (no *DOMAIN* prefix is used). This is good and is used by a few different services such as ssh. My problem is that I have a database that has permissions bound to usernames and the usernames currently in the database contain the *DOMAIN* prefix. Thus, user permissions are different than if they had authenticated using *DOMAIN\username*. But since there are a lot of scripts authenticating with the system, getting connecting users to start using the *DOMAIN* prefix would be a serious pain.

I need to change something, possibly in Apache or PAM so that when I give apache a *username*, apache will then connect to pam and authenticate it using the *DOMAIN* as a prefix. Or at least when it tracks the user with the database, the prefix is used.

As it stands, my apache config */etc/apache2/sites-available/default* is:
```

NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	ServerName hellboy	
	DocumentRoot /var/www/

	<Directory />
		AuthType basic
		AuthName "Recall - HTTP is NOT HTTPS"
		AuthPAM_Enabled on
		AuthBasicAuthoritative off
		Require valid-user

		Options FollowSymLinks
		AllowOverride None
	</Directory>
	ErrorLog /var/log/apache2/error.log
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined
	ServerSignature On
</VirtualHost>
```

I suspect this can be taken care of in */etc/pam.d/apache2* or */etc/apache2/sites-available/default* above.

My */etc/pam.d/apache2* is:
```

@include common-auth
@include common-account
```


**Help me** Obiwan Kenobi (or anyone else), you're my only hope.

---

