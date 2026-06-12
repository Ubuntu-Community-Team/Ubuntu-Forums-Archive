---
title: "Apache2 Setup for New Sites"
date: 2014-10-26
forum: Server Platforms
---

### Post by MikeyDL on 2014-10-26
I usually use Ubuntu server on Virtualbox to setup new Joomla test sites.  With the new version out security settings have changed in apache2.  Currently it will only allow me to display the index.html file from the /var/www/html directory.  However, I need to copy Joomla to a sub directory and run index.php files from there (I already have copied files over to /var/www/Joomla_3).  Doing a quick google search providing me with the following info on others having similar problems.

***** START OF SUPPORT TEXT ****

In my Ubuntu 14.04 LTS, the document root was set to /var/www/html. It was configured in the following file:

/etc/apache2/sites-available/000-default.conf

So just do a

sudo nano /etc/apache2/sites-available/000-default.conf

and change the following line to what you want:

DocumentRoot /var/www/html

Also do a

sudo nano /etc/apache2/apache2.conf

and find this

<Directory /var/www/html/>
Options Indexes FollowSymLinks
AllowOverride None
Require all granted
</Directory>

and change /var/www/html to your preferred directory
and save it.

After you saved your changes, just restart the apache2 webserver and you'll be done :)

sudo service apache2 restart


If you prefer a graphical text editor, you can just replace the sudo nano by a gksu gedit.

**** END OF SUPPORT TEXT *****

The problem is that even after editing the referenced files my Apache site keeps pulling up index.html.  Any suggestions on what I might be missing?

Thanks!

---

### Post by Lars Noodén on 2014-10-26
I would leave /etc/apache2/apache2.conf alone and only make changes in the vhost's own configuration file.  Otherwise things will get mixed up.  

About the indexing of the PHP file, have you enabled the PHP5 module?

```

sudo a2enmod php5

```

If so, then check to be sure that your [DirectoryIndex](http://httpd.apache.org/docs/2.4/mod/mod_dir.html#directoryindex) directive is configured to include an index.php option.

---

