---
title: "/etc/httpd.conf': No such file or directory"
date: 2011-05-19
forum: Server Platforms
---

### Post by koshiuk on 2011-05-19
Hi,

I'm on the verge of setting up a webserver on my newly installed ubuntu desktop 11.04.  I've done the dyndns, port forwarding ok and get a index / page when i access my URL.

i only installed apache2, and since then found out about LAMP, so installed the following:

        sudo apt-get install php5 
         sudo apt-get install mysql-server 

Then i've followed the link
[http://www.easy-ubuntu-linux.com/apache-modules-ubuntu-configuration-2.html](http://www.easy-ubuntu-linux.com/apache-modules-ubuntu-configuration-2.html)

I got as far as backing up my .conf file using:

          sudo cp /etc/httpd.conf /etc/httpd.conf_backup

and now it says 

cp: cannot stat `/etc/httpd.conf': No such file or directory

I've restarted apache and now get this:
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName



HELP PLEASE!!!

---

### Post by mhgsys on 2011-05-19
read the link a little closer 
> Apache on Ubuntu has two main configuration files: apache2.conf and httpd.conf. Both are found in the directory '/etc/apache2'

so...
 ```
sudo cp /etc/apache2/httpd.conf /etc/apache2/httpd.conf_backup
```

edit; Also the error; apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
will be solved for you following the rest of your link,. as that problem is solved by adding ServerName localhost in the /etc/apache2/httpd.conf your gonna edit

---

### Post by koshiuk on 2011-05-19
Many thanks for that....appreciated.

getting this now

gav@ThinkPadT61:/etc/apache2$ sudo /etc/init.d/apache2 restart
Syntax error on line 1 of /etc/apache2/httpd.conf:
Invalid command 'Userdir', perhaps misspelled or defined by a module not included in the server configuration
Action 'configtest' failed.
The Apache error log may have more information.
   ...fail!

-------------------------------------------------
/etc/apache2/httpd.conf


Userdir public_html
Options +Indexes
Options All

ServerName localhost

<Directory "/home/gav/public_html/">
Order allow,deny
Allow from all
AllowOverride All
</Directory>

---

### Post by mhgsys on 2011-05-19
[quote=koshiuk]Invalid command 'Userdir', perhaps misspelled or defined by a module not included in the server configuration
Action 'configtest' failed.[/quote]

> **By default, Apache on Ubuntu does not allow the use of user directories (enabled by the UserDir module)**
> After installing Apache, you will want to ensure a few modules are available to process programs and to ease the development and maintenance of your website. A module is an extension that enables the server to handle more advanced programming. **Some modules are installed by default as a matter of course, and others may be installed separately.**

On Ubuntu, **the configuration files for Apache are held in the directory '/etc/apache2**'. **To learn what is supported by the web server, visit '/mods-enabled**'. There several files with a suffix of '.load' are listed. These are the modules themselves, and their configuration files are in the corresponding '.conf' files.

Some of the basic modules that come with Ubuntu's installation of Apache:

    * alias
    * autoindex
    * cgi
    * dir
    * env
    * mime
    * negotiation
    * status 

This may seem a bit sparse, and it is. **To see which modules are available, see the corresponding 'mods-available' directory (/etc/apache2/mods-available). Here you will find a list of all the modules that can be enabled.** 

I bet you forgot to enable the module

---

### Post by tapi0n on 2011-05-19
> By default, Apache on Ubuntu does not allow the use of user directories (enabled by the UserDir module)

Sorry to go off topic, but this could also be the cause of a problem with VirtualHosts ?

---

### Post by mhgsys on 2011-05-19
I'm in a nice mood so I reproduced the error using the same conf file
> mhg@mhg-laptop:/etc/apache2/mods-enabled$ sudo service apache2 start
 * Starting web server apache2                                                  Syntax error on line 1 of /etc/apache2/httpd.conf:
Invalid command 'Userdir', perhaps misspelled or defined by a module not included in the server configuration
                                                                         [fail]


so...
```
sudo a2enmod
``` (you could do a sudo a2enmod userdir, but this way you know how to see the available modules)
> Your choices are: actions alias asis auth_basic auth_digest authn_alias authn_anon authn_dbd authn_dbm authn_default authn_file authnz_ldap authz_dbm authz_default authz_groupfile authz_host authz_owner authz_user autoindex cache cern_meta cgi cgid charset_lite dav dav_fs dav_lock dbd deflate dir disk_cache dump_io env expires ext_filter file_cache filter headers ident imagemap include info ldap log_forensic mem_cache mime mime_magic negotiation php5 proxy proxy_ajp proxy_balancer proxy_connect proxy_ftp proxy_http proxy_scgi reqtimeout rewrite setenvif speling ssl status substitute suexec unique_id userdir usertrack version vhost_alias
Which module(s) do you want to enable (wildcards ok)?
**userdir**
Enabling module userdir. Run '/etc/init.d/apache2 restart' to activate new configuration!

> mhg@mhg-laptop:/etc/apache2/mods-enabled$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                         [ OK ] 

seems to work ; and dubble-checked it works
> mhg@mhg-laptop:/etc/apache2/mods-enabled$ sudo /etc/init.d/apache2 force-reload
 * Reloading web server config apache2       
mhg@mhg-laptop:/etc/apache2/mods-enabled$ sudo /etc/init.d/apache2 stop
 * Stopping web server apache2                                                   ... waiting                                                     [ OK ]
mhg@mhg-laptop:/etc/apache2/mods-enabled$ sudo /etc/init.d/apache2 start
 * Starting web server apache2                                           [ OK ] 


---

### Post by koshiuk on 2011-05-19
wow thanks..... great help again :)

---

### Post by mhgsys on 2011-05-19
your welcome, although perhaps it might be a good idea to start reading things a little closer before beginning configurating it

although the countless times I messed up something while half reading,the errors my mistakes returned, and the nights I used to spend to understand it correctly  finally paid off (a little)

---

### Post by koshiuk on 2011-05-19
yeh forgot the module.... doh  all working now, thanks mate

---

### Post by mhgsys on 2011-05-19
again ; your welcome
don't forget to mark your thread as solved
(it will save some time for people on the forum not reading this thread wanting to help)

---

### Post by koshiuk on 2011-05-19
> **mhgsys said:**
> your welcome, although perhaps it might be a good idea to start reading things a little closer before beginning configurating it

although the countless times I messed up something while half reading,the errors my mistakes returned, and the nights I used to spend to understand it correctly  finally paid off (a little)


true true... i do tend to give it a go before reading much and just scan over things, installed ubuntu few days ago.....  was going to get a mac as bored of windowzzz, but decided on ubuntu, thought id get back into a bit of command line action.

---

### Post by mhgsys on 2011-05-19
Yes; good choice, it's so nice to have a OS that allows you to screw it all up, and does not screw things up for you
(well ok, sometimes a little maybe)

linux is great!, I have 6 machines here booting linux, (5 Ubuntu 1 Debian) and they never fail me.. 

although it took me some time configuring what I wanted with them , 
xbmc,lirc,sane scannersharing , printersharing, pxe boot, plop boot,isoboot, wine,dosbox, apache2, ssh, rutorrent, nagios, darkstat, samba, uuid mounts in fstab, motion detection, and everything I might have forgot to write down all work great.

you sir, should never switch to anything else but linux

---

