---
title: "Apache Virtual Hosts"
date: 2010-06-10
forum: Server Platforms
---

### Post by expatCM on 2010-06-10
I am attempting to set up three web sites as virtual hosts.  If I look at sites-available I see a file for default and one for each of the sites.  sites-enabled lists the three sites.

However, if I try to access the sites from a client I end up with google telling me that there is nothing found which is not quite what I was expecting.

The apache log is clean.

I have added the site names to the hosts file as an addition to localhost.

So I guess that things are set up correctly and I have missed a step.  How should I approach finding out what?

---

### Post by Bachstelze on 2010-06-10
You definitely shouldn't see anything Google... What are you typing in your browser?

---

### Post by expatCM on 2010-06-10
The sites have been set up as [www.sitename.com](www.sitename.com) so that appears as a directory and also is the name of the entry in sites-enabled (and added in hosts).

So in browser I enter [http://www.sitename.com](http://www.sitename.com)

---

### Post by Bachstelze on 2010-06-10
And you end up on Google? Are using Google's DNS servers, by any chance. If you do, change that, they are "lying DNS" and give false results, which get in the way when you try to figure out what's wrong.

---

### Post by expatCM on 2010-06-10
I think this may now be easy but I do not quite understand the fix ...

From a client, if I enter [http://www.website.com](http://www.website.com) in the browser address bar I end up with google.  However, I enter [http://serverIP/www.website.com](http://serverIP/www.website.com) I get the index.html to display for the site.

So what am I doing wrong........  Should I have an entry on the client hosts file to show that the sites are on the server IP?

---

### Post by Bachstelze on 2010-06-10
> **expatCM said:**
> I think this may now be easy but I do not quite understand the fix ...

From a client, if I enter [http://www.website.com](http://www.website.com) in the browser address bar I end up with google.  However, I enter [http://serverIP/www.website.com](http://serverIP/www.website.com) I get the index.html to display for the site.

So what am I doing wrong........  Should I have an entry on the client hosts file to show that the sites are on the server IP?

Can you paste the contents of the files you have in sites-enabled?

---

### Post by expatCM on 2010-06-10
Thank you for your help.  sites-enabled has four files.  Three are edited copies of each other.

The three sites follow this file.  The only change is the name 

This is the file [www.siteone.com](www.siteone.com).  sitetwo and sitethree reflect the same.
```

<VirtualHost *:80>
        ServerAdmin webmaster@siteone.com
ServerName www.siteone.com
        ServerAlias siteone.com

        # Indexes + Directory Root.
        DirectoryIndex index.html
DocumentRoot /mounts/drive2/users/xhomes/www.siteone.com/htdocs/

        # CGI Directory
        ScriptAlias /cgi-bin/ /mounts/drive2/users/xhomes/www.siteone.com/cgi-bin/
        <Location /cgi-bin>
                Options +ExecCGI
        </Location>


        # Logfiles
        ErrorLog  /mounts/drive2/users/xhomes/www.siteone.com/logs/error.log
        CustomLog /mounts/drive2/users/xhomes/www.siteone.com/logs/access.log combined
</VirtualHost>
```

The other file is called default
```

<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /mounts/drive2/users/xhomes/
	<Directory />
		Options FollowSymLinks
		AllowOverride AuthConfig
	</Directory>
	<Directory /mounts/drive2/users/xhomes/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride AuthConfig
		Order allow,deny
		allow from all
		RedirectMatch ^/$ /no_auth/
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

That is all there is ......

---

