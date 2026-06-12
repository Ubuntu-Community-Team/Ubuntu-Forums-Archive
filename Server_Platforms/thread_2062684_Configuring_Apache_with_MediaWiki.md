---
title: "Configuring Apache with MediaWiki"
date: 2012-09-25
forum: Server Platforms
---

### Post by suhaib on 2012-09-25
Hi All,

This one is proving to be a nuisance for me.  Basically, I've installed MediaWiki on 12.04 server ed. Now I've tried changing  the document root, ServerName variable in apache and more, but I can't get my server's domain name to resolve to the directory where mediawiki is installed (grr!).  So going to let's say foo.bar.com resolves to /var/www.  To get to media wiki I have to append it to foo.bar.com/mediawiki.

I want to merely type foo.bar.com so it resolves to the mediawiki site.  Usually, I create a config file in /etc/apache2/sites-available named with the url and set the doc root accordingly.  But it seems mediawiki creates it's own file in /etc/mediawiki/apache2.conf.  I've tried changing the document root, serverName and more therein, but to no success.

Has anyone done this before who can help?  Thanks in advance!

---

### Post by CharlesA on 2012-09-25
How did you install mediawiki? I have installed it from the tar.gz off the mediawiki site and it worked fine for me.

---

### Post by suhaib on 2012-09-25
I made the mistake of installing via apt-get...

However, MediaWiki itself works fine - so far.  But it's default way of working with Apache - I don't like and would like to change.

---

### Post by CharlesA on 2012-09-25
You could just purge it and install it from the mediawiki site. Easier to deal with that way.

Otherwise, just edit the main documentroot in apache and then restart the service and see what happens.

---

### Post by lisati on 2012-09-25
> **CharlesA said:**
> How did you install mediawiki? I have installed it from the tar.gz off the mediawiki site and it worked fine for me.

Same here.

The only thing I'd add to this is that if you're using a folder other than /var/www and need to tinker with apache's sites-available settings, you'll need to use a2ensite followed by a restart or reload of apache.

---

### Post by suhaib on 2012-09-26
Thanks.

I've removed the files, got from the site direct and moved the folder to /var/www.  I then edited the /etc/apache2/site-available/default and appended the document root to /var/www/mediawiki.

After a restart, it worked, and I realised that it could've been my Firefox cache all along.  How could I forget that one!?

---

