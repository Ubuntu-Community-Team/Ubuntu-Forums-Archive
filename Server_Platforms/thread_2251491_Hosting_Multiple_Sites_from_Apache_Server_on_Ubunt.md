---
title: "Hosting Multiple Sites from Apache Server on Ubuntu"
date: 2014-11-04
forum: Server Platforms
---

### Post by bee2 on 2014-11-04
Hi,

This is something that I have been trying to master, however I don't seem to be getting my head around despite all the reading I have done (hours and hours) on this topic.

Firstly is it actually possible to host multiple websites on my ubuntu based server? It is running Apache and has one IP address, however I would ideally like to have different domains going to different folders in my var/www/ folder. I thought this was called a virtual host? However when I have been reading and trying to set this up, I just don't seem to be able to get it to work.

If anyone is able to help or give me a really basic guide to do this in ubuntu then this would be really appreciated and certainly useful to solve my current issues.

I should add that today I was trying to follow these instructions [here]("https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts"), however these did not seem to work. Have these worked for others and am I just being totally think? :)

---

### Post by Habitual on 2014-11-04
> **bee2 said:**
> Hi,

This is something that I have been trying to master, however I don't seem to be getting my head around despite all the reading I have done (hours and hours) on this topic.

Firstly is it actually possible to host multiple websites on my ubuntu based server? It is running Apache and has one IP address, however I would ideally like to have different domains going to different folders in my var/www/ folder. I thought this was called a virtual host? However when I have been reading and trying to set this up, I just don't seem to be able to get it to work.

If anyone is able to help or give me a really basic guide to do this in ubuntu then this would be really appreciated and certainly useful to solve my current issues.

I should add that today I was trying to follow these instructions [here]("https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts"), however these did not seem to work. Have these worked for others and am I just being totally think? :)

Well, it's called Name-based Virtual Hosts.
Yes, it is possible.
See [http://httpd.apache.org/docs/2.2/vhosts/name-based.html](http://httpd.apache.org/docs/2.2/vhosts/name-based.html) for tips.

---

### Post by sandyd on 2014-11-04
> **bee2 said:**
> Hi,

This is something that I have been trying to master, however I don't seem to be getting my head around despite all the reading I have done (hours and hours) on this topic.

Firstly is it actually possible to host multiple websites on my ubuntu based server? It is running Apache and has one IP address, however I would ideally like to have different domains going to different folders in my var/www/ folder. I thought this was called a virtual host? However when I have been reading and trying to set this up, I just don't seem to be able to get it to work.

If anyone is able to help or give me a really basic guide to do this in ubuntu then this would be really appreciated and certainly useful to solve my current issues.

I should add that today I was trying to follow these instructions [here]("https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts"), however these did not seem to work. Have these worked for others and am I just being totally think? :)

Yes, it it possible.

What section of the guide are you having trouble with?

> **Habitual said:**
> Well, it's called Name-based Virtual Hosts.
Yes, it is possible.
See [http://httpd.apache.org/docs/2.2/vhosts/name-based.html](http://httpd.apache.org/docs/2.2/vhosts/name-based.html) for tips.

Note that if the user is using Ubuntu 14.04, they would need the 2.4 docs, in which many things have [changed]("http://httpd.apache.org/docs/2.4/upgrading.html")

---

### Post by bee2 on 2014-11-04
OK thanks for the replies and the link to that section. That makes some sense I think and now I have an idea what I need to do. 

One thing on my mind, which is probably really obvious. If now I am hosting a website in the root, do I just put that domain pointing to the root directory and then 2nd to the sub folder that will be hosting this one and so on? I don't want to mess up the main site, if I don't need to - hence I want to try and get this right when I start playing again using these instructions.  :)

Also which file would I be editing to insert this section of code into to create these virtual hosts?

---

### Post by SeijiSensei on 2014-11-05
[https://help.ubuntu.com/14.04/serverguide/httpd.html](https://help.ubuntu.com/14.04/serverguide/httpd.html)

---

### Post by bee2 on 2014-11-06
I just wanted to say thanks for the quick replies and help, now all up and running. I can't believe I spent hours on this prior to this help for a task that just took minutes.

One question about SEO freindly URLs which someone may be able to answer? Do these work on an Ubuntu server? If so how do I go about making them work? My .htaccess file from my old commercial host used to work however doesnt seem to be working now on my Ubuntu setup, so guessing this is something really simple I need to configure as well?

---

### Post by SeijiSensei on 2014-11-06
You should move the statements from .htaccess into the <Directory> section of the virtual host configuration files you created.  The .htaccess method enables hosting services to delegate some of the Apache configuration to the users.  When you're the admin yourself, it makes more sense to consolidate everything in the .conf files.

Use of the .htaccess file is controlled by the "[AllowOverride]("http://httpd.apache.org/docs/current/mod/core.html#allowoverride")" directive in a <Directory> container.  "AllowOverride None" is the usual default.

---

### Post by bee2 on 2014-11-06
> **SeijiSensei said:**
> You should move the statements from .htaccess into the <Directory> section of the virtual host configuration files you created.  The .htaccess method enables hosting services to delegate some of the Apache configuration to the users.  When you're the admin yourself, it makes more sense to consolidate everything in the .conf files.

Use of the .htaccess file is controlled by the "[AllowOverride]("http://httpd.apache.org/docs/current/mod/core.html#allowoverride")" directive in a <Directory> container.  "AllowOverride None" is the usual default.

Thanks for the prompt reply. :)

So just to make sure Im reading and understanding the above correctly in my .conf file I created for the virtual host, I add a section with the <Directory> container. Then within this section I place the contents of the .htaccess file.

I have I read this right or been a noob and really misunderstood this? Thanks for you time and patience with me. :)

---

### Post by SeijiSensei on 2014-11-06
Usually a <VirtualHost> container will include these directives:
```

<VirtualHost *:80>
[...]
DocumentRoot /path/to/your/website/root
[...]

     <Directory "/path/to/your/website/root">
          Options ...
          [...]
     </Directory>

</VirtualHost>

```
If you have such a container already, then add the directives in .htaccess to it.  If not, you'll need to create the container.

---

### Post by Habitual on 2014-11-06
> **SeijiSensei said:**
> You should move the statements from .htaccess into the <Directory> section of the virtual host configuration files you created.  The .htaccess method enables hosting services to delegate some of the Apache configuration to the users.and it easier on resources also as .htaccess gets ready for every file/directory "read".

---

### Post by bee2 on 2014-11-07
Maybe I am being a little thick here, but my .conf file is now looking like this, however the SEO friendly URLs dont seem to be working.

```

<VirtualHost *:80>
    ServerAdmin admin@xxxx.co.uk
    ServerName xxx.co.uk
    ServerAlias www.xxxx.co.uk
    DocumentRoot /var/www/1/3
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
<DIRECTORY>
##
# @package    Joomla
# @copyright  Copyright (C) 2005 - 2014 Open Source Matters. All rights reserved.
# @license    GNU General Public License version 2 or later; see LICENSE.txt
##


##
# READ THIS COMPLETELY IF YOU CHOOSE TO USE THIS FILE!
#
# The line just below this section: 'Options +FollowSymLinks' may cause problems
# with some server configurations.  It is required for use of mod_rewrite, but may already
# be set by your server administrator in a way that dissallows changing it in
# your .htaccess file.  If using it causes your server to error out, comment it out (add # to
# beginning of line), reload your site in your browser and test your sef url's.  If they work,
# it has been set by your server administrator and you do not need it set here.
##


## Can be commented out if causes errors, see notes above.
Options +FollowSymLinks


## Mod_rewrite in use.


RewriteEngine On


## Begin - Rewrite rules to block out some common exploits.
# If you experience problems on your site block out the operations listed below
# This attempts to block the most common type of exploit `attempts` to Joomla!
#
# Block out any script trying to base64_encode data within the URL.
RewriteCond %{QUERY_STRING} base64_encode[^(]*\([^)]*\) [OR]
# Block out any script that includes a <script> tag in URL.
RewriteCond %{QUERY_STRING} (<|%3C)([^s]*s)+cript.*(>|%3E) [NC,OR]
# Block out any script trying to set a PHP GLOBALS variable via URL.
RewriteCond %{QUERY_STRING} GLOBALS(=|\[|\%[0-9A-Z]{0,2}) [OR]
# Block out any script trying to modify a _REQUEST variable via URL.
RewriteCond %{QUERY_STRING} _REQUEST(=|\[|\%[0-9A-Z]{0,2})
# Return 403 Forbidden header and show the content of the root homepage
RewriteRule .* index.php [F]
#
## End - Rewrite rules to block out some common exploits.


## Begin - Custom redirects
#
# If you need to redirect some pages, or set a canonical non-www to
# www redirect (or vice versa), place that code here. Ensure those
# redirects use the correct RewriteRule syntax and the [R=301,L] flags.
#
## End - Custom redirects


##
# Uncomment following line if your webserver's URL
# is not directly related to physical file paths.
# Update Your Joomla! Directory (just / for root).
##


# RewriteBase /


## Begin - Joomla! core SEF Section.
#
RewriteRule .* - [E=HTTP_AUTHORIZATION:%{HTTP:Authorization}]
#
# If the requested path and file is not /index.php and the request
# has not already been internally rewritten to the index.php script
RewriteCond %{REQUEST_URI} !^/index\.php
# and the requested path and file doesn't directly match a physical file
RewriteCond %{REQUEST_FILENAME} !-f
# and the requested path and file doesn't directly match a physical folder
RewriteCond %{REQUEST_FILENAME} !-d
# internally rewrite the request to the index.php script
RewriteRule .* index.php [L]
#
## End - Joomla! core SEF Section.
</DIRECTORY>

</VirtualHost>

```

---

### Post by SeijiSensei on 2014-11-07
See any errors in /var/log/apache2/error.log?

Can you give us an example of an "SEO-friendly" URL?  How does it differ from just [http://www.xxx.co.uk/](http://www.xxx.co.uk/) or [http://xxx.co.uk/?](http://xxx.co.uk/?)

---

### Post by bee2 on 2014-11-08
No errors in the log.

in normally turns it from say [www.xx.co.uk/index.php/xxx](www.xx.co.uk/index.php/xxx)

to

[www.xx.co.uk/xxx](www.xx.co.uk/xxx)

---

### Post by Doug S on 2014-11-08
did you enable rewrite?```
sudo a2enmod rewrite
```You can check by:```
doug@doug-64:~$ [COLOR=#ff0000]ls -l /etc/apache2/mods-enabled[/COLOR]
total 0
lrwxrwxrwx 1 root root 28 Oct 12  2012 alias.conf -> ../mods-available/alias.conf
lrwxrwxrwx 1 root root 28 Oct 12  2012 alias.load -> ../mods-available/alias.load
lrwxrwxrwx 1 root root 33 Oct 12  2012 auth_basic.load -> ../mods-available/auth_basic.load
... deleted a bunch of stuff ...
lrwxrwxrwx 1 root root 33 Oct 12  2012 reqtimeout.load -> ../mods-available/reqtimeout.load
[COLOR=#ff0000]lrwxrwxrwx 1 root root 30 Sep 11  2013 rewrite.load -> ../mods-available/rewrite.load[/COLOR]
lrwxrwxrwx 1 root root 31 Oct 12  2012 setenvif.conf -> ../mods-available/setenvif.conf
... deleted a bunch of stuff ...
lrwxrwxrwx 1 root root 30 Oct 12  2012 userdir.conf -> ../mods-available/userdir.conf
lrwxrwxrwx 1 root root 30 Oct 12  2012 userdir.load -> ../mods-available/userdir.load
```

---

