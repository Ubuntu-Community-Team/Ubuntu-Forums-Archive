---
title: "Problem installing Wordpress on Ubuntu Server installed in a Virtual Box VM"
date: 2020-07-30
forum: Virtualisation
---

### Post by matthorton2 on 2020-07-30
Hi Everyone, 

I'm having a bit of trouble setting up Wordpress on Ubuntu Server.

I've followed this guide: [https://ubuntu.com/server/docs/lamp-applications](https://ubuntu.com/server/docs/lamp-applications)

When I got to the end, I went to: [http://192.168.1.24/blog/wp-admin/install.php](http://192.168.1.24/blog/wp-admin/install.php) .. but I get the error:[INDENT]Neither /etc/wordpress/config-192.168.1.24.php nor /etc/wordpress/config-168.1.24.php could be found. [/INDENT]
[INDENT]Ensure one of them exists, is readable by the webserver and contains the right password/username.[/INDENT]

I'm not sure where to go from here. 

Another thing I noticed is that putting ubuntu-web-server.local into my browser doesn't work but 192.168.1.24 shows an Apache Page

Thanks



EDIT: I can confirm that neither /etc/wordpress/config-192.168.1.24.php nor /etc/wordpress/config-168.1.24.php exist. I have /etc/wordpress/config-localhost.php instead.

EDIT: I renamed /etc/wordpress/config-localhost.php to /etc/wordpress/config-192.168.1.24.php - Didn't work

EDIT: Networking on my VM is in Bridged mode

---

### Post by SeijiSensei on 2020-07-30
I don't who wrote those instructions, but I can't imagine ever using /etc/wordpress.

If you create a default installation of Apache, for instance using the lamp-server method, then the default directory for all sites is /var/www/html.

Get the most recent ZIP file for WordPress, then create a directory for it and unzip the file there.

```

cd /var/www/html
sudo mkdir wordpress
cd wordpress
sudo unzip /path/to/latest.zip

```

Restart Apache with "sudo systemctl restart apache2".

Now create an empty MySQL database if you haven't done so already.  See [https://www.digitalocean.com/community/tutorials/a-basic-mysql-tutorial#how-to-create-and-delete-a-mysql-database](https://www.digitalocean.com/community/tutorials/a-basic-mysql-tutorial#how-to-create-and-delete-a-mysql-database).  I'd use the "create database" command to set up a separate database for the WP installation, say "create database wordpress".  You might consider creating a separate username and password for this database as well.

Now open a browser and point it to [http://ip.addr.of.server/wordpress/wp-config.php](http://ip.addr.of.server/wordpress/wp-config.php).  It should walk you through the rest of the installation.

---

### Post by matthorton2 on 2020-07-30
Hi thanks for the reply. I might try this at some point, but I've actually just remembered TurnKey linux. I've used their wordpress appliance to set up a server and so far so good! It also includes a nice management control panel.

---

### Post by TheFu on 2020-08-01
When it comes to Wordpress stuff, I listen to SeijiSensei.
Easier setup methods are only easier for the first 10 days.  After that, they become a nightmare to secure and maintain.  It is common for there to be about 1 million hacked wordpress sites on the internet.  Know all those phishing emails we all get? Most have deep URLs into hacked content management systems, like wordpress.

---

### Post by SeijiSensei on 2020-08-01
Yes, you'll need to upgrade your WP installation when new versions are released to avoid security holes.  You'll see a notice in the site's "Dashboard" when there is a pending upgrade.

That said, I usually run a couple of simple scripts to adjust ownerships in the wordpress directory. By default the webserver can write into this directory which is a big security hole.  On my systems I have a phony user that owns /var/www/html/wordpress, say "wpuser", and the files contained therein.  I put this user in the "www-data" group

```
sudo useradd -G www-data wpuser
```

and run this script when I need to update the installation:

```
$ more /usr/local/sbin/wpupdate-pre

#!/bin/sh
chmod g+w wp-admin wp-includes wp-content -R
chmod g+w *
echo "Run update now"

```

When the update is completed I run
```

$ more /usr/local/sbin/wpupdate-post

#!/bin/sh
chmod g-w wp-admin wp-includes wp-content -R
chmod g-w *

```

---

