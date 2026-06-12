---
title: "Multiple sites in apache"
date: 2008-08-06
forum: Server Platforms
---

### Post by amai on 2008-08-06
On Ubuntu how do do set up multiple sites.
Checking on the net does point to change httpd.conf
but with Apache2, Httpd.conf is empty.

So where do you do the set up.
Is it in 
apache.conf or default.conf ?

Thanks

---

### Post by ingeva on 2008-08-06
> **amai said:**
> 
but with Apache2, Httpd.conf is empty.


I have no default.conf file any longer, but I have the apache2.conf file. I may have copied it over. Check the appendix, which contains my file unchanged extept the name, which I had to redefine as apache2.txt.

In the httpd.conf file I've only added the main server name, intertrafico:

```
ServerName intertrafico
```

Both these files are read by Apache, and I believe even the default.conf file is read if it's in the same directory. The best would be to move it somewhere else, so you can keep the original.

For defining multiple hosts I've created various virtual hosts in the "sites-enabled" directory, and I made a backup for them in "sites-available".

I'm a quite new user myself (and I could never set up Apache properly on Windows! :( ) so I don't know if everything is right, but at least it works for me.
FireFox is a little particular though. It has a tendency to change my local URLs and add both "www" and ".com" to them, making it hard to access my local files properly. I may have to add a TLD to the local domain names.

---

### Post by amai on 2008-08-06
Thanks ingeva, but the file doesnt have any vhosts configured

---

### Post by Oldsoldier2003 on 2008-08-06
Moved from ABT to Server Platforms and slightly renamed to get visibility from the server crowd :)

---

### Post by StickyStyle on 2008-08-06
> **ingeva said:**
> 
For defining multiple hosts I've created various virtual hosts in the "sites-enabled" directory, and I made a backup for them in "sites-available".


You have close to the right idea here ;)
What you want to do is create a file for each vhost (I tend to name the file with the site name) as you have done, but put have the file in the sites-available directory.  From there you have two handy scripts 'a2ensite' and 'a2dissite' that work like this...
```

$sudo a2ensite www.example1.com
$apache2ctl -t
$sudo /etc/init.d/apache2 reload

```

What that did was create a symlink in the sites-enabled directory (you could do it manually with ln -s /etc/apache2/sites-avaiable/www.example1.com /etc/apache2/sites-enabled/, but that's too much to type) with a2ensite, then we ran a sanity check on the apache config with 'apache2ctl -t' which now includes the vhost because its a good habit to get into, then we reloaded apache to enable the new vhost.

---

### Post by ingeva on 2008-08-07
> **amai said:**
> Thanks ingeva, but the file doesnt have any vhosts configured

That's right, but in order to have any use of Apache you want at least one.
Use the file "default" in sites-available as a starting point. Make new files, one for each vhost, then copy all except "default" to sites-enabled. Then you have a nice backup too.

---

### Post by amai on 2008-08-13
Thank all for your input.

Resolved.....

on virtual hosts

comment
NameVirtualHost *:80

so it will look like

#NameVirtualHost *:80

---

### Post by mbeach on 2008-08-13
you really shouldn't be copying to sites-enabled.  Use the a2ensite command which creates a sym link in sites-enabled to sites-available.

---

### Post by Dedoimedo on 2008-08-14
Hello,
If you're interested, I've written about it extensively.
Please check my guide, if you want (sig), see the Advanced Setup chapter, Virtual Host section.
Dedoimedo

---

### Post by ingeva on 2008-08-15
> **mbeach said:**
> you really shouldn't be copying to sites-enabled.  Use the a2ensite command which creates a sym link in sites-enabled to sites-available.

Sounds reasonable, but then you don't have the backup.

---

### Post by windependence on 2008-08-15
> **ingeva said:**
> Sounds reasonable, but then you don't have the backup.

No, but doing it your way breaks the modularity of Apache2. The correct way is the method mbeach suggested. If you want a backup, just make a backup of all your config files.

-Tim

---

### Post by StickyStyle on 2008-08-15
> **ingeva said:**
> Sounds reasonable, but then you don't have the backup.

If you want a backup you should look into either real backup software like bacula, or what I do for everything in my /etc (which is in addition to bacula actually); check your files into an SVN repository [1].  This lets you easily see what has changed in the file when you don't know what you did to break it, and let's you easily check back and see what the default file was setup like.

[1] Here is an example of what I'm talking about...
[http://www.barryodonovan.com/index.php/2007/04/25/putting-etc-under-subversion-svn](http://www.barryodonovan.com/index.php/2007/04/25/putting-etc-under-subversion-svn)

---

### Post by ingeva on 2008-08-15
> **windependence said:**
> No, but doing it your way breaks the modularity of Apache2. The correct way is the method mbeach suggested. If you want a backup, just make a backup of all your config files.

-Tim

I might find something in the Apache documentation, but I understand less than half of it.
Could you explain in simple words how the way I am doing it breaks the modularity?
As far as I had understood, this would be the preferred method.

Of course I take backups anyway .... :)

---

### Post by ingeva on 2008-08-15
> **StickyStyle said:**
> check your files into an SVN repository [1].  This lets you easily see what has changed in the file when you don't know what you did to...
[http://www.barryodonovan.com/index.php/2007/04/25/putting-etc-under-subversion-svn](http://www.barryodonovan.com/index.php/2007/04/25/putting-etc-under-subversion-svn)

OK. A quick look told me that I need to concentrate to find out what it's about.
I'm now using the cp command to backup new and changed files, but I understand that this may be just too resource consuming.

---

### Post by mbeach on 2008-08-15
ingeva, your method is fine(sites-available as backup).  The reasons I wouldn't personally do it are:

- when I get hit by the bus, get transfered, sell my business etc, if I've got things setup in a near to standard way as possible, my successor theoretically has an easier time taking over.  This successor could also be me a year or more in the future  having not changed a conf file, or restarted apache, and having to read the documentation to remember how to do stuff.  

- if the order of the loading of the virtual host files is important and in some cases it is for me, leaving the ordering up to the sym link name in sites-enabled makes more sense to me.

- I've burned myself too many times having a 'backup' in just another nearby file location - often forgetting which is the most correct backup.  Leaving backups to other backup routines is something I'm trying to stick with now (but admittedly I still have a bunch of files around named blarg.ext.20080227.bak).  Also, I'd probably just end up changing the file in use, and forget about the 'backup' making it more dangerous than useful (but that's me - if a fella is disiplined it could be fine)  

- If you quickly want to shut a particular site down, to be potentially re-enabled later, using the a2ensite and a2dissite commands are very handy.

I think in the end, as long as you understand how you are handling it, its all good.

---

### Post by mbeach on 2008-08-15
on the now other topic, and again this is more more open to discussion/debate, I'd probably lean away from using svn as a method of backing up your conf and other type files.  If you want to have version control in your backup in this manner, I think GIT might be a better solution.  Quick hit to google yeilds:
[http://hwasungmars.wordpress.com/2007/11/25/journey-to-a-backup-solution-git/](http://hwasungmars.wordpress.com/2007/11/25/journey-to-a-backup-solution-git/)

---

