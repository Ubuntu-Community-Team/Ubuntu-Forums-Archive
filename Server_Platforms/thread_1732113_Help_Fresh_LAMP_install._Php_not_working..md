---
title: "Help Fresh LAMP install. Php not working."
date: 2011-04-17
forum: Server Platforms
---

### Post by Sirkyuubi on 2011-04-17
I just installed lamp stack on my my Ubuntu 10.10 Desktop about 2 weeks ago. (wanted to practice web hosting)
 
I spent 3 days getting apache setup. (I knew nothing about it at the time)

Everything installed ok. My main issue is that I can't get php working properly. The only php command that works is <?php phpinfo(); ?> Any other command including echo doesn't work. The page just stays blank.

since I know you guys need info heres what I got and what I've done.

Hardware
- Router: Belkin - Model F5D8236-4 V2
- 8 port switch
- Computer: Old Dell Workstation 3.6ghz p4 socket 775 wired eithernet connection
- OS: Ubuntu Desktop 10.10 with AMP installed
- Modem/ISP: Comcast High Speed Internet with phone service.


What I've done so far
- I have setup the dell workstation on it's own IP and added it to DMZ to (hopefully) lower complications of dealing with NAT.
- With apache2 /etc/apache2/sites-ava*/coolness is used as default and default is my backup.
- Apache2 listen and vhost are set on port 9000 (I heard some isp's block ports so I used a random one)
- The only files I have changed for apache2 are sites-available/coolness (default file) and ports.conf
- /home/coolness/public_html/index.php has been added and leaves a blank for any command other than <?php phpinfo(); ?>.  Anything thats not php does work though.
- Everything in the public_html folder is permission level 755.
- I have ssh'd into another system outside my network and links'd my wan ip. Still blank.

Any help would be greatly appreciated.

---

### Post by wojox on 2011-04-17
Show some of the code your using. If phpinfo() works then php is working. It may be your code.

---

### Post by Sirkyuubi on 2011-04-17
I copied this simple block from the amp book im reading. It gives me a blank page.
Also any block that I copied from anywhere online doesn't work either.

I put this in index.php

<html>
<head>
<title>My First PHP Program</title>
</head>
<body>
<?php
echo &#8220;I&#8217;m a lumberjack.&#8221;;
?>
</body>
</html>

---

### Post by Sirkyuubi on 2011-04-17
Anyone have any ideas? I know someone out there must have an idea to whats happening here.

---

### Post by BkkBonanza on 2011-04-17
You need to narrow down the actual changes you make to figure out what is stopping this from working. If you edit your index.php file and the absolute only change is that phpinfo works and echo ... doesn't then for sure something else has changed because it makes no sense that echo won't work when phpinfo does.

When you load the page you say is blank does it have the correct title (in browser title bar)? 

How are you editing the page? If you do it via an editor using Nautilus (ssh/sftp remote) then it will change the file ownership/permission unless you have specifically set the directory sticky guid (so files are created with group access). But in that case the page should give a not found or denied error due to wrong permissions. So, that's just something to check that dosen't really explain the problem.

Basically, the problem you descibe indicates that something else is wrong - not your code because the info you provide doesn't give any reason for it not working.

Are you sure that the only change is the index.php and not how you access the page, eg. from LAN or from external location. Something is being overlooked, step back and verify that only ONE variable is being changed between working and not working pages.

---

### Post by tgalati4 on 2011-04-17
Sounds like a web home directory problem.  Any errors in:

/var/log/apache2/error.log

Also check for your root web directory in /etc/apache2/sites-enabled

It should look something like:


tgalati4@hardy-back:/etc/apache2/sites-enabled$ cat 000-default 
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
	</Directory>
.
.
.

---

### Post by Sirkyuubi on 2011-04-17
Ok just to make sure I cd'd to the public_html dir made a file called test.php then did chmod 755 *.*

afterwards I opened test.php in gedit and added only one line <?php echo &#8220;test&#8221;; ?> then saved.

I opened firefox went to [http://localhost/test.php](http://localhost/test.php) and it turned up BLANK.

I then reopened test.php in gedit and inserted one line <?php phpinfo(); ?> removing the pervious line and saved. This worked. I am baffled.

Also, to recap, I have also copied dozens of examples from online that have multiple different php commands into test.php and test.php also turned up blank everytime. The only time its not blank is when I use <?php phpinfo(); ?>

Did I leave anything out?

---

### Post by fibster on 2011-04-17
> **Sirkyuubi said:**
> Anyone have any ideas? I know someone out there must have an idea to whats happening here.
Take a look at this,

[http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-10.10-lamp](http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-10.10-lamp)

---

### Post by Sirkyuubi on 2011-04-17
/etc/apache2/sites-enabled$ gksudo gedit coolness

<VirtualHost *:9000>
    ServerAdmin webmaster@localhost

    DocumentRoot /home/coolness/public_html
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /home/coolness/public_html>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>

    ScriptAlias /cgi-bin/ /home/coolness/public_html/cgi-bin/
    <Directory "/home/coolness/public_html/cgi-bin">
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

<VirtualHost *:80>
    ServerAdmin webmaster@localhost

    DocumentRoot /home/coolness/public_html
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /home/coolness/public_html>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>

    ScriptAlias /cgi-bin/ /home/coolness/public_html/cgi-bin/
    <Directory "/home/coolness/public_html/cgi-bin">
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

End of file


gksudo gedit /var/log/apache2/error.log

PHP Warning:  Module 'mysql' already loaded in Unknown on line 0
PHP Warning:  Module 'mysqli' already loaded in Unknown on line 0
[Sun Apr 17 19:40:35 2011] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.3 with Suhosin-Patch configured -- resuming normal operations
[Sun Apr 17 19:40:53 2011] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_STRING, expecting ',' or ';' in /home/coolness/public_html/test.php on line 6
[Sun Apr 17 19:41:49 2011] [notice] SIGHUP received.  Attempting to restart
PHP Warning:  Module 'mysql' already loaded in Unknown on line 0
PHP Warning:  Module 'mysqli' already loaded in Unknown on line 0
[Sun Apr 17 19:41:49 2011] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.3 with Suhosin-Patch configured -- resuming normal operations
[Sun Apr 17 19:41:54 2011] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_STRING, expecting ',' or ';' in /home/coolness/public_html/test.php on line 6
[Sun Apr 17 19:43:16 2011] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_STRING, expecting ',' or ';' in /home/coolness/public_html/test.php on line 1
[Sun Apr 17 19:43:18 2011] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_STRING, expecting ',' or ';' in /home/coolness/public_html/test.php on line 1
[Sun Apr 17 20:00:38 2011] [notice] caught SIGTERM, shutting down
PHP Warning:  Module 'mysql' already loaded in Unknown on line 0
PHP Warning:  Module 'mysqli' already loaded in Unknown on line 0
[Sun Apr 17 20:08:16 2011] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.3 with Suhosin-Patch configured -- resuming normal operations
[Sun Apr 17 20:08:18 2011] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_STRING, expecting ',' or ';' in /home/coolness/public_html/test.php on line 1
[Sun Apr 17 20:08:59 2011] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_STRING, expecting ',' or ';' in /home/coolness/public_html/test.php on line 2
[Sun Apr 17 20:09:00 2011] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_STRING, expecting ',' or ';' in /home/coolness/public_html/test.php on line 2
[Sun Apr 17 20:09:01 2011] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_STRING, expecting ',' or ';' in /home/coolness/public_html/test.php on line 2
[Sun Apr 17 20:09:02 2011] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_STRING, expecting ',' or ';' in /home/coolness/public_html/test.php on line 2
[Sun Apr 17 20:09:03 2011] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_STRING, expecting ',' or ';' in /home/coolness/public_html/test.php on line 2
[Sun Apr 17 20:09:04 2011] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_STRING, expecting ',' or ';' in /home/coolness/public_html/test.php on line 2
[Sun Apr 17 20:09:06 2011] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_STRING, expecting ',' or ';' in /home/coolness/public_html/test.php on line 2
[Sun Apr 17 20:09:08 2011] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_STRING, expecting ',' or ';' in /home/coolness/public_html/test.php on line 2
[Sun Apr 17 20:09:51 2011] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_STRING, expecting ',' or ';' in /home/coolness/public_html/test.php on line 2
[Sun Apr 17 20:10:59 2011] [error] [client 127.0.0.1] PHP Notice:  Use of undefined constant \xe2\x80\x9ctest\xe2\x80\x9d - assumed '\xe2\x80\x9ctest\xe2\x80\x9d' in /home/coolness/public_html/test.php on line 7
[Sun Apr 17 20:11:40 2011] [error] [client 127.0.0.1] PHP Notice:  Use of undefined constant \xe2\x80\x9ctest\xe2\x80\x9d - assumed '\xe2\x80\x9ctest\xe2\x80\x9d' in /home/coolness/public_html/test.php on line 7

end of file

---

### Post by Sirkyuubi on 2011-04-17
Ok. I copied this into test.php

<html>
<head>
<title>My First PHP Program</title>
</head>
<body>
<?php
echo “test”;
?>
</body>
</html>

and I got this in firefox...

â€œtestâ€   

> **BkkBonanza said:**
> 

When you load the page you say is blank does it have the correct title (in browser title bar)? 

How are you editing the page?

Yes the title is showing.

I'm using gedit to edit these.
No im not using sudo gedit or gksudo gedit

---

### Post by BkkBonanza on 2011-04-18
It would appear you are getting the quotes wrong when you save the file. I'm not sure why but your error log message indicates there is unknown (maybe UTF or wrongly encoded) chars before and after the test word. This is why the php interperer is not outputing them. It see's "test" as <garbage>test<garbage>, and doesn't kow what to do without the correct quote chars. See final error lines in log. Quotes chars are definitely not "undefined constants". 

Use a different editor to fix the file. eg. at coonsole use nano test.php.
Likely you'll see garbage in the file there. Fix it and re load the page in browser.

I have no idea why gedit would be saving bad quotes but my guess is an language encoding issue like UTF-8 mode or something.

The title being correct indicates the page is received and the html portion is good enough for the browser to grab the title value. After that php chokes and stops sending output.

For debugging purpose I would recommend editing your php.ini file and setting the display errors value to show them in the output rather than log them. For final production web sites you want that off but for testing having it on makes it easy to see when something is wrong because the errors get thrown in your face.

---

### Post by Sirkyuubi on 2011-04-18
I think I may have figured it out...
I have been copy and pasting from the book. The whitespace that has been copied from the book is infact not whitespace and php sees it as something else. I believe this is what was causing the problem. Upon typing out the examples that I see instead of copying them I don't get any errors.

Thank you everyone for your hard work and help.

P.S. How do I change this thread to solved?

---

### Post by garycahill on 2011-05-24
Check the php5 modules are all on for LAMP:

apt-get install php5 apache2-mpm-prefork libapache2-mod-php5 php5 php5-common php5-mysql php5-xmlrpc 

gary

---

