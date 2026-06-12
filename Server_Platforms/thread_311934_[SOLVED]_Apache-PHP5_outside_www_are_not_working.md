---
title: "[SOLVED] Apache-PHP5 outside www are not working"
date: 2006-12-03
forum: Server Platforms
---

### Post by gregor171 on 2006-12-03
Hi
I've been googling to solve this issue with no luck. I have installed Apache2 & PHP5 module. Everything, including PHP scripts, is working well in **/var/www** directory.

I've try to map pages outside www and also that works untill it comes to php scripts.:confused:  For now I'm not intending to map domains to those directories for testing new applications and I'm trying to tell Apache to run scripts in "alias" file with (so far):

[COLOR="Blue"]Alias /testweb /web1/test/
<Directory /testweb /web1/test/>
  	Options Indexes FollowSymLinks
	DirectoryIndex index.html index.htm index.php
	AddHandler php-script .php
	AddHandler php5-script .php5 .php 
	AddType application/x-httpd-php .php
	<Files *.php>
		SetOutputFilter PHP
		SetInputFilter PHP
	</Files>
  	AllowOverride All
  	Order allow,deny
  	Allow from all
</Directory> [/COLOR]

But still it wants to download scripts, similar as in post:
[http://ubuntuforums.org/showthread.php?t=307395&highlight=apache+php](http://ubuntuforums.org/showthread.php?t=307395&highlight=apache+php)
But this was not my problem. My scripts ase working in [http://localhost/test.php](http://localhost/test.php)
but NOT in
[http://localhost/testweb/test.php](http://localhost/testweb/test.php)
Can anyone help me with this.
Gregor

---

### Post by gregor171 on 2006-12-04
Hi
I have an idea, that I'll try later. I havent configure **testweb** in [COLOR="black"]**sites-available**[/COLOR] section. Could this be a solution. Can I just copy **default** and change some settings inside?

---

### Post by tturrisi on 2006-12-04
You can't just creat a dir and expect apache to serve www content from it.  You need to config apache to use the dir you created.  The dirs need to be subdirs of /var/www or /home/~/public_html.  Best way to do what you want is to add a user for each domain and serve the pages from their /home/public_html dir.  Access them with localhost/~username or config separate virtual domains for the users.

---

### Post by gregor171 on 2006-12-05
Sorry, but I've been developing aplications in win32, asp.net and I'm used to iis and now I'm moving part of my projects to php/cxx on Ubuntu server with KDE I'm not an Lunux expert ;-(( Since Apache did serve to html files in that dirs it was a logical conclusion that PHP will do as well. I wanted to avoid /home dir to seperate content. I'll mount them there and I hope it will work. Thanks for answering! I'll get back. :p

---

### Post by jpmrblood on 2006-12-05
Have you enable the php5 module?
```
# a2enmod php5
```
I always put my html docs on non standard place. If you want the non standard to be working, I suggest you change the owner as the apache2's default user. For instance:
```

# sudo mkdir /myDoc
# sudo chown www-data:www-data /myDoc
```
And then, you could put the /myDoc like usual (e.g. /etc/apache2/sites-available/default)
```

Alias /testweb /myDoc
<Directory /myDoc>
Options Indexes FollowSymLinks
AllowOverride All
Order allow,deny
Allow from all
</Directory> 
```
Restart the apache:
```
 # /etc/init.d/apache2 restart 
```
Btw, if you want to know what modules available, you could see it by typing:
```
 # a2enmod 
```

EDIT:
Btw, the structure of an apache2 server is
For any site that will runs on apache2 (in another words, directory that will be used as apache's home) is sets on **/etc/apache2/sites-available**. By default, there is a file named **default** that contains default directory to play with. You could start your own configuration there.

---

### Post by gregor171 on 2006-12-05
Thanks guys for answering! The solution was in front of my eyes, but no direct answers I found on the web.  Almost. Have to think out of a box and  now it's working. Since people are watching this thred, I'd like to point the way to happines for this problem. Explination of most of the steps can be found on the web as well.

**1.First instal Apache2 and PHP** with desired modules (xml, gd, mysql etc). Enable PHP either by creating link to 2 files /etc/apache2/mods-available  in mods-available by:

[COLOR="RoyalBlue"]cd /etc/apache2/mods-enabled/

ln -s /etc/apache2/mods-available/php5.load

ln -s /etc/apache2/mods-available/php5.conf[/COLOR]

or simply with (as mentioned in one repyl):

[COLOR="RoyalBlue"]a2enmod php5[/COLOR]

Restart or just reload Apache:
[COLOR="RoyalBlue"]sudo /etc/init.d/apache2 {reload | restart}[/COLOR]

**2. To test that PHP is working**, create test.php on www root:

[COLOR="RoyalBlue"]sudo gedit /var/www/test.php[/COLOR]

and enter code in file:

[COLOR="RoyalBlue"]<?PHP
	echo ("foo!");
?>[/COLOR]

Save and test if everything is working:
[COLOR="RoyalBlue"]http://localhost/test.php[/COLOR]

**3.Alias for Virual host**

Now create alias file (virtual host) by creating file:

[COLOR="Blue"]sudo gedit /etc/apache2/conf.d/alias[/COLOR]
In the alias file insert as many pages as you want.  Insert directive for this web page in alias file:

[COLOR="RoyalBlue"]Alias /testweb /web1/testweb/www/
<Directory /web1/testweb/www>
	Options Indexes FollowSymLinks MultiViews
	AllowOverride All
	Order allow,deny
	Allow from all
</Directory>[/COLOR]

*This will create virual host to a files stored in [COLOR="RoyalBlue"]“/web1/testweb/www”[/COLOR] directory!

**4.**
I was not sure that this step is important, but I did it, since last time it didn't execute any php files.  Now it works even if I delete “testweb” link in  sites-available? You will neeed this file if you are creating virtual named host.

For enabling PHP scripts on that VD (similar procedure is done for cgi and other scripts – in web you can find a lot of help for that) you have to add directive to Apache2 to use “script processor” create :
[COLOR="RoyalBlue"]
cd /etc/apache2/sites-available
sudo cp default testweb
sudo gedit testweb[/COLOR]

And change inside of testweb file, similar as in alias file. Many of directives there are well explined in Apachi web. Create link to this file in sites-enabled dir:
[COLOR="RoyalBlue"]
cd /etc/apache2/sites-enabled
sudo ln -s /etc/apache2/sites-available/testweb[/COLOR]

**5. Named virtual host**
If you want your virtual host to reply to a specific domain name ([www.example1.com](www.example1.com) and [www.example2.com](www.example2.com) ), that is also done in VirtualHost section in site file, that is stored in:
[COLOR="RoyalBlue"]/etc/apache2/sites-available[/COLOR]

**6. Now it's time to restart apache to see a resoult:**
[COLOR="RoyalBlue"]sudo /etc/init.d/apache2 restart[/COLOR]
If everything went well, you are now able to test your new site. If you do not have any files in /web1/testweb/www/ directory, copy  /var/www/test.php  to this location. Test your web by typing (in web browser normaly):
[COLOR="RoyalBlue"]http://localhost/testweb/test.php[/COLOR]

If someone need more detail infos, go to this urls that I find most useful:
[COLOR="DarkRed"]http://ubuntuguide.org/wiki/Ubuntu_Edgy[/COLOR]
[COLOR="DarkRed"]https://help.ubuntu.com/6.10/ubuntu/serverguide/C/httpd.html[/COLOR]
[COLOR="DarkRed"]http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch20_:_The_Apache_Web_Server#Table_20-2_Web_Hosting_Scenario_Summary[/COLOR]
But also server guide in ubuntu home web and Apache web.

---

### Post by jpmrblood on 2006-12-08
> **gregor171 said:**
> 
And change inside of testweb file, similar as in alias file. Many of directives there are well explined in Apachi web. Create link to this file in sites-enabled dir:
[COLOR="RoyalBlue"]
cd /etc/apache2/sites-enabled
sudo ln -s /etc/apache2/sites-available/testweb[/COLOR]


You could done the elegant way: :P
```
a2ensite testweb
``` Btw, it's great that you could sum all it up in a post. :-D

---

### Post by gregor171 on 2006-12-08
hi thx!
I read many posts that say only: thx I found an answer and it's working now.

I have stiil problems with enabling: xml+xslt and gdchatr php functions (they are installed and also I uncommented it in php.ini but only gd is working correct) and also "sl" "iso-8859-2" characters are not working - this I read is a mime functionality (normaly i added charset in apache  config) but I find no entry for "sl" chars in mime configs (they are not to be edited). mime might not be up to date?

I also find apache2 slow on 500mhz, but this i've solved with configuring threds in apache config  (from 5 by default to 3) and not running kde in server mode.

---

