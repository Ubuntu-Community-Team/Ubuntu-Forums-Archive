---
title: "Ubuntu 6.06/Apache 2/MoinMoin configuration help needed"
date: 2006-12-22
forum: Server Platforms
---

### Post by InThane on 2006-12-22
Greetings,

I am currently in the process of putting together a Wiki farm for my place of employment. I'm quite capable of getting a single Wiki up and running on a given server, but in my opinion it's kind of a waste to use one VMWare image per wiki, especially on the system resources side of things.

So, I started poking around [here]("https://wiki.ubuntu.com/HelpOnInstalling") and [here]("http://moinmoin.wikiwikiweb.de/HelpOnInstalling#head-4b27889e7fd5f911c3d6961efcc0a736bd580fd5"), trying to figure out how to make this work. Ideally, I'd like to script the whole mess too, so that I can just type './addwiki {wikiname}' and have a new Wiki up.

Of course, step one is to figure out how to add a Wiki.

System is Ubuntu LTS 6.06, bare bones.

Internally, the server is at x.x.96.21. For now, I've set up references in the hosts file both on my test PC, and on the server, to refer to 96.21 as 'wikitest1' and 'wikitest2'. Eventually, entries will be added to the DNS server instead.

Now, in /etc/moin/farmconfig.py, I've added the following lines:

[FONT="Courier New"]wikis = [
    ("wikitest1",   r"wikitest1/.*$"),
    ("wikitest2",   r"wikitest2/.*$"),
][/FONT]

This appears to match the examples given in the configuration file. Moving on...

Now the directions for inserting a Wiki into Apache2 aren't horribly clear. By the directions on the MoinMoin page, you need to find the configuration file and point it at the farmconfig.py. There are multiple farmconfig.py files, but the moin.cgi file in the wiki folder has the following code:

[FONT="Courier New"]sys.path.insert(0, '/etc/moin')[/FONT]

If I'm reading that right, it means that any .py files in /etc/moin automagically make it into the syspath for Python. So, I'm pretty certain that all that has been taken care of for me.

On to Apache 2.

Now, if I make minor modifications to the farmconfig.py file, and stick this chunk of code in /etc/apache2/sites-available/default, right after &ltVirtualHost *>, then the wiki shows up at /wikitest1.

[FONT="Courier New"]NameVirtualHost *
<VirtualHost *>
        ScriptAlias /wikitest1 "/usr/share/moin/wikitest1/moin.cgi"
        alias /wiki "/usr/share/moin/htdocs"
        <Directory /usr/share/moin/htdocs>
                Order allow,deny
                allow from all
        </Directory>[/FONT]

What I want is when I visit "http://wikitest1/" for the wikitest1 homepage to show up. So, I slightly munge the code.

[FONT="Courier New"]NameVirtualHost wikitest1
<VirtualHost wikitest1>
        ScriptAlias / "/usr/share/moin/wikitest1/moin.cgi"
        alias /wiki "/usr/share/moin/htdocs"
        <Directory /usr/share/moin/htdocs>
                Order allow,deny
                allow from all
        </Directory>[/FONT]

I then do an '/etc/init.d/apache2 restart', which generates the following spew:

[FONT="Courier New"] * Forcing reload of apache 2.0 web server...                                                                                                                
[Fri Dec 22 05:00:51 2006] [warn] The Alias directive in /etc/apache2/sites-enabled/000-default at line 4 will probably never match because it overlaps an earlier ScriptAlias.
[Fri Dec 22 05:00:51 2006] [warn] The ScriptAlias directive in /etc/apache2/sites-enabled/000-default at line 26 will probably never match because it overlaps an earlier ScriptAlias.
[Fri Dec 22 05:00:51 2006] [warn] The Alias directive in /etc/apache2/sites-enabled/000-default at line 43 will probably never match because it overlaps an earlier ScriptAlias.
apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Fri Dec 22 05:00:52 2006] [warn] The Alias directive in /etc/apache2/sites-enabled/000-default at line 4 will probably never match because it overlaps an earlier ScriptAlias.
[Fri Dec 22 05:00:52 2006] [warn] The ScriptAlias directive in /etc/apache2/sites-enabled/000-default at line 26 will probably never match because it overlaps an earlier ScriptAlias.
[Fri Dec 22 05:00:52 2006] [warn] The Alias directive in /etc/apache2/sites-enabled/000-default at line 43 will probably never match because it overlaps an earlier ScriptAlias.
apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName[/FONT]

Any suggestions?

---

### Post by InThane on 2006-12-22
I know, bad form to reply to your own thread, but I think I've found something.

A subtle problem.

I've been poking around the 3rd Edition "Apache: A Definitive Guide" from O'Reilly publishing. They mention that you do not want to write the following in a config file:

[FONT="Courier New"]Alias /somewhere_else/ /usr/www/APACHE3/somewhere_else[/FONT]

Apparently, ending an address with a '/' can cause problems for Apache. My guess is that the line '[FONT="Courier New"]ScriptAlias / "/usr/share/moin/wikitest1/moin.cgi[/FONT]"' is what is causing the problem - but I'm not sure how to change that for the better. Investigating.

---

### Post by chaplinux on 2006-12-24
REF: 
apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName



/etc/hosts 
------------------------------
127.0.0.1       localhost
127.0.1.1       debian-server


/etc/apache2/apache2.conf
---------------------------------
#...
ServerRoot "/etc/apache2"
ServerName debian-server
#...

:mrgreen:

---

### Post by BigDaddyEBK on 2007-02-12
> **chaplinux said:**
> REF: 
apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

/etc/hosts 
------------------------------
127.0.0.1       localhost
127.0.1.1       debian-server

/etc/apache2/apache2.conf
---------------------------------
#...
ServerRoot "/etc/apache2"
ServerName debian-server
#...



Thanks, the info REALLY helped this Ubuntu n00b!!

---

