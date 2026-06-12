---
title: "alias_mod and multiple domains"
date: 2013-04-05
forum: Server Platforms
---

### Post by mastablasta on 2013-04-05
alias_mod

As per Google's advice I plan to use Apache's alias_mod to do permanent redirect from old links (static website) to new website with new links. While i managed to achieve this on local ubutnu server at home by reading the Apache documentation and using .htaccess file, i am not sure how to do it on host.
My issue is that the main joomla site is using the domain. I've also added an open cart site to it. so this is how it currently looks like in browser:
```

[www.example.com]("http://www.example.com")                   <<<<--main page
[www.example.com/shop]("http://www.example.com/shop")            <<<<--online shop

```

these pages are int heir directories. e.g. public_html/joomla, public_html/opencart
i've now added a wordpress to the mix (public_html/wp)
and this site currently has this as domain:
```

[www.example.com/wp]("http://www.example.com/wp")

```
but all this above will be later replaced by another domain
```

[www.examplenew.com]("http://www.examplenew.com")

```
ok so what does actually go in as link
```

redirect 301 /[COLOR=#ff0000]**whatgoeshere?.**[/COLOR]html [http://www.examplenew.com/newwebsitemenu/newsite/](http://www.examplenew.com/newwebsitemenu/newsite/)

```
at the moment i can probably give /wp/oldsite.html but later this wp won't be there will it? it is maybe /examplenew/oldsite.html?

i think the host is using RHEL if it matters.

---

### Post by Azrayal on 2013-04-05
Hi, 

You really need to provide the configs for the current and new apache setup for people to understand fully your issue. 

If your migrating wp to a new server and it's going to be located in the root of the new apache server (if RHEL) /var/www/html/ then the domain may not matter so much as it's pointing at the server. 

Can you provide config samples to futher explain your request. 

Thanks

---

### Post by mastablasta on 2013-04-06
i do not actually have access to server so everything is done via .htaccess.

This is the main .htaccess

```
##
# @version $Id: htaccess.txt 13415 2009-11-03 15:53:25Z ian $
# @package Joomla
# @copyright Copyright (C) 2005 - 2008 Open Source Matters. All rights reserved.
# @license http://www.gnu.org/copyleft/gpl.html GNU/GPL
# Joomla! is Free Software
##


#####################################################
#  READ THIS COMPLETELY IF YOU CHOOSE TO USE THIS FILE
#
# The line just below this section: 'Options +FollowSymLinks' may cause problems
# with some server configurations.  It is required for use of mod_rewrite, but may already
# be set by your server administrator in a way that dissallows changing it in
# your .htaccess file.  If using it causes your server to error out, comment it out (add # to
# beginning of line), reload your site in your browser and test your sef url's.  If they work,
# it has been set by your server administrator and you do not need it set here.
#
#####################################################

##  Can be commented out if causes errors, see notes above.
Options +FollowSymLinks

#
#  mod_rewrite in use

RewriteEngine On

########## Begin - Rewrite rules to block out some common exploits
## If you experience problems on your site block out the operations listed below
## This attempts to block the most common type of exploit `attempts` to Joomla!
#
## Deny access to extension xml files (uncomment out to activate)
#<Files ~ "\.xml$">
#Order allow,deny
#Deny from all
#Satisfy all
#</Files>
## End of deny access to extension xml files
RewriteCond %{QUERY_STRING} mosConfig_[a-zA-Z_]{1,21}(=|\%3D) [OR]
# Block out any script trying to base64_encode crap to send via URL
RewriteCond %{QUERY_STRING} base64_encode.*\(.*\) [OR]
# Block out any script that includes a <script> tag in URL
RewriteCond %{QUERY_STRING} (\<|%3C).*script.*(\>|%3E) [NC,OR]
# Block out any script trying to set a PHP GLOBALS variable via URL
RewriteCond %{QUERY_STRING} GLOBALS(=|\[|\%[0-9A-Z]{0,2}) [OR]
# Block out any script trying to modify a _REQUEST variable via URL
RewriteCond %{QUERY_STRING} _REQUEST(=|\[|\%[0-9A-Z]{0,2})
# Send all blocked request to homepage with 403 Forbidden error!
RewriteRule ^(.*)$ index.php [F,L]
#
########## End - Rewrite rules to block out some common exploits

#  Uncomment following line if your webserver's URL
#  is not directly related to physical file paths.
#  Update Your Joomla! Directory (just / for root)

# RewriteBase /


########## Begin - Joomla! core SEF Section
#
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteCond %{REQUEST_URI} !^/index.php
RewriteCond %{REQUEST_URI} (/|\.php|\.html|\.htm|\.feed|\.pdf|\.raw|/[^.]*)$  [NC]
RewriteRule (.*) index.php
RewriteRule .* - [E=HTTP_AUTHORIZATION:%{HTTP:Authorization},L]
#
########## End - Joomla! core SEF Section


suPHP_ConfigPath /home/mithrasi/public_html
```

in wordpress subfolder is the following .htaccess:
```

# BEGIN WordPress
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteBase /wp/
RewriteRule ^index\.php$ - [L]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /wp/index.php [L]
</IfModule>

# END WordPress
```
This one is continously generated by wordpress. which is why i had to put mod_alias outside of that area. What i need it to be is like so:
```
<ifmodule mod_alias.c>
RewriteEngine On
Redirect 301 [COLOR=#0000ff]**/wp/oldsite.html**[/COLOR] **[COLOR=#00ff00]http://localhost/wp/[/COLOR]**indonesian-food-recipes/recipe/
</ifmodule>

# BEGIN WordPress
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteBase /wp/
RewriteRule ^index\.php$ - [L]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /wp/index.php [L]
</IfModule>

# END WordPress 
```

however i do not know what  should be here: [COLOR=#0000ff]**/wp/oldsite.html**[/COLOR]
while i do knwo that this part **[COLOR=#00ff00]http://localhost/wp/[/COLOR]** will become the [http://www.newdomain.com](http://www.newdomain.com)/

This is the folder structure under /public_html and /www (they are one and the same): [http://ubuntuone.com/296j4gCBWeeuPgeDOW59ud](http://ubuntuone.com/296j4gCBWeeuPgeDOW59ud)

the main domain is pointing to joomla site. the /domain/shop is the webshop. i will now add a new .com domain that will point to /www/wp/ so that the wordpress site would be at the new domain. and i need to have old links form static website redirected. the static website was all in one folder. i do not know what they use or how they do it since it is all hidden from users. but i do know that using wget to download from the site all .html files were in same folder. the old site was hosted at Sitesell AKA Site Build It! AKA SBI! :oops: they are like a cult and we are trying to move out....

---

### Post by mastablasta on 2013-04-08
bump. it would be really good to know the answer to this, otherwise i am destined for try and see session which could take a while. especially since i do not have extensive apache knowledge system.

for the moment i've placed a placeholder on the part i will need to change

---

