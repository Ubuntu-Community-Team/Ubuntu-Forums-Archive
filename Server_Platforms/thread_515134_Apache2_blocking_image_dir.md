---
title: "Apache2 blocking /image dir"
date: 2007-08-01
forum: Server Platforms
---

### Post by brooksbp on 2007-08-01
Just did a fresh install of Apache2.  I noticed that the dirs are left open... anyone can browse my image dir.

How do you restrict stuff like this?

---

### Post by mathewb on 2007-08-01
run the following:
```
sudo gedit /etc/apache2/sites-available/default
```

enter the password and a text editor should open up. This is the apache site config file. Find the <Directory "/var/www/"> section. Inside there is a line called "Options Indexs...". Take out the word "Indexes", and directory listing will be disabled. When done it should look like:
```

...
	<Directory /var/www/>
		Options FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
	</Directory>
...

```

---

### Post by mathewb on 2007-08-01
Or, to just apply the blocking to /images add the following section after the /var/www section:
```

	<Directory /var/www/images/>
		Options FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

```

---

