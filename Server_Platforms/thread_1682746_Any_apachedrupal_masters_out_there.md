---
title: "Any apache/drupal masters out there?"
date: 2011-02-06
forum: Server Platforms
---

### Post by bazz on 2011-02-06
I'm not to sure this is the place I should post this, but couldn't find any place for it to fit.

So here is the deal..I am running 10.10 with the standard LAMP setup. I am running a drupal 7 site no problems. What I need to do is run a multi site sub directory. (domain.com/newsite). So far the best I can do is get a directory index of the second site (domain.com/newsite), but cant run the installer. (I did the symbolic link to the doc root of the drupal install.)If I type in the url domain.com/newsite/install.php I get not found. 

I placed an index.html test page and it renders fine. I think I'm close but just not there yet.

Any ideas from anyone? I can get Sobdomains to work fine on a test mache, but sadly I need the domain/site to work due to lack of DNS support at the moment.

I tried to get some info from the drupal forum, but everything always points to subdomin setups. I also posted over there, but it seems like the forums have very little support and are a bit on the slow side.

Any ideas?
Below is a copy of my /etc/apache2/sites-available/default
Please help if you can.
Thanks

<VirtualHost *:80>
	ServerAdmin webmaster@localhost
DocumentRoot /var/www/drupal
	<Directory />
		Options +Indexes FollowSymLinks 
		AllowOverride all
                Order allow,deny
                allow from all
	</Directory>
<Directory /var/www/drupal/>
		Options Indexes FollowSymLinks MultiViews 
		AllowOverride all
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

	ErrorLog ${APACHE_LOG_DIR}/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog ${APACHE_LOG_DIR}/access.log combined

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

### Post by bazz on 2011-02-06
nothing here either eh? Not one little guess?

---

### Post by bazz on 2011-02-07
Can anyone suggest a forum where I could post this where I might be able to get some help?

---

### Post by bazz on 2011-02-08
Why am I not surprised....sigh

---

### Post by bazz on 2011-02-11
This is a very sad day for Drupal and Apache :(

---

### Post by uRock on 2011-02-11
Bump for move to Server Platforms.

Regards,
uRock

---

### Post by Thirtysixway on 2011-02-11
What does your /sites/ folder look like for drupal?

You need to have a seperate folder for each /site such as

/sites/default/
/sites/www.mysite.com/
/sites/www.mysite.com.newsite1/
/sites/www.mysite.com.newsite2/

Just add the .foldername to the end of your site url, if that makes sense. Shouldn't have to do any special apache configuration or sym links.

As an FYI, all of this information is in the INSTALL.txt file that comes with Drupal. Read through it and if you have any questions, then post. The documentation helps.

---

### Post by bazz on 2011-02-13
Yeah I gave all that a go. I'm using IP's I wonder if that could be a problem? But even if I use a hosts file I still cant get it to work. D6 everything works fine. D7 I can only get sub.domains.com to work and not domain.com/newsite

My set up is 
/sites/default/
/sites/mysite.com/
/sites/mysite.com.newsite

Well I just gave your advice a go with the url being sitename.com.newsite
It worked...all docs I have read says sitename.com/newsite. The only downer with a url like that is I need dns. Is there a way to do it with a url of sitename.com/newsite? 
There here claims its possible...
[http://drupal.org/getting-started/6/install/multi-site](http://drupal.org/getting-started/6/install/multi-site)
THANKS!!

---

### Post by earlf on 2011-02-17
Hey Bazz,

I can't solve your problem, but I hear your frustrations/have a similar problem. I tried this guide:[http://drupal.org/node/823990](http://drupal.org/node/823990).
so far, I have one subsite of localhost working but my other one isn't. its completely blank.
alas. Good luck on your configuration!

---

### Post by bazz on 2011-03-16
I did finally get it to work. I was creating the link wrong, and a few other things missed.
This is the post that got it to work for me.
[http://drupal.org/node/1032286#comment-4110298](http://drupal.org/node/1032286#comment-4110298)

---

