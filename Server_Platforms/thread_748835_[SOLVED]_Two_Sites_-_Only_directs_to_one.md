---
title: "[SOLVED] Two Sites - Only directs to one"
date: 2008-04-07
forum: Server Platforms
---

### Post by yodomino6 on 2008-04-07
I know this has been in other threads but I still cannot seem to find an answer.

I am trying to host 2 web sites on one server and for some reason whichever domain you go to, it only takes to to one of the sites. That is unless you specify the file. (i.e. add '/index.html' to the end.)

Please help! Thanks!

---

### Post by hyperlobic on 2008-04-08
What does your httpd.conf file look like?

---

### Post by yodomino6 on 2008-04-08
It's currently blank, but I've had it set up several different ways. Right now I set them up as 'New file under virtual servers directory /etc/apache2/sites-available'. But if I set them up in the httpd.conf file it looks like this:

```
<VirtualHost *:80>
DocumentRoot "/var/www/site1"
ServerName site1.com
<Directory "/var/www/site1">
allow from all
Options +Indexes
</Directory>
</VirtualHost>

<VirtualHost *:80>
DocumentRoot "/var/www/site2"
ServerName site2.com
<Directory "/var/www/site2">
allow from all
Options +Indexes
</Directory>
</VirtualHost>
```

---

### Post by yodomino6 on 2008-04-09
Nobody has any ideas?

---

### Post by subzero06 on 2008-04-09
ok, i think the problem is bcus you have them in the same directory

make one site in /var/www/site1/site_two_files
and the other in /var/www/site2/site_two files

or create a new user and its folder and set virtual host to that location :
ex:

/home/www/user1/siteone/
/home/www/user2/sitetwo/

and restart apache.

---

### Post by yodomino6 on 2008-04-10
That is how it is set up, but it still wont work. I even reinstalled my whole system. This problem is starting to frustrate me!

Anyone with any ideas?

---

### Post by yodomino6 on 2008-04-10
I must be setting it up wrong.

When I create the Virtual Host, which do I choose?
Standard httpd.conf file
New file under virtual servers directory /etc/apache2/sites-available
or
Selected file..?

Also should there be a Per-Directory, and what is it?

Thanks in advance for your help!

---

### Post by subzero06 on 2008-04-10
> **yodomino6 said:**
> I must be setting it up wrong.

When I create the Virtual Host, which do I choose?
Standard httpd.conf file
New file under virtual servers directory /etc/apache2/sites-available
or
Selected file..?

Also should there be a Per-Directory, and what is it?

Thanks in advance for your help!

select new file

---

### Post by Wim Sturkenboom on 2008-04-11
Have you enabled name-based virtual hosts ? You should have a line *NameVirtualHost* somehwere in your apache configuration files

I'm not familiar with the Ubuntu way of doing things so can not further advise.

---

### Post by shane2peru on 2008-04-11
> **yodomino6 said:**
> It's currently blank, but I've had it set up several different ways. Right now I set them up as 'New file under virtual servers directory /etc/apache2/sites-available'. But if I set them up in the httpd.conf file it looks like this:

```
<VirtualHost *:80>
DocumentRoot "/var/www/site1"
ServerName site1.com
<Directory "/var/www/site1">
allow from all
Options +Indexes
</Directory>
</VirtualHost>

<VirtualHost *:80>
DocumentRoot "/var/www/site2"
ServerName site2.com
<Directory "/var/www/site2">
allow from all
Options +Indexes
</Directory>
</VirtualHost>
```
I know absolutely nothing about this. :lolflag:  However, I do know about web pages, and htmlcoding. :)    According to this file, it seems as though you have them in the same directory, and you need a '/'  after site1 and after site2 to make them two different sites.  Web pages automatically open the index.html site of any folder that it is pointed to.  That is a basic rule of html-ing.  It just seems as though this file is pointing to the same directory for both sites, just my 2 cents worth.  I stumbled across this hoping to find answers on how to set this up, because I would like to do something like this too.

Shane

---

### Post by yodomino6 on 2008-04-11
You're 100% correct, but I've tried many many different ways, and that doesn't seem to make a difference.

To help you more, I found this in my apache2.conf file:
```
# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/
<VirtualHost *:80>
DocumentRoot "/var/www/**site1**/"
ServerName **site1.com**
<Directory "/var/www/**site1**/">
allow from all
Options +Indexes
</Directory>
<Location "/var/www/**site1**/">
</Location>
</VirtualHost>
<VirtualHost *:80>
DocumentRoot "/var/www/**site2**/"
ServerName **site2.com**
<Directory "/var/www/**site2**/">
allow from all
Options +Indexes
</Directory>
<Location "/var/www/**site2**/">
</Location>
</VirtualHost>

```

I added the Location thinking it might help but didn't. Anybody notice anything missing?

---

### Post by shane2peru on 2008-04-11
> **yodomino6 said:**
> You're 100% correct, but I've tried many many different ways, and that doesn't seem to make a difference.

To help you more, I found this in my apache2.conf file:
```
# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/
<VirtualHost [COLOR="Red"]*[/COLOR]:80>
DocumentRoot "/var/www/**site1**/"
ServerName **site1.com**
<Directory "/var/www/**site1**/">
allow from all
Options +Indexes
</Directory>
<Location "/var/www/**site1**/">
</Location>
</VirtualHost>
<VirtualHost [COLOR="Red"]*[/COLOR]:80>
DocumentRoot "/var/www/**site2**/"
ServerName **site2.com**
<Directory "/var/www/**site2**/">
allow from all
Options +Indexes
</Directory>
<Location "/var/www/**site2**/">
</Location>
</VirtualHost>

```

I added the Location thinking it might help but didn't. Anybody notice anything missing?

This is only a guess because as I stated before, I really don't know anything about this, I'm stumbling through this with you and hope to be able to replicate your setup! :)  What I'm thinking is that you need to replace the * that I made red with 1.  an ip number, or 2.  better yet, probably the domain name like:  mydomain.dnydns.com:80  That way it would know to point that domain to the directory pointed out, and then the other domain name would be pointed to the other directory.  Like I said this is only a hunch, but worth a try.

Shane

---

### Post by rickyjones on 2008-04-11
I have a single server that is hosting about 10 internal websites. Each website is accessible via its own CNAME through DNS.

I will post a few of my virtual host files and a directory listing and you should be able to base your configuration on mine.

First and foremost I do not host my sites in /var/www. I use a different directory.

```

root@vm-webserver:/# ls -l | grep "data"
drwxrwxrwx  4 root root  4096 2008-02-22 14:02 data
root@vm-webserver:/#

```

Here is a directory listing of the sites that I host:
```

root@vm-webserver:/# ls -l /data/http/
total 100
drwxrwxrwx  2 nobody   nogroup  4096 2007-12-21 15:13 authentication_system
drwxrwxrwx  5 nobody   nogroup  4096 2007-12-21 16:42 cms
drwxrwxrwx  9 nobody   nogroup  4096 2007-11-23 16:38 drupal
drwxrwxrwx  5 nobody   nogroup  4096 2007-12-21 11:55 employeedb
drwxr-xr-x  6 nobody   nogroup  4096 2008-03-21 15:39 fais
drwxrwxrwx 10 root     root     4096 2007-10-19 15:51 faq
drwxrwxrwx 14 root     root     4096 2007-10-19 15:59 _flyspray
drwxrwxrwx  3 root     root     4096 2008-03-07 10:35 fusionautogr.com
drwxrwxrwx  6 root     root     4096 2007-12-27 09:41 fusion_inventory
drwxrwxrwx  2 root     root     4096 2007-11-16 14:54 help
drwxrwxrwx  7 nobody   nogroup  4096 2008-04-01 15:51 intense
drwxrwxrwx 10 root     root     4096 2007-10-19 15:52 inventory
drwxrwxrwx  6 richard  richard  4096 2007-11-16 10:55 ios
drwxrwxrwx  5 nobody   nogroup  4096 2008-01-02 10:54 issues
drwxrwxrwx  2 sysadmin sysadmin 4096 2007-10-30 08:51 issues-dev
drwxrwxrwx 14 nobody   nogroup  4096 2007-11-15 17:46 joomla_test
drwxrwxrwx 12 www-data www-data 4096 2006-12-19 12:30 _phpBB2
drwxrwxrwx 12 nobody   nogroup  4096 2007-10-26 09:53 _phpBB2 (copy)
drwxrwxrwx  5 nobody   nogroup  4096 2008-03-21 17:04 rrcc_tt
drwxrwxrwx  2 nobody   nogroup  4096 2007-11-15 09:14 _SYNCAPP
drwxrwxrwx 13 root     root     4096 2007-10-19 16:02 tt
drwxrwxrwx 13 nobody   nogroup  4096 2007-11-01 11:14 tt_backup
drwxrwxrwx  4 root     root     4096 2007-11-30 09:29 zzp
drwxrwxrwx 14 nobody   nogroup  4096 2008-04-11 10:46 zzp_store_testing
drwxr-xr-x  4 nobody   nogroup  4096 2008-01-25 13:51 zzp_web_custom_scripts
root@vm-webserver:/#

```

Here is a directory listing of my **/etc/apache2/sites-available** directory:
```

root@vm-webserver:/etc/apache2/sites-available# ls -l
total 156
-rw-r--r-- 1 root root 1241 2007-12-21 15:16 cms
-rw-r--r-- 1 root root 1281 2007-12-21 15:17 cms.zzperformance.local
-rw-r--r-- 1 root root 1262 2007-10-19 15:48 default
-rw-r--r-- 1 root root 1253 2007-11-23 16:54 drupal
-rw-r--r-- 1 root root 1293 2007-11-23 16:54 drupal.zzperformance.local
-rw-r--r-- 1 root root 1269 2007-12-13 16:17 employeedb
-rw-r--r-- 1 root root 1309 2007-12-13 16:18 employeedb.zzperformance.local
-rw-r--r-- 1 root root 1245 2008-03-07 10:37 fais
-rw-r--r-- 1 root root 1285 2008-03-07 10:38 fais.zzperformance.local
-rw-r--r-- 1 root root 1241 2007-11-16 14:57 faq
-rw-r--r-- 1 root root 1281 2007-11-16 14:56 faq.zzperformance.local
-rw-r--r-- 1 root root 1292 2008-02-21 17:09 fusionautogr.com
-rw-r--r-- 1 root root 1279 2007-11-16 14:58 fusioninv
-rw-r--r-- 1 root root 1319 2007-11-16 14:57 fusioninv.zzperformance.local
-rw-r--r-- 1 root root 1243 2007-11-16 14:53 help
-rw-r--r-- 1 root root 1283 2007-11-16 14:52 help.zzperformance.local
-rw-r--r-- 1 root root 1257 2008-03-07 10:20 immense
-rw-r--r-- 1 root root 1297 2008-03-07 10:20 immense.zzperformance.local
-rw-r--r-- 1 root root 1258 2007-11-16 15:04 inventory
-rw-r--r-- 1 root root 1298 2007-11-16 14:56 inventory.zzperformance.local
-rw-r--r-- 1 root root 1241 2007-11-16 15:05 ios
-rw-r--r-- 1 root root 1281 2007-11-16 14:56 ios.zzperformance.local
-rw-r--r-- 1 root root 1253 2007-11-16 15:05 issues
-rw-r--r-- 1 root root 1309 2007-10-26 11:21 issues-dev
-rw-r--r-- 1 root root 1293 2007-11-16 14:56 issues.zzperformance.local
-rw-r--r-- 1 root root 1303 2007-11-15 17:34 joomla
-rw-r--r-- 1 root root 1258 2008-03-06 16:26 rrcc_tt
-rw-r--r-- 1 root root 1298 2008-03-06 16:27 rrcc_tt.zzperformance.local
-rw-r--r-- 1 root root 1269 2008-02-26 15:51 store_test
-rw-r--r-- 1 root root 1309 2008-02-26 15:52 store_test.zzperformance.local
-rw-r--r-- 1 root root 1237 2007-11-16 15:06 tt
-rw-r--r-- 1 root root 1277 2007-11-16 14:56 tt.zzperformance.local
-rw-r--r-- 1 root root 1300 2008-02-21 17:09 www.fusionautogr.com
-rw-r--r-- 1 root root 1240 2007-11-16 14:55 zzp
-rw-r--r-- 1 root root 1298 2008-04-03 12:52 zzp_store_testing
-rw-r--r-- 1 root root 1338 2008-04-03 12:52 zzp_store_testing.zzperformance.local
-rw-r--r-- 1 root root 1317 2008-01-25 13:29 zzp_web_custom_scripts
-rw-r--r-- 1 root root 1357 2008-01-25 13:29 zzp_web_custom_scripts.zzperformance.local
-rw-r--r-- 1 root root 1280 2007-11-16 14:55 zzp.zzperformance.local
root@vm-webserver:/etc/apache2/sites-available#

```

We'll pick on my "tt.zzperformance.local" file.

Here is the contents of this file:
```

root@vm-webserver:/etc/apache2/sites-available# cat tt.zzperformance.local
NameVirtualHost tt.zzperformance.local:80
<VirtualHost tt.zzperformance.local:80>
        ServerAdmin administrator@zzperformance.com

#       DocumentRoot /var/www/
        DocumentRoot /data/http/tt/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /data/http/tt/>
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
                Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
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
root@vm-webserver:/etc/apache2/sites-available#

```

Every single one of my files look like this. I just copy/rename them and change the virtual host name and the target directories.

Once you have your file created in **/etc/apache2/sites-available** you will need to enable it.

```

a2ensite **nameoffile**

```

In the **/etc/apache2/sites-enabled** directory you should then see symlinks pointing to your files in **/etc/apache2/sites-available**.

```

root@vm-webserver:/etc/apache2/sites-enabled# ls -l
total 8
lrwxrwxrwx 1 root root 36 2007-10-19 10:55 000-default -> /etc/apache2/sites-available/default
lrwxrwxrwx 1 root root 32 2007-12-21 15:17 cms -> /etc/apache2/sites-available/cms
lrwxrwxrwx 1 root root 52 2007-12-21 15:17 cms.zzperformance.local -> /etc/apache2/sites-available/cms.zzperformance.local
lrwxrwxrwx 1 root root 35 2007-11-23 16:51 drupal -> /etc/apache2/sites-available/drupal
lrwxrwxrwx 1 root root 55 2007-11-23 16:52 drupal.zzperformance.local -> /etc/apache2/sites-available/drupal.zzperformance.local
lrwxrwxrwx 1 root root 39 2007-12-13 16:25 employeedb -> /etc/apache2/sites-available/employeedb
lrwxrwxrwx 1 root root 59 2007-12-13 16:25 employeedb.zzperformance.local -> /etc/apache2/sites-available/employeedb.zzperformance.local
lrwxrwxrwx 1 root root 33 2008-03-07 10:38 fais -> /etc/apache2/sites-available/fais
lrwxrwxrwx 1 root root 53 2008-03-07 10:38 fais.zzperformance.local -> /etc/apache2/sites-available/fais.zzperformance.local
lrwxrwxrwx 1 root root 32 2007-10-19 15:46 faq -> /etc/apache2/sites-available/faq
lrwxrwxrwx 1 root root 52 2007-11-16 14:58 faq.zzperformance.local -> /etc/apache2/sites-available/faq.zzperformance.local
lrwxrwxrwx 1 root root 45 2008-02-21 17:10 fusionautogr.com -> /etc/apache2/sites-available/fusionautogr.com
lrwxrwxrwx 1 root root 38 2007-11-16 15:03 fusioninv -> /etc/apache2/sites-available/fusioninv
lrwxrwxrwx 1 root root 58 2007-11-16 15:01 fusioninv.zzperformance.local -> /etc/apache2/sites-available/fusioninv.zzperformance.local
lrwxrwxrwx 1 root root 33 2007-11-16 14:50 help -> /etc/apache2/sites-available/help
lrwxrwxrwx 1 root root 53 2007-11-16 14:53 help.zzperformance.local -> /etc/apache2/sites-available/help.zzperformance.local
lrwxrwxrwx 1 root root 36 2008-03-07 10:21 immense -> /etc/apache2/sites-available/immense
lrwxrwxrwx 1 root root 56 2008-03-07 10:21 immense.zzperformance.local -> /etc/apache2/sites-available/immense.zzperformance.local
lrwxrwxrwx 1 root root 38 2007-10-19 15:51 inventory -> /etc/apache2/sites-available/inventory
lrwxrwxrwx 1 root root 58 2007-11-16 15:04 inventory.zzperformance.local -> /etc/apache2/sites-available/inventory.zzperformance.local
lrwxrwxrwx 1 root root 32 2007-11-08 13:52 ios -> /etc/apache2/sites-available/ios
lrwxrwxrwx 1 root root 52 2007-11-16 15:05 ios.zzperformance.local -> /etc/apache2/sites-available/ios.zzperformance.local
lrwxrwxrwx 1 root root 35 2007-10-23 11:43 issues -> /etc/apache2/sites-available/issues
lrwxrwxrwx 1 root root 39 2007-10-26 11:21 issues-dev -> /etc/apache2/sites-available/issues-dev
lrwxrwxrwx 1 root root 55 2007-11-16 15:05 issues.zzperformance.local -> /etc/apache2/sites-available/issues.zzperformance.local
lrwxrwxrwx 1 root root 35 2007-11-15 17:34 joomla -> /etc/apache2/sites-available/joomla
lrwxrwxrwx 1 root root 36 2008-03-06 16:27 rrcc_tt -> /etc/apache2/sites-available/rrcc_tt
lrwxrwxrwx 1 root root 56 2008-03-06 16:27 rrcc_tt.zzperformance.local -> /etc/apache2/sites-available/rrcc_tt.zzperformance.local
lrwxrwxrwx 1 root root 39 2008-02-26 15:52 store_test -> /etc/apache2/sites-available/store_test
lrwxrwxrwx 1 root root 59 2008-02-26 15:52 store_test.zzperformance.local -> /etc/apache2/sites-available/store_test.zzperformance.local
lrwxrwxrwx 1 root root 31 2007-10-19 15:56 tt -> /etc/apache2/sites-available/tt
lrwxrwxrwx 1 root root 51 2007-11-16 15:06 tt.zzperformance.local -> /etc/apache2/sites-available/tt.zzperformance.local
lrwxrwxrwx 1 root root 49 2008-02-21 17:10 www.fusionautogr.com -> /etc/apache2/sites-available/www.fusionautogr.com
lrwxrwxrwx 1 root root 32 2007-11-16 14:50 zzp -> /etc/apache2/sites-available/zzp
lrwxrwxrwx 1 root root 46 2008-04-03 12:53 zzp_store_testing -> /etc/apache2/sites-available/zzp_store_testing
lrwxrwxrwx 1 root root 66 2008-04-03 12:53 zzp_store_testing.zzperformance.local -> /etc/apache2/sites-available/zzp_store_testing.zzperformance.local
lrwxrwxrwx 1 root root 51 2008-01-25 13:29 zzp_web_custom_scripts -> /etc/apache2/sites-available/zzp_web_custom_scripts
lrwxrwxrwx 1 root root 71 2008-01-25 13:29 zzp_web_custom_scripts.zzperformance.local -> /etc/apache2/sites-available/zzp_web_custom_scripts.zzperformance.local
lrwxrwxrwx 1 root root 52 2007-11-16 14:55 zzp.zzperformance.local -> /etc/apache2/sites-available/zzp.zzperformance.local
root@vm-webserver:/etc/apache2/sites-enabled#

```

A lot of information to sift through but I think this will help get you on your way.

Sincerely,
Richard

---

### Post by yodomino6 on 2008-04-11
I really appreciate you trying to help me!
Ok, so I've made changes to look like this and it's still a no go, both sites go to site1.com

```
# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/
<VirtualHost **http://www.site1.com:80**>
DocumentRoot "/var/www/site1/"
ServerName site1.com
<Directory "/var/www/site1/">
allow from all
Options +Indexes
</Directory>
<Location "/var/www/site1/">
</Location>

</VirtualHost>
<VirtualHost **http://www.site2.com:80**>
DocumentRoot "/var/www/site2/"
ServerName site2.com
<Directory "/var/www/site2/">
allow from all
Options +Indexes
</Directory>
<Location "/var/www/site2/">
</Location>
</VirtualHost>
```

Is that what you meant?

---

### Post by yodomino6 on 2008-04-11
Thanks so much Richard. You're right, it is a lot to go through. More than I can do at work! I will read through it when I get home tonight and let you know why I come up with.

Thanks!!!

---

### Post by shane2peru on 2008-04-11
> **rickyjones said:**
> I have a single server that is hosting about 10 internal websites. Each website is accessible via its own CNAME through DNS.

I will post a few of my virtual host files and a directory listing and you should be able to base your configuration on mine.

First and foremost I do not host my sites in /var/www. I use a different directory.



Here is a directory listing of my **/etc/apache2/sites-available** 

A lot of information to sift through but I think this will help get you on your way.

Sincerely,
Richard
Richard can you post your apache.conf file?  I think that would be helpfull.  Or tell us how you setup your virtual server to host more than one site?

> **yodomino6 said:**
> I really appreciate you trying to help me!
Ok, so I've made changes to look like this and it's still a no go, both sites go to site1.com

```
# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/
<VirtualHost **http://www.site1.com:80**>
DocumentRoot "/var/www/site1/"
ServerName site1.com
<Directory "/var/www/site1/">
allow from all
Options +Indexes
</Directory>
<Location "/var/www/site1/">
</Location>

</VirtualHost>
<VirtualHost **http://www.site2.com:80**>
DocumentRoot "/var/www/site2/"
ServerName site2.com
<Directory "/var/www/site2/">
allow from all
Options +Indexes
</Directory>
<Location "/var/www/site2/">
</Location>
</VirtualHost>
```

Is that what you meant?

That is what I meant, however you may need to drop the www depending on how you are setup.  For example, my setup with dyndns.com will not allow me to use the www part unless I set it for wildcards.  In other words, [http://www.rices.homelinux.com](http://www.rices.homelinux.com)  doesn't reach my site, but [http://rices.homelinux.com](http://rices.homelinux.com) does.  It is a matter of [www.dyndns.com](www.dyndns.com) setup.  Or perhaps you only need the domain name, like rices.homelinux.com:80  and that incoming domain name would be sent to the correct location.  

Shane

---

### Post by yodomino6 on 2008-04-11
ok ok ok ok ok. This is not perfect but it's a step in the right direction. if I type in [http://site2.com](http://site2.com) it takes me to site2, but if I type in [www.site2.com](www.site2.com), it takes me to site1.

So basically heres' the rundown, what you get when you type:
site1.com  ->  site1
[www.site1.com](www.site1.com)  ->  site1
site2.com  ->  site2
[www.site2.com](www.site2.com)  ->  site1

And here is the current setup:
```
# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/
<VirtualHost www.site1.com:80>
DocumentRoot "/var/www/site1/"
ServerName site1.com
<Directory "/var/www/site1/">
allow from all
Options +Indexes
</Directory>
<Location "/var/www/site1/">
</Location>
</VirtualHost>
<VirtualHost www.site2.com:80>
DocumentRoot "/var/www/site2/"
ServerName site2.com
<Directory "/var/www/site2/">
allow from all
Options +Indexes
</Directory>
<Location "/var/www/site2/">
</Location>
</VirtualHost>

```

It was without the 'www.' after VirtualHost, but I added it after I discovered this, still the same.

---

### Post by shane2peru on 2008-04-11
> **yodomino6 said:**
> ok ok ok ok ok. This is not perfect but it's a step in the right direction. if I type in [http://site2.com](http://site2.com) it takes me to site2, but if I type in [www.site2.com](www.site2.com), it takes me to site1.

So basically heres' the rundown, what you get when you type:
site1.com  ->  site1
[www.site1.com](www.site1.com)  ->  site1
site2.com  ->  site2
[www.site2.com](www.site2.com)  ->  site1

And here is the current setup:
```
# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/
<VirtualHost www.site1.com:80>
DocumentRoot "/var/www/site1/"
ServerName site1.com
<Directory "/var/www/site1/">
allow from all
Options +Indexes
</Directory>
<Location "/var/www/site1/">
</Location>
</VirtualHost>
<VirtualHost www.site2.com:80>
DocumentRoot "/var/www/site2/"
ServerName site2.com
<Directory "/var/www/site2/">
allow from all
Options +Indexes
</Directory>
<Location "/var/www/site2/">
</Location>
</VirtualHost>

```

It was without the 'www.' after VirtualHost, but I added it after I discovered this, still the same.

Ok, then what I'm thinking is this doesn't necesarily have to do with your apache setup, I think it probably has to do with how your domain names are setup.  I don't have a good grasp on those things yet either.  :lolflag:  are you using dyndns.com?  Do you have two separate domain names or are they based off of each other, ie: site1.com    and site2.site1.com  ?   How are they setup?  This is going to determine where they are coming from.  At least this what I'm thinking.  Once again, shooting in the dark here.

Shane

---

### Post by yodomino6 on 2008-04-11
No, because I currently host them on a Windows 2003 Server. I haven't changed any dns settings, I just change my router settings to go to my Ubuntu box instead. When I am done working on it I switch back and they work fine.
I host them through NameSecure.com.

My sites are just [www.site1.com](www.site1.com) and [www.site2.com](www.site2.com)

---

### Post by shane2peru on 2008-04-11
> **yodomino6 said:**
> No, because I currently host them on a Windows 2003 Server. I haven't changed any dns settings, I just change my router settings to go to my Ubuntu box instead. When I am done working on it I switch back and they work fine.
I host them through NameSecure.com.

My sites are just [www.site1.com](www.site1.com) and [www.site2.com](www.site2.com)

hmm, I'm not sure about that.  I'm working off a different system.  WE are on the right track as far as the [www.site1.com](www.site1.com) and site2.com without the www.  I really wish I knew more about it to help you more.  At least we are pointed in the right direction.   :KS  Hopefully a knowledgeable person will read this and post the answer. :D

Shane

---

### Post by yodomino6 on 2008-04-11
> **shane2peru said:**
> hmm, I'm not sure about that.  I'm working off a different system.  WE are on the right track as far as the [www.site1.com](www.site1.com) and site2.com without the www.  I really wish I knew more about it to help you more.  At least we are pointed in the right direction.   :KS  Hopefully a knowledgeable person will read this and post the answer. :D

Shane

Thanks SO MUCH for helping me!!!!!!!! Yes, hopefully somebody can take me all the way!

---

### Post by cdenley on 2008-04-11
You need to use ServerAlias
```

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/
<VirtualHost www.site1.com:80>
DocumentRoot "/var/www/site1/"
ServerName site1.com
**ServerAlias www.site1.com**
<Directory "/var/www/site1/">
allow from all
Options +Indexes
</Directory>
<Location "/var/www/site1/">
</Location>
</VirtualHost>
<VirtualHost www.site2.com:80>
DocumentRoot "/var/www/site2/"
ServerName site2.com
**ServerAlias www.site2.com**
<Directory "/var/www/site2/">
allow from all
Options +Indexes
</Directory>
<Location "/var/www/site2/">
</Location>
</VirtualHost>

```

---

### Post by yodomino6 on 2008-04-11
> **cdenley said:**
> You need to use ServerAlias
```

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/
<VirtualHost www.site1.com:80>
DocumentRoot "/var/www/site1/"
ServerName site1.com
**ServerAlias www.site1.com**
<Directory "/var/www/site1/">
allow from all
Options +Indexes
</Directory>
<Location "/var/www/site1/">
</Location>
</VirtualHost>
<VirtualHost www.site2.com:80>
DocumentRoot "/var/www/site2/"
ServerName site2.com
**ServerAlias www.site2.com**
<Directory "/var/www/site2/">
allow from all
Options +Indexes
</Directory>
<Location "/var/www/site2/">
</Location>
</VirtualHost>

```

WHERE HAVE YOU BEEN ALL MY LIFE?! I can finally sleep tonight!!

THANK YOU THANK YOU THANK YOU!!!!!:)

---

### Post by shane2peru on 2008-04-11
> **yodomino6 said:**
> WHERE HAVE YOU BEEN ALL MY LIFE?! I can finally sleep tonight!!

THANK YOU THANK YOU THANK YOU!!!!!:)

yodomino6, Glad you got it!  Can you explain or share what howto you followed?  I have been tinkering with this, and can't get it! :lolflag:  Even after reading all this!  I have been trying webadmin, and thought that would be easier, however I think just direct editing of my config files would be the best method.

Shane

---

### Post by yodomino6 on 2008-04-11
> **shane2peru said:**
> yodomino6, Glad you got it!  Can you explain or share what howto you followed?  I have been tinkering with this, and can't get it! :lolflag:  Even after reading all this!  I have been trying webadmin, and thought that would be easier, however I think just direct editing of my config files would be the best method.

Shane

Not sure what did what, but here are my config files now. I re-created the Virtual Hosts to "New file under virtual servers directory /etc/apache2/sites-available"

So each site has a different file. This is what I have for site1:
```
<VirtualHost *:80>
DocumentRoot "/var/www/site1/"
ServerName site1.com
<Directory "/var/www/site1/">
allow from all
Options +Indexes
</Directory>
</VirtualHost>
```
I didn't put ServerAlias in that because that one was working, but I suppose if you want to be safe, it couldn't hurt.
Here is site2:
```
<VirtualHost *:80>
DocumentRoot "/var/www/site2/"
ServerName site2.com
ServerAlias www.site2.com
<Directory "/var/www/site2/">
allow from all
Options +Indexes
</Directory>
</VirtualHost>
```

But I will say that the ServerAlias command was key to success. Though I couldn't have done it without your help either!

---

### Post by shane2peru on 2008-04-11
> **yodomino6 said:**
> Not sure what did what, but here are my config files now. I re-created the Virtual Hosts to "New file under virtual servers directory /etc/apache2/sites-available"

So each site has a different file. This is what I have for site1:
```
<VirtualHost *:80>
DocumentRoot "/var/www/site1/"
ServerName site1.com
<Directory "/var/www/site1/">
allow from all
Options +Indexes
</Directory>
</VirtualHost>
```
I didn't put ServerAlias in that because that one was working, but I suppose if you want to be safe, it couldn't hurt.
Here is site2:
```
<VirtualHost *:80>
DocumentRoot "/var/www/site2/"
ServerName site2.com
ServerAlias www.site2.com
<Directory "/var/www/site2/">
allow from all
Options +Indexes
</Directory>
</VirtualHost>
```

But I will say that the ServerAlias command was key to success. Though I couldn't have done it without your help either!
Are those new files then called site1 and site2?  or should they be like site1.com   site2.com    Just so I have a good example.  Thanks!

Shane

---

### Post by yodomino6 on 2008-04-11
> **shane2peru said:**
> Are those new files then called site1 and site2?  or should they be like site1.com   site2.com    Just so I have a good example.  Thanks!

Shane

Well it automatically names them site1.com.conf and puts it in the '/etc/apache2/sites-available/' folder. Example:
/etc/apache2/sites-available/site1.com.conf

You can view them in Webmin by clicking the Global Configuration Tab then Edit Config Files and in the drop-down list they will be at the very bottom with the default.

---

### Post by shane2peru on 2008-04-11
HE HE!   :popcorn:  Here is a simple cli configuration method!  (in case you have to setup again sometime) [http://wowtutorial.org/en/node/24](http://wowtutorial.org/en/node/24)

I tried that webmin thing too, wow, did I really mess some files up! :lolflag:  I had so many errors everytime I reloaded my apache, it wasn't funny.  Finally got rid of them!  My problem is I tried webmin, then cli, then webmin then cli and webmin ha ha, what a mess!  Anyway I got mine working too!  I appreciate the help!

Shane

---

