---
title: "mod_rewrite problem"
date: 2006-03-15
forum: Server Platforms
---

### Post by VinceDee on 2006-03-15
I'm having problems getting mod_rewrite to work in on my LAMP server, and I can't figure out what's wrong. I've also already googled and searched the forums to no avail:


according to phpinfo.php mod_rewrite is loaded

following the various directions available that are apparently working for everyone else (including the following link):
[http://www.ubuntuforums.org/showthread.php?t=7304&highlight=mod_rewrite](http://www.ubuntuforums.org/showthread.php?t=7304&highlight=mod_rewrite)

1. sudo a2enmod rewrite
2. made sure that the following was in either the apache2.conf, or .htaccess file of whatever website directory I'm working with:

<IfModule mod_rewrite.c>
  RewriteEngine on
</IfModule>

3. modified the /etc/apache2/sites_enabled/000-default.conf file so that the directory entry read:

AllowOverride all

But the progam I'm installing (drupalCMS from drupal.org) on one of my virtual websites says:

"It appears your host is not configured correctly for Clean URLs. Please check for ModRewrite support with your administrator."

Any ideas?

---

### Post by scix on 2007-01-25
I'm have exactly the same problem. Nothing happen when I try to use .htaccess for rewriting

---

### Post by zipperback on 2007-01-28
> **scix said:**
> I'm have exactly the same problem. Nothing happen when I try to use .htaccess for rewriting


Make sure the first line of your .htaccess file says:

RewriteEngine On

---

### Post by HAL98 SE on 2007-01-28
I'm having a similar problem.  if you look in the /mods-available/ dir, it contains a rewrite.**load** but NOT a rewrite.**conf** file, not sure why, or if this has an effect but i'm looking into it atm....

It may have an effect considering most other standard modules appear to have both a **.load** and a **.conf** file, or is rewrite an exception to the rule?

Have tried adding RewriteEngine On to .htaccess but no luck.

SORTED - I set **AllowOverride [COLOR="Red"]all[/COLOR]** in virtualhosts and it solved it

---

