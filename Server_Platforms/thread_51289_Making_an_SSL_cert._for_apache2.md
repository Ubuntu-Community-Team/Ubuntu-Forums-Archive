---
title: "Making an SSL cert. for apache2"
date: 2005-07-23
forum: Server Platforms
---

### Post by Paul Bramscher on 2005-07-23
I'm a LAMP programmer and need an SSL/443 port on pretty much any box I work with.  I hunted for docs on how to set it up on Ubuntu and found an Ubuntu discussion that was about 90% complete, but not quite.  I want to make it easy enough for a newbie to make his own self-signed cert.

So I put together a doc and added some explanatory text here:
[http://www.tc.umn.edu/~brams006/selfsign_ubuntu.html](http://www.tc.umn.edu/~brams006/selfsign_ubuntu.html)

My other doc ([http://www.tc.umn.edu/~brams006/selfsign.html](http://www.tc.umn.edu/~brams006/selfsign.html)) works for SuSE and RH based distros.  If anyone's interested, check them out.  Suggestions/additions are welcome.

I'm curious if the Ubuntu procedures apply equally to Debian -- whether it's essentially the same directory setup, apache/openssl version, etc.

-Paul Bramscher

---

### Post by LordHunter317 on 2005-07-23
Your document has several issues:[list][*]Step 4 can be replaced with:```
sudo a2ensite ssl
```[*]Unlike RedHat, no html directory is used by default, so don't create one in either site.  If you're going to suggest a new dir, I recommend making a 'default' directory under /var/www and directing them to put their port 80 files there, and a 'ssl' directory under /var/www and their SSL files there.  Updating the Virtualhost directives as necessary.[*]Do not tell them to adjust the NameVirtualHost directive.  There's no need[*]Similiary, don't tell them to change the address on the VirtualHost directives, merely the ports.[/list]

---

### Post by Paul Bramscher on 2005-07-23
[QUOTE=LordHunter317]Your document has several issues:[list][*]Step 4 can be replaced with:```
sudo a2ensite ssl
```[*]Unlike RedHat, no html directory is used by default, so don't create one in either site.  If you're going to suggest a new dir, I recommend making a 'default' directory under /var/www and directing them to put their port 80 files there, and a 'ssl' directory under /var/www and their SSL files there.  Updating the Virtualhost directives as necessary.[*]Do not tell them to adjust the NameVirtualHost directive.  There's no need[*]Similiary, don't tell them to change the address on the VirtualHost directives, merely the ports.[/list][/QUOTE]

Earlier in the document, I already recommend that users sudo (so they should already be sudo by step 4), but I'll check into the a2ensite command.

The advantage of /var/www/html and /var/www-ssl/html is that it is more consistent to what other linux and unix distros do (SuSE is /srv/www/html).  Also, you can then set up /var/www/cgi-bin, etc. as opposed to /var/www/html.  It all depends on how you want to organize.  Since I work with solaris, RH, SuSE and (now) Ubuntu, I like the architecture all to match.  Totally up the individual, though.

I'll look into what you say about the virtual host addresses, though as I recall it didn't work for me to leave them blank.  In any case, if you ever get a more complex server and have multi-homed IP's and DNS names, leaving it alone isn't an option: you need to plug in the IP's.

Anyway, thanks for the tips.  I'm going to refine that doc.  It works as-is, but I'll make it better.

---

