---
title: "XAMPP: Couldn't start MySQL"
date: 2011-07-21
forum: Server Platforms
---

### Post by gilrez on 2011-07-21
[COLOR=#000000][FONT=Arial]XAMPP: Couldn't start MySQL![/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]Hello fellow Ubuntu’s![/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]                                                  *** I have Ubuntu 11.4***[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]After  downloading  XAMPP, I went to my Downloads. I then went to the Folder  (xampp-linux-1.7.4.tar.gz) and right clicked on it. The options window  opened, and I selected ‘Extract Here’! after doing so a Folder called  lampp appeared.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]The  next step I did was open my Terminal and typed ( sudo nautilus / ). I  pressed Enter and a window with a bunch Folders opened up. I selected,  and opened the opt Folder. I then dragged the lampp Folder to the opt  Folder.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]The  lampp Folder is now in the opt Folder. I right clicked on the lampp  Folder and selected Properties, and then the Permissions tap. I set all 3  Folder access: -to- Create delete files  and all 3 File access: -to-  Read and write. I checked  Allow executing file as program, and Apply  Permissions to Enclosed Files button, then closed. [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I went back to Terminal and typed ( sudo /opt/lampp/lampp start ) and pressed Enter. Everything is working fine execpt MySQL! [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Starting XAMPP for Linux 1.7.4...[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]XAMPP: Starting Apache with SSL (and PHP5)...[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]XAMPP: Starting MySQL...[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]XAMPP: [/FONT][/COLOR][COLOR=#990000][FONT=Arial]Couldn't start MySQL![/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]XAMPP: Starting ProFTPD...[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]XAMPP for Linux started.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I  don’t know if it makes any difference but I do have Netbeans IDE 7.0  php installed and I’ve only worked on html and CSS on it. [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I appreciate any help that anyone can give me![/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Thank You![/FONT][/COLOR]

---

### Post by chandanreddy on 2011-12-02
i am having the same problem 
please help me . . . . .

---

### Post by mörgæs on 2011-12-02
Why did you install XAMPP and not LAMP?

---

### Post by __FrontSide__ on 2011-12-15
I've had the same problem..
Did you correctly install your xampp using the following command line?

[B]sudo tar xvfz xampp-linux-1.7.7.tar.gz -C /opt

[/B]It worked for me!

---

### Post by rathin2j on 2012-06-20
welll, i WAS having the same problem,when i started reading this thread,i was on this problem since last 11 hrs but right now i TOOK a break and when i cam back  a idea struck me that people were telling me to change 
> 
$cfg['Servers'][$i]['host']          = 'localhost';
to
$cfg['Servers'][$i]['host']          = 127.0.0.1;

in 
config.inc.php

but i was not able to locate that line in my file.. later on right now it struck that what if i ADD IT!!?

and i added and VOILA!! it was done!!

simply add 

> $cfg['Servers'][$i]['host']          = 'localhost';
in ur  /opt/lampp/phpmyadmin/config.inc.php file and u r ready to go!

---

### Post by jbrice on 2012-07-24
The problem with MySQL issues in XAMPP is that by default there is no error logging in MySQL.
So if you are having problems getting MySQL to run, add the following line to /opt/lampp/etc/my.cnf under the [MYSQLD] section -
```
log-error=/opt/lampp/logs/mysql_errors.log
```

and check this file after trying to start. It will probably give you a clue. Comment out when all is fixed, so it's there next time you have a problem.

---

### Post by YasinG on 2012-11-20
This is quite old, but I'm having the same problem. I followed jprice's advice, and this is what is in the mysql_error.log file:

```
121120 18:24:06 mysqld_safe Starting mysqld daemon with databases from /opt/lampp/var/mysql
121120 18:24:06 [Note] Plugin 'FEDERATED' is disabled.
/opt/lampp/sbin/mysqld: Can't find file: './mysql/plugin.frm' (errno: 13)
121120 18:24:06 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
121120 18:24:06  InnoDB: Started; log sequence number 0 44233
121120 18:24:06 [ERROR] /opt/lampp/sbin/mysqld: Can't find file: './mysql/host.frm' (errno: 13)
121120 18:24:06 [ERROR] Fatal error: Can't open and lock privilege tables: Can't find file: './mysql/host.frm' (errno: 13)
121120 18:24:06 mysqld_safe mysqld from pid file /opt/lampp/var/mysql/Yasin.pid ended
```

---

### Post by Lars Noodén on 2012-11-20
You're going about it the hard way.  I'd second mörgæs question and ask that you look more closely at doing things the normal way and use LAMP.  XAMPP is a useful crutch for those still on Windows, but for those that have upgraded to Linux, it is about the hardest possible way to go about setting up web services.

---

### Post by YasinG on 2012-11-20
I re-installed it, so the problem is solved, and I'm actually using lampp not xampp. But why is xampp harder than lampp anyway ?.

---

### Post by Lars Noodén on 2012-11-20
> **YasinG said:**
> I re-installed it, so the problem is solved, and I'm actually using lampp not xampp. But why is xampp harder than lampp anyway ?.

Both are wrong.  The main problem is that they avoid using the package manager.  The package manager helps greatly with both installation and maintenance, including updates and security updates.  LAMPP also installs things in non-standard places.  There is [a place for everything](http://manpages.ubuntu.com/manpages/precise/en/man7/hier.7.html) and the package manager puts programs and configuration data in the right spots.  Then there is the issue of redundant packages python and perl are built into most Linux distros, including Ubuntu.  Adding extra copies of the same programs just creates confusion.  And, because LAMPP and XAMPP need to be maintained manually, it is a lot of extra work that the computer should have been doing for you.  

The LAMP stack can be installed easily with one line in the shell, or the corresponding clicks in Synaptic.

```

sudo lamp-server^

```

That will get you the packages you need, put them in the right places so they will work with other applications and will allow the updates to be managed automatically.

---

### Post by nunop on 2013-01-09
i had the same problem but it was related to the /opt/lampp/etc/my.cnf file permissions.

so i just
chmod 555 /opt/lampp/etc/my.cnf

and its working

---

### Post by Jing1327 on 2013-05-24
[FONT=arial black][SIZE=2][COLOR=#000000]First thing you must do is to install xampp as [/COLOR][/SIZE][/FONT][COLOR=#ff0000][SIZE=4]**super user**[/SIZE][/COLOR][FONT=arial black][SIZE=2][COLOR=#000000] to avoid errors like couldn't start MySQL and can't start PHPMyAdmin
[/COLOR][/SIZE][/FONT][COLOR=#000000][FONT=arial black]
>if you have already install xampp on your system before just type '[/FONT][/COLOR]*[FONT=arial]rm -rf /opt/lampp' [/FONT]*[COLOR=#000000][FONT=arial black]to have a fresh install:[/FONT][/COLOR]
[FONT=arial black][SIZE=2][COLOR=#000000]
[/COLOR][/SIZE][/FONT][FONT=arial black][SIZE=2][COLOR=#000000]Open terminal and login as the system administrator root:
[/COLOR][/SIZE][/FONT]*[SIZE=2][COLOR=#000000]su[/COLOR][/SIZE]*
[FONT=arial black][SIZE=2][COLOR=#000000]Extract the downloaded archive file to /opt:
[/COLOR][/SIZE][/FONT][FONT=arial][COLOR=#000000][COLOR=#000000]*tar xvfz xampp-linux-1.8.1.tar.gz -C /opt*[/COLOR][SIZE=2][COLOR=#000000]
[/COLOR][/SIZE][/COLOR][/FONT][COLOR=#000000][COLOR=#000000]**then**[/COLOR][/COLOR]
[COLOR=#000000][FONT=arial black][SIZE=2][COLOR=#000000]*[FONT=arial]sudo gedit /opt/lampp/etc/extra/httpd-xampp.conf[/FONT]*
this is to fix PHPMyAdmin error;[/COLOR][/SIZE][/FONT][/COLOR]
[FONT=arial black][SIZE=2][COLOR=#000000]copy and paste this 

[/COLOR][/SIZE][/FONT]```
<IfDefine PHP4>
LoadModule php4_module        modules/libphp4.so
</IfDefine>
<IfDefine PHP5>
LoadModule php5_module        modules/libphp5.so
</IfDefine>
# Disabled in XAMPP 1.8.0-beta2 because of current incompatibilities with Apache 2.4
# LoadModule perl_module        modules/mod_perl.so




Alias /phpmyadmin "/opt/lampp/phpmyadmin"
Alias /phpsqliteadmin "/opt/lampp/phpsqliteadmin"


# since XAMPP 1.4.3
<Directory "/opt/lampp/phpmyadmin">
    AllowOverride AuthConfig Limit
    Require all granted
    Order allow,deny
    Allow from all
</Directory>


<Directory "/opt/lampp/phpsqliteadmin">
    AllowOverride AuthConfig Limit
    Order allow,deny
    Allow from all
</Directory>


# since LAMPP 1.0RC1
AddType application/x-httpd-php .php .php3 .php4


XBitHack on


# since 0.9.8 we've mod_perl
<IfModule mod_perl.c>
        AddHandler perl-script .pl
    PerlHandler ModPerl::PerlRunPrefork
    PerlOptions +ParseHeaders
        PerlSendHeader On
</IfModule>


# demo for mod_perl responsehandler
#PerlModule Apache::CurrentTime
#<Location /time>
#      SetHandler modperl
#      PerlResponseHandler Apache::CurrentTime
#</Location>


# AcceptMutex sysvsem is default but on some systems we need this
# thanks to jeff ort for this hint
#AcceptMutex flock
#LockFile /opt/lampp/logs/accept.lock


# this makes mod_dbd happy - oswald, 02aug06
# mod_dbd doesn't work in Apache 2.2.3: getting always heaps of "glibc detected *** corrupted double-linked list" on shutdown - oswald, 10sep06
#DBDriver sqlite3


#
# New XAMPP security concept
#
<LocationMatch "^/(?i:(?:xampp|security|licenses|phpmyadmin|webalizer|server-status|server-info))">
    Order deny,allow
    Allow from all
    Allow from ::1 127.0.0.0/8 \
        fc00::/7 10.0.0.0/8 172.16.0.0/12 192.168.0.0/16 \
        fe80::/10 169.254.0.0/16


    ErrorDocument 403 /error/XAMPP_FORBIDDEN.html.var
</LocationMatch>

[FONT=arial black][SIZE=2][COLOR=#000000]
[/COLOR][/SIZE][/FONT]


```
[FONT=arial black]if you have some problem on the login as super user or su command just do this:
[/FONT]$ sudo passwd root
[sudo] password for user:
Enter new UNIX password:
Retype new UNIX password:
password update succesfully


credit to [Daksh Bhatt]("https://plus.google.com/100104804407283458860") @ [http://daksh21ubuntu.blogspot.com/2012/07/new-xampp-security-concept-problem-in.html](http://daksh21ubuntu.blogspot.com/2012/07/new-xampp-security-concept-problem-in.html) and
[COLOR=#888888][FONT=Helvetica Neue]RAMESH NATARAJAN @ [/FONT][/COLOR][http://www.thegeekstuff.com/2009/09/ubuntu-tips-how-to-login-using-su-command-su-gives-authentication-failure-error-message/](http://www.thegeekstuff.com/2009/09/ubuntu-tips-how-to-login-using-su-command-su-gives-authentication-failure-error-message/)

---

