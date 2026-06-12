---
title: "Apache2, perl, and Ubunt 13.10"
date: 2013-10-28
forum: Server Platforms
---

### Post by Roberto.Lionello on 2013-10-28
Hi,

I have installed Ubuntu 13.10 on my new laptop. I would like  to run on localhost a  web site that has perl scripts. I have installed libapache2-mod-perl2, assuming it was necessary. The files of the website are in /var/www. When I go to localhost, the initial screen shows up correctly. However, whenever I try to load a perl script, the text appears in the browser and the script is not executed. What do I have to do to make the web site working? Thanks!

---

### Post by Lars Noodén on 2013-10-29
Where did you get the scripts?  There should be some instruction about where to place them.

In order to run CGI, the module cgi must be activated.

```

sudo a2enmod cgi
sudo service apache2 restart

```

The default location for CGI scripts in Apache2 is /usr/lib/cgi-bin/ but that is almost always changed when actually writing CGI scripts.  Your vhost should point to the location and make the appropriate settings.  e.g.

```

ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
<Directory "/usr/lib/cgi-bin">
                        AllowOverride None
                        Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                        Require all granted
</Directory>

```

That will make a script, such as /usr/lib/cgi-bin/x.pl, available via the local host, such as [http://127.0.0.1/cgi-bin/x.pl](http://127.0.0.1/cgi-bin/x.pl)  Note the [ScriptAlias](http://httpd.apache.org/docs/2.4/mod/mod_alias.html#scriptalias) and [Directory](http://httpd.apache.org/docs/2.4/mod/core.html#directory) directives and how they work.

For the script to run, it has to be executable (mode 555, 755, or 775) and of course can't contain errors.  

You might want to put [http://localhost/cgi-bin/](http://localhost/cgi-bin/) behind a password or block outside access with the firewall while getting things set up.

---

### Post by Roberto.Lionello on 2013-10-29
First of all, many thanks! By following your instructions I was able to make it work. I downloaded the perl scripts using 

svn checkout [http://divinum-officium.googlecode.com/svn/trunk/](http://divinum-officium.googlecode.com/svn/trunk/) divinum-officium-read-only

to make a standalone version of [http://divinumofficium.com](http://divinumofficium.com) on my laptop, to use when an Internet connection is not available.

I put all in /var/www and made the following symbolic links in /usr/lib/cgi-bin

lrwxrwxrwx 1 root root  23 Oct 28 12:31 horas -> /var/www/cgi-bin/horas//
lrwxrwxrwx 1 root root  23 Oct 28 12:31 missa -> /var/www/cgi-bin/missa//

It works perfectly!

---

### Post by Lars Noodén on 2013-10-29
Great.  If you need to add a second vhost, you'll have to move around the directories but that's not hard.

---

