---
title: "Symbolic link to htdocs on localhost?"
date: 2007-02-12
forum: Server Platforms
---

### Post by loclarkey on 2007-02-12
Hi community.  I set up a LAMP server on my ubuntu box to test websites locally, courtesy of the people at XAMPP.  It works like a charm, but my web root is located at //opt/lampp/htdocs.  I would like for my web root to be at ~/Websites.  In other words, I start the server, type [http://localhost](http://localhost) into a browser, and the contents of ~/Websites is displayed.  I have never used symbolic links but I get the feeling that those could do the job.  How do I do this?

---

### Post by kidders on 2007-02-12
Hi there,

It sounds like the best thing to do might be to alter apache's config so the webroot is /home/loclarkey/Websites. If you wanted to, you could symlink /opt/lampp/htdocs to ~/Websites, but your stuff would still technically be in /opt, not /home.

This doesn't apply to your particular situation, but it's worth mentioning that afaik apache will refuse to follow symlinks below the webroot (for security reasons) unless you instruct it to do so. (Just in case you try it and wonder what's going on.)

**Edit:** What you want to do just dawned on me! You were asking about turning /opt/lampp/htdocs into a symlink, right? You can do that if you'd like to, either. In fact, /var/www (where my webroot is) is a symlink at the moment.

---

### Post by loclarkey on 2007-02-12
Thanks for the prompt reply, kidders.

1) I tried the first approach you mentioned, and went into httpd.conf and changed the following values:

ServerRoot "/home/loclarkey/Websites"
DocumentRoot "/home/loclarkey/Websites"
<Directory "/home/loclarkey/Websites">

and restarted the server, but it is still using /opt/lampp/htdocs as the webroot.  What am I missing?

2) Regarding the second option (creating symlinks), how do I do that specifically?  I would like to use this as a learning opportunity.  :)

---

### Post by kidders on 2007-02-12
> **loclarkey said:**
> ServerRoot "/home/loclarkey/Websites"
DocumentRoot "/home/loclarkey/Websites"
<Directory "/home/loclarkey/Websites">Odd. Something is probably overriding those settings. On my apache installation, for instance, I have an /etc/apache2/sites-available directory that contains all my hosts. This fragmented config file style can be handy, but it's hell when you're trying to track something down!

If you've got something similar (lots of config files, all included in eachother), see if you can find the offending setting with something like **find /etc/apache2 -type f -print -exec grep -i documentroot {} \;** ... that will list all apache's configuration files, and show you any "DocumentRoot" lines along the way. If you only have one site, you should only see one "DocumentRoot", I suppose. I suspect though, that more than one will turn up.

> **loclarkey said:**
> Regarding the second option (creating symlinks), how do I do that specifically?Use **ln** to create links ... the man page has all the details. Basically, you would do something like **ln -s /home/loclarkey/Websites /opt/lampp/htdocs**.

---

### Post by loclarkey on 2007-02-12
Okay, got it.  I reverted httpd.conf to its original configuration.  I don't know what was overriding that configuration.

Anyway, I put a symlink in htdocs pointing to the folder in my home directory.  It didn't work at first because my permissions were too restrictive.  But, I changed that and got it working.  I can now keep all my www folders in my home folder.  

Thanks for your help! Gotta love the ubuntu community.

---

