---
title: "[SOLVED] Apache looking in wrong dir for htaccess?"
date: 2008-05-17
forum: Server Platforms
---

### Post by bennybobw on 2008-05-17
I'm having trouble setting up a virtual host in apache.
I'm getting a 403 error when I try to go to the site.
DocumentRoot should be /home/bennybobw/www/franksmith/drupal but it looks like apache is looking in /home/bennybobw/www for my .htaccess file.

Here's my site config file:

```

<VirtualHost *>
	ServerAlias franksmith
	ServerAdmin webmaster@localhost
	ServerName franksmith
	DocumentRoot /home/bennybobw/www/franksmith/drupal
	<Directory /home/bennybobw/www/franksmith/drupal>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
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

	ErrorLog /var/log/apache2/franksmith-error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/franksmith-access.log combined
	ServerSignature On

</VirtualHost>

```

And /var/log/apache2/franksmith-error.log 

> [Sat May 17 15:12:49 2008] [crit] [client 127.0.0.1] (13)Permission denied: /home/bennybobw/www/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable

I chmodded -R 755 /home/bennybobw/www/franksmith/drupal
```

-rwxr-xr-x  1 bennybobw bennybobw 32225 2008-05-17 13:03 CHANGELOG.txt
-rwxr-xr-x  1 bennybobw bennybobw   273 2008-05-17 13:03 cron.php
lrwxrwxrwx  1 bennybobw bennybobw     8 2008-05-17 13:03 files -> ../files
-rwxr-xr-x  1 bennybobw bennybobw  3978 2008-05-17 13:03 .htaccess
drwxr-xr-x  3 bennybobw bennybobw  4096 2008-05-17 13:03 includes
-rwxr-xr-x  1 bennybobw bennybobw   908 2008-05-17 13:03 index.php
-rwxr-xr-x  1 bennybobw bennybobw  1475 2008-05-17 13:03 INSTALL.mysql.txt
-rwxr-xr-x  1 bennybobw bennybobw  1101 2008-05-17 13:03 INSTALL.pgsql.txt
-rwxr-xr-x  1 bennybobw bennybobw 22895 2008-05-17 13:03 install.php
-rwxr-xr-x  1 bennybobw bennybobw  9485 2008-05-17 13:03 INSTALL.txt
-rwxr-xr-x  1 bennybobw bennybobw 18406 2008-05-17 13:03 LICENSE.txt
-rwxr-xr-x  1 bennybobw bennybobw  1856 2008-05-17 13:03 MAINTAINERS.txt
drwxr-xr-x  4 bennybobw bennybobw  4096 2008-05-17 13:03 misc
drwxr-xr-x 32 bennybobw bennybobw  4096 2008-05-17 13:03 modules
drwxr-xr-x  4 bennybobw bennybobw  4096 2008-05-17 13:03 profiles
-rwxr-xr-x  1 bennybobw bennybobw  1746 2008-05-17 13:03 robots.txt
drwxr-xr-x  3 bennybobw bennybobw  4096 2008-05-17 13:03 scripts
drwxr-xr-x  5 bennybobw bennybobw  4096 2008-05-17 13:03 sites
drwxr-xr-x  6 bennybobw bennybobw  4096 2008-05-17 13:04 .svn
drwxr-xr-x  8 bennybobw bennybobw  4096 2008-05-17 13:03 themes
-rwxr-xr-x  1 bennybobw bennybobw 31341 2008-05-17 13:03 update.php
-rwxr-xr-x  1 bennybobw bennybobw  3020 2008-05-17 13:03 UPGRADE.txt
-rwxr-xr-x  1 bennybobw bennybobw   366 2008-05-17 13:03 xmlrpc.php

```

Thanks for your help.

---

### Post by bennybobw on 2008-05-18
I purged and removed Apache2 and php5 and re-installed, but I'm still getting the same error. I had virtual hosts working fine on Feisty and previous. Now I can't seem to get it to work.

Any ideas??

---

### Post by spiderbatdad on 2008-05-18
I believe AllowOverride All causes apache to look for an .htaccess file in the directory...usually I put this in httpd.conf as well. Change to AllowOverride None

---

### Post by bennybobw on 2008-05-18
I know that AllowOverride All makes Apache look for an .htaccess file. I have an .htaccess file in the DocRoot, /home/bennybobw/www/franksmith/drupal. But why is it looking in /home/bennybobw/www instead of /home/bennybobw/www/franksmith/drupal? That's what the error message seems to be indicating.

---

### Post by spiderbatdad on 2008-05-18
ah. I apologise for not paying closer attention to your post. One possible problem is that the directory does not end with a forward slash:
```
<Directory /home/bennybobw/www/franksmith/drupal>
```should look like:```
<Directory /home/bennybobw/www/franksmith/drupal/>
```

Is there anything in httpd.conf regarding directives for .htaccess?

---

### Post by bennybobw on 2008-05-18
Yeah, I tried it with and withouth the slashes. No dice. This is the version without the slashes. I don't see anything in my apache2.conf about .htaccess (only defining it as the config file, but no other rules) and my httpd.conf is empty.
It must be something incredibly simple that I'm missing. I could have sworn I had almost exactly the same thing set up on my last system, but I didn't copy the config files over.

---

### Post by spiderbatdad on 2008-05-19
Just had a thought. Is the .htpasswd file readable? That is, does it have correct permissions? And accessible to .htaccess by being in the /home directory.

Document Root doesn't look right either, I thought it should look like:
```
DocumentRoot /home/bennybobw/www/franksmith/drupal/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
```Then your first directory would begin under that:
        <Directory /home/bennybobw/www/franksmith/drupal/>
        Options None
		AllowOverride All
		Order allow,deny
		allow from all
	</Directory>

In httpd.comf:
ServerName localhost
ServerName <your dns or public ip here>
<Directory /home/bennybobw/www/franksmith/drupal>
AllowOverride All
</Directory>

<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
</Files>

Here is an example of mine, though I have disabled .htaccess, as I got tired of requiring authentication. The ht.access files are still in all my directories, I would just change AllowOverride (in each directory) and they work. Also they are renamed to .htsomethingelse and the filename specification in apache2.conf is changed to match.

my virtual host:
```
NameVirtualHost *
<VirtualHost *>
	ServerAdmin admin@<my dns>
	
	DocumentRoot /home/spiderbatdad/public_docs/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/spiderbatdad/public_docs/>
		Options None
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>
        <Directory /home/spiderbatdad/public_docs/Sheetmusic/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>
         <Directory /home/spiderbatdad/public_docs/Music/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

```

My httpd.conf:
```
ServerName localhost
ServerName <my dns>
<Directory /home/spiderbatdad/public_docs/>
AllowOverride None <This gets changed to ALL for htaccess>
</Directory>

<Files ~ "^\.ht">   (copied here from apache2.conf)
    Order allow,deny
    Deny from all
</Files>

```

---

### Post by bennybobw on 2008-05-19
Spiderbatdad thanks for your response. I don't have a .htpasswd file, since I'm not actually restricting access to certain users, just rewrite rules, etc. 

The .htaccess file rule [<Files ~ "^\.ht">] you have below is in my apache2.conf by default. 

I also tried adding the / to my site config, but maybe I'll give it another shot. Since that's an absolute path though, isn't that just blocking access to the actual root on the server? Anyway I'll try a couple of things when I get home from work.

---

### Post by bennybobw on 2008-05-21
Still getting the same error with this: 
```

<VirtualHost *>
	ServerAdmin webmaster@localhost
	ServerName franksmith
	DocumentRoot /home/bennybobw/www/franksmith/drupal/
	<Directory />	
		AllowOverride All
		Options +ExecCGI FollowSymLinks MultiViews
		Order allow,deny
		Allow from all
	</Directory>	
	<Directory "/home/bennybobw/www">
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory "home/bennybobw/www/franksmith/drupal/">
		AllowOverride All
		Options +ExecCGI FollowSymLinks MultiViews
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/franksmith-error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/franksmith-access.log combined
	ServerSignature On
</VirtualHost>


```

What am I doing wrong?
Thanks for your help

---

### Post by bennybobw on 2008-05-21
If I change the line Allow Override All to Allow Override None under the / directory, I still get the same error.

---

### Post by spiderbatdad on 2008-05-21
I would set it up like so:

```
<VirtualHost *>
	ServerAdmin webmaster@localhost
	ServerName franksmith
	DocumentRoot /home/bennybobw/www/
	<Directory />	
		AllowOverride All
		Options None
		Order allow,deny
		Allow from all
	</Directory>	
	<Directory /home/bennybobw/www/franksmith/drupal/>
		Options FollowSymLinks
		AllowOverride All
	</Directory>
	<Directory "home/bennybobw/www/franksmith/drupal/">
		AllowOverride All
		Options +ExecCGI FollowSymLinks MultiViews
		Order allow,deny
		Allow from all
	</Directory>

```
Of course you have to have the .htaccess in each directory using AllowOverride All. In the example above, it is assumed the DocRoot has an index.html and an .htaccess file.

Additionally, I found I had to include the directive in httpd.conf

So httpd.conf gets set up like:
```
ServerName localhost
ServerName franksmith (though this should actually be a dns or public ip)
<Directory /home/bennybobw/www/>
AllowOverride All
</Directory>

<Files ~ "^\.ht">
Order allow,deny
Deny from all
</Files>

```

Again, it is assumed /home/bennybw/www has an index.html and an .htaccess file.
I know you have ^\.ht directive in apache2.conf.

---

### Post by bennybobw on 2008-05-21
Thanks for your reply spiderbatdad.

I think this is getting way too complicated. The examples on  [URL="http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/"]
ubuntu-tutorials.com[/URL] or the [apache2 virtualhost documentation]("http://httpd.apache.org/docs/2.2/vhosts/examples.html") or [here on this very forum ]("http://ubuntuforums.org/showthread.php?t=800146&highlight=virtualhost")are not this complex.

I've had this set up on Gutsy, Feisty and Edgy, so I know it works. 

Let's go back to the original problem. I want to set up a bunch of virtual hosts inside the dir /home/bennybobw/www/
e.g. 
/home/bennbybw/www/mysite1
/home/bennybobw/www/mysite2

where /etc/hosts reads
127.0.0.1 localhost mysite1 mysite2

I **do not want /home/bennybobw/www accessible or as a DocumentRoot and I don't think I need to put anything about it in the site file**. The DocumentRoot for each virtual host should be in /home/bennybobw/www/sitename, which is where Apache2 should be looking for an .htaccess file.

Here's the only things I'm thinking I need to include in my site file:
```

<VirtualHost *>
        ServerName franksmith
        ServerAlias *.franksmith
        DocumentRoot /home/bennybobw/www/franksmith/drupal
        <Directory /home/bennybobw/www/franksmith/drupal>
            AllowOverride All
	    Options +ExecCGI FollowSymLinks MultiViews
	    Order allow,deny
	    Allow from all
        </Directory>  
</VirtualHost>

```

It's looks like [I'm not the only one having this problem]("http://ubuntuforums.org/showthread.php?p=5012507#post5012507"), and I've asked him to post his errors over here. Maybe all of us together can solve this.

I've never put anything in httpd.conf before, but maybe Hardy has a new configuration that I need to? There shouldn't be any need to post duplicate directives though...

---

### Post by spiderbatdad on 2008-05-21
what you have posted above should work fine. However, put this in httpd.conf, also, and it will work:```
ServerName localhost
ServerName <your_ip>
<Directory /home/bennybobw/www/franksmith/drupal/>
AllowOverride All
</Directory>
```
Restart the server of course.

---

### Post by bennybobw on 2008-05-22
Ok...
So I copied my www file from ext3 to FAT16 and then back to ext3. The permissions on all the files inside www were preserved but www itself was set so only the owner could read it....

The problem wasn't in my conf but the permissions on www ....Ahhhhh....](*,)

Thanks for your help SpiderBatDad.

p.s. in the end, I didn't need that line in httpd.conf, just the virtualhost declaration I posted last.

---

### Post by madhusudancs on 2008-06-01
Hi,
   You people had asked me to post here about my problem in the post I had done. So this is how my sites-available/drupal6 file looks.

<VirtualHost *>
	ServerAdmin [email]madhusudancs@gmail.com[/email]
	ServerName drupal6
        ServerAlias [www.locald6.com](www.locald6.com)

	DocumentRoot /home/madhu/mywebdevelopment/drupal6.0/
	<Directory />
		Options FollowSymLinks
		AllowOverride All
	</Directory>
	<Directory /home/madhu/mywebdevelopment/drupal6.0/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
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

and as you said have enabled the site and have added 127.0.0.3 drupal6
to the host. But when I give drupal6 in browser it gives the following error, and have added same configurations as you have indicated to httpd.conf. 

403 Forbidden

You don’t have permission to access / on this server.

My apache error.log has the following entries

Mon Jun 02 09:18:50 2008] [crit] [client 127.0.0.3] (13)Permission denied: /home/madhu/mywebdevelopment/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable

Note that even though my DocRoot points to one directory below i. /home/…/mywebdevelopment/drupal6.0 it is looking for .htaccess in mywebdevelopment. So just to test I put my .htaccess copy there also. Still it shows the same error. Permission on all the files and directories is set to 777.

Please help me. Thanks a lot

---

### Post by bennybobw on 2008-06-02
Make sure the permissions on /home/madhu/mywebdevelopment are 755
That's what was causing the problem with mine.

---

### Post by madhusudancs on 2008-06-02
Hey thanks a lot, chmod 755 on mywebdevelopment is working. But I had kept it as 777. Why not 777 and why only 755? Any idea?

---

### Post by kwinto on 2012-01-26
For any google strangers here, **/home/%username% should be executable by apache**, so chmod a+x /home/%username%

---

### Post by lisati on 2012-01-26
And with that useful tip, this thread can go back to sleep.

---

