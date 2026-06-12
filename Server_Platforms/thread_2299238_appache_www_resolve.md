---
title: "appache www resolve"
date: 2015-10-16
forum: Server Platforms
---

### Post by Joe67 on 2015-10-16
Hi guys, before i start.. Ill warn you, my knowlege is little..


I have a unbuntu 12.04 lts vps server with a few websites hosted via virtual hosts.. I read it isnt a good idea to place a .htaccess file in the root to help fix www resolve problem i have...

My question is, can i add the 

```
RewriteEngine on
RewriteCond %{HTTP_HOST} ^www\.jamieskitchenservices\.com$ [NC]
RewriteRule ^(.*)$ http://jamieskitchenservices.co.uk/$1 [R=301,L]

```

to the sites-available/enabled file,any helps appreciated. Thanks

---

### Post by sandyd on 2015-10-16
Moved to *Server Platforms*
=====================
Place the rewrite in the appropraite<Directory> section of your config.

i.e.
```

<Directory /var/www>
    <IfModule rewrite_module>
    RewriteEngine On
    RewriteBase /
    RewriteCond %{HTTP_HOST} ^www\.jamieskitchenservices\.com$ [NC]
    RewriteRule ^(.*)$ http://jamieskitchenservices.co.uk/$1 [R=301,L]
    </IfModule>
</Directory>

```

If you post your virtualhost config, I can show you exactly where to add it.

---

### Post by Joe67 on 2015-10-16
thanks very much :D

```
<VirtualHost 31.>       ServerAdmin ....@jamieskitchenservices.co.uk
	ServerName jamieskitchenservices.co.uk
       ServerAlias www.jamieskitchenservices.co.uk
DocumentRoot /home/kitchen/public_html/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/kitchen/public_html/>
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



```

---

### Post by sandyd on 2015-10-16
Give this a try

```
<VirtualHost 31.>       ServerAdmin ....@jamieskitchenservices.co.uk
	ServerName jamieskitchenservices.co.uk
       ServerAlias www.jamieskitchenservices.co.uk
DocumentRoot /home/kitchen/public_html/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/kitchen/public_html/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
                <IfModule rewrite_module>
                RewriteEngine On
                RewriteBase /
                RewriteCond %{HTTP_HOST} ^www\.jamieskitchenservices\.com$ [NC]
                RewriteRule ^(.*)$ http://jamieskitchenservices.co.uk/$1 [R=301,L]
                </IfModule>
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
```

---

### Post by Joe67 on 2015-10-17
not working, the code above wasnt 100% as i wasnt sure if it would risk website etc being posted on public forum

heres the edit:

```
<VirtualHost [ip removed]:80>       ServerAdmin [email removed]
	ServerName jamieskitchenservices.co.uk
       ServerAlias www.jamieskitchenservices.co.uk
DocumentRoot /home/js/public_html/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/js/public_html/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
        <IfModule rewrite_module>
        RewriteEngine On
        RewriteBase /
        RewriteCond %{HTTP_HOST} ^www\.jamieskitchenservices\.co.uk$ [NC]
        RewriteRule ^(.*)$ http://jamieskitchenservices.co.uk/$1 [R=301,L]
        </IfModule>				
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



```

---

### Post by sandyd on 2015-10-18
Finger slipped, should be
```

<VirtualHost [removed ip address]:80>
        ServerAdmin [removed email]
        ServerName jamieskitchenservices.co.uk
        ServerAlias www.jamieskitchenservices.co.uk
        DocumentRoot /home/js/public_html/
        <IfModule mod_rewrite.c>
        RewriteEngine On
        RewriteCond %{HTTP_HOST} ^www.jamieskitchenservices.co.uk$ [NC]
        RewriteRule ^(.*)$ http://jamieskitchenservices.co.uk/$1 [R=301,L]
        </IfModule>
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /home/js/public_html/>
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

```

Please replace the ip and the email - removed them for security reasons.

---

### Post by Joe67 on 2015-10-20
the above doesnt load or find the page, or redirect..


do you mean remove server alias and make a new virtual host file?

sandy, just to be sure

remove server alias from the current virtual host then make a new one with only

```
[COLOR=#000000][FONT=Ubuntu Mono]<VirtualHost x.x.x.x:80>[/FONT][/COLOR]  ServerName www.jamieskitchenservices.co.uk
  Redirect 301 / http://jamieskitchenservices.co.uk/ [COLOR=#000000][FONT=Ubuntu Mono]</VirtualHost>[/FONT][/COLOR]
```

sandy? :(

---

### Post by sandyd on 2015-10-27
Sorry about the wait - seems I forgot to check back on the thread.

I accidentally posted configuration edits for Apache 2.4.x instead of Apache 2.2.x - should be fixed now.

---

### Post by Joe67 on 2015-10-28
no problem and thanks

it might be me.... to be sure, how do i know www resolve is working/not working?

---

### Post by sandyd on 2015-10-28
visit www -> it should redirect to non-www.

---

### Post by Joe67 on 2015-10-28
its not working, edit is still live, can test yourself..

---

### Post by sandyd on 2015-10-28
This is odd, it is working here.

Are there any other virtual hosts files other than the current one?
If you remove the lines that start with
```

<IfModule mod_rewrite.c>

```
and ```
</IfModule>
```
does it work?

---

### Post by Joe67 on 2015-10-28
Yes, theres five in total.

this is the current file, still not working

```
<VirtualHost >        ServerAdmin 
        ServerName jamieskitchenservices.co.uk
        ServerAlias www.jamieskitchenservices.co.uk
        DocumentRoot /home/js/public_html/
        RewriteEngine On
        RewriteCond %{HTTP_HOST} ^www.jamieskitchenservices.co.uk$ [NC]
        RewriteRule ^(.*)$ http://jamieskitchenservices.co.uk/$1 [R=301,L]
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /home/js/public_html/>
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
```

---

### Post by sandyd on 2015-10-28
I can't reproduce that here.

Are there any errors in the error logs (/var/log/apache2/error.log), or any errors when restarting apache2?

---

### Post by Joe67 on 2015-10-29
when restarting appache, get the error:

> 

root@:~# service apache2 restart
Syntax error on line 6 of /etc/apache2/sites-enabled/jamieskitchenservices.co.uk                                :
Invalid command 'RewriteEngine', perhaps misspelled or defined by a module not i                                ncluded in the server configuration
Action 'configtest' failed.
The Apache error log may have more information.
   ...fail!




---

### Post by sandyd on 2015-10-29
You haven't enabled rewrite module.
```

sudo a2enmod rewrite && sudo apache2 restart
```

---

### Post by Joe67 on 2015-10-30
great, thanks sandy.. :D

to use www. it would be:?

```
        RewriteEngine on                  RewriteCond %{HTTP_HOST} !^www\.jamieskitchenservices\.co.uk$ [NC]
                  RewriteRule ^(.*)$ http://www.jamieskitchenservices.co.uk/$1 [R=301,L]
```

i gave the above a try, it is working but i get two // at the end of the url.. any help would be appreciated ;)

---

### Post by darkod on 2016-02-02
Have you tried removing the final / in the RewriteRule? Your RewriteCond ends only in .co.uk and you are rewriting that with .co.uk/ which creates additional /. That's why rewriting might show up with two //.

No?

When trying rewrite/replace be very EXACT with the characters. If you want to rewrite [www.something.co.uk](www.something.co.uk) into something.co.uk put it exactly like that. Not as something.co.uk/

---

### Post by Joe67 on 2016-02-03
ive tryed, i did again to be sure.. it doesnt make a difference. thanks

---

### Post by darkod on 2016-02-03
Can you give us an example specifying:
1. Which URL you are putting into the browser?
2. Which URL does it rewrite to?
3. Which URL you want it to rewrite to?

It might help having it written to compare. Also please re-post the current rewrite part of the site .conf file.

---

### Post by Joe67 on 2016-02-03
1.jamieskitchenservices.co.uk
2.[http://www.jamieskitchenservices.co.uk//](http://www.jamieskitchenservices.co.uk//)
3.[http://www.jamieskitchenservices.co.uk](http://www.jamieskitchenservices.co.uk)

        RewriteEngine on
        RewriteCond %{HTTP_HOST} !^www\.jamieskitchenservices\.co.uk$ [NC]
        RewriteRule ^(.*)$ http://www.jamieskitchenservices.co.uk/$1 [R=301,L]

---

### Post by darkod on 2016-02-03
Are you trying to simply add the www when it is not entered, or something more?

Because if I understand that RewriteCond correctly, every URL different from [www.jamieskitchenservices.co.uk](www.jamieskitchenservices.co.uk) will get rewritten as [www.jamieskitchenservices.co.uk](www.jamieskitchenservices.co.uk). This includes for example if you have products page, and someone enters jamieskitchenservices.co.uk/products it will be rewritten as [www.jamieskitchenservices.co.uk](www.jamieskitchenservices.co.uk), not as [www.jamieskitchesservices.co.uk/products](www.jamieskitchesservices.co.uk/products).

---

### Post by darkod on 2016-02-03
I haven't done anything like this on apache before, but if the only thing you want is force-rewrite the URL with www at the front, try something like this.

The following code does not even need or use mod_rewrite module, so comment out your Rewrite* related commands in the .conf file and try something like simple If:
```
<If "%{HTTP_HOST} != 'www.jamieskitchenservices.co.uk'">
      Redirect "/" "http://www.jamieskitchenservices.co.uk/"
</If>
```

According to the apache website this is actually the preferred way to handle adding www in the URL. Source: [https://httpd.apache.org/docs/2.4/rewrite/remapping.html](https://httpd.apache.org/docs/2.4/rewrite/remapping.html)

Of course you will have to restart apache after modifying the site .conf file.

---

### Post by Joe67 on 2016-02-06
thanks for your help, heres what am getting:

Invalid command '<If', perhaps misspelled or defined by a module not included in the server configuration
Action 'configtest' failed.

---

### Post by darkod on 2016-02-06
If was introduced since apache 2.3. If you are running an older version it is not available.

Let me search more...

---

### Post by darkod on 2016-02-06
I don't know if there is a typo somewhere, but I founf RewriteCond little different from yours posted in post #21. The RewriteRule is the same, so you can use the one from #21.

Try with this RewriteCond:
```
RewriteCond %{HTTP_HOST} ^jamieskitchenservices\.co\.uk [NC]
```

Only that. Compared to your current RewriteCond it does not have the ! in front of the domain and the $ at the end. As I said, I don't know if it's a typo but this is the example I found for adding www when the visitor didn't enter it.

PS. Also looking at your post #21 I now realized that you didn't use \. for the .uk in the RewriteCond. In such cases the \ is called something like escape character, to show that the following character after it is not part of the command, but it is part of the condition. So, all the dots you have "escape" with \.

And you don't need the www. part in the Cond because that is actually what you are trying to do. If the domain is without www you want to add it. So the Cond is to apply the Rule on URLs that have no www, hence the www should not be in the Cond.

Give the above a shot and lets see.

---

### Post by Joe67 on 2016-02-11
i really appreciate your help mate, ive done the above edit. still have the same problem :(

---

