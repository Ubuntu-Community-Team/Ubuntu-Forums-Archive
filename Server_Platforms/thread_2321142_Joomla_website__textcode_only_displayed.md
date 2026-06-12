---
title: "Joomla website:  text/code only displayed"
date: 2016-04-20
forum: Server Platforms
---

### Post by ivan125 on 2016-04-20
Hello, I'm a beginner with Ubuntu. On my Cloud Server i installed Ubuntu 14.04, php5,lamp... installed Joomla website and everything was OK until i reboot the VPS. Now my website looks like this
[www.deltasoft.solutions]("http://www.deltasoft.solutions")

Only plain text. I don't know if it has something with privileges to execute .php? I tried a ton of things but nothing worked. Please help

SOLVED! 

[COLOR=#444444][FONT=Open Sans]For starters we need to enable this module using following command:[/FONT][/COLOR][COLOR=#110000][FONT=Open Sans][TABLE="width: 1"]
[TR]
[TD="class: code"][COLOR=#C20CB9]**sudo**[/COLOR] a2enmod userdir[/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]
[COLOR=#444444][FONT=Open Sans]Now we will configure Apache module userdir by editing userdir.conf file like this:[/FONT][/COLOR]
[COLOR=#110000][FONT=Open Sans][TABLE="width: 1"]
[TR]
[TD="class: code"][COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**nano**[/COLOR] [COLOR=#000000]**/**[/COLOR]etc[COLOR=#000000]**/**[/COLOR]apache2[COLOR=#000000]**/**[/COLOR]mods-enabled[COLOR=#000000]**/**[/COLOR]userdir.conf[/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]
[COLOR=#444444][FONT=Open Sans]Next you should replace the contents of that configuration file with the following code:[/FONT][/COLOR]
[COLOR=#110000][FONT=Open Sans][TABLE="width: 1"]
[TR]
[TD="class: code"]<[COLOR=#000000]**IfModule**[/COLOR] mod_userdir.c>
        [COLOR=#00007F]UserDir[/COLOR] public_html
        [COLOR=#00007F]UserDir[/COLOR] disabled root
 
        <[COLOR=#000000]**Directory**[/COLOR] /home/*/public_html>
		[COLOR=#00007F]AllowOverride[/COLOR] [COLOR=#0000FF]All[/COLOR]
		[COLOR=#00007F]Options[/COLOR] MultiViews [COLOR=#0000FF]Indexes[/COLOR] SymLinksIfOwnerMatch
		<[COLOR=#000000]**Limit**[/COLOR] GET POST OPTIONS>
			[COLOR=#ADADAD]*# Apache <= 2.2:*[/COLOR]
		        [COLOR=#00007F]Order[/COLOR] [COLOR=#00007F]allow[/COLOR],[COLOR=#00007F]deny[/COLOR]
		        [COLOR=#00007F]Allow[/COLOR] from [COLOR=#0000FF]all[/COLOR]
 
		        [COLOR=#ADADAD]*# Apache >= 2.4:*[/COLOR]
		        [COLOR=#ADADAD]*#Require all granted*[/COLOR]
		</[COLOR=#000000]**Limit**[/COLOR]>
		<[COLOR=#000000]**LimitExcept**[/COLOR] GET POST OPTIONS>
			[COLOR=#ADADAD]*# Apache <= 2.2:*[/COLOR]
		        [COLOR=#00007F]Order[/COLOR] [COLOR=#00007F]deny[/COLOR],[COLOR=#00007F]allow[/COLOR]
		        [COLOR=#00007F]Deny[/COLOR] from [COLOR=#0000FF]all[/COLOR]
 
			[COLOR=#ADADAD]*# Apache >= 2.4:*[/COLOR]
			[COLOR=#ADADAD]*#Require all denied*[/COLOR]
		</[COLOR=#000000]**LimitExcept**[/COLOR]>
        </[COLOR=#000000]**Directory**[/COLOR]>
</[COLOR=#000000]**IfModule**[/COLOR]>[/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]
[COLOR=#444444][FONT=Open Sans]With this setup Apache web server would serve HTML files from public_html directory of every user on your pc. This HTML files would be accessible using the [http://example.com/~user/](http://example.com/~user/) syntax. Serving PHP files from user's public_html directoriy is disabled by default for security reasons. If you want to enable PHP processing when using userdir this is what you need to do. First you edit following Apache configuration file in this way:[/FONT][/COLOR]
[COLOR=#110000][FONT=Open Sans][TABLE="width: 1"]
[TR]
[TD="class: code"][COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**nano**[/COLOR] [COLOR=#000000]**/**[/COLOR]etc[COLOR=#000000]**/**[/COLOR]apache2[COLOR=#000000]**/**[/COLOR]mods-available[COLOR=#000000]**/**[/COLOR]php5.conf[/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]
[COLOR=#444444][FONT=Open Sans]Now you need to comment out a few lines from <IfModule mod_userdir.c> to the next </IfModule>so you get something like this:[/FONT][/COLOR]
[COLOR=#110000][FONT=Open Sans][TABLE="width: 1"]
[TR]
[TD="class: code"]<[COLOR=#000000]**IfModule**[/COLOR] mod_php5.c>
    <[COLOR=#000000]**FilesMatch**[/COLOR] [COLOR=#7F007F]"[COLOR=#000099]**\.**[/COLOR]ph(p3?|tml)$"[/COLOR]>
	[COLOR=#00007F]SetHandler[/COLOR] application/x-httpd-php
    </[COLOR=#000000]**FilesMatch**[/COLOR]>
    <[COLOR=#000000]**FilesMatch**[/COLOR] [COLOR=#7F007F]"[COLOR=#000099]**\.**[/COLOR]phps$"[/COLOR]>
	[COLOR=#00007F]SetHandler[/COLOR] application/x-httpd-php-source
    </[COLOR=#000000]**FilesMatch**[/COLOR]>
    [COLOR=#ADADAD]*# To re-enable php in user directories comment the following lines*[/COLOR]
    [COLOR=#ADADAD]*# (from <IfModule ...> to </IfModule>.) Do NOT set it to On as it*[/COLOR]
    [COLOR=#ADADAD]*# prevents .htaccess files from disabling it.*[/COLOR]
    [COLOR=#ADADAD]*#<IfModule mod_userdir.c>*[/COLOR]
    [COLOR=#ADADAD]*#    <Directory /home/*/public_html>*[/COLOR]
    [COLOR=#ADADAD]*#        php_admin_value engine Off*[/COLOR]
    [COLOR=#ADADAD]*#    </Directory>*[/COLOR]
    [COLOR=#ADADAD]*#</IfModule>*[/COLOR]
</[COLOR=#000000]**IfModule**[/COLOR]>[/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]
[COLOR=#444444][FONT=Open Sans]Last thing you just restart Apache web server and create public_html directory inside your home directory like this:[/FONT][/COLOR]
[COLOR=#110000][FONT=Open Sans][TABLE="width: 1"]
[TR]
[TD="class: code"][COLOR=#C20CB9]**sudo**[/COLOR] service apache2 restart
[COLOR=#C20CB9]**mkdir**[/COLOR] [COLOR=#000000]**/**[/COLOR]home[COLOR=#000000]**/**[/COLOR][COLOR=#007800]$USER[/COLOR][COLOR=#000000]**/**[/COLOR]public_html[/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]

---

### Post by QIII on 2016-04-20
*Moved to **Server Platforms***

Not exactly a beginner problem.  ;)

---

