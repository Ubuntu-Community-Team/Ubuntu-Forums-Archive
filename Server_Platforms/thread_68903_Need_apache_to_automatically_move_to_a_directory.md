---
title: "Need apache to automatically move to a directory"
date: 2005-09-24
forum: Server Platforms
---

### Post by bigdufstuff on 2005-09-24
I have a site hosted at mydomain.org all the content is in mydomain.org/wiki I am not sure how to configure apache to automatically go to that directory when people hit the site.

right now you are presented with apache's directory view with just one folder available.

I have configured it so [www.mydomain.org](www.mydomain.org) redirects to mydomain.org/wiki/ but I can't get it to do that if you type in the real address. If you want me to post my apache config I will.

---

### Post by SSTwinrova on 2005-09-24
I don't know of an Apache setting to make that happen (not saying it doesn't exist, I'm just not too familiar with Apache), but a temporary solution would be to create an index.htm page in / and set a redirect in the <head> section for 1 second or something.

---

### Post by bigdufstuff on 2005-09-24
Thanks, I have that set up and it is working good enough for now. I am still curious if this can be done through apache though

---

### Post by majikstreet on 2005-09-24
[QUOTE=bigdufstuff]Thanks, I have that set up and it is working good enough for now. I am still curious if this can be done through apache though[/QUOTE]
 I don't think you can through apache, but you probably could have installed the wiki software in the main directory for apache eg /var/www/ if you have no virtual hosts... (I have virtual hosts so its /var/www/majikstreet for my site)

---

### Post by fatbastard spice on 2005-09-25
[QUOTE=bigdufstuff]I have a site hosted at mydomain.org all the content is in mydomain.org/wiki I am not sure how to configure apache to automatically go to that directory when people hit the site.

right now you are presented with apache's directory view with just one folder available.

I have configured it so [www.mydomain.org](www.mydomain.org) redirects to mydomain.org/wiki/ but I can't get it to do that if you type in the real address. If you want me to post my apache config I will.[/QUOTE]
 Not sure if this is what you want but if you're running apache2 create a new virtual host file in /etc/apache2/sites-available - something along the lines of:

<VirtualHost *>
ServerName [www.mydomain.org](www.mydomain.org)
DocumentRoot /var/www/mydomain/wiki (or whatever the path is)
</VirtualHost>

That should serve up the index file at that path whenever apache gets a request for [www.mydomain.org](www.mydomain.org).

Then just use a2ensite to create a symlink to the sites-enabled directory.

---

### Post by majikstreet on 2005-09-25
[QUOTE=fatbastard spice]Not sure if this is what you want but if you're running apache2 create a new virtual host file in /etc/apache2/sites-available - something along the lines of:

<VirtualHost *>
ServerName [www.mydomain.org](www.mydomain.org)
DocumentRoot /var/www/mydomain/wiki (or whatever the path is)
</VirtualHost>

That should serve up the index file at that path whenever apache gets a request for [www.mydomain.org](www.mydomain.org).

Then just use a2ensite to create a symlink to the sites-enabled directory.[/QUOTE]
 *duh* I can't believe I forgot about that....

That would work perfectly.

I had some trouble creating virtual hosts at first-- post back here if you need any help. \\:D/

---

