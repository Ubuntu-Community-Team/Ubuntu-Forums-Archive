---
title: "Apache2 documentation confusion!!"
date: 2008-01-29
forum: Server Platforms
---

### Post by lemuren on 2008-01-29
Hi all.

I have a documentation question.

When i look at the apache docs at ubuntu site [https://help.ubuntu.com/7.10/server/C/httpd.html](https://help.ubuntu.com/7.10/server/C/httpd.html),
i can´t find the corresponding info in the apache documentation [http://httpd.apache.org/docs/2.2/](http://httpd.apache.org/docs/2.2/)

A few examples.
[LIST]
[*]Searched for the command **a2ensite** at apache, no hits.
[*]Searched for **apache2.conf**  at apache, no hits.
[*]At apache they refer to **httpd.conf**, which is empty in ubuntu.
[*]The virtualhost concept in ubuntu with multiple config files like **/etc/apache2/sites-available/site1**, **/etc/apache2/sites-available/site2** doesn´t seem to exist at apache.
[*]**httpd** command all over apache, not in ubuntu.
[/LIST]

Can anyone explain this to me?:confused:
I´m **very** confused right now...

Thanks in advance,
Lage

---

### Post by MJN on 2008-01-29
This is a common cause of confusion.... (so take some comfort in that!)
 
The issue is that the Apache package has been customised quite heavily for Debian, and Debian-based distributions (like Ubuntu), and follows a modularised configuration strategy.
 
Hence, whilst the Apache source may httpd.conf for its configuration, you will actually find the config has been split amongst various files - apache2.conf for server-level config, sites-available/* for site-specific config, conf.d/* for other specific config etc etc.
 
It takes a bit to get your head round, and indeed makes following generic Apache HowTo's/guides somewhat difficult to get your head around at first but you will soon learn to know what's where. Once you gain familiarity you will then begin to realise the advantages this modularisation brings. It also aids the integration of functionality from other packages.
 
I seem to recall /usr/share/doc/apache2/README.Debian (or similar) may hold some further info (I'm not at my machine to check).
 
Something which may help tie all this apparent madness up - have a read through apache2.conf and you will see various Include statements which include the config from the quoted files. Hence, apache2.conf can be viewed as the 'top level' configuration file (much like httpd.conf is elsewhere) and all the lower level (site-, module-specific etc) config is included in the config without requiring a single massive file.
 
Does that help?
 
Mathew

---

### Post by lemuren on 2008-01-29
> **MJN said:**
> This is a common cause of confusion.... (so take some comfort in that!)
 
The issue is that the Apache package has been customised quite heavily for Debian, and Debian-based distributions (like Ubuntu), and follows a modularised configuration strategy.
 
Hence, whilst the Apache source may httpd.conf for its configuration, you will actually find the config has been split amongst various files - apache2.conf for server-level config, sites-available/* for site-specific config, conf.d/* for other specific config etc etc.
 
It takes a bit to get your head round, and indeed makes following generic Apache HowTo's/guides somewhat difficult to get your head around at first but you will soon learn to know what's where. Once you gain familiarity you will then begin to realise the advantages this modularisation brings. It also aids the integration of functionality from other packages.
 
I seem to recall /usr/share/doc/apache2/README.Debian (or similar) may hold some further info (I'm not at my machine to check).
 
Something which may help tie all this apparent madness up - have a read through apache2.conf and you will see various Include statements which include the config from the quoted files. Hence, apache2.conf can be viewed as the 'top level' configuration file (much like httpd.conf is elsewhere) and all the lower level (site-, module-specific etc) config is included in the config without requiring a single massive file.
 
Does that help?
 
Mathew

Thanks Mathew.
It´s always nice to know that i´m not the only one confused :-)

The README.Debian explained a bit.

Too bad that this info isn´t available in the ubuntu documentation, or referred to.
Is there any sort of cross reference guide between apache and debian/ubuntu, or any more extensive docs describing the debian/ubuntu apache flavour that you know of?
I´m trying to get WebGUI working, and since they are referring to httpd.conf, which is empty, i guess i should put the stuff somewhere else... :confused:

Anyway, thanks again Mathew for pointing me in the right direction.

Best regards,
Lage

---

### Post by MJN on 2008-01-29
I'm not personally aware of any such documentation but I'd be surprised if there wasn't something somewhere on the web.

Regarding httpd.conf you indeed best staying out of it - it's purely there for backwards compatibility (e.g. packages which would otherwise write to this file expecting it to be Apache's config) and so you should go with apache2.conf and/or your virtualhost config in sites-available/.

For what it's worth I've added very little to apache2.conf - the majority changes I've made are just changing specific default directives that were already in it. Instead I have a different file in sites-available/ for each of the domains I host, and separate <virtualhost> containers inside each for the individual hosts - it is inside these that I have put my config.

If you have specific questions on where the best place is for a certain directive, or a collection of directives from a HowTo etc, just shout and I'm sure someone can steer you in the right direction.

Mathew

---

### Post by patton508 on 2008-01-30
Windows guy here trying hard to convert to Linux via Ubuntu 7.10.  I know IIS well enough but have problems getting a few basics down with ubuntu and apache/lamp.  Question is how do I get a browser to read my site by typing it in as when I do this I see a directory showing the two sites (default and site 1).  Apache doesn't DISPLAY the index.html by default and I assume my default setting directive is is not correct as it doesn't open up index.html.  I can click in the directory and the site displays correctly but obviously this isn't what I want to do.  I am sure it is just me doing some stupid rookie thing but I am determined to figure this out.  I am runnning out of web searching gas after a week of fooling around with it.  I feel like I am very close to getting it but just need to get it to open up the page rather than show the domain site index when typing the URL

See below screen capture from the displayed page whether internal or external IP is used:

Index of /
[ICO]	Name	Last modified	Size	Description
[DIR]	apache2-default/	20-Nov-2004 15:16 	-
[DIR]	site1/	22-Jan-2008 23:33 	-
Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6 Server at 10.75.0.5 Port 80

Not sure if the problems revolves around the sites-available/sites-enabled directive but I am lost.  Please help and thanks in advance.  As soon as I figure this out I would love to host a few domains at home for fun and training and get off IIS at home.  Any help on that would be great.  Can anyone recommend the best and or quickest way to learn apache a little better as we would like to lean on external support less for the more simple admin work and I am dying to know more and improve my skills.  I don't give up easily:)

One other question - I have been reading about frontpage extensions running on apache.  Does this work as if this is possible and runs well I have a frontpage site and it would be nice to use it on this apache server?  Thanks  Patton

---

### Post by MJN on 2008-01-30
Do you have two sites? Does each have their own <Virtualhost> containers in either the same, or different, files in /etc/apache2/sites-available/ ?
 
You need change the DocumentRoot settings for each site - to tell Apache the root for each site is /var/www/apache2-default and /var/www/site1 respectively (or wherever your sites are in the filesystem).
 
In order to support the displaying of index.html by default you need to find the DirectoryIndex directive in /etc/apache2/apache2.conf (I'm pretty sure it exists as standard) and add index.html to the line. Note that the order of this line is important - earlier entries take precedence in the case of multiple matches.
 
Does that help? Shout if you need it in more detail (and/or post your config for specific advice).
 
Mathew

---

### Post by patton508 on 2008-01-30
here is contents of the file /etc/apache2/sites-available/default: 

NameVirtualHost *
<VirtualHost *>
	ServerAdmin [email]myname@yahoo.com[/email]
	
	DocumentRoot /var/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined
	ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>


I have not made the changes you suggested but thought it made sense to let you see what I have now from the default build to avoid error.  I don't "need" multiple sites if it too much of as hassle given my newbie linux skills but it would be cool to try and host a couple at home (one quasi work tech like and another personal).  If that poses large obstacles I am totally fine with doing that later and only having one site up and running.  I have the option of having multiple pc's and a decent firewall at home and am comfortable with that so the big obstacle is my ubuntu/apache skills.  Ignorant by determined! Thanks in advance.

---

### Post by MJN on 2008-01-31
That's fine. Just edit it as per the following (changes in **bold**):
 
[FONT=Arial]NameVirtualHost *[/FONT]
[FONT=Arial]<VirtualHost *>[/FONT]
[FONT=Arial]**ServerName **[/FONT][[FONT=Arial]**www.mymainsite.com**[/FONT]]("http://www.mymainsite.com")
[FONT=Arial]**ServerAlias mymainsite.com**[/FONT]
[FONT=Arial]ServerAdmin [/FONT][EMAIL="myname@yahoo.com"][FONT=Arial]myname@yahoo.com[/FONT][/EMAIL]
 
[FONT=Arial]DocumentRoot /var/www/**apache2-default**[/FONT]
[FONT=Arial]<Directory />[/FONT]
[FONT=Arial]Options FollowSymLinks[/FONT]
[FONT=Arial]AllowOverride None[/FONT]
[FONT=Arial]</Directory>[/FONT]
[FONT=Arial]<Directory /var/www/**apache2-default**>[/FONT]
[FONT=Arial]Options Indexes FollowSymLinks MultiViews[/FONT]
[FONT=Arial]AllowOverride None[/FONT]
[FONT=Arial]Order allow,deny[/FONT]
[FONT=Arial]allow from all[/FONT]
[FONT=Arial]# This directive allows us to have apache2's default start page[/FONT]
[FONT=Arial]# in /apache2-default/, but still have / go to the right place[/FONT]
[FONT=Arial]#RedirectMatch ^/$ /apache2-default/[/FONT]
[FONT=Arial]</Directory>[/FONT]
 
[FONT=Arial]ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/[/FONT]
[FONT=Arial]<Directory "/usr/lib/cgi-bin">[/FONT]
[FONT=Arial]AllowOverride None[/FONT]
[FONT=Arial]Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch[/FONT]
[FONT=Arial]Order allow,deny[/FONT]
[FONT=Arial]Allow from all[/FONT]
[FONT=Arial]</Directory>[/FONT]
 
[FONT=Arial]ErrorLog /var/log/apache2/error.log[/FONT]
 
[FONT=Arial]# Possible values include: debug, info, notice, warn, error, crit,[/FONT]
[FONT=Arial]# alert, emerg.[/FONT]
[FONT=Arial]LogLevel warn[/FONT]
 
[FONT=Arial]CustomLog /var/log/apache2/access.log combined[/FONT]
[FONT=Arial]ServerSignature On[/FONT]
 
[FONT=Arial]Alias /doc/ "/usr/share/doc/"[/FONT]
[FONT=Arial]<Directory "/usr/share/doc/">[/FONT]
[FONT=Arial]Options Indexes MultiViews FollowSymLinks[/FONT]
[FONT=Arial]AllowOverride None[/FONT]
[FONT=Arial]Order deny,allow[/FONT]
[FONT=Arial]Deny from all[/FONT]
[FONT=Arial]Allow from 127.0.0.0/255.0.0.0 ::1/128[/FONT]
[FONT=Arial]</Directory>[/FONT]
 
[FONT=Arial]</VirtualHost> [/FONT]
 
That'll be your first/main site. Just repeat this config (without the **NameVirtualHost *** directive - this is required only once) in a second file in /etc/apache2/sites-available/ and
edit **ServerName**, **ServerAlias, DocumentRoot, Directory <DocumentRoot> **and, optionally, **ErrorLog/CustomLog** (to keep the logs for this site separate).
 
Then enable your second site with **sudo a2ensite <filename of site>**
 
Does that makes sense?
 
Mathew

---

### Post by Pekkalainen on 2008-02-14
Pardon me for dragging an old thread out of the pits of forgotten threads. Im configuring a server with 2 sites and I found this thread to be the most enlightening, but not enough to make my server work as intended ;)

So my problem is this: I have made 2 files in */sites-enabled/ one called mainsite wich is supposed to be the root of my server that my no-ip.org adress will point to by default. The other one directed to my experimental wordpress blog so the file is simply called blog.

mainsite points to var/www and blog points to var/www/blog where the blog is. I have followed the directions here but for some reason when I type in my no-ip.org adress I get directed to the blog!

here is my */sites-enabled/mainsite;

```

NameVirtualHost *
<VirtualHost *>
        ServerName http://myurl.no-ip.org/
        ServerAlias myurl.no-ip.org/
        ServerAdmin mymail@gmail.com

        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>


```

And here is my */sites-enabled/blog: 

```

<VirtualHost *>
        ServerName http://myurl.no-ip.org/blog/
        ServerAlias myurl.no-ip.org/blog/
        ServerAdmin mymail@gmail.com

        DocumentRoot /var/www/blog
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/blog>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```


So I want myurl.no-ip.org to point to the index.html I have placed in /var/www/ and I want myurl.no-ip.org/blog/ to point to /var/www/blog/ where wordpress does the rest. But when i type in myurl.no-ip.org I am redirected to the blog and myurl.no-ip.org/blog/ gives me a slightly annoying 404.

What gives? Any other newbie tips for an aspiring webmaster is also appreciated of course :)

---

### Post by MJN on 2008-02-14
Believe it or not it's partly because *blog* comes before *mainsite* alphabetically...
 
However, you would not have fallen into this trap had you put the config files in the right place! ;-)
 
Your config should go in /etc/apache2/sites-available/ and then have symlinks (not the files/config themselves) in /etc/apache2/sites-enabled/
 
The 'default' site config would have been /etc/apache2/sites-available/default and the symlink /etc/apache2/sites-enabled/000-default. Note the symlink filename - chosen so that it always appears first in sites-enabled hence determines the default site when no ServerName matches.
 
Another problem you have is your ServerName and ServerAlias syntax - strip out the http: and all slashes as you need only the name in these directives.
 
Fix these problems and you should be up-and-running.
 
Mathew

---

### Post by Pekkalainen on 2008-02-14
> **MJN said:**
> Believe it or not it's partly because *blog* comes before *mainsite* alphabetically...
 
However, you would not have fallen into this trap had you put the config files in the right place! ;-)
 
Your config should go in /etc/apache2/sites-available/ and then have symlinks (not the files/config themselves) in /etc/apache2/sites-enabled/
 
The 'default' site config would have been /etc/apache2/sites-available/default and the symlink /etc/apache2/sites-enabled/000-default. Note the symlink filename - chosen so that it always appears first in sites-enabled hence determines the default site when no ServerName matches.
 
Another problem you have is your ServerName and ServerAlias syntax - strip out the http: and all slashes as you need only the name in these directives.
 
Fix these problems and you should be up-and-running.
 
Mathew

That cleared a lot of things up thanks ;)
It works now but when I restarted apache after creating the symlink I get a weird error:

```

 * Restarting web server apache2                                                                
[Thu Feb 14 17:50:02 2008] [warn] NameVirtualHost *:0 has no VirtualHosts
[Thu Feb 14 17:50:14 2008] [warn] NameVirtualHost *:0 has no VirtualHosts
                                                                                         [ OK ]

```

I have looked through the files for a spelling error of *:80 but I only have * everywhere, no port specified. :confused:

---

### Post by Pekkalainen on 2008-02-14
should the blogs folder be owned by anyone else than root? I suppose it should...

---

### Post by MJN on 2008-02-14
The names in NameVirtualHost and VirtualHost directives must match exactly. HAve you changed your config from the above? Do you have a NameVirtualHost directive anywhere else in your config (e.g. in apache2.conf etc)?

What do you mean by the blogs 'folder'? The folder where the blog content sits? If so, it should ideally be owned by Apache (www-data) then you don't need to open up the permissions like you would if it is owned by root.

Mathew

---

### Post by Pekkalainen on 2008-02-14
Yeah the folder /var/www/blog/ is owned by root. I'm googling the commands for that so lets just focus on apache itself.

I managed to get rid of the error msgs, apache is happy for now. But I seem to have a problem with my router. My server is connected to a router and is given its own internal IP, when someone from the outside access the mainsite it works fine, but when they try the blog the server tries to route them to the servers internal IP, got any suggestions on that? It of course works fine for me behind the router but that doesnt make for a nice ammount of hits on the page :D

Thanks for putting up with all of this :)

---

### Post by MJN on 2008-02-14
Your problem of external visitors trying to reach your private IP is likely a DNS issue i.e. your no-ip configuration. If you are using some sort of client to update the DNS you will have to ensure it updates it with the external (public) IP address and not whatever the address of the machine itself.

Without knowing the URL all this is guesswork I'm afraid!

Mathew

---

### Post by Pekkalainen on 2008-02-14
Okay since I dont want this spread around the world quite yet I will PM you the adresses if its OK so you can check it out and we solve it right here, there's nothing bad on the site it's just my vanity playing tricks on me :D

---

### Post by MJN on 2008-02-15
I got the info - thanks.

As the domains are the same we can rule out a DNS issue so I ran a packet trace on a connection request to your blog and saw a '301 Move Permanently' redirect to your internal address.

On the assumption you haven't changed the config above (or, at least, haven't added some ReWrite rules) then it must be your blogging software... whatever it is I don't have any experience of it but someone might!

Mathew

---

### Post by Pekkalainen on 2008-02-15
You know what? That did the trick! Wordpress was the bad guy all along, I dug deep within its settings (normal settings didnt suffice here apparently) and I found an adress setting that pointed towards the internal IP, changed it to the domain adress and voila! :)

Thanks for all your help!

---

### Post by MJN on 2008-02-15
Excellent! :)

---

### Post by Enforcer83 on 2008-03-16
sorry about digging up this old thread but I just want to make sure this looks right from my /etc/apache2/sites-available/default because I am getting this error

apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

```
NameVirtualHost *
<VirtualHost *>
	ServerName localhost
	ServerAdmin webmaster@localhost
	
	DocumentRoot /home/enforcer/www/public-html/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/enforcer/www/public-html/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
	</Directory>

	ScriptAlias /cgi-bin/ /home/enforcer/www/cgi-bin/
	<Directory "/home/enforcer/www/cgi-bin/">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined
	ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

---

### Post by MJN on 2008-03-17
That's not an error as such, but more of a warning.
 
It is basically saying it doesn't know what it's **fully qualified** name is - you've only told it 'localhost' but to be full qualified required the domain e.g. localhost.localdomain would suffice in your case.
 
It matters little in this situation as you only have the one site hence all requests would be satisfied by the same virtual host. Only when you start hosting multiple sites on the same box does it become necessary to ensure each site is correctly (and fully) labelled with a fully qualified server name.
 
There are some other benefits for removing the ambiguities regarding server names but it'll complicate matters if raised for this.
 
Mathew

---

