---
title: "apache2 ldap authentication"
date: 2011-12-02
forum: Server Platforms
---

### Post by talkingtek on 2011-12-02
How would I get Active Directory users to access the intranet on Ubuntu 10.04?
I can allow or deny from specify ip address, but that's not what I need.  I need users to login with their windows domain credential at the prompt.  the following is what I have so far.  I got a prompt to sign in but it doesn't matter which user I try it won't allow me to sing in.

/sites-available/default

<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		#allow from all
		#deny from 192.168.11
Order allow,deny
allow from all
# Using this to bind
AuthLDAPBindDN "OU=IT-users,Support Services,OU=WA,OU=MCPL,dc=horizon,dc=local"
AuthLDAPBindPassword "XXX"
# search user
AuthLDAPURL "ldap://192.168.101.10/ou=mcpl,dc=horizon,dc=local?sAMAccountName?sub?(objectClass=*)"

AuthType Basic
AuthName "Use Your Windows Login"
AuthBasicProvider ldap
# Important, otherwise "(9)Bad file descriptor: Could not open password file: (null)"
AuthUserFile /dev/null
require valid-user
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>
	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

thank you!

---

