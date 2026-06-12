---
title: "apache help"
date: 2007-06-23
forum: Server Platforms
---

### Post by aeleneski on 2007-06-23
Hi guys, I am trying to get apache2 setup on my machine and am having difficulty.  First off, it did not start at boot time, so I went and did sudo apache2 -k start and I got this output:

> 
[Sat Jun 23 13:48:02 2007] [warn] module authn_file_module is already loaded, skipping
[Sat Jun 23 13:48:02 2007] [warn] module authz_host_module is already loaded, skipping
[Sat Jun 23 13:48:02 2007] [warn] module authz_groupfile_module is already loaded, skipping
[Sat Jun 23 13:48:02 2007] [warn] module authz_user_module is already loaded, skipping
[Sat Jun 23 13:48:02 2007] [warn] module authz_default_module is already loaded, skipping
[Sat Jun 23 13:48:02 2007] [warn] module auth_basic_module is already loaded, skipping
[Sat Jun 23 13:48:02 2007] [warn] module env_module is already loaded, skipping
[Sat Jun 23 13:48:02 2007] [warn] module setenvif_module is already loaded, skipping
[Sat Jun 23 13:48:02 2007] [warn] module mime_module is already loaded, skipping
[Sat Jun 23 13:48:02 2007] [warn] module dav_module is already loaded, skipping
[Sat Jun 23 13:48:02 2007] [warn] module status_module is already loaded, skipping
[Sat Jun 23 13:48:02 2007] [warn] module autoindex_module is already loaded, skipping
[Sat Jun 23 13:48:02 2007] [warn] module cgi_module is already loaded, skipping
[Sat Jun 23 13:48:02 2007] [warn] module negotiation_module is already loaded, skipping
[Sat Jun 23 13:48:02 2007] [warn] module dir_module is already loaded, skipping
[Sat Jun 23 13:48:02 2007] [warn] module alias_module is already loaded, skipping
[Sat Jun 23 13:48:02 2007] [warn] module rewrite_module is already loaded, skipping
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs


How to I fix this?

---

### Post by jtc on 2007-06-23
Are you sure Apache didn't already start? Because that looks exactly like the kind of errors you would get trying to start an already running Apache.

---

### Post by aeleneski on 2007-06-23
Yes, becasue if I do stop instead of start I get:

> [Sat Jun 23 14:31:18 2007] [warn] module authn_file_module is already loaded, skipping
[Sat Jun 23 14:31:18 2007] [warn] module authz_host_module is already loaded, skipping
[Sat Jun 23 14:31:18 2007] [warn] module authz_groupfile_module is already loaded, skipping
[Sat Jun 23 14:31:18 2007] [warn] module authz_user_module is already loaded, skipping
[Sat Jun 23 14:31:18 2007] [warn] module authz_default_module is already loaded, skipping
[Sat Jun 23 14:31:18 2007] [warn] module auth_basic_module is already loaded, skipping
[Sat Jun 23 14:31:18 2007] [warn] module env_module is already loaded, skipping
[Sat Jun 23 14:31:18 2007] [warn] module setenvif_module is already loaded, skipping
[Sat Jun 23 14:31:18 2007] [warn] module mime_module is already loaded, skipping
[Sat Jun 23 14:31:18 2007] [warn] module dav_module is already loaded, skipping
[Sat Jun 23 14:31:18 2007] [warn] module status_module is already loaded, skipping
[Sat Jun 23 14:31:18 2007] [warn] module autoindex_module is already loaded, skipping
[Sat Jun 23 14:31:18 2007] [warn] module cgi_module is already loaded, skipping
[Sat Jun 23 14:31:18 2007] [warn] module negotiation_module is already loaded, skipping
[Sat Jun 23 14:31:18 2007] [warn] module dir_module is already loaded, skipping
[Sat Jun 23 14:31:18 2007] [warn] module alias_module is already loaded, skipping
[Sat Jun 23 14:31:18 2007] [warn] module rewrite_module is already loaded, skipping
httpd (no pid file) not running

Or with restart I get the same type of errors.

---

### Post by hockey97 on 2007-06-23
try using the stop command.

and then put start command.

and see what happen's if it dosne't work.

then did you when typing in the terminal type the  dir address.

like /etc/ini.d/apache2 -k start??

if you didn't do that then try that becuse it's supposed to be like that.

I am not sure where the apache2.exe is to control the stop and start and restart.

But you need that whole dir address.

if you got that and still not working.

then turn off everything meaning every  server you have installed like bind9  ect.

and then first start apache 2 and then starthe other servers.

becuse some other servers may be using those modules  and can be running already.

if it still dosent work then try reinstalling it or try and install webmin

it would make it much more easier to do, since it's a gui for all stuff on your ubunut. 

I had the same problem how I cleared it was to remove every part of those error's

I copied and paste all the names of thos modules and put it in a writing program like note pad,  

I then type in the terminal sudo apt-get autoremove (then the names here)  

then I reinstalled it, that's usally the case if you had a previous install of apache and had also another apache server install and running only one would run.

but try these things hope this helps.

If all fails I suggest really to reintall ubuntu or what ever your OS version is . 

I had some problems with apache2 a month ago and never figured out what happened.

So I uninstalled my OS version and install a fresh new installation.

and apache2 really worked .


But try deleting all those modulers and install them again , to me look's like thos modules are already running before apache and having some convlict's.

it look's to me somthing is conflicting or you have another verison of apache server that didn't remove and still is running and run's at boot ect.

---

### Post by aeleneski on 2007-06-23
Ok, I uninstalled and then reinstalled apache.  So now when it starts up it seems to be working.  But now I am having problems with php.  I just create a test php file, with <? phpinfo(); ?> in it  and when I click on it to test php, I get a download file popup.  

I have installed: libapache2-mod-php5 and php5

But when I go to do this: sudo a2enmod php5

I get "This module does not exist!".

And I do not see it anywhere in the mods-enabled or mods-available directories.

---

### Post by aeleneski on 2007-06-23
Ok, I got php working.  I had to add this to my apache2.conf file:

LoadModule php5_module       /usr/lib/apache2/modules/libphp5.so


But now I am having problems with the subversion module.  When trying to install I get:

Setting up libapache2-svn (1.4.3dfsg1-1ubuntu1) ...
This module does not exist!
dpkg: error processing libapache2-svn (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 libapache2-svn
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by hockey97 on 2007-06-23
When you uninstalled apache2 did you do it by sudo apt-get autoremove (file modules names here)
, try deleting that module if you had it installed and reinstall it by redownloading it, this has happened to me before, something is conflicting with those files, and the thing that is conflicting it you must reinstall it.
To me I would delete every module that you installed for the servers ect, and even apache2 and install them back in with a fresh new download of them. But make sure you remove all the files becuse if you use remove command thing in the terminal it dosent' alway's remove everything, it leaves some file behind and could conflict with other files or a reinstalltion could get messed up somewhere.

I can't fully help you if  you had to do some configs for that portation to work.

Hope someone else with a bit of more apache2 experiance could help.

---

