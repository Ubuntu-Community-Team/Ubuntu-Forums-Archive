---
title: "Apache Missing File Icons"
date: 2010-09-09
forum: Server Platforms
---

### Post by cdnjay on 2010-09-09
Hi,

For some reason my directory listings are missing their icons for Apache on Ubuntu Server.  An example:

[http://cconsulting.ca/saskmug/sep_2010/](http://cconsulting.ca/saskmug/sep_2010/)

They all come up not found.  Anyone have any ideas for this?

Thanks,

Jason

---

### Post by MechaMechanism on 2010-09-09
Do you mean the icons in /usr/share/apache2/icons ?

---

### Post by cdnjay on 2010-09-09
> **MechaMechanism said:**
> Do you mean the icons in /usr/share/apache2/icons ?

Yes, I believe so.

---

### Post by MechaMechanism on 2010-09-09
In /etc/apache2/mods-available/ There is a file called alias.conf.  Look at it.

Also make sure you have the index turned on.  sudo a2enmod autoindex You may need to load alias as well if it is not enabled, it should be enabled by default.  sudo a2enmod alias.

Also if you have an /icons/ directory in /www/icons/ that will mess it up too.  If you want icons in /www/ then you need to put /icons/ in a sub directory such as /www/images/icons etc.

Remember to restart apache2, note ubuntu nows uses the service command.
sudo service apache2 restart.

---

### Post by cdnjay on 2010-09-09
> **MechaMechanism said:**
> In /etc/apache2/mods-available/ There is a file called alias.conf.  Look at it.

Also make sure you have the index turned on.  sudo a2enmod autoindex You may need to load alias as well if it is not enabled, it should be enabled by default.  sudo a2enmod alias.

Also if you have an /icons/ directory in /www/icons/ that will mess it up too.  If you want icons in /www/ then you need to put /icons/ in a sub directory such as /www/images/icons etc.

Remember to restart apache2, note ubuntu nows uses the service command.
sudo service apache2 restart.

Here's my alias.conf file:

```
<IfModule alias_module>
#
# Aliases: Add here as many aliases as you need (with no limit). The format is 
# Alias fakename realname
#
# Note that if you include a trailing / on fakename then the server will
# require it to be present in the URL.  So "/icons" isn't aliased in this
# example, only "/icons/".  If the fakename is slash-terminated, then the 
# realname must also be slash terminated, and if the fakename omits the 
# trailing slash, the realname must also omit it.
#
# We include the /icons/ alias for FancyIndexed directory listings.  If
# you do not use FancyIndexing, you may comment this out.
#
Alias /icons/ "/usr/share/apache2/icons/"

<Directory "/usr/share/apache2/icons">
    Options Indexes MultiViews
    AllowOverride None
    Order allow,deny
    Allow from all
</Directory>

</IfModule>

```

Both "autoindex" and "alias" were already enabled.  Restarted Apache2, no change.  I don't have an icons directory or file in the 'www' directory.

Thanks for your help so far.  Any other ideas?

---

### Post by cdnjay on 2010-09-09
I have been having difficulty with some of my other modules however, specifically mod_rewrite.  I wonder if this could be related, could there be some kind of problem between Apache and it's modules?

---

### Post by MechaMechanism on 2010-09-09
I'm stumped on this one.  One thing you could try is putting your /icons/ directory in /www/ and leave everything else the same.  If that don't work then change alias to point right at /www/icons/.  Do you have a non-standard setup.

---

