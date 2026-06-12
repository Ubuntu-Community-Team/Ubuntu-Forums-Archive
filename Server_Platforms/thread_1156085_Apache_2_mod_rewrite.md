---
title: "Apache 2 mod_rewrite"
date: 2009-05-11
forum: Server Platforms
---

### Post by danielgroves on 2009-05-11
Hi all,

**How do I enable mod_rewrite on Apache?** 

I have never set-up a proper working development server before, and need a mod-rewrite enabled for testing as I am currently writing a customer CMS.  How can I do this?  I tryed running the following command:
```
a2enmod rewrite
```
And got the response:
```
Run '/etc/init.d/apache2 restart to activate new configeration!
```

I did this and I then got this response:
```

*Restarting web server apache2
apache2: Could not reliably determine the server's fully qualified name name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified name name, using 127.0.1.1 for ServerName
(13)Permission denied: make_sock: could not bind address 0.0.0.0:80 no listing sockets avalable, shutting down
Unable to open logs
                                         [fail]

```
After this I tried to sudo the command:
```

*Restarting web server apache2
apache2: Could not reliably determine the server's fully qualified name name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified name name, using 127.0.1.1 for ServerName
                                                 [OK]

```

---

### Post by Alekz_ on 2009-05-11
Did you run the restart commando as root (sudo)?

---

### Post by danielgroves on 2009-05-11
Thanks fort your reply!

Yes, result is in the very last box on my first post.

---

### Post by Alekz_ on 2009-05-11
Sorry! My mistake! :)

You have to modify your /etc/hosts with the FQDN of you server!

ie
```
xxx.xxx.xxx.xxx yourserver.yourdomain yourserver
```

And then, restart apache!

---

### Post by danielgroves on 2009-05-11
The folder /etc/hosts/ doesn't exits!?!

I should probably make it clear that I am not used to doing this type of task, so off you point I do have a few questions:

What is the FQDN?
Where you right xxx.xxx.xxx.xxx is that where the machine IP goes?
Can I put anything whjere it says yourserver.yourdomain?
Is yourserver the name of my server?

Thanks, Dan.

---

### Post by Alekz_ on 2009-05-11
Well, I'll give you an example, but first...

FQDN = Full Qualified Domain Name
xxx.xxx.xxx.xxx = You server IP address
yourserver.yourdomain = Yeah.. You can use something like: myserver.com
YES! yourserver is YOUR SERVER name!

/etc/hosts isn't a directory, but a file!

You have to edit this file... 

The head lines will look like this:

```
127.0.0.1       localhost
127.0.0.1       yourserver
```

You need to modify the file and put the "FQDN".

```
127.0.0.1       yourserver.com       yourserver
```

Hmm Hope you understand! :)

---

### Post by danielgroves on 2009-05-11
Ok, I think I got it!

Does this about right (before I save it and screw everything up!)

```

127.0.0.1       danielserver.local       DANIEL-SERVER

#127.0.0.1	localhost
#127.0.1.1	daniel-server

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

Everything below "# The following lines are desirable for IPv6 capable hosts" was alreay there so I just left it.  

Thanks, Dan.

---

### Post by Alekz_ on 2009-05-11
OK! You don't have to worry about IPV6, unless you're using it! :)

That's it! I just forgot to mension.. You MUST use TABs between the filds (IP, FQDN and hostname) on your hosts file!

Try it and post the results (don't forget to restart apache)

---

### Post by danielgroves on 2009-05-11
Nope, still not working :(
Heres what restarting apache returned:
```
 * Restarting web server apache2                                                 ... waiting    
```

Could it accessing the server over a network be the problem?  i.e. I have my vista laptop connected to the same network.  When I put [http://daniel-server](http://daniel-server) into a browser I can access the files in my servers /var/www/ directory.  

In this directory I have wordpress installed using the mod_rewrite to generate the URLs so I have daniel-server/about rather than daniel-server/post_id=2.  

Could me accessing this off another machine on the network be the problem?

---

### Post by Alekz_ on 2009-05-11
You set your server name on the hosts file, but you have to set the httpd.conf with the new information about your servername!

If you're trying to access the site from a client, make sure that your client understand that daniel-server is the IP xxx.xxx.xxx.xxx (yeah! your server address).

But your apache was able to start? You post that the service was "waiting", but the service became available?

---

### Post by danielgroves on 2009-05-11
Ok, I added this line to httpd.conf:
```
127.0.0.1       danielserver.local       DANIEL-SERVER

```

When I restarted apache it just ended on waiting... and then let me type another command.  I just ran the restart command again, and this is the result:

```
/etc/apache2$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                 * We failed to correctly shutdown apache, so we're now killing all running apache processes. This is almost certainly suboptimal, so please make sure your system is working as you'd expect now!
 ... waiting Syntax error on line 1 of /etc/apache2/httpd.conf:
Invalid command '127.0.0.1', perhaps misspelled or defined by a module not included in the server configuration
[fail]

```

---

### Post by Alekz_ on 2009-05-11
NO! :)

You don't put this line into your httpd.conf..

When I said "put the new information", you should update the information of ServerName field!

Hmm looks like you are not familiar with the configuration file.. 

Find the line with:
```
ServerName www.example.com:80
```

and replace with
```
ServerName danielserver.local:80
```

I recommend that you read the Apache Documentation (httpd.apache.org/docs/)

It'll help you to understand a lot of things, include the ServerName and LoadModule

[]'s

---

### Post by danielgroves on 2009-05-11
Ok the httpd.conf file was empty, so I added the line anyway.  

This time when I started apache I got this message:
```
 * Restarting web server apache2                                         [ OK ] 

```

Still no luck on my laptop top, but I tried as localhost on my ubuntu machine, and it worked perfectly.  The first time.  But, after that it didn't work! :/

---

### Post by Alekz_ on 2009-05-11
NOOOO!! EMPTY? The httpd.conf cannot be empty!

Are you sure you're looking for the correct file?

I don't know where's your apache installed, but the file suposed to be in:
```
installation_dir/conf/httpd.conf
```

That's the default configuration.. Of course it can be changed..

---

### Post by danielgroves on 2009-05-11
/etc/apache2/httpd.conf

theres no /etc/apache2/conf/ folder

but there is apache2.conf which is also empty!

Running a search for any other instances now

---

### Post by cdenley on 2009-05-11
First, a couple things.

1. The warning about not being able to determine your fqdn is harmless.
2. The httpd.conf file should no longer be used.
```

zcat /usr/share/doc/apache2/README.Debian.gz|less

```

Now, what exactly is the problem you're experiencing?

---

### Post by danielgroves on 2009-05-11
From the top:

mod_rewrite isn't working.  I can't seem to get it to work either.

---

### Post by cdenley on 2009-05-11
> **danielgroves said:**
> From the top:

mod_rewrite isn't working.  I can't seem to get it to work either.

Works fine for me. Post the site configuration you're having trouble with. If it is the default site:
```

cat /etc/apache2/sites-available/default

```
Are you sure you're browser isn't displaying a cached page? So when accessed from your server ([http://localhost](http://localhost)), it redirects you based on a rule you created, but when accessed from your laptop, what happens?

---

### Post by danielgroves on 2009-05-11
> **cdenley said:**
> Works fine for me. Post the site configuration you're having trouble with. If it is the default site:
```

cat /etc/apache2/sites-available/default

```
Are you sure you're browser isn't displaying a cached page? So when accessed from your server ([http://localhost](http://localhost)), it redirects you based on a rule you created, but when accessed from your laptop, what happens?

```

<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
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


The same happens on both machines: 404.

---

### Post by cdenley on 2009-05-11
> **danielgroves said:**
> ```

<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
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


The same happens on both machines: 404.

What do you expect to happen? I don't see any mod_rewrite rules.
```

<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options FollowSymLinks MultiViews
		AllowOverride Options Indexes
		Order allow,deny
		allow from all
		[B]RewriteEngine On
		RewriteRule ^old\.html$ new.html[/B]
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
[http://httpd.apache.org/docs/2.2/mod/mod_rewrite.html](http://httpd.apache.org/docs/2.2/mod/mod_rewrite.html)

---

### Post by danielgroves on 2009-05-11
Cleared the cache on both machines, and still no luck with either.  I added the lines you showed and restarted apache, again no luck.  Still not working.  

@cdenley At this point I would like to repeat that I am a complete novice at server-side stuff.  I am a web design and so not used to dealing with this type of stuff.

---

### Post by cdenley on 2009-05-11
> **danielgroves said:**
> Cleared the cache on both machines, and still no luck with either.  I added the lines you showed and restarted apache, again no luck.  Still not working.  

@cdenley At this point I would like to repeat that I am a complete novice at server-side stuff.  I am a web design and so not used to dealing with this type of stuff.

What do you expect mod_rewrite to actually do?!?! Where have you configured it to do this? Simply enabling the module doesn't do anything but make the configuration options in the link I posted available to you.

---

### Post by danielgroves on 2009-05-11
I hvae a wordpress installationg set-up on the server.  The permalink structures require mod_rewrite in order to have (for example) a page at example.com/about/ or a blog post at example.com/category/post-name.

As far as I was aware all I needed to do was to install mod_rewrite (which I am told LAMP has pre-installed) and cofigure wordpress, which is what I havce done as far as I can tell.

---

### Post by cdenley on 2009-05-11
> **danielgroves said:**
> I hvae a wordpress installationg set-up on the server.  The permalink structures require mod_rewrite in order to have (for example) a page at example.com/about/ or a blog post at example.com/category/post-name.

As far as I was aware all I needed to do was to install mod_rewrite (which I am told LAMP has pre-installed) and cofigure wordpress, which is what I havce done as far as I can tell.

Sorry, I don't know anything about wordpress. You should have mod_rewrite working, though. Perhaps you should start a new thread indicating you have a problem with wordpress.

---

### Post by danielgroves on 2009-05-11
OK, thanks for your time and help.

---

