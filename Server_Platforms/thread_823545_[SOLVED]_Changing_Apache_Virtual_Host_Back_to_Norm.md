---
title: "[SOLVED] Changing Apache Virtual Host Back to Normal Host"
date: 2008-06-09
forum: Server Platforms
---

### Post by Cerin on 2008-06-09
Hi,

I originally configured my Apache/PHP setup to handle multiple sites via virtual hosts, but now I just want to host one site so that [http://mydomain/](http://mydomain/) goes to the root of a single site, instead of [http://mydomain/some/long/site/alias](http://mydomain/some/long/site/alias). I tried modifying my apache2.conf file by commenting out the lines:

Include /etc/apache2/conf.d/
Include /etc/apache2/sites-enabled/

and adding the line:

DocumentRoot /var/lib/mysinglesite

but after I restart Apache, browsing to / just gives me a directory listing, and clicking on index.php gives me a 404 error. What am I doing wrong?

I noticed there's a commented out line in /etc/apache2/conf.d/mysinglesite.conf to alias my site's filesystem path to the web root, but notes that it won't work for virtual hosts, and sure enough it doesn't. Is there an easy way to disable virtual hosts so that I can use that?

---

### Post by mbeach on 2008-06-10
You probably want to use the 
a2dissite
command to disable the original sites, leaving all but Default active.  Then you should really only have to edit the /etc/apache2/sites-available/Default file which would be your default site.
Check in /etc/apache2/sites-enabled/ and use the a2dissite command for each site listed in there other than the 000-default.
[ref: [http://www.debian-administration.org/articles/207](http://www.debian-administration.org/articles/207) ]

your /etc/apache2/apache2.conf would need the 
Include /etc/apache2/sites-enabled/
uncommented.
I'd also remove the DocumentRoot line from apache2.conf, and let it be set in the /etc/apache2/site-available/default file.

Basically, I'd use the virtual hosts, but only have the one host enabled.

---

### Post by Cerin on 2008-06-10
Actually, I think that's what I basically did. I didn't use a2dissite, but I created my new site, then deleted the default site. The only problem is I can't access the new site from the web root. It only works if I browse to /some/really/long/path.

---

### Post by mbeach on 2008-06-11
where are the php pages you want to serve up with apache?  That will be your documentroot.

You should have a file in sites-available, and an symbolic link in sites-enabled (best was is to use a2ensite) pointing to your conf file in sites-available.

If you have to browse to /some/really/long/path, it would appear the document root is set incorrectly.

I would suggest creating a folder in your home directory for your website, say
/home/cerin/mysites/mysitename

then create a file based on the default file (copy default and edit)
/etc/apache2/sites-available/mysitename (your config file)

In there set your DocumentRoot to /home/cerin/mysites/mysitename

and and a corresponding 
<Directory /home/cerin/mysites/mysitename/>
directive.

when you are happy, be sure to enable the site
a2ensite mysitename
or just type a2ensite and it will ask you which site.

tell apache to reload the configuration with
sudo /etc/init.d/apache2 reload

---

### Post by Cerin on 2008-06-11
Sorry, turns out if was a config issue with the PHP app. It had that long url hardcoded. Removing that and using an Apache Alias fixed the problem. Thanks for your help.

---

### Post by mbeach on 2008-06-11
good to hear.  mark the thread as solved if you get a moment.

---

