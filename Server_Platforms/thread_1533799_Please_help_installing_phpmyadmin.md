---
title: "Please help installing phpmyadmin"
date: 2010-07-18
forum: Server Platforms
---

### Post by thatryan on 2010-07-18
I am kinda lost as this should be super easy.
I am on a media temple (ve) server, and running Ubuntu 10.04.
I ran apt-get install phpmyadmin and set it to use apache2
and according to instructions, 
[https://help.ubuntu.com/community/phpMyAdmin](https://help.ubuntu.com/community/phpMyAdmin)
I should be able to navigate to my URL/phpmyadmin but I just get a 404 error. 
I then tried adding 
Include /etc/phpmyadmin/apache.conf
to my apache config file, and I then got an error saying could not locate. So I FTP in and looked at the phpmyadmin folder itself and there is nothing in it except for 1 config file.
I then ran apt-get remove phpmyadmin to start over, and I deleted the folder via ftp. 
Now when I install it again still does not work and still nothing is in the phpmyadmin folder.
Any ideas would be helpful, thank you!

---

### Post by wojox on 2010-07-18
You followed everything from here down? *Should you get a 404 "Not Found" error*

---

### Post by thatryan on 2010-07-18
Yes I did. And I did choose apache in the set up config steps. 
And I ran the next command but it failed because there are no other files in the phpmyadmin folder, so trying to include it just fails...

---

### Post by NullHead on 2010-07-18
I found the default ubuntu, a wile ago, goes to yourcomain.com/php**M**y**A**dmin

---

### Post by Ryan Dwyer on 2010-07-18
> **thatryan said:**
> I should be able to navigate to my URL/phpmyadmin but I just get a 404 error.

Did you reload Apache after installing phpMyAdmin? What URL did you try to browse to? It should be something like [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/), not [http://localhost/some/folder/phpmyadmin/](http://localhost/some/folder/phpmyadmin/).

> **thatryan said:**
> I then tried adding 
Include /etc/phpmyadmin/apache.conf
to my apache config file, and I then got an error saying could not locate.

You shouldn't need to touch your Apache config. When you install phpMyAdmin it adds config at /etc/apache2/conf.d/phpmyadmin.conf.

> **thatryan said:**
> I then ran apt-get remove phpmyadmin to start over, and I deleted the folder via ftp.

Running apt-get remove doesn't remove any config files. You want apt-get purge for that.
 
> **thatryan said:**
> Now when I install it again still does not work and still nothing is in the phpmyadmin folder.

It doesn't work because you've deleted some of its files while it still believes they are there. You should run apt-get purge phpmyadmin, then reinstall it.

---

### Post by thatryan on 2010-07-18
Hm ok thanks.
I ran purge but it said not installed so not removed. Guess I deleted all of it?

Also, when you say go to [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) what do you mean by localhost? My domain? I have phpmyadmin installed on my local computer with MAMP, so going to localhost takes me there...

edit: I try reinstalling, then reload apache and this the shell from that attempt.

```


root@domain:~# apt-get install phpmyadmin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  phpmyadmin
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/4285kB of archives.
After this operation, 17.4MB of additional disk space will be used.
Preconfiguring packages ...
Can't exec "/tmp/phpmyadmin.config.241751": Permission denied at /usr/share/perl/5.10/IPC/Open3.pm line 168.
open2: exec of /tmp/phpmyadmin.config.241751 configure  failed at /usr/share/perl5/Debconf/ConfModule.pm line 59
phpmyadmin failed to preconfigure, with exit status 255
Selecting previously deselected package phpmyadmin.
(Reading database ... 22738 files and directories currently installed.)
Unpacking phpmyadmin (from .../phpmyadmin_4%3a3.3.2-1_all.deb) ...
Setting up phpmyadmin (4:3.3.2-1) ...
dbconfig-common: writing config to /etc/dbconfig-common/phpmyadmin.conf
Replacing config file /etc/phpmyadmin/config-db.php with new version
dbconfig-common: flushing administrative password

root@domain:~# /etc/init.d/apache2 reload
apache2: Syntax error on line 233 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/conf.d/phpmyadmin.conf: No such file or directory
   ...fail!
root@domain:~# 

```

---

### Post by jcinteractive on 2010-07-18
Right, lets have a look....

Once you do a Apache reload, it moans about not locating the file. So, what you could do is touch the file, and place this as the contents:

```

Include /etc/phpmyadmin/apache.conf

```

Once that is in there, save the file, and reload Apache. Hope this helps :)

---

### Post by thatryan on 2010-07-18
Right, but the phpmyadmin folder has nothing in it, except for config-db.php ....?

---

### Post by jcinteractive on 2010-07-19
Ok, the best option now is to download the package from the PHPMyAdmin site, and just extract it in the location. That should solve your issue, as for some weird reason your installer messed up :)

---

### Post by thatryan on 2010-07-19
lol ok I just downloaded phpmyadmin from their site, unzipped it and uploaded its contents via FTP to the empty phpmyadmin folder on my server. Still though, inside it did not have the apache.conf file.
What the hell did I break?! ;)

Should I just remove apache and start over? And if so, will doing so allow my site on there to still work once apache re installed, or do I have to go through all the settings again for forwarding etc..?

---

