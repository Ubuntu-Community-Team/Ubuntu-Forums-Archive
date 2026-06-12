---
title: "Apache2 authentication"
date: 2005-03-02
forum: Server Platforms
---

### Post by maitreya on 2005-03-02
Problem: can't get apache authentication/authorization to accept login and password. Still asking for login/password after entering the correct one.

Created a private directory: /var/www/html/private

Created a new password file for test:test in
/var/www/passwd/passwords

Added the following line to the config file

	<Directory /var/www/html/private>
		AuthType Basic
		AuthName "Restricted Files"
		AuthUserFile /var/www/passws/passwords
		Require test
	</Directory>

Also tried with a .htaccess file with the above line in the private directory and the AllowOverride AuthConfig in the apache configuration file, but it is still prompts after authorization after entering test:test.

Any help would be appreciated

---

### Post by maitreya on 2005-03-02
[QUOTE=maitreya]<Directory /var/www/html/private>
		AuthType Basic
		AuthName "Restricted Files"
		AuthUserFile /var/www/passws/passwords
		Require test
	</Directory>
[/QUOTE]

Sorry problem solved. Wrong path.
Should be /var/www/passwd/passwords

---

