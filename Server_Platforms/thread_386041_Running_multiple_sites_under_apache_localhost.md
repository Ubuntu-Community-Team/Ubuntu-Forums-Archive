---
title: "Running multiple sites under apache localhost"
date: 2007-03-16
forum: Server Platforms
---

### Post by maniacmusician on 2007-03-16
I'm an amateur (very amateur) web developer, and in the past, I've found that setting up a local server with apache has been super useful. However, at the time, I was only working on one website.

Now I need to work on 2 or 3 at the same time. So, is it possible to set up multiple servers? Or have many dirs and have apache treat each one as "/" and assign each a different address?

This would really be invaluable to me, and would make everything a hell of a lot easier. 

Thanks.

---

### Post by elst on 2007-03-16
Try using "virtual hosts", one per site. This functionality is built-in to Apache, and the documentation explains how it works.

---

### Post by maniacmusician on 2007-03-16
> **elst said:**
> Try using "virtual hosts", one per site. This functionality is built-in to Apache, and the documentation explains how it works.
Thanks for the reply, it did enlighten me a little bit...but some of that documentation is indeed over my head. I get the general drift of it, I think. Tell me if the following is right;

To get different websites, I have to set up different "virtual hosts", which I configure in /etc/apache2/sites-enabled/default ? That's the understanding of it that I have so far, but there a few things that puzzle me. For instance, here's my sites-enabled/default:

```

NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
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
		Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
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
Why is there an asterisk in the beginning by VirtualHost? Isn't the name of the virtualhost supposed to be there? If I try to replace the asterisk with a name, it spits out errors at me when I restart apache.

So I'm afraid I don't quite understand this yet...

---

### Post by elst on 2007-03-16
The way to do this on Ubuntu or Debian is to create a file per virtual host in /etc/apache2/sites-available/. The contents of each file should look something like this:

```

  ## --- Apache 2 Virtual Host for site1 ---
  <VirtualHost *>

    # Virtual host name in DNS
    ServerName site1.mydomain.com

    # The main directory for this site
    DocumentRoot /srv/sites/site1

    # Separate error log for this site
    ErrorLog /var/log/apache2/site1-error.log

   # Separate access log for this site
   CustomLog /var/log/apache2/site1-access.log combined

    <Directory /srv/sites/site1/ >

      # Allow access from all systems
      Allow from all
      Order allow,deny

    </Directory>

  </VirtualHost>

```

The * means that the site is available from any IP address associated with the host system - you only need to change it for those virtual hosts identified by IP address or port number.

Once you have a file for a virtual host you enable the virtual host like this:

sudo /usr/sbin/a2ensite <file name>

Then reload Apache:

sudo /etc/init.d/apache2 reload

This arrangement means that you can disable a specific virtual host at any time with a2dissite:

sudo /usr/sbin/a2dissite <file name>
sudo /etc/init.d/apache2 reload

I'd recommend leaving the default site alone as much as possible, and creating subdirectories within /srv/ for your sites.

Hope that helps.

---

### Post by maniacmusician on 2007-03-16
Okay, that makes more sense.

I added two dummy sites to /var/www. Now, when I browse to "localhost", **I get an apache frontpage giving me a list of dir's**. This is supposed to happen, right?

When I click on one of the sites, I get an error
> You don't have permission to access /site/index.html on this server.
Which effectively prevents me from viewing the site. I assume the answer lies somewhere in apache2.conf.....

---

### Post by elst on 2007-03-16
With Ubuntu and Debian you don't need to touch the supplied configuration files at all - just make virtual hosts, and enable or disable modules you need with a2enmod/a2dismod.

Again, I'd recommend that you keep your private sites in /srv/, with one directory per virtual host. This keeps things simple and clean. Putting stuff inside /var/www/ has two issues: The contents are populated by packages, and it is used for the default Apache Web site. The /srv/ directory is explicitly for administrators to put their own files in, so you won't get conflicts.

EDIT: If you have named virtual hosts then you need to add those names to DNS, or the /etc/hosts file on the local system, and access sites by using those names.

---

### Post by maniacmusician on 2007-03-16
> **elst said:**
> With Ubuntu and Debian you don't need to touch the supplied configuration files at all - just make virtual hosts, and enable or disable modules you need with a2enmod/a2dismod.

Again, I'd recommend that you keep your private sites in /srv/, with one directory per virtual host. This keeps things simple and clean. Putting stuff inside /var/www/ has two issues: The contents are populated by packages, and it is used for the default Apache Web site. The /srv/ directory is explicitly for administrators to put their own files in, so you won't get conflicts.

EDIT: If you have named virtual hosts then you need to add those names to DNS, or the /etc/hosts file on the local system, and access sites by using those names.
okay, I did that, but it still didn't change anything. I still get the 403 forbidden when I try to access either one of the dummy sites that I set up.

Also, when I reload apache2, I get this error:
>  * Reloading web server config...                                                                                                        5637
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Fri Mar 16 19:35:05 2007] [warn] NameVirtualHost *:0 has no VirtualHosts
[Fri Mar 16 19:35:05 2007] [warn] NameVirtualHost *:0 has no VirtualHosts

is that okay?

---

### Post by elst on 2007-03-16
OK, double-check your config files for your virtual hosts, and the permissions on the directories that the virtual hosts use. 403 is usually permissions.

EDIT: The error message that you posted implies that there are no enabled virtual hosts. You can see links to all of the enabled sites in /etc/apache2/sites-enabled/.

---

### Post by maniacmusician on 2007-03-16
> **elst said:**
> OK, double-check your config files for your virtual hosts, and the permissions on the directories that the virtual hosts use. 403 is usually permissions.

EDIT: The error message that you posted implies that there are no enabled virtual hosts. You can see links to all of the enabled sites in /etc/apache2/sites-enabled/.
How do I check the permissions? I mean, what are the permissions directives?

Also, sites-enabled contains links for both of the VirtualHosts.

---

### Post by outofnicks on 2007-03-16
I'm kind of a novice at server setup, but seems to me that using virtual hosts is more trouble than it's worth if you don't have or need domains attached to your sites--if they're only local, why not just create a user for each site? Then all you have to do is enable each user in /etc/apache/http.conf  here:
```
#
# UserDir: The name of the directory which is appended onto a user's home
# directory if a ~user request is received.
#
<IfModule mod_userdir.c>
    UserDir public_html
UserDir disabled
UserDir enabled user1 user2
```

And create a directory in each user's account named "public_html" or whatever you want.

Your URLs will be [http://localhost/~user1](http://localhost/~user1) and [http://localhost/~user2](http://localhost/~user2) and...
That's what I'm doing and works fine as long as you don't need a domain name for them.
I'm running Apache (pre Apache2) so I'm not sure how different Apache2 is but it should be similar.

---

### Post by maniacmusician on 2007-03-16
> **outofnicks said:**
> I'm kind of a novice at server setup, but seems to me that using virtual hosts is more trouble than it's worth if you don't have or need domains attached to your sites--if they're only local, why not just create a user for each site? Then all you have to do is enable each user in /etc/apache/http.conf  here:
```
#
# UserDir: The name of the directory which is appended onto a user's home
# directory if a ~user request is received.
#
<IfModule mod_userdir.c>
    UserDir public_html
UserDir disabled
UserDir enabled user1 user2
```

And create a directory in each user's account named "public_html" or whatever you want.

Your URLs will be [http://localhost/~user1](http://localhost/~user1) and [http://localhost/~user2](http://localhost/~user2) and...
That's what I'm doing and works fine as long as you don't need a domain name for them.
I'm running Apache (pre Apache2) so I'm not sure how different Apache2 is but it should be similar.
well I've already set up virtualhosts...and it really wasn't that hard. I just copied over the default VirtualHost file and made a few modifications. I just need to figure out how to get around the 403 issue.

edit: actually, it's not even seeing the virtualhosts...I'm looking again at the site files, I don't know why it's not working

---

### Post by maniacmusician on 2007-03-16
I got it to see the VirtualHosts by mapping them to specific IP addresses instead of leaving it at *. Now, another question; How do I get other computers on the same network to be able to see these virtualhosts?

---

### Post by elst on 2007-03-17
You'll have to add those IP addresses as "aliases" for your computer's network interface. The graphical tool doesn't support this, so you'll need to edit the configuration file directly:

sudo nano /etc/network/interfaces

Thinking about it, port-based vhosts are probably best on a development laptop or similar - just assign one per site, and then you can do "http://localhost:85", "http://localhost:86" etc. Obviously that's not so good for publically accessible sites.

@outofnicks: Using virtual hosts gives you a separately working Apache config file for each site without modifying any .htaccess files in the site. Rails in particular seems to assume virtual hosts, and uses a .htaccess file within each application.

---

### Post by maniacmusician on 2007-03-17
> **elst said:**
> You'll have to add those IP addresses as "aliases" for your computer's network interface. The graphical tool doesn't support this, so you'll need to edit the configuration file directly:

sudo nano /etc/network/interfaces

Thinking about it, port-based vhosts are probably best on a development laptop or similar - just assign one per site, and then you can do "http://localhost:85", "http://localhost:86" etc. Obviously that's not so good for publically accessible sites.

@outofnicks: Using virtual hosts gives you a separately working Apache config file for each site without modifying any .htaccess files in the site. Rails in particular seems to assume virtual hosts, and uses a .htaccess file within each application.
What's the format for entering that? How do I tell it localhost:11 equates to 127.0.1.3?

Also, I'm sort of confused as to how it would let other computers on the network see the site. Could you explain the logic behind it please?

---

### Post by elst on 2007-03-17
[http://httpd.apache.org/docs/2.2/vhosts/examples.html](http://httpd.apache.org/docs/2.2/vhosts/examples.html)

If you do a find on the page for "Running different sites on different ports.", you'll get to the section. The only difference on Ubuntu is that you split the settings for each site into a different file.

---

### Post by maniacmusician on 2007-03-17
alright, thanks. That works beautifully.

Now, say I turned this box into a web server. How would I get it to serve up the site from behind a wireless router? or should I really start another thread for that? :)

---

### Post by elst on 2007-03-17
With port-based vhosts it should just work (I really wish I'd thought of that earlier), e.g. just put http://<ip address>:<site port> in a Web browser. 

For IP -based hosts the system has to actually have those addresses associated with a network interface. For name-based hosts the names need to be associated with the system, either in DNS, or in the hosts file for each system.

If it works from the system itself, but you can't access sites from remote systems then it's probably a networking issue, so best handled with a fresh thread.

---

