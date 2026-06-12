---
title: "Ubuntu 8.04 not parsing PHP on one site"
date: 2008-12-01
forum: Server Platforms
---

### Post by DragonFlyEye on 2008-12-01
OK, here's the situation: I have a linode.com VPS system running three different domains at the moment.  The VPS is setup with Ubuntu Server 8.04, PHP5.  They're all running PHP on them, and each has it's own VirtualServer file for it's configuration.  

Of those three, two are running just fine, the third is not.  That third one is not parsing PHP and instead just allowing FF to download the files.  Yikes!

There are no errors in the error logs germane to this problem.

Seeing as how there is only one bit of configuration which I've deliberately done differently from site to site - that being the VirtualHost files - I naturally assumed it must be some typo or other silliness in the file for my troubled site.  So I:

[LIST=1]
[*]a2dissite-ed the troubled site.
[*]Reloaded Apache (/etc/init.d/apache2 force-reload).
[*]Renamed the troubled site's config file.
[*]Copied a working site's VirtualHost file to replace the troubled site's file.
[*]Changed the directory references in the new file to match the correct site.
[*]a2ensite-ed the troubled site.
[*]Reloaded Apache again.
[/LIST]
Sadly, this has had no effect.

Can someone tell me where else to look?  I'm totally thrown by the fact that this is a new installation and everything works for every other site. 

Thank you all very much for any insight you can provide me.

---

### Post by DragonFlyEye on 2008-12-02
Bump.  Any ideas out there?  Thanks for the help.

---

### Post by lamapper on 2008-12-28
Not sure if this is your solution, but do not see the harm in trying it.

Add the following line to your /etc/apache2/httpd.conf  file:

AddType application/x-httpd-php .php 

Got this out of a book on PHP, per the book, "Apache uses the AddType directive to determine how a file should be treated."

Also mentioned, "If PHP is not installed on your server OR your file's extension is not recognized, you might not see the output shown..." basically you will be prompted to download the file, rather than your browser rendering the file correctly.

The comment about "download the file" from the book made me think of your situation when I read your post.

---

### Post by hyper_ch on 2008-12-28
you have libapache2-mod-php5 intalled?

---

### Post by mbeach on 2008-12-28
> **lamapper said:**
> Add the following line to your /etc/apache2/httpd.conf  file

That will now be in /etc/apache2/mods-available/php5.conf instead of httpd.conf.

For Debian/Ubuntu Apache file layout see:
/usr/share/doc/apache2/README.Debian
and a bit more at:
[http://wiki.apache.org/httpd/DistrosDefaultLayout#head-b5762a3e9764f34f7587e35f4db9ff35d508ced1](http://wiki.apache.org/httpd/DistrosDefaultLayout#head-b5762a3e9764f34f7587e35f4db9ff35d508ced1)

---

