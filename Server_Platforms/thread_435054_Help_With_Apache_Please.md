---
title: "Help With Apache Please"
date: 2007-05-06
forum: Server Platforms
---

### Post by Tridion2000 on 2007-05-06
I installed Feisty Desktop on my PC and then decided I wanted to do a little web development just for fun really. Rather than install Feisty Server, I just went into Synaptics app and installed by task "LAMP Server" which installed Apache, MySQL, PHP, etc.

However I am now at a loss. I've worked out that the web files go in /var/www but had to connect as root in natilus to put files in there. Main problem is that I thought I'd start by taking a look at Joomla. Put all the Joomla files in /var/www and opened localhost in firefox. Joomla complains that none of the files or directories are writable.

How do I correct this? Also is there a simple GUI I can use for Apache admin. I hate command lines (yes I'm a Linux noob).

---

### Post by mlind on 2007-05-06
It's probably better to use Apache's userdir module (mod_userdir) which should be enabled by default is feisty. Then just create public_html folder in your home directory and do your development stuff locally.

```

sudo a2enmod userdir
mkdir ~/public_html

```

then point your browser to [http://localhost/~**user**](http://localhost/~**user**) where **user** is your login name.

---

### Post by Tridion2000 on 2007-05-06
Tried that but it doesn't work. Anyone else have any ideas?

---

### Post by mlind on 2007-05-06
> **Tridion2000 said:**
> Tried that but it doesn't work. Anyone else have any ideas?

Could you be more specific what doesn't work?
There was a thread about userdir few days back [http://ubuntuforums.org/showthread.php?t=421076](http://ubuntuforums.org/showthread.php?t=421076)

This should work for you too [http://ubuntuforums.org/showpost.php?p=2525158&postcount=12](http://ubuntuforums.org/showpost.php?p=2525158&postcount=12)

---

### Post by Tridion2000 on 2007-05-06
Tried that, Joomla still says that all directories and files are read only. Anyone else able to help?

As well as that I don't want to type [http://localhost/~user](http://localhost/~user) I want it to be [http://localhost](http://localhost).

---

### Post by mlind on 2007-05-06
> **Tridion2000 said:**
> Tried that, Joomla still says that all directories and files are read only. Anyone else able to help?

As well as that I don't want to type [http://localhost/~user](http://localhost/~user) I want it to be [http://localhost](http://localhost).

Okay then.. 

If you put your stuff to /var/www
```

$ ls -la  /var/www/
total 12
drwxr-xr-x  3 root root 4096 2007-04-23 21:28 .
drwxr-xr-x 16 root root 4096 2007-04-23 21:28 ..
drwxr-xr-x  2 root root 4096 2007-05-05 00:53 apache2-default

```
You see that this directory is owned by root, and "others" don't have write permission
as required by your application.

Create new subdirectory to /var/www and chmod it with o+rw (or that www-data group has g+rw and chroup it to www-data). Then place your stuff in there. Or you can create this directory to somewhere else, and use Apache's Alias directive to make it visible in server root.

Using userdir is safer though, you don't need to mess with permissions or additional stuff that may break your apache. Is writing [http://localhost/~tridion/joomla](http://localhost/~tridion/joomla) that hard?
(btw. you did copy your application to ~/public_html and made sure that the application directory has www-data group with g+rw or even  o+rw permissions?)

---

### Post by Tridion2000 on 2007-05-06
Following that now gives me the following in firefox:

Internal Server Error

The server encountered an internal error or misconfiguration and was unable to complete your request.

Please contact the server administrator, webmaster@localhost and inform them of the time the error occurred, and anything you might have done that may have caused the error.

More information about this error may be available in the server error log.


I am going backwards. At least before I could see the directories. Thanks for your attempt at helping mlind but could someone else help out here please. I think my apache installation is now screwed.

---

### Post by mlind on 2007-05-06
yeah, no problem. I hope you get it fixed. Just don't go changing permissions or ownership of /var/www or you'll get into problems. I'll suggest to read the apache docs about [Alias directive]("http://httpd.apache.org/docs/2.2/mod/mod_alias.html") and [mod_userdir]("http://httpd.apache.org/docs/2.2/mod/mod_userdir.html") before continuing.

---

### Post by mudoch on 2007-05-06
Ok first I too am new at this and I too had your issue using the /var/www folder. I did lots of digging here and found a suggestion.   

Not sure about the security risks but it did work.

I run the following on the joomla folder.   I replaced the ??????? with the folder I wanted to alter.

sudo chown -hR www-data:www-data /var/www/??????

One thing I found is that I also need phpMyAdmin to manage the DB (MySQL) it is a web tool (used through your web browser) Also BE SURE to Check About MYSQL config. there are docs on setting up the Root password for MYSQL, YOU REALLY SHOULD SET THIS and then through phpMyAdmin add a user that will be used by Joomla to access the joomla dbs.

BTW I´m doing the same thing as You.  Setting up web (LAMP) trying different CMS tools.   If you do not know about it look up [http://www.opensourcecms.com/](http://www.opensourcecms.com/) for a site that demos several CMS.

Larry

---

