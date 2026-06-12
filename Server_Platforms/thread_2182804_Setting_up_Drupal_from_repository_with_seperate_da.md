---
title: "Setting up Drupal from repository with seperate database server"
date: 2013-10-22
forum: Server Platforms
---

### Post by bcm37 on 2013-10-22
I am setting up a Drupal server on 12.04 LTS. I installed 7 as per:[[https://help.ubuntu.com/community/Drupal]](https://help.ubuntu.com/community/Drupal]), however since it's policy that my database reside on a separate server, I declined the database setup in the installer.

In looking at the documentation mentioned and at [[https://drupal.org/documentation/install/]](https://drupal.org/documentation/install/]) I have come to a couple of questions.

It seems that the default installation puts the config file at /etc/drupl/7/sites/default, I do not have /var/www/drupal/ directory and sub-directories as is in the manual install, should I go ahead and create that as well? Should I continue from there the manual installation?

---

### Post by SeijiSensei on 2013-10-22
I haven't installed drupal for quite a while, but isn't it possible to specify a remote host and port for the database location during the installation?

---

### Post by tgalati4 on 2013-10-22
I would go ahead and perform the local database installation first, test everything, add a few dummy content pages, and make sure it works first.  Then I would go onto the drupal forums and search for remote database setup.  Why does the database have to be separate from the server?  This policy seems like something that is needed for a Windows server, but not a linux server.  Besides, you might take a serious performance hit that will make the website crawl when it gets large.

---

### Post by SeijiSensei on 2013-10-22
> **tgalati4 said:**
> Why does the database have to be separate from the server?  This policy seems like something that is needed for a Windows server, but not a linux server.  Besides, you might take a serious performance hit that will make the website crawl when it gets large.

Not to mention that it makes the website more fragile since it will fall over if there is a network problem.

---

### Post by bcm37 on 2013-10-22
> **tgalati4 said:**
> I would go ahead and perform the local database installation first, test everything, add a few dummy content pages, and make sure it works first.  Then I would go onto the drupal forums and search for remote database setup.  Why does the database have to be separate from the server?  This policy seems like something that is needed for a Windows server, but not a linux server.  Besides, you might take a serious performance hit that will make the website crawl when it gets large.

I work a small department in a big bureaucracy. It was determined that any database that *could* contain sensitive info be on a non-public IP address. Since a web sever is a public IP address, that's a no-go, and frankly easier than trying to explain to someone it's not sensitive. It's not so many people that we're worried about performance. Probably 30-50 at any one time, and no prospects for any major change in the next couple of decades, and everything is on the same virtual host.

I tried a couple of different things... looked around a little more. Its only the repository that's pushing mySql, and maybe it shouldn't. I was also a little confused with the setup instructions, I now see that the database is configured for Drupal in the browser, and doesn't need to be preconfigured in settings for the browser settings to continue.

It seems the repository doesn't contain "default.settings.php" and I had to copy it back from settings.php to get it to continue. Also, settings.php did not have its permissions set to allow it to be written to by the browser setup. I don't know if that's an error or just not cited as a step.

I'm getting three notices: "Undefined index: distribution_name() (line 196 of /usr/share/drupal7/includes/install.inc)", "Undefined offset:0 in Database::openConnection() (line 1510 of /usr/share/drupal7/includes/database/database.inc)", "Undefined index: driver in Database::openConnection() (line 1662 of /usr/share/drupal7/includes/database/database.inc)". 

It seems that the firewall permissions for this server didn't go through yet, so I can't say if everything is fine, but the options are there for using a non-local server.

It should be noted that the directory under etc is where the repository install leaves the files, and not in www or htdocs as other guides or the manual install indicate.

Hopefully those notes help the next person, and I'll report back when the rules go through if everything works correctly.

---

### Post by SeijiSensei on 2013-10-22
> **bcm37 said:**
> It seems that the default installation puts the config file at /etc/drupl/7/sites/default, I do not have /var/www/drupal/ directory and sub-directories as is in the manual install, should I go ahead and create that as well? Should I continue from there the manual installation?

No, you shouldn't need that if you copied the apache2.conf file over to mods-enabled as the directions suggest.

> **bcm37 said:**
> I work a small department in a big bureaucracy. It was determined that any database that *could* contain sensitive info be on a non-public IP address.

I wrote an application a while back for a health center.  To comply with HIPAA regulations, I had to put the database with patient information on another server (and encrypt everything in it to boot).  So I appreciate those sorts of organizational limitations.

> 
I tried a couple of different things... looked around a little more. Its only the repository that's pushing mySql, and maybe it shouldn't. I was also a little confused with the setup instructions, I now see that the database is configured for Drupal in the browser, and doesn't need to be preconfigured in settings for the browser settings to continue.

I'm getting three notices: "Undefined index: distribution_name() (line 196 of /usr/share/drupal7/includes/install.inc)", "Undefined offset:0 in Database::openConnection() (line 1510 of /usr/share/drupal7/includes/database/database.inc)", "Undefined index: driver in Database::openConnection() (line 1662 of /usr/share/drupal7/includes/database/database.inc)". 


The two Database:: errors mean that the connection cannot be made.  Take a look at [this post](http://ubuntuforums.org/showthread.php?t=2182846&p=12824861&viewfull=1#post12824861) which discusses problems that can arise when using a default MySQL configuration in a setting where the server resides on a different machine.

You did already install a copy of MySQL on the database server, right?  Nothing will work correctly until you have done that.

---

### Post by tgalati4 on 2013-10-22
Yes, it seems that drupal installations purposely leave out a few steps to keep you on your toes.  #-o

There are several php settings that need to be tweaked, so keep your eye out for them.  Mostly memory and cache settings in php.ini.

---

### Post by bcm37 on 2013-10-23
> **SeijiSensei said:**
> 
The two Database:: errors mean that the connection cannot be made.  Take a look at [this post]("http://ubuntuforums.org/showthread.php?t=2182846&p=12824861&viewfull=1#post12824861") which discusses problems that can arise when using a default MySQL configuration in a setting where the server resides on a different machine.

You did already install a copy of MySQL on the database server, right?  Nothing will work correctly until you have done that.

Yup. I have a database server up and running. Thanks for your help.

---

### Post by bcm37 on 2013-11-04
So far... slightly better.

I am getting the following:
```


[LIST]
[*]*Notice*: Undefined index: distribution_name in*drupal_install_profile_distribution_name()* (line *196* of*/usr/share/drupal7/includes/install.inc*).
[*]*Notice*: Undefined offset: 6 in *Database::parseConnectionInfo()* (line *1510*of */usr/share/drupal7/includes/database/database.inc*).
[*]*Notice*: Undefined index: driver in *Database::openConnection()* (line *1662*of */usr/share/drupal7/includes/database/database.inc*).
[/LIST]

```

I tried the patch at [https://drupal.org/node/1170360](https://drupal.org/node/1170360) with no help.

Database tables are being populated, but the installer goes back to "Database Configuration" when I "Save and Continue"

---

### Post by bcm37 on 2013-11-04
I also had to make /var/lib/drupal7/files writable and executable, and make /etc/drupal/7/sites/default/dbconfig.php read/write.

does defaultsettings.php need to be writable as well?

---

### Post by bcm37 on 2013-11-06
Well, after going though everything, the repository package is definitely broken. It doesn't work.

Just download it from [https://drupal.org/project/drupal](https://drupal.org/project/drupal) and save yourself some hassle.

Make sure that the web server has write access to the correct files and directories, it will create the "files" directory if it has permission to do so. I did not have to copy the settings file, however that may have been due to the several attempts, so check before you copy.

---

