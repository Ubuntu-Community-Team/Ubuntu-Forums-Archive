---
title: "Beginner Apache2 questions"
date: 2011-12-23
forum: Server Platforms
---

### Post by mike_abc on 2011-12-23
Hi guys,

I have been using Ubuntu Desktop for 2 years. Now I try to learn PHP to develop a website, so I installed LAMP (not LAMPP) and I have the following questions:

(1) Why is there more than 1 way to start Apache ?

  /usr/local.../apachectl; service apache2 start; /etc/init.d/apache2 start

*What is the difference between the 3 commands above ?*


(2) When I use [COLOR=Blue]**apachectl**[/COLOR] to (re)start Apache (which my book says I must do), I get:

```
httpd not running, trying to start
98 Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

```
But immediately afterwards I checked whether apache is running, and got the following:

```
root@Sumatra:/home/mikey# service apache2 status
Apache is running (pid 2319).

```
By the way, my book is**: [COLOR=RoyalBlue]Quentin Zervaas - Practical Web 2.0 Apps[/COLOR]**, which isn't helpful at all (but maybe one of you has succeeded in installing LAMP with instructions from there).

PS. In my book, I am required to configure apache to run a VirtualHost, which I did - or at least thought so. Has that anything to do with the above ? 

Thanks/regards,

Mike
[/SIZE]

---

### Post by Lars Noodén on 2011-12-23
> **mike_abc said:**
> 
(1) Why is there more than 1 way to start Apache ?

  /usr/local.../apachectl; service apache2 start; /etc/init.d/apache2 start

**What is the difference between the 3 commands above ?**



[font=Courier New]/usr/sbin/apache2ctl[/font] is the generic script that comes with Apache.  You'll find this script on all systems where Apache is installed.
 
[font=Courier New]/etc/init.d/apache2[/font] is the SystemV method that comes on Unix and Unix-like systems.

[font=Courier New]service apache2 start[/font] is from [Upstart](http://upstart.ubuntu.com/), Ubuntu's intended replacement for SystemV scripts.

---

### Post by mike_abc on 2011-12-23
[SIZE=2]Ok,

thanks for your answer - which unfortunately doesn't help me :). 

I asked the question because the **commands are not equivalent**,** i.e. interchangable** ! 

It seems neither the same **httpd.conf**, nor the same **index.html** are used with any of those 3 commands.

What is also unnerving, puzzling etc. - at least to a greenhorn like me - is the fact that there are more **httpd.conf** files spread throughut my system, so I'm not sure which one is used by Apache. 

What I found out is that (seemingly) **apachectl** uses the one in /usr/local/..., whereas **service** uses the one in /etc/apache2 (?).

And what about question #2 ? :confused:
[/SIZE]

---

### Post by Lars Noodén on 2011-12-23
> **mike_abc said:**
> What is also unnerving, puzzling etc. - at least to a greenhorn like me - is the fact that there are more **httpd.conf** files spread throughut my system, so I'm not sure which one is used by Apache.

There should only be one AND the control scripts should all work the same.  

So it sounds like you have multiple copies of Apache installed on your system.  Did you use any method besides the package manager?  Safe methods include The Software Center, Synaptic and apt-get.

As to question #2, "98 Address already in use: make_sock: could not bind to address 0.0.0.0:80" indicates that there is already a server of some kind listening at port 80.  That is almost certainly a web server and further indicates that you might have ended up with multiple copies of Apache on your machine.  

If so, uninstall them and use only the one from The Software Center, Synaptic or apt-get.

---

### Post by mike_abc on 2011-12-23
[SIZE=2]Yeah, that may be so. And how am I sure to uninstall ALL the copies ? Is sudo apt-get uninstall apache (or apache2 ?) the correct way to proceed ?[/SIZE]
[SIZE=2]
[SIZE=2]Or s[/SIZE][/SIZE][SIZE=2]hould I use the Synaptic PM ?[/SIZE]

[SIZE=2]Thanx

PS. The author of the book said to download the tar.gz, make and make install it. Does this conflict with the SPM ? Usually, I know the SPM doesn't have the latest editions. I prefer using it, since, as a long time PC (MS Windows) user & programmer (since DOS times, though), I prefer a GUI. 
[/SIZE]

---

### Post by Lars Noodén on 2011-12-23
First you have to find the copies.  The ones that were installed by the package manager are the ones you want to keep.

```

sudo updatedb
locate apache2 | grep bin/
locate httpd   | grep bin/

```

If there is any apache2 or httpd outside of /usr/sbin, then we have probably found the troublemaker.

---

### Post by mike_abc on 2011-12-23
[SIZE=2]Thanks Lars,

but my book, and also sources on Internet say that the default installation folder is 

/usr/local/apache2 and subdirs. Doesn't that contradict your advice (/usr/sbin/) :( ? Sorry, I'm a greenhorn re: Apache, I may be asking silly questions.[/SIZE]

---

### Post by Lars Noodén on 2011-12-23
The book might say [font=Courier New]/usr/local/sbin[/font] but in Ubuntu, Apache2 is installed in [font=Courier New]/usr/sbin[/font].  You can check for yourself.  What we are looking for is instances of Apache2 that are in some other location.  That's where [locate](http://linux.die.net/man/1/locate) comes in.

---

### Post by mike_abc on 2011-12-23
[SIZE=2]But in the meantime,

locate apache2 | grep bin/ has generated the following:

```
/usr/local/apache2/bin/ab
/usr/local/apache2/bin/apachectl
/usr/local/apache2/bin/apr-1-config
/usr/local/apache2/bin/apu-1-config
/usr/local/apache2/bin/apxs
/usr/local/apache2/bin/checkgid
/usr/local/apache2/bin/dbmmanage
/usr/local/apache2/bin/envvars
/usr/local/apache2/bin/envvars-std
/usr/local/apache2/bin/htcacheclean
/usr/local/apache2/bin/htdbm
/usr/local/apache2/bin/htdigest
/usr/local/apache2/bin/htpasswd
/usr/local/apache2/bin/httpd
/usr/local/apache2/bin/httxt2dbm
/usr/local/apache2/bin/logresolve
/usr/local/apache2/bin/rotatelogs
/usr/local/apache2/cgi-bin/printenv
/usr/local/apache2/cgi-bin/test-cgi
[B]/usr/sbin/apache2
/usr/sbin/apache2ctl
[/B]/usr/share/doc/apache2.2-bin/changelog.Debian.gz
/usr/share/doc/apache2.2-bin/changelog.gz
/usr/share/doc/apache2.2-bin/copyright

``` 
and

locate httpd | grep bin/

has generated

```
/usr/lib/couchdb/erlang/lib/couch-0.10.0/ebin/couch_httpd.beam
/usr/lib/couchdb/erlang/lib/couch-0.10.0/ebin/couch_httpd_auth.beam
/usr/lib/couchdb/erlang/lib/couch-0.10.0/ebin/couch_httpd_db.beam
/usr/lib/couchdb/erlang/lib/couch-0.10.0/ebin/couch_httpd_external.beam
/usr/lib/couchdb/erlang/lib/couch-0.10.0/ebin/couch_httpd_misc_handlers.beam
/usr/lib/couchdb/erlang/lib/couch-0.10.0/ebin/couch_httpd_oauth.beam
/usr/lib/couchdb/erlang/lib/couch-0.10.0/ebin/couch_httpd_show.beam
/usr/lib/couchdb/erlang/lib/couch-0.10.0/ebin/couch_httpd_stats_handlers.beam
/usr/lib/couchdb/erlang/lib/couch-0.10.0/ebin/couch_httpd_view.beam
/usr/lib/erlang/lib/inets-5.2/ebin/httpd.beam
/usr/lib/erlang/lib/inets-5.2/ebin/httpd_acceptor.beam
/usr/lib/erlang/lib/inets-5.2/ebin/httpd_acceptor_sup.beam
/usr/lib/erlang/lib/inets-5.2/ebin/httpd_cgi.beam
/usr/lib/erlang/lib/inets-5.2/ebin/httpd_conf.beam
/usr/lib/erlang/lib/inets-5.2/ebin/httpd_esi.beam
/usr/lib/erlang/lib/inets-5.2/ebin/httpd_example.beam
/usr/lib/erlang/lib/inets-5.2/ebin/httpd_file.beam
/usr/lib/erlang/lib/inets-5.2/ebin/httpd_instance_sup.beam
/usr/lib/erlang/lib/inets-5.2/ebin/httpd_log.beam
/usr/lib/erlang/lib/inets-5.2/ebin/httpd_manager.beam
/usr/lib/erlang/lib/inets-5.2/ebin/httpd_misc_sup.beam
/usr/lib/erlang/lib/inets-5.2/ebin/httpd_request.beam
/usr/lib/erlang/lib/inets-5.2/ebin/httpd_request_handler.beam
/usr/lib/erlang/lib/inets-5.2/ebin/httpd_response.beam
/usr/lib/erlang/lib/inets-5.2/ebin/httpd_script_env.beam
/usr/lib/erlang/lib/inets-5.2/ebin/httpd_socket.beam
/usr/lib/erlang/lib/inets-5.2/ebin/httpd_sup.beam
/usr/lib/erlang/lib/inets-5.2/ebin/httpd_util.beam
/usr/local/apache2/bin/httpd

```

In Synaptic (with [COLOR=Blue]apache2[/COLOR] as filter), the following packages appear:

```
apache2
apache2-mpm-prefork
apache2-utils
apache2.2-bin
apache2.2-common
libapache2-mod-php5

```
To me, it doesn't look like 2 installations. Or should it ? 
Anyway, I can reinstall Apache. Do I subsequently have to reinstall PHP, too ?

---

### Post by Lars Noodén on 2011-12-23
You definitely have a second instance of Apache.  The whole hierarchy [font=Courier New]/usr/local/apache2/[/font] shouldn't exist if you only got Apache from the package manager.  [font=Courier New]/usr/local/apache2/bin/httpd[/font] is the extra one.  How did you get it?  The method by which you acquired it will help determine what needs to be removed from where.

Did you download and install something with [font=Courier New].tar.gz[/font] and then unpack it?

---

### Post by Lars Noodén on 2011-12-23
I've looked at the tarball from the main [Apache web site](http://httpd.apache.org/download.cgi) and it seems to install everything into [font=Courier New]/usr/local/apache2[/font]  If that is the case, you can safely remove the directory and its contents.  

When you work with the version of Apache that was installed via Ubuntu's package repository, your configuration file for the default virtual host will be found in [font=Courier New]/etc/apache2/sites-enabled/000-default[/font]

---

### Post by mike_abc on 2011-12-23
[SIZE=2]Thanks again Lars,
[/SIZE]
[SIZE=2]but I'm thinking the other way round, especially since the book I'm learning from says to install Apache manually via "make" and "make install". So I won't use synaptic, I'll "make-install" things. Isn't that OK ? In the meantime I deleted every apache directory in sight (finding files with "locate apache") - including /etc/apache2 - leaving only the apache ones that seem to belong to the repository. Before that, I deleted every apache2 package Synaptic knew about.

Thanx again for your continued support, I'm not being stubborn, and I don't want to waste your time. If it won't work correctly this time either,[SIZE=2] I'll [/SIZE][/SIZE][SIZE=2]install it via Synaptic, or better yet, via XAMPP.

Besides, the documentation and a book I've read about apache2 (Apache 2.0 Server Bible) say /usr/local is the usual Apache2 directory (and for PHP, too)[/SIZE].
[SIZE=2]
In the end, I don't tell the system where to install it: "make install" makes the decision, after "make" processes the source with the "--enable-modules-all" option - which is why the author seems to want to steer things this way. He never mentions neither synaptic, nor - and this would have been a very easy way - XAMPP.[/SIZE]

---

### Post by Lars Noodén on 2011-12-23
The files in [font=Courier New]/etc/apache2[/font] actually belong to the correct version of Apache, the one from the Ubuntu repositories.  You'll need them to work with Apache.

The [font=Courier New]./configure && make && sudo make install[/font] method is the way it was done in the 1990's before there were package managers.  Similar for XAMPP, which is a crutch for people still on Windows and does not fit well with the [Linux or Ubuntu way of doing things](http://linux.die.net/man/7/hier).  If you're using Ubuntu, I can't overstate the importance of taking advantage of the package manager.  

Now that you've got a clean system, I would recommend re-installing Apache from the package manager.

```

sudo apt-get --reinstall install apache2

```

Once that's done, you'll find you default virtual server's configuration file to be [font=Courier New]/etc/apache2/sites-enabled/000-default[/url]

---

### Post by mike_abc on 2011-12-23
[SIZE=2]Something interesting:

I reinstalled apache2 and tested it is working with the [http://localhost](http://localhost) "It works !" index.html page. Yeah, it works. 

But interestingly enough, the command "sudo service apache2 status" returns
"apache2: unrecognized service". 

And Synaptic also, doesn't report any apache2 package installed.

It's the same as with "standalone" .exe file in Windows, which you copy to some folder and run, but the Windows Registry knows nothing about (because they were not "installed"). 

BUT I would've thought that Linux is SOMEWHAT more evolved and "make install" would SOMEHOW report it has installed (the wonderful) Apache2 Server.


[/SIZE]

---

### Post by Lars Noodén on 2011-12-23
> **mike_abc said:**
> BUT I would've thought that Linux is SOMEWHAT more evolved and "make install" would SOMEHOW report it has installed (the wonderful) Apache2 Server.

It can't and won't.  [Make](http://manpages.ubuntu.com/manpages/oneiric/en/man1/make.1.html) is only for compiling.  Unless you take the extra step of [rolling your own package](http://www.debian-administration.org/articles/336) and installing it via the package manager (with [dpkg](http://manpages.ubuntu.com/manpages/oneiric/en/man1/dpkg.1.html)) then you are working outside the database.  Further, the tarball from the plain vanilla Apache from ASF will put the [files](http://linux.die.net/man/7/hier) in the wrong place for a Linux system.

As mentioned, [font=Courier New]./configure && make && sudo make install[/font] method is the way it was done in the 1990's before there were package managers.  If instead you use the package manager, it will automatically maintain a database of not only what is installed but also the versions of what is installed.

---

### Post by lisati on 2011-12-23
@mike_abc: I've edited your posts. Using [COLOR="Magenta"]Magenta[/COLOR] is a bit hard on my eyes, and it's common here for quotes from system logs and command output to be wrapped in [noparse]```
 and 
```[/noparse] tags.

---

### Post by mike_abc on 2011-12-24
[SIZE=2]Ok, lisati, got it.
[/SIZE]
[SIZE=2]Thank you, Lars. It's the same with Windows - software should be **installed**.[/SIZE] [SIZE=2]Still, I want to try to make the Project in my book work. Mind you, it's hailed as one of the most advanced books in its field :P !

Happy holidays !

Mike

[/SIZE]

---

### Post by mike_abc on 2011-12-24
[SIZE=2]PS. Still, I can't resist a question: if the Apache 2.2 website documentation recommends compiling and installing to **/usr/local**, why, then, doesn't Synaptic install Apache to the same location ? 

The [/SIZE][SIZE=2][COLOR=RoyalBlue]Apache 2.2 Compiling & Installing Documentation[/COLOR][/SIZE][SIZE=2] begins with the following: **This document covers compilation and installation of the Apache HTTP     Server on Unix and Unix-like systems only.**

Ubuntu is Linux is Unix, isn't it ? Or is there "a war" going on between Apache and Ubuntu ?

I don't debate installing via Synaptic. I just debate non-conformity.
[/SIZE]

---

### Post by Lars Noodén on 2011-12-24
> **mike_abc said:**
> [SIZE=2]... why, then, doesn't Synaptic install Apache to the same location ? 


Because there is a place for everything and everything should be in its proper place.  Things that you build yourself with [font=Courier New]make[/font] are often intended for customization first.  You don't just take a stock build and install it, but instead adapt a little to the actual system it will run on.  

Just as it is for Ubuntu it is for [Linux](http://refspecs.linuxfoundation.org/lsb.shtml), so it is even other Unix-like systems:

[http://manpages.ubuntu.com/manpages/oneiric/en/man7/hier.7.html](http://manpages.ubuntu.com/manpages/oneiric/en/man7/hier.7.html)
[http://linux.die.net/man/7/hier](http://linux.die.net/man/7/hier)
[http://www.openbsd.org/cgi-bin/man.cgi?query=hier](http://www.openbsd.org/cgi-bin/man.cgi?query=hier)
[http://developer.apple.com/library/mac/#documentation/Darwin/Reference/ManPages/man7/hier.7.html](http://developer.apple.com/library/mac/#documentation/Darwin/Reference/ManPages/man7/hier.7.html)
Same for Solaris, etc.

Using the proper locations is especially important when there will be more than one sysadmin over the life of a machine, either at the same time or one after the other.

---

### Post by mike_abc on 2011-12-24
[SIZE=2]I have news ! Interesting things occured:

After installing PHP Version 5.3.8, some Apache 2.2.14 modules are now visible in Synaptic (have been installed by PHP, obviously), whereas my manually installed version was Apache 2.2.21 and is, of course, not visible.

The modules are:

[B]apache2.2-common
apache2.2-bin
apache2.2-utils
apache2.2-mpm-prefork

[/B]- all of them version 2.2.14.

Now, is this a second Apache server copy on my server ?

**phpinfo()** ( /var/www/test.php ) reports the following:

Configuration
apache2handler

Apache Version     Apache/2.2.14 (Ubuntu)
Apache API Version     20051115
Server Administrator     webmaster@localhost
Hostname Port     127.0.1.1:80
User/Group     www-data(33)/33
Max Requests     Per Child: 0 - Keep Alive: on - Max Per Connection: 100
Timeouts     Connection: 300 - Keep-Alive: 15
Virtual Server     Yes
[COLOR=Blue]**Server Root     /etc/apache2**[/COLOR]
Loaded Modules     core mod_log_config mod_logio 
           prefork http_core mod_so mod_alias 
           mod_auth_basic mod_authn_file 
           mod_authz_default mod_authz_groupfile 
           mod_authz_host mod_authz_user 
           mod_autoindex mod_cgi mod_deflate 
   mod_dir mod_env mod_mime 
           mod_negotiation mod_php5 
           mod_reqtimeout mod_setenvif 
           mod_status

Apache Environment
Variable    Value
HTTP_HOST         localhost
HTTP_USER_AGENT     Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.24) Gecko/20111107 Ubuntu/10.04 (lucid) Firefox/3.6.24
HTTP_ACCEPT         text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
HTTP_ACCEPT_LANGUAGE     chrome://global/locale/intl.properties
HTTP_ACCEPT_ENCODING     gzip,deflate
HTTP_ACCEPT_CHARSET     ISO-8859-1,utf-8;q=0.7,*;q=0.7
HTTP_KEEP_ALIVE     115
HTTP_CONNECTION     keep-alive
PATH             /usr/local/bin:/usr/bin:/bin
SERVER_SIGNATURE     <address>Apache/2.2.14 (Ubuntu) Server at localhost Port 80</address>
SERVER_SOFTWARE     Apache/2.2.14 (Ubuntu)
SERVER_NAME         localhost
SERVER_ADDR         127.0.0.1
SERVER_PORT         80
REMOTE_ADDR         127.0.0.1
DOCUMENT_ROOT         /var/www
SERVER_ADMIN         webmaster@localhost
SCRIPT_FILENAME     /var/www/test.php
REMOTE_PORT         36641
GATEWAY_INTERFACE     CGI/1.1
SERVER_PROTOCOL     HTTP/1.1
REQUEST_METHOD         GET
QUERY_STRING         no value
REQUEST_URI         /test.php
SCRIPT_NAME         /test.php 

Since ServerRoot now appears to be /etc/apache2 -- instead of /usr/local/apache2 -- I'd say the answer is rather Yes.

(... Lars ?...)

[/SIZE]

---

### Post by Lars Noodén on 2011-12-24
> **mike_abc said:**
> 
Since ServerRoot now appears to be /etc/apache2 -- instead of /usr/local/apache2 -- I'd say the answer is rather Yes.


That is where Ubuntu's package for Apache set up the configuration files.  The DocumentRoot is where you will put your XHTML files and that will be [font=Courier New]/var/www[/font] 

You can see if you installed Apache via the package manager like this:

```

dpkg --get-selections apache2

```

If the output is 'apache2' then you're set.  If it returns nothing, then intsall Apache:

```

sudo apt-get update
sudo apt-get install apache2

```

You can still follow the exercises in the book, just translate the file locations in your head from [font=Courier New]/usr/local/apache2[/font] to the corresponding standard directory.

---

### Post by mike_abc on 2011-12-24
[SIZE=2]Yes, 

I outpaced you a little (this whole thing was starting to get on my nerves, its now 3 days since I started): I deleted the /usr/local/ installation and issued the comand you suggested some posts before:

```

sudo apt-get --reinstall install apache2

```which was a brief affair, since, it seems, apache was ALREADY there.

Now, with

```

dpkg --get-selections apache2

```I get the following:

```

apache2                                  install

```Is that good, or bad ? 

Also, there's a httpd.conf in etc/apache2, which, by the way, is invisible to the "locate httpd.conf" that I issue as root. Strange thing, this Linux.


[/SIZE]

---

### Post by Lars Noodén on 2011-12-24
> **mike_abc said:**
> I get the following:

```

apache2                                  install

```Is that good, or bad ? 

Also, there's a httpd.conf in etc/apache2, which, by the way, is invisible to the "locate httpd.conf" that I issue as root. Strange thing, this Linux.

That is good.  That means that the package apache2 is installed.  

You might need to run refresh [font=Courier New]locate[/font]'s database by running [sudo updatedb](http://manpages.ubuntu.com/manpages/oneiric/en/man8/updatedb.8.html)  However, the place where you need to be making your changes is in [font=Courier New]/etc/apache2/sites-enabled/000-default[/font]

---

### Post by mike_abc on 2011-12-24
[SIZE=2]Yes, I remember you saying that already, I think it was several times, but it seems I'm not so able at GETTING the information IN :).

Do I understand there should be a file **000-default** with the content of **httpd.conf** ? :confused:

(Thank you for all your answers...)
[/SIZE]

---

### Post by Lars Noodén on 2011-12-24
> **mike_abc said:**
> [SIZE=2]Yes, I remember you saying that already, I think it was several times, but it seems I'm not so able at GETTING the information IN :).

Do I understand there should be a file **000-default** with the content of **httpd.conf** ? :confused:

(Thank you for all your answers...)
[/SIZE]

No worries.

In this setup, (nearly) all changes to the configuration should go in [font=Courier New]000-default[/font].  So when the book refers to [font=Courier New]httpd.conf[/font], which is how old Apache 1.3 used to do it, then translate in your head to [font=Courier New]000-default[/font]

---

### Post by mike_abc on 2011-12-24
[SIZE=2][COLOR=Blue]**Sorry, I posted this while you were answering.**[/COLOR]

OK,

so I found 000-default (finally ! I'm still writing **dir** instead of **dir -al** or something else).

The guy in my book wants me to write the following:

```


<VirtualHost 192.168.0.80> 
    ServerName phpweb20 
    DocumentRoot /var/www/phpweb20/htdocs 
 
    <Directory /var/www/phpweb20/htdocs> 
        AllowOverride All 
        Options All 
    </Directory> 
 
    php_value include_path .:/var/www/phpweb20/include**:/usr/local/lib/pear **
    php_value magic_quotes_gpc off 
    php_value register_globals off 
</VirtualHost>


```But I'm not sure I can replace the whole contents of the original **000-default** file with the above. I guess the answer is NO (never mind the **/usr/local/lib/pear** thingy, I'll have to change it with something appropriate). 
[/SIZE][SIZE=2]
  Any suggestions ?

[/SIZE][SIZE=2]


[/SIZE]

---

### Post by Lars Noodén on 2011-12-24
1) Yes, but make a backup copy of [font=Courier New]000-default[/font] first.  That's in case you decide to restore it.

2) Yes but don't change it.  Observe carefully the last lines of that file:

```

# Include the virtual host configurations:
Include sites-enabled/

```

That pulls in any files that you've put in [font=Courier New]sites-enabled[/font]

---

### Post by mike_abc on 2011-12-24
[SIZE=2]OK, it's almost Christmas time, and this will be my last post until AFTER Christmas (hopefully).

I wrote the following in **000-default **configuration file. Some of them are there because I didn't see them in apache.conf, but I have to check **envvars** and **ports.conf**

```

[FONT=Fixedsys]
[/FONT] [FONT=Courier New][FONT=Fixedsys]<VirtualHost 192.168.1.80>

    ServerName phpweb20
    ServerAdmin webmaster@localhost

    DocumentRoot /var/www/phpweb20/htdocs

    <Directory /var/www/phpweb20/htdocs>
        AllowOverride All
        Options All
    </Directory>

    <Directory />
    Options FollowSymLinks
    AllowOverride None
        Order deny,allow
        Deny from all
    </Directory>

#    <Directory /var/www/>
#        Options Indexes FollowSymLinks MultiViews
#        AllowOverride None
#        Order allow,deny
#        allow from all
#        </Directory>

    <IfModule dir_module>
        DirectoryIndex index.php index.html
        </IfModule>

    <FilesMatch "^\.ht">
        Order allow,deny
        Deny from all
        Satisfy All
    </FilesMatch>

    ErrorLog /var/log/apache2/error.log

#   Possible values include: debug, info, notice, warn, error, crit,
#   alert, emerg.

    LogLevel warn

    CustomLog /var/log/apache2/access.log combined

    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory "/usr/lib/cgi-bin">
    AllowOverride None
    Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
    Order allow,deny
    Allow from all
    </Directory>

    <IfModule mime_module>
        TypesConfig conf/mime.types

        AddType application/x-compress .Z
        AddType application/x-gzip .gz .tgz

        AddType application/x-httpd-php .php
        AddType application/x-httpd-php-source .phps
        </IfModule>

#    Alias /doc/ "/usr/share/doc/"
#    <Directory "/usr/share/doc/">
#        Options Indexes MultiViews FollowSymLinks
#        AllowOverride None
#        Order deny,allow
#        Deny from all
#        Allow from 127.0.0.0/255.0.0.0 ::1/128
#        </Directory>

    php_value include_path .:/var/www/phpweb20/include:/usr/local/lib/php/PEAR
    php_value magic_quotes_gpc off
    php_value register_globals off

</VirtualHost>[/FONT]                    

[/FONT] 
```I am now able to restart the server with only these warnings:

```

[FONT=Fixedsys] ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sat Dec 24 17:58:38 2011] [warn] NameVirtualHost *:80 has no VirtualHosts[/FONT]

```

I don't really understand the severity of the warnings.
Also, I don't know whether I should out-comment the "Alias" paragraph, which at present is commented.

Merry Christmas !

[COLOR=Red][B][SIZE=3]Thanks a lot Lars, for your support the whole day.
[/SIZE][/B][/COLOR]
[/SIZE]

---

### Post by Lars Noodén on 2011-12-24
Warnings are just that, warnings.  If the site continues to work then you're fine -- at least at the novice level.  The first warning is because you don't have an official domain name registered for your site in DNS.  When you're working on a real server you'd want to fix those, but for right now it's not a big deal.  Here's the page on Name-based virtual hosts, but as said, it's not a worry right now:
[http://httpd.apache.org/docs/2.3/vhosts/name-based.html](http://httpd.apache.org/docs/2.3/vhosts/name-based.html)

The line [font=Courier New]Alias /doc/ "/usr/share/doc/"[/font] and the lines below it make it so you can look up documentation at the URL [http://localhost/doc/](http://localhost/doc/).  The lines as you can see give read permission to the documentation directory.

You might also be interested in [man2html](http://packages.ubuntu.com/oneiric/man2html) to be able to serve up the system's manual pages via your web server.

Merry Christmas!  Enjoy playing with Apache, it's fun to use.

---

