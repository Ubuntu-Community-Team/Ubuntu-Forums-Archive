---
title: "Virtual Host Issues after upgrade to 9.10"
date: 2009-10-31
forum: Server Platforms
---

### Post by thescubadude on 2009-10-31
I just upgraded from JJ 9.04 to the new Ubuntu 9.10.

I have samba installed for shares which is still working great.

I also have apache installed with several virtual hosts.

The problem is that when I try to access any of the virtual hosts, whether from my ubuntu machine or the network machines, I get the following error:

**Forbidden**

 You don't have permission to access / on this server.
  Apache/2.2.12 (Ubuntu) Server at mywebsite.com Port 80

I have checked and the virtual hosts appear to be enabled so... any ideas.

---

### Post by fahadsadah on 2009-10-31
Please check permissions on the document roots.

---

### Post by thescubadude on 2009-10-31
I am very new to Ubuntu and all the technical stuff. Used to just design and programming.

I'm not sure how I check permissions

But I did the following to set them?

sudo chmod 0777 /media/urchin/www

Which is my external drive that i have my virtual hosts on.

By the way I can access my default apache host and my phpmyadmin setup within this.

---

### Post by Vegan on 2009-10-31
You should be OK, make sure you use CHMOD as needed to make sure the root has access to the directory.

---

### Post by thescubadude on 2009-11-01
Hi I'm still having problems.

While trying to fix this problem I tried to re-install apache, php etc and managed to mess everything up to the point where nothing was working. So downloaded 9.10 as I had upgraded previously. I made a fresh install. Installed LAMP, set up my virtual hosts and still having the same problem.

Being a complete beginner I need basic guidelines on what to do. php, phpmyadmin, and mysql working 100% but i still cannot access virtual hosts. They were working perfectly in 9.4.

What do I need to do to set permissions for root etc step by step please if possible.

virtual hosts are on /media/urchin/www/folderNameForEachSite (media being an external drive - laptop I'm using as server is old so keeping sites on new external drive)

Any help would be great. Don't want to break everything again.

I have tried: [B]

sudo chmod 0777 /media/urchin/www[/B] 

and 
**sudo chown -R www-data.www-data ****/media/urchin/www**But neither have helped!

This is my virtualhost conf file. it has been enabled and I have edited /etc/hosts to 127.0.0.1 scubadive.ex :

Again it was working in Ubuntu 9.4 

<VirtualHost *:80>
  
    ServerName scubadive.ex
        DocumentRoot /media/urchin/www/scubadive
        <Directory />
                Options FollowSymLinks
                AllowOverride All
        </Directory>
        <Directory /media/urchin/www/scubadive>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>

---

### Post by thescubadude on 2009-11-01
Is it possible I need to do something in the apache config file? or my php5 confg file that i am missing?

---

### Post by thescubadude on 2009-11-01
**THis is from the apache error log log:** 
[Sun Nov 01 15:33:43 2009] [crit] [client 127.0.0.1] (13)Permission denied: /media/urchin/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable

**This is the virtualhost setup**:
<VirtualHost *:80>
   
     ServerName scubadive.ex
         DocumentRoot /media/urchin/www/scubadive
         <Directory />
                 Options FollowSymLinks
                 AllowOverride All
         </Directory>
         <Directory /media/urchin/www/scubadive>
                 Options Indexes FollowSymLinks MultiViews
                 AllowOverride All
                 Order allow,deny
                 allow from all
         </Directory>
 </VirtualHost>

**From the apache2.conf file:**
AccessFileName .htaccess

#
# The following lines prevent .htaccess and .htpasswd files from being 
# viewed by Web clients. 
#
<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
</Files>

---

### Post by thescubadude on 2009-11-02
Ok so after 1 upgraded to 9.10 using the upgrade option, then re-downloading the ubuntu image and doing two fresh install, trying to set various permissions, using chmod, chown, installing webmin and trying to set everything from there I had absolutely no luck getting my virtual hosts to work on an external drive!

So finally called it a day, re-installed ubuntu 9.04, downloaded all the updates, installed and downloaded all the relevant packages. LAMP server, phpmyadmin, samba. Set up my virtual hosts, and my shares and what do you know its working 100%. 

Not sure what that is all about as I am completely new to linux. It could just be something simple that I'm missing.  Guess I'm just glad I started just before 9.10 came out otherwise I may still be using windows! 

If anyone has some ideas to fix these issues let me know cos I would still like to be using the latest version but for now it's just easier to use what I can get to work.

---

### Post by obeyrobots on 2009-11-02
I wish I had an answer for you but I wanted to chime in that I'm having the a very similar problem and wanted to throw some more info at it.  I had multiple virtual hosts running just fine under 9,04 + Apache 2 + PHP 5.

Going from 9.04 -> 9.10 I now have all of my src="/foo/bar" trying to pull from /usr/share/foo/bar instead of what I set docroot to in the virtual hosts.  Pages themselves execute via PHP just fine, Apache just seems blind to the Virtual Host instructions.

No conf files and/or php.ini have changed..  I recursively chowned the docroot's group to what apache is running as (www-data) in case it was a permission issue.  This is all running on localhost (my dev environment).

Any hints would be fantastic.

Example log entry of what used to work:
[error] [client 127.0.0.1] File does not exist: /usr/share/javascript/supermenu.js, referer: [http://www.url.com/](http://www.url.com/)

---

### Post by Vegan on 2009-11-03
I have my setup files on my forum in case you want to see what does work on 9.10 which is what I am using today.

---

### Post by cariboo on 2009-11-03
> From the apache2.conf file:
AccessFileName .htaccess

#
# The following lines prevent .htaccess and .htpasswd files from being
# viewed by Web clients.
#
<Files ~ "^\.ht">
Order allow,deny
Deny from all
</Files>

If you look at the above rule you have access to .htaccess set to deny from all, so you won't be able to access the file.

---

### Post by thescubadude on 2009-11-04
> **obeyrobots said:**
> I wish I had an answer for you but I wanted to chime in that I'm having the a very similar problem and wanted to throw some more info at it.  I had multiple virtual hosts running just fine under 9,04 + Apache 2 + PHP 5.

Going from 9.04 -> 9.10 I now have all of my src="/foo/bar" trying to pull from /usr/share/foo/bar instead of what I set docroot to in the virtual hosts.  Pages themselves execute via PHP just fine, Apache just seems blind to the Virtual Host instructions.

No conf files and/or php.ini have changed..  I recursively chowned the docroot's group to what apache is running as (www-data) in case it was a permission issue.  This is all running on localhost (my dev environment).

Any hints would be fantastic.

Example log entry of what used to work:
[error] [client 127.0.0.1] File does not exist: /usr/share/javascript/supermenu.js, referer: [http://www.url.com/](http://www.url.com/)

Just wondering if you were able to sort it out?? I don't want to waste time going back to 9.10 if I'm going to spend another two days without resolving the issues.

As far as the htaccess goes I thought that was to prevent people from accessing these files. Those are the same settings I have in 9.04 and it works perfectly. I'm running it now with no issues.

---

