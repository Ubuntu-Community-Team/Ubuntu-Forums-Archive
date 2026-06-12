---
title: "Index.cgi not rendering, showing text only."
date: 2011-10-25
forum: Server Platforms
---

### Post by jaks on 2011-10-25
Hello everyone, I’m setting up bugzilla on Ubuntu Server, and for some reason the main page, index.cgi, is displayed as raw text in a web browser – instead of being displayed/rendered as a login page. It’s literally displayed as if you looked at it in a text editor.
I’ve spent time searching for answers on this and have come up empty. I’m new to Linux but I want to learn, any help would be appreciated!

---

### Post by Jonathan L on 2011-10-26
> **jaks said:**
> [FONT=Arial][SIZE=2]Hello everyone, I&#8217;m setting up bugzilla on Ubuntu Server, and for some reason the main page, index.cgi, is displayed as raw text in a web browser &#8211; instead of being displayed/rendered as a login page. It&#8217;s literally displayed as if you looked at it in a text editor.
[/SIZE][/FONT] [FONT=Arial][SIZE=2]I&#8217;ve spent time searching for answers on this and have come up empty. I&#8217;m new to Linux but I want to learn, any help would be appreciated![/SIZE][/FONT][FONT=Arial][SIZE=2]

Hi Jaks

When your .cgi (or .php) pro[/SIZE][/FONT][FONT=Arial][SIZE=2]grams display as text, it means that the Apache web server software isn't configured to run them, merely to display them.
[/SIZE][/FONT] [FONT=Arial][SIZE=2]
The default settings (/etc/apache2/sites-enabled/000-default) only allows cgi scripts in /usr/lib/cgi-bin

So either: put your scripts in there, or allow ExecCGI in the directory where you want your script by editing the 000-default settings.[/SIZE][/FONT] [FONT=Arial][SIZE=2]

The following is a fragment of 000-default and will allow CGI scripts anywhere:[/SIZE][/FONT] [FONT=Arial][SIZE=2]
[/SIZE][/FONT]```
<VirtualHost *:80>
    ...
    <Directory /var/www/>
        Options Indexes [COLOR=Red]+ExecCGI[/COLOR] FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>
    ...
</VirtualHost>
```[FONT=Arial][SIZE=2]

[/SIZE][/FONT][FONT=Arial][SIZE=2]Be aware that the reason it's off by default is in case you have misbehaving programs or users.

After you change Apache configs, you (almost always) have to restart the server program:[/SIZE][/FONT] [FONT=Arial][SIZE=2]
```
sudo /etc/init.d/apache2 graceful
```(Also, depending on your browser, you may find that you need to empty your browser cache or it won't ask the server and you'll see the old page.)

(Tested on Apache2 on Ubuntu 10.04 LTS server; other releases might be slightly different.)

Hope that helps you.[/SIZE][/FONT] [FONT=Arial][SIZE=2]

Kind regards,[/SIZE][/FONT] [FONT=Arial][SIZE=2]
Jonathan.[/SIZE][/FONT]

---

### Post by jaks on 2011-10-27
Thanks, this is helping me narrow it down. I made the change and now I can get passed the first page which apparently redirects me to the next. This one looks more like html with javascript and it's only being displayed in straight text like the last ](*,) 
 
I added a seperate section to the 000-default file to get to this point - 
 
[COLOR=black][FONT=Arial]<Directory “/var/www/bugzilla”>[/FONT][/COLOR]
[FONT=Arial][COLOR=black]AddHandler cgi-script cgi[/COLOR][/FONT]
[FONT=Arial][COLOR=black]DirectoryIndex index.cgi[/COLOR][/FONT]
[FONT=Arial][COLOR=black]Options +Indexes +ExecCGI -MultiViews +SymLinksIfOwnerMatch +FollowSymLinks[/COLOR][/FONT]
[FONT=Arial][COLOR=black]AllowOverride None[/COLOR][/FONT]
[FONT=Arial][COLOR=black]Order allow,deny[/COLOR][/FONT]
[FONT=Arial][COLOR=black]Allow from all[/COLOR][/FONT]
[FONT=Arial][COLOR=black]</Directory>[/COLOR][/FONT]
 
 
Any ideas? I'm looking into making further modifications to this file.

---

### Post by Jonathan L on 2011-10-28
> **jaks said:**
> Thanks, this is helping me narrow it down. ...
Any ideas? I'm looking into making further modifications to this file.

Hi Jaks

Seems that getting Bugzilla running is a bit tricky!  I think the direct answer to your problem is to add .pl to the AddHandler line, as Bugzilla code is written in perl as .pl files which are actually executable by the shell (as they have #!/usr/bin/perl at the top of each file).
```
AddHandler cgi-script .cgi .pl
```But as I was interested in this I thought I'd take a closer look, and I was very surprised at how fiddly it is to get all the bits of perl right.  So I thought I'd write it up in detail in case it helps someone.

Basically following the instructions at 
[http://www.bugzilla.org/docs/4.0/en/html/installation.html](http://www.bugzilla.org/docs/4.0/en/html/installation.html) and
[http://www.bugzilla.org/docs/4.0/en/html/configuration.html](http://www.bugzilla.org/docs/4.0/en/html/configuration.html) I found the tricky part was they don't tell you about Apache config, and they don't tell you much about getting all the perl installed.

The following are the exact steps from a completely fresh installation of 10.04 server (at AWS with machine image ami-311f2b45, if anyone wants to exactly repeat it.)

In detail:

Web server, database server (MySQL), C compiler (required for perl modules later).  During lamp server you give the MySQL root user password.  NB note caret in lamp-server^
```
sudo apt-get update
sudo apt-get install -y lamp-server^
sudo apt-get install -y gcc

```Now, (basically following  [http://httpd.apache.org/docs/2.0/howto/cgi.html](http://httpd.apache.org/docs/2.0/howto/cgi.html)) we edit 
```
/etc/apache2/sites-enabled/000-default

```To give diff:
```
0a1,2
> AddHandler cgi-script .cgi .pl
> 
14a17,19
>     <Directory /var/www/bugzilla-4.0.2>
>         Options +ExecCGI
>     </Directory>

```Restart web server
```
sudo apache2ctl graceful

```Get bugzilla files, deal with modes
```
cd /var/www
sudo chmod 777 .
wget [http://ftp.mozilla.org/pub/mozilla.org/webtools/bugzilla-4.0.2.tar.gz](http://ftp.mozilla.org/pub/mozilla.org/webtools/bugzilla-4.0.2.tar.gz)
tar xf bugzilla-4.0.2.tar.gz 

```Bugzilla installation of modules
```
cd bugzilla-4.0.2/
sudo ./checksetup.pl --check-modules

```The check-modules will complain about some required (and some optional) modules, so you do the install process suggested:
```
sudo /usr/bin/perl install-module.pl --all
```Note that this takes 20 minutes!  And ends with some error about "won't install without force": just ignore this.

Check it again, and should not mention any required modules, only some optional ones.
```
sudo ./checksetup.pl --check-modules

```We check the setup with the script
```
 sudo ./checksetup.pl

```This will say it's okay, and have to edit the file 'localconfig'

Edit localconfig and change the webservergroup to www-data and a password for the bugzilla MySQL account, to give this diff:
```
27c27
< $webservergroup = 'apache';
---
> $webservergroup = 'www-data';
59c59
< $db_pass = '';
---
> $db_pass = 'bunny';


```Now make a MySQL account for user 'bugs'
```
mysql -uroot -ppassword

```Paste in the SQL:
```
GRANT SELECT, INSERT,
           UPDATE, DELETE, INDEX, ALTER, CREATE, LOCK TABLES,
           CREATE TEMPORARY TABLES, DROP, REFERENCES ON bugs.*
           TO bugs@localhost IDENTIFIED BY 'bunny';
FLUSH PRIVILEGES;

```Quit MySQL.

Test you can start MySQL as this user, then quit:
```
mysql -ubugs -pbunny
```Finally, run the check again, which actually creates the database and the tables:
```
sudo ./checksetup.pl
```This requires making a first adminstrator user for Bugzilla:
```
Enter the e-mail address of the administrator: [EMAIL="bugs@example.com"]bugs@example.com[/EMAIL]
Enter the real name of the administrator: Bugs Bunny
Enter a password for the administrator account: password2
```Then browse to it: [http://1.2.3.4/bugzilla-4.0.3](http://1.2.3.4/bugzilla-4.0.3)

It worked immediately after these, and I could log in as 'bugs@example.com'  make a bug report, and search for it.  I'm sure there's more work to get it secure and other customisations, but it's running.  (I think some work would be needed on file permissions, removing the tarfile, and similar.)


Phew!

In passing, I notice that there is also a ready-made package, but of a different version, which may or may not be suitable.
```
apt-get install lamp-server^
install bugzilla3

```Browse to [http://1.2.3.4/bugzilla3](http://1.2.3.4/bugzilla3)


Hope that's of use to you!

Kind regards,
Jonathan.

---

### Post by jaks on 2011-11-07
> **Jonathan L said:**
> Hi Jaks
 
Seems that getting Bugzilla running is a bit tricky! I think the direct answer to your problem is to add .pl to the AddHandler line, as Bugzilla code is written in perl as .pl files which are actually executable by the shell (as they have #!/usr/bin/perl at the top of each file).
```
AddHandler cgi-script .cgi .pl
```But as I was interested in this I thought I'd take a closer look, and I was very surprised at how fiddly it is to get all the bits of perl right. So I thought I'd write it up in detail in case it helps someone.
 
Basically following the instructions at 
[http://www.bugzilla.org/docs/4.0/en/html/installation.html](http://www.bugzilla.org/docs/4.0/en/html/installation.html) and
[http://www.bugzilla.org/docs/4.0/en/html/configuration.html](http://www.bugzilla.org/docs/4.0/en/html/configuration.html) I found the tricky part was they don't tell you about Apache config, and they don't tell you much about getting all the perl installed.
 
The following are the exact steps from a completely fresh installation of 10.04 server (at AWS with machine image ami-311f2b45, if anyone wants to exactly repeat it.)
 
In detail:
 
Web server, database server (MySQL), C compiler (required for perl modules later). During lamp server you give the MySQL root user password. NB note caret in lamp-server^
```
sudo apt-get update
sudo apt-get install -y lamp-server^
sudo apt-get install -y gcc

```Now, (basically following [http://httpd.apache.org/docs/2.0/howto/cgi.html](http://httpd.apache.org/docs/2.0/howto/cgi.html)) we edit 
```
/etc/apache2/sites-enabled/000-default

```To give diff:
```
0a1,2
> AddHandler cgi-script .cgi .pl
> 
14a17,19
>     <Directory /var/www/bugzilla-4.0.2>
>         Options +ExecCGI
>     </Directory>

```Restart web server
```
sudo apache2ctl graceful

```Get bugzilla files, deal with modes
```
cd /var/www
sudo chmod 777 .
wget [http://ftp.mozilla.org/pub/mozilla.org/webtools/bugzilla-4.0.2.tar.gz](http://ftp.mozilla.org/pub/mozilla.org/webtools/bugzilla-4.0.2.tar.gz)
tar xf bugzilla-4.0.2.tar.gz 

```Bugzilla installation of modules
```
cd bugzilla-4.0.2/
sudo ./checksetup.pl --check-modules

```The check-modules will complain about some required (and some optional) modules, so you do the install process suggested:
```
sudo /usr/bin/perl install-module.pl --all
```Note that this takes 20 minutes! And ends with some error about "won't install without force": just ignore this.
 
Check it again, and should not mention any required modules, only some optional ones.
```
sudo ./checksetup.pl --check-modules

```We check the setup with the script
```
 sudo ./checksetup.pl

```This will say it's okay, and have to edit the file 'localconfig'
 
Edit localconfig and change the webservergroup to www-data and a password for the bugzilla MySQL account, to give this diff:
```
27c27
< $webservergroup = 'apache';
---
> $webservergroup = 'www-data';
59c59
< $db_pass = '';
---
> $db_pass = 'bunny';
 

```Now make a MySQL account for user 'bugs'
```
mysql -uroot -ppassword

```Paste in the SQL:
```
GRANT SELECT, INSERT,
           UPDATE, DELETE, INDEX, ALTER, CREATE, LOCK TABLES,
           CREATE TEMPORARY TABLES, DROP, REFERENCES ON bugs.*
           TO bugs@localhost IDENTIFIED BY 'bunny';
FLUSH PRIVILEGES;

```Quit MySQL.
 
Test you can start MySQL as this user, then quit:
```
mysql -ubugs -pbunny
```Finally, run the check again, which actually creates the database and the tables:
```
sudo ./checksetup.pl
```This requires making a first adminstrator user for Bugzilla:
```
Enter the e-mail address of the administrator: [EMAIL="bugs@example.com"]bugs@example.com[/EMAIL]
Enter the real name of the administrator: Bugs Bunny
Enter a password for the administrator account: password2
```Then browse to it: [http://1.2.3.4/bugzilla-4.0.3](http://1.2.3.4/bugzilla-4.0.3)
 
It worked immediately after these, and I could log in as 'bugs@example.com' make a bug report, and search for it. I'm sure there's more work to get it secure and other customisations, but it's running. (I think some work would be needed on file permissions, removing the tarfile, and similar.)
 
 
Phew!
 
In passing, I notice that there is also a ready-made package, but of a different version, which may or may not be suitable.
```
apt-get install lamp-server^
install bugzilla3

```Browse to [http://1.2.3.4/bugzilla3](http://1.2.3.4/bugzilla3)
 
 
Hope that's of use to you!
 
Kind regards,
Jonathan.
 
 
 
Thanks for the reply. I looked at the site you listed and it really helped also. I ended up making a lot of little changes, mainly updated mysql permissions and then updated the 000-default file to -
 
```

<Directory /var/www/bugzilla>
AddHandler cgi-script .cgi
Options +Indexes +ExecCGI
DirectoryIndex index.cgi
AllowOverride Limit FileInfo Indexes
</Directory>

```
 
I think the 000-default file was the key, so thanks to both of you guys for pointing me in that direction and taking the time to help. Now it's off to install Testopia on top!:eek:

---

