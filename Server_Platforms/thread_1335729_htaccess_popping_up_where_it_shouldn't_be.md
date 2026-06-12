---
title: "htaccess popping up where it shouldn't be"
date: 2009-11-23
forum: Server Platforms
---

### Post by dwasifar on 2009-11-23
There are five domains hosted on my Apache install, using virtualhosts on port 80.  The other day I set up SSL on one of them by creating a separate documentroot directory entry for ssl and a virtualhost on port 443.  This directory has .htaccess security; entries in httpd.conf and .htaccess files in the directories.  So far, so good; it all works like I want it to.

Today, I decided to set up another SSL virtualhost for a different domain.  I cloned the existing virtualhost, changing the servername and the documentroot and certificate paths, and restarted Apache.  Everything seems to work, except that for some reason, the new SSL domain is prompting for .htaccess login, expecting the user and passwords as specified for the first SSL domain.  

I don't understand why this is.  There are no .htaccess files in the DocumentRoot of the new domain, and it has no entries in http.conf.

---

### Post by JillK on 2009-11-23
can you post the .htaccess content?

---

### Post by dwasifar on 2009-11-23
> **JillK said:**
> can you post the .htaccess content?

That's the thing.  There IS no .htaccess content in these directories.  It's getting it from some other place in the system.

---

### Post by JillK on 2009-11-23
what if you create one does that change the behaviour?

---

### Post by dwasifar on 2009-11-24
It actually did not change the behavior.  But eventually I found out why this was happening.

It has to do with SSL and non-SSL being handled differently in virtual hosting, along with a stray .htaccess file that was not where I thought to look.  

I had had my non-SSL domains set up and working as I wanted, and each of them handled .htaccess restrictions as I expected.  The <directory> directives in the configuration files affected only the directories I wanted, because each of the domains was separately specified using a name-based vhost.  

When I set up the SSL sections, I used the same structure, not realizing that name-based vhosts don't work with SSL.  Consequently the SSL vhosts were loading with global defaults for some things.  One of those things was htaccess.  My directory structure is /var/www/[domain.com]/html for each domain, with the .htaccess files residing in the html directories or their subdirectories.  There was a forgotten .htaccess file in /var/www.  It never caused any trouble before, but when I set up an SSL vhost, it suddenly got picked up and used by the global defaults.  This led to some very frustrating experiences; at one point I was getting htaccess prompts even after (temporarily) deleting all the .htaccess files I knew about!  Fortunately this clued me in that I must have missed one, which led me to the solution.

Thanks for the offer of help though.  :)  I'm learning.

---

