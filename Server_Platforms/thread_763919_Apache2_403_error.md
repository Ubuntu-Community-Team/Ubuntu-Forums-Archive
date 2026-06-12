---
title: "Apache2 403 error"
date: 2008-04-23
forum: Server Platforms
---

### Post by rideout83 on 2008-04-23
Problem:
I am getting a 403 error when trying to view pages I created with dreamweaver. I can view pages build with open office and the default apache page. Though [http://localhost](http://localhost) buti if i change the index page to my dreamweaver page then I get the 403 error.

History:
So I navigated to my /VAR/WWW and click on my index.html created from dreamweaver it tell's me its an executable. Then I click display and the page loads. But if I click on my index.htm which I created with open office it displays the page no message.  

Any help would be great.

---

### Post by Oldsoldier2003 on 2008-04-23
lets see your /etc/apache2/sites-available/default and the url/path to the problem pages. it could be something really simple. But its hard to tell right off since 403 is a blanket error message

---

### Post by rideout83 on 2008-04-23
I have 2 index page in the /var/www one is the index.htm which works and the other is index.html which errors.  I type [http://localhost/index.htm](http://localhost/index.htm) to have the one that works then [http://localhost/index.html](http://localhost/index.html) to get my error. If I swapped the extensions on both index files. Then one built with open office will work.   

I had to add index.htm to dir.conf to get that to work.

I think my problem could be when I manualy launch my index page created by dreamweaver from the computer browser it thinks its an executable.

Sites-available -default

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

### Post by rideout83 on 2008-05-22
Just in case this helps anyone. I found what was happing. I had to use the root file browser and set the permissions of the site folder of "others" to Access files and Read Only. After I did that I was able to view the site I created with dreamweaver.

---

### Post by gmlga on 2010-03-20
Thank you for posting your solution. That worked for me.

---

### Post by WTBCompPro on 2011-02-09
I can't believe it was that easy thank you I had seriously almost given up.

---

### Post by mapBaker on 2013-02-01
All,

I'm getting a '403 forbidden' error with this message:

**Forbidden**

 You don't have permission to access / on this server.




This thread seems to have some leads, but I can't figure it out...


Any more ideas / thoughts?


Thanks!


-m

---

