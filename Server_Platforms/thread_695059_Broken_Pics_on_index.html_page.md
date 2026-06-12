---
title: "Broken Pics on index.html page"
date: 2008-02-12
forum: Server Platforms
---

### Post by stock1232 on 2008-02-12
I just config my first virtual host. [www.amswebsitedesign](www.amswebsitedesign). I have the index.html file and two .jpg files in var/www When I view the file through the file manager the pics load. When I type the url into firefox the pics are broken but the text on the page comes through. its a very simple test page. I have made sure the pic names are correctly spelled and the capitalization is the same. I think it might have to do with a apache or v host configuration.

<HTML>
<HEAD>
<TITLE>
Ana's Web Design
</TITLE>
</HEAD>
<BODY>
<H1> AMS Website Design </H1>

<P><img src="vonni.jpg" WIDTH=250 Height=259 ALT="Little Vonni">

<P><img src="kenny.jpg" WIDTH=250 Height=259 ALT="Little Kenny">

</BODY>
</HTML>

---

### Post by stock1232 on 2008-02-12
Here is the v host config and i have not modified the apache config.

NameVirtualHost *
<VirtualHost *>
	Listen 80
	ServerAdmin [email]psustock1232@yahoo.com[/email]
	ServerName [www.amswebsitedesign.com:80](www.amswebsitedesign.com:80)
	ServerAlias amswebsitedesign.com *.amswebsitedesign.com
	
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

---

### Post by faulkes on 2008-02-12
Check permissions on the jpg files

```

ls -l vonni.jpg
ls -l kenny.jpg

```

In all likelyhood the r bit isn't set for world readable.

Faulkes

---

### Post by stock1232 on 2008-02-13
Thanks that worked!!!!! 

Do I need to give permission to every file in www? I gave permission to the folder and thought it would pass to the files inside?

If I have a bunch of imagines and html files, do I need to give permission to every file?

Thanks

---

### Post by faulkes on 2008-02-13
> **stock1232 said:**
> Thanks that worked!!!!! 

Do I need to give permission to every file in www? I gave permission to the folder and thought it would pass to the files inside?

If I have a bunch of imagines and html files, do I need to give permission to every file?

Thanks

File permissions are dependent upon several factors, such as how the flies in the directory were initially created.  i.e. if you used vi or nano to create the files, then it will typically follow the umask setting, if you used sftp/scp or even a gui client for those to upload the files, then it may apply it's own mask to them.

The safest way is to apply it individually apply new permissions to the existing files (vs. attempting a global change).  Once that is fixed, investigate whether it is your umask setting or the client you used to upload the files.

To learn about umask and changing permissions

```

man chmod

as well as 

man bash (if you are using the bash/sh shell)

```

The settings for umask typically live in .bashrc and profile and you may have to
create these files (probably just .profile)

Or, if you prefer, you can test out on the command line with

```

UMASK=<octal 4 digit umask>
export UMASK

```


Faulkes

---

