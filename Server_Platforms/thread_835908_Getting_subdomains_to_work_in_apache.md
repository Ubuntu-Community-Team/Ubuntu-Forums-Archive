---
title: "Getting subdomains to work in apache"
date: 2008-06-20
forum: Server Platforms
---

### Post by mrpeenut24 on 2008-06-20
I've set up my server and I'm currently forcing it to run with ssl via mod_rewrite, so I've got two different files here that may be causing my problem.  Here's what I want to do:

I have a domain and I've set up a couple of CNAME entries.  What I want is for each of those CNAME entries to direct to different directories in my server.  For instance:

I have [www.mydomain.com]("http://www.mydomain.com") pointing to /var/www
I want to have mail.mydomain.com pointing to /usr/share/squirrelmail
and blog.mydomain.com pointing to /usr/share/wordpress.

Am I able to do this with VirtualHosts in apache?  How should I go about doing this, because what I've got now isn't working.  Here's my current sites-available/default:

```

NameVirtualHost *:80
<VirtualHost *:80>
    ServerAdmin me@mail.mydomain.com
    ServerName www.mydomain.com
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
        <IfModule mod_rewrite.c>
          <IfModule mod_ssl.c>
            RewriteEngine on
            RewriteCond %{HTTPS} !^on$ [NC]
            RewriteRule . https://%{HTTP_HOST}%{REQUEST_URI} [L]
          </IfModule>
        </IfModule>
    </Directory>

    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory "/usr/lib/cgi-bin">
        ...
    </Directory>

    ErrorLog /var/log/apache2/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog /var/log/apache2/access.log combined
    ServerSignature Off

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
       ...
    </Directory>

</VirtualHost>

<VirtualHost *:80>
    ServerAdmin me@mail.mydomain.com
    ServerName mail.mydomain.com
    DocumentRoot /usr/share/wordpress/
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /usr/share/wordpress>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
        <IfModule mod_rewrite.c>
          <IfModule mod_ssl.c>
            RewriteEngine on
            RewriteCond %{HTTPS} !^on$ [NC]
            RewriteRule . https://%{HTTP_HOST}%{REQUEST_URI} [L]
          </IfModule>
        </IfModule>
    </Directory>
</VirtualHost>

```
I've got a similar file called sites-available/ssl that handles the redirect to https.  Any ideas what the problem is or how I should go about getting this done (mod_rewrite maybe?)?

---

### Post by mbeach on 2008-06-21
yes, forgetting about the ssl for a moment, you need (or it is recommended you have) a file for each 'site' in sites-available.

So you'd have 3 files
/etc/apache2/sites-available/default
/etc/apache2/sites-available/mail
/etc/apache2/sites-available/blog

In each file you'd set the following ServerNames and DocumentRoots
/sites-available/default
ServerName [www.yoursite.com](www.yoursite.com)
DocumentRoot /var/www

/sites-available/mail
ServerName mail.yoursite.com
DocumentRoot /usr/share/squirrelmail

/sites-available/blog
ServerName blog.yoursite.com
DocumentRoot/usr/share/wordpress

Along with the corresponding <Directory > directives.

Use a2ensite to enable sites which creates a symbolic link in sites-enabled (as well as a couple of other steps I believe).

Use 
sudo /etc/init.d/apache2 reload 

to reload the configuration changes.  Once all that is working, deal with the ssl.


Some references:
[http://www.debian-administration.org/articles/207](http://www.debian-administration.org/articles/207)

This one will probably cover what you need for the ssl:
[http://mario.espaciolinux.com/apache2_ssl.html](http://mario.espaciolinux.com/apache2_ssl.html)

Good luck,
mb.

---

### Post by mbeach on 2008-06-21
if you've got a static IP, then I believe you want to be creating "A records" instead of CNAMES's in your registrar's control panel.  If you are using a dynamic ip service, then yes, you'd be creating CNAMES to point to your yoursite.dyndns.org (or whichever service you are using).

If it is the static IP scenario, all 3 [www.yoursite.com](www.yoursite.com), blog.yoursite.com, and mail.yoursite.com A RECORDS would point to the same IP address, then apache would take over from there using whatever is in the ServerName directive, matching up to what was originally requested by the client.

---

### Post by mrpeenut24 on 2008-06-21
I don't have a static IP.  I'm using no-ip, hence the cnames.  I've created the three separate entries and disabled ssl, but they all keep directing me to /var/www.  Do I need to have a <VirtualHost> tag at the top, or a NameVirtualHost?  As of now, the only one with the <VirtualHost> tag is default, and everything else is inside that.

---

### Post by mbeach on 2008-06-22
the sites are loaded in alphabetical order as listed in /etc/apache2/site-enabled, and only the first one needs the  NameVirtualHost (you'll get warnings otherwise, no biggie, just warnings).  You do need the VirtualHost tag in each of your site files.

so for example, your /etc/apache2/sites-available/mail file you'd likely have something like (here only to illustrate the virtual host parts, the other directives should be understood prior to use):
```

      1 NameVirtualHost *
      2 <VirtualHost *>
      3     ServerName mail.yoursite.com
      4     ServerAdmin you@yoursite.com
      5     DocumentRoot /usr/share/squirrelmail
      .     
      .     
     11     <Directory /usr/share/squirrelmail/>
     12         Options Indexes FollowSymLinks MultiViews
     13         #AllowOverride None
     14         AllowOverride All
     15         Order allow,deny
     16         allow from all
     17     </Directory>
      .
      .

```

don't forget to enable the sites, and tell apache to reload the configuration.

You may want to alter the "allow from all" for your particular needs.

If it still doesn't work, try editing the hosts file on the machine you are trying from to ensure its got nothing to do with the cname records.  I'd also check the access/error logs in /var/log/apache2 (or whereever you have the logs set) to see if the request is actually coming as mail.yoursite.com or is it arriving as yoursite.no-ip.net

---

### Post by mrpeenut24 on 2008-06-25
Thanks!  I just needed the <VirtualHost> tag.


EDIT:  I take that back.  Now it's telling me that it can't find the fqdn and it uses my IP address (not localhost).  Even if I disable all the sites except default.  And every one of them has a ServerName.  This doesn't seem to cause a problem, but it wasn't showing up before.  Any ideas?

---

### Post by mbeach on 2008-06-26
I suspect you are getting something like:
> 
 * Reloading apache 2.0 configuration...                                                                                            apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName

But does that prevent anything from working?

Its not really an apache issue I don't think.  Try running "hostname" and "hostname --fqdn" at the command line.

To get around that error, I believe you may need to edit your /etc/hosts file.
I'd do a "man hostname" and read up on the fqdn.  Specifically 
> 
Therefore  it  depends on the configuration (usually in /etc/host.conf) how you can change it. Usually (if the hosts file
is parsed before DNS or NIS) you can change it in /etc/hosts.


I've never really bothered since the virtual hosts work regardless (for me anyway).

---

