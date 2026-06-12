---
title: "htaccess setup"
date: 2007-01-31
forum: Server Platforms
---

### Post by qwerty2 on 2007-01-31
Hi everyone.

Yesterday I signed up for a new server it has ubuntu 6.06 on it, I have another server with Fedora Core and used this htaccess file which worked fine, I am now trying to get it to work on the ubuntu server

RewriteEngine on

# redirect non-www to www subdomain.
RewriteCond %{HTTP_HOST} ^domain\.co\.uk [NC]
RewriteRule (.*) http://www.domain.co.uk/$1 [R=301,L]

RewriteRule ^index.php$ [http://www.domain.co.uk/](http://www.domain.co.uk/) [R=301,L]

This doesnt work, and when its uploaded the page wont display at all, I have done some research but cant find any posts with my particular issue, some are looking at mod_rewrite and the general census was telling them to edit via putty.

I have putty but have never edited a file or backed up a file, if editing is what I need to do can somebody show me the steps I need to take, ie, edit what where how.

I want this htaccess setup to used on this one site I have, so only on this account not a permanent setting server wide, but will allow me to add the htaccess file to whichever sites need it.

Thanks in advance

---

