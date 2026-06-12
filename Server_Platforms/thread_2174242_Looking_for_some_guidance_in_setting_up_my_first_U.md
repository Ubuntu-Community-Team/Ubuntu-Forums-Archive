---
title: "Looking for some guidance in setting up my first Ubuntu Server without Webmin"
date: 2013-09-13
forum: Server Platforms
---

### Post by icebox83 on 2013-09-13
[FONT=Helvetica]This past April I ventured into Linux server administration with basically no Linux or command line experience. What I ended up doing was installing TurnKey Linux and using the built in Webmin interface to manage virtual hosts and sFTP in as root for file access. But now, after running that as a virtual machine for five months, I'm ready to do this the right way and give the barebones Ubuntu Server a try…but I need some help.[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]The physical box I have to work with is a 3.2 GHz P4 with 1.75 GB RAM. Will probably just use a 40GB HDD in there. It also has a graphics card, but I might take that out.[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]I am able to successfully install Ubuntu Server 12.04.3 LTS and get that alive on the network, SSH in remotely, do some very basic things, etc., without any hassle. What I need help with is accomplishing everything else. Below is a basic outline of what I need to not only learn how to do, but also understand:[/FONT]
[FONT=Helvetica]
[/FONT]

[LIST]
[*]Install phpMyAdmin. Actually I more or less figured this out. I just don't understand why every guide is slightly different, e.g. different commands, etc.
[*]Install anything else conducive to a WordPress environment (suggestions are welcome)
[*]Figure out where to locate the folder that will hold my dozen or so websites and create a user that owns this directory so that I don't run into permissions problems (I think I'm using the right terminology here) when connecting via sFTP. With TurnKey Linux one of the problems I ran into is having to manually "chmod" the master var/www directory from Webmin's GUI file manager every time I wanted to set up a new WordPress installation.
[*]Learn how to create, modify and delete virtual hosts. It is my understanding that all one needs to do is open an Apache config file and edit it from the command line, but I could be wrong.
[*]Learn what needs to be backed up (other than files and databases) and how to do it the correct and/or best way.
[*]SECURE anything that I need to secure, e.g. standard practices when setting up a basic server
[*]I would also LOVE to set this box up as the VPN portal for my home network if at all possible.
[*]Lastly, if it is possible or practical, I would like to set up regular FTP (unless sFTP is far superior and there's no reason to use FTP).
[/LIST]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]That's pretty much it. Just looking to host a proper command line Ubuntu Server box on my static IP so that I can serve up about a dozen or so websites (and that number is slowly growing). If anyone can walk me through some of this or point me in the right direction, that would be AWESOME!!! Thanks so much![/FONT]

---

### Post by Lars Noodén on 2013-09-13
[sftp is far superior to ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp) in most ways, especially if you want to transfer files to your server not just from it.

About the web sites, you'll want to make a separate directory under /var/www for each of your sites.  Then you'll need a separate virtual host for each one, with each vhost having its own configuraiton file.  If you are using Apache2 and not nginx, then the configuration files are in /etc/apache2/sites-available.  Add them one by one and enable them.  You start out with one by default which has the name *000-default*  Just copy it and then make your changes.  You can enable the configured vhost with [a2ensite](http://manpages.ubuntu.com/manpages/raring/en/man8/a2ensite.8.html)  If you are the only user of the system it is enough that you take ownership of the directories with [chown](http://manpages.ubuntu.com/manpages/raring/en/man1/chown.1.html).  You can test the configuration files for your vhosts with *apachectl configtest*.

Your config files will point to various directories using DocumentRoot, ScriptAlias and such.  Those are the only files you need unless you also want to back up the log files.  

The server is more or less secure out of the box.  The weak point will be any PHP or CGI scripts you add.  This includes WordPress, Drupal or any others.  The mistakes there are usually not sanitizing input before passing it on to the system.  If you are working with databases via PHP or CGI, always use the API provided with "placeholders" for the data and  always sanitize input (see also Tainted Variables)  If all you need are standardized headers, footers and navigation menus, then you can use *IncludesNOEXEC* to give you Server Side Includes.  No need for PHP or Perl in that case.

---

### Post by icebox83 on 2013-09-13
> **Lars Noodén said:**
> [sftp is far superior to ftp]("http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp") in most ways, especially if you want to transfer files to your server not just from it.

About the web sites, you'll want to make a separate directory under /var/www for each of your sites.  Then you'll need a separate virtual host for each one, with each vhost having its own configuraiton file.  If you are using Apache2 and not nginx, then the configuration files are in /etc/apache2/sites-available.  Add them one by one and enable them.  You start out with one by default which has the name *000-default*  Just copy it and then make your changes.  You can enable the configured vhost with [a2ensite]("http://manpages.ubuntu.com/manpages/raring/en/man8/a2ensite.8.html")  If you are the only user of the system it is enough that you take ownership of the directories with [chown]("http://manpages.ubuntu.com/manpages/raring/en/man1/chown.1.html").  You can test the configuration files for your vhosts with *apachectl configtest*.

Your config files will point to various directories using DocumentRoot, ScriptAlias and such.  Those are the only files you need unless you also want to back up the log files.  

The server is more or less secure out of the box.  The weak point will be any PHP or CGI scripts you add.  This includes WordPress, Drupal or any others.  The mistakes there are usually not sanitizing input before passing it on to the system.  If you are working with databases via PHP or CGI, always use the API provided with "placeholders" for the data and  always sanitize input (see also Tainted Variables)  If all you need are standardized headers, footers and navigation menus, then you can use *IncludesNOEXEC* to give you Server Side Includes.  No need for PHP or Perl in that case.

Thanks! I followed some of this. Please bear with me as I work through all of this and hopefully learn how to do it all correctly!

So I've got a server running with OpenSSH and LAMP installed. I did the apt-get and installed phpMyAdmin and added Include /etc/phpmyadmin/apache.conf to Apache config file to access phpMyAdmin at /phpmyadmin/. So at least *that much* is currently working.

So sFTP it is - I read the article, thanks! On my TurnKey Linux server I had [http://domain1.com/](http://domain1.com/), [http://domain2.com/](http://domain2.com/), etc. all within var/www/ and intend to do the same here. This brings me to creating a user and/or taking ownership. I am indeed the only user of the system, so if I understand correctly I just need to use chwown to give my user, which is *not* root, by the way, ownership of var/www/? Is it just var/www/, the location in which my sites will reside, the only location I need to take ownership of?

Hmm...using Coda I was able to sFTP into the server. Using my user it placed me into /home/user by default. Is this normal? Is it normal that my user can go two levels up and access the entire contents of the server? Is it anything to worry about as far as security is concerned so long as my password is strong?

Thank you SOO much!!!

---

### Post by icebox83 on 2013-09-13
Just out of curiosity I tried to install WordPress and found that my user can't write to the /var/www directory *at all*. So I ran sudo chown username.users /var/www and am now able to write to /var/www (and I can still write to /home/username too). I then copied WordPress into the /var/www directory, but WordPress still gives me the below error. What do I have to do next? Was I right in running sudo chown username.users /var/www, or is there a security problem with doing that?

[ATTACH=CONFIG]246212[/ATTACH]

---

### Post by CharlesA on 2013-09-13
> **icebox83 said:**
> 

[LIST]
[*]Install phpMyAdmin. Actually I more or less figured this out. I just don't understand why every guide is slightly different, e.g. different commands, etc.
[*]Install anything else conducive to a WordPress environment (suggestions are welcome)
[*]Figure out where to locate the folder that will hold my dozen or so websites and create a user that owns this directory so that I don't run into permissions problems (I think I'm using the right terminology here) when connecting via sFTP. With TurnKey Linux one of the problems I ran into is having to manually "chmod" the master var/www directory from Webmin's GUI file manager every time I wanted to set up a new WordPress installation.
[*]Learn how to create, modify and delete virtual hosts. It is my understanding that all one needs to do is open an Apache config file and edit it from the command line, but I could be wrong.
[*]Learn what needs to be backed up (other than files and databases) and how to do it the correct and/or best way.
[*]SECURE anything that I need to secure, e.g. standard practices when setting up a basic server
[*]I would also LOVE to set this box up as the VPN portal for my home network if at all possible.
[*]Lastly, if it is possible or practical, I would like to set up regular FTP (unless sFTP is far superior and there's no reason to use FTP).
[/LIST]

1) I use the regular MySQL CLI client instead of phpMyAdmin, but that is just any apt-get away.
2) What web server software are you going to use? I think the most popular is Apache and that should be fine to run Wordpress.
3) I store my websites in /webroot but /var/www/ is the default for Apache (LAMP stack install).
4) I use SFTP/SSH over plain FTP because it is more secure and I only need to worry about allowing SSH through the firewall and securing it (keys only, no root login).
5) VirtualHosts aren't that hard to figure out. :) [Check this out]("http://httpd.apache.org/docs/2.2/vhosts/name-based.html").
6) I think the stock install of Apache is fairly secure, but you can find out how to harden it by searching around.
7) I kinda have my home server set up like that, except I use SSH tunnels instead of a pure VPN solution. Check out OpenVPN.
> **Lars Noodén said:**
> [sftp is far superior to ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp) in most ways, especially if you want to transfer files to your server not just from it.

Nice link. ;)

> 
The server is more or less secure out of the box.  The weak point will be any PHP or CGI scripts you add.  This includes WordPress, Drupal or any others.  The mistakes there are usually not sanitizing input before passing it on to the system.  If you are working with databases via PHP or CGI, always use the API provided with "placeholders" for the data and  always sanitize input (see also Tainted Variables)  If all you need are standardized headers, footers and navigation menus, then you can use *IncludesNOEXEC* to give you Server Side Includes.  No need for PHP or Perl in that case.

Pretty much nailed it. Also, checking logs helps a lot. Logwatch is a huge timeserver if you want your logs emailed to you.

> **icebox83 said:**
> Just out of curiosity I tried to install WordPress and found that my user can't write to the /var/www directory *at all*. So I ran sudo chown username.users /var/www and am now able to write to /var/www (and I can still write to /home/username too). I then copied WordPress into the /var/www directory, but WordPress still gives me the below error. What do I have to do next? Was I right in running sudo chown username.users /var/www, or is there a security problem with doing that?


Check this out: [http://ubuntuforums.org/showthread.php?t=2173865](http://ubuntuforums.org/showthread.php?t=2173865)

---

### Post by Lars Noodén on 2013-09-14
> **icebox83 said:**
> So sFTP it is - I read the article, thanks! On my TurnKey Linux server I had [http://domain1.com/](http://domain1.com/), [http://domain2.com/](http://domain2.com/), etc. all within var/www/ and intend to do the same here. This brings me to creating a user and/or taking ownership. I am indeed the only user of the system, so if I understand correctly I just need to use chwown to give my user, which is *not* root, by the way, ownership of var/www/? Is it just var/www/, the location in which my sites will reside, the only location I need to take ownership of?

So you'll need separate directories for the two vhosts.  You can choose whatever names you want but something like /var/www/domain1.com/ and /var/www/domain2.com/ would be unambiguous.  Yes, chown is enough.  For normal operation, the web server only needs to be able to read the files in the vhost's DocumentRoot.   So, with all the other settings the same, just changing ownership will allow you to edit the files while allowing the web server to serve (read) the files.  Be sure to read the link to Apache's online documentation that CharlesA posted.  It provides the basics.  

> **icebox83 said:**
> Just out of curiosity I tried to install WordPress and found that my user can't write to the /var/www directory *at all*. So I ran sudo chown username.users /var/www and am now able to write to /var/www (and I can still write to /home/username too). I then copied WordPress into the /var/www directory, but WordPress still gives me the below error. What do I have to do next? Was I right in running sudo chown username.users /var/www, or is there a security problem with doing that?


When you are working through the web interface you aren't you any more.  You are the user that Apache2 is running as.  Though it is a little convoluted the way Apache2 does it, you can read between /etc/apache2/envvars and /etc/apache2/apache2.conf that apache2 runs as the user *www-data*.  You shouldn't need to change either of  those files, just look up stuff from time to time.  

There are several ways you could get WordPress to write that configuraion file for you through the web server interface but they all involve serveral steps to open things way up and then close them again and mistakes in those steps would potentially open your machine to trouble.  Instead, can you edit that file (wp-config.php) by hand using *nano -w* or *vi*?  That would be the safe way and you would get practice that would help you work much more flexibly.

---

### Post by CharlesA on 2013-09-14
> **Lars Noodén said:**
> 
There are several ways you could get WordPress to write that configuraion file for you through the web server interface but they all involve serveral steps to open things way up and then close them again and mistakes in those steps would potentially open your machine to trouble.  **Instead, can you edit that file (wp-config.php) by hand using *nano -w* or *vi*?  That would be the safe way and you would get practice that would help you work much more flexibly.**

+1 from me. That's what I was doing instead of messing with permissions. When you run the Install Wizard, it will complain then let you copy/paste the wp-config.php file contents.

---

### Post by icebox83 on 2013-09-14
Is there anything wrong with doing the following? After some research I found [this]("http://stackoverflow.com/questions/3106005/how-to-set-default-group-permissions-for-sftp-uploads") article.

```
[FONT=Helvetica]chmod g+s /var/www[/FONT]
```

Basically what I found is that no matter what I do with chown or adduser, anything I upload via sFTP is still owned by my user. So if I chown /var/www to user:www-data and then upload the wordpress directory, when I look at the info for not only the directory but also the files within, I see user:user. I then started searching for how to inherit ownership for everything uploaded in the future via sFTP and have since found the above. Thoughts? Any security concerns?

---

### Post by Lars Noodén on 2013-09-14
> **icebox83 said:**
> So if I chown /var/www to user:www-data and then upload the wordpress directory, when I look at the info for not only the directory but also the files within, I see user:user. I then started searching for how to inherit ownership for everything uploaded in the future via sFTP and have since found the above. Thoughts? Any security concerns?

Yes, if the directories are chowned to www-data there are big security concerns.  It would be best -- if that is done at all -- that the machine be isolated from the net while that happens and then that the directory be restored to another user as soon as the configurations are done.  The isolation can be as simple as unplugging the ethernet cable or the ADSL line (if you have one).  If the machine is hosted somewhere else, off site, then you have to play with iptables or something like that.  

The reason it is an issue is because not only are all the settings still in their defaults, but also that www-data (in that situation) has write access to scripts.  The user www-data exists to provide an uprivileged account to allow privilege separation for the HTTP daemon.  Giving write access to www-data circumvents that protection so if it is done that way, it needs to be done carefully and with the steps in the right order.  It is much simpler to find a way around that such as editing the config file via the shell and not worrying about the web interface in regards to initial configuration. 

Just to add an anecdote, I have seen consultants get owned in less than 5 minutes online because they opened the machine up and connected it to the net before hardening it.  Remember that the scans are going on *all* the time.  Just check your logs to see.  They're not after your machine specifically, just after any machine that happens to have its pants down.

---

### Post by icebox83 on 2013-09-14
> **Lars Noodén said:**
> Yes, if the directories are chowned to www-data there are big security concerns.  It would be best -- if that is done at all -- that the machine be isolated from the net while that happens and then that the directory be restored to another user as soon as the configurations are done.  The isolation can be as simple as unplugging the ethernet cable or the ADSL line (if you have one).  If the machine is hosted somewhere else, off site, then you have to play with iptables or something like that.  

The reason it is an issue is because not only are all the settings still in their defaults, but also that www-data (in that situation) has write access to scripts.  The user www-data exists to provide an uprivileged account to allow privilege separation for the HTTP daemon.  Giving write access to www-data circumvents that protection so if it is done that way, it needs to be done carefully and with the steps in the right order.  It is much simpler to find a way around that such as editing the config file via the shell and not worrying about the web interface in regards to initial configuration. 

Just to add an anecdote, I have seen consultants get owned in less than 5 minutes online because they opened the machine up and connected it to the net before hardening it.  Remember that the scans are going on *all* the time.  Just check your logs to see.  They're not after your machine specifically, just after any machine that happens to have its pants down.

Alright, so scratch that. How, then, can I use my FTP client to write files to /var/www over sFTP? Can I chown user:user just like my user's home directory at /home/user? Or perhaps chown user:root? Sorry for all the questions, I'm learning :)

Edit: Oh dear! I just found out that my present TurnKey Linux install - the virtual server that's been running since April or May and is still live - is www-data:www-data for /var/www...

---

### Post by Lars Noodén on 2013-09-14
> **icebox83 said:**
> Alright, so scratch that. How, then, can I use my FTP client to write files to /var/www over sFTP? Can I chown user:user just like my user's home directory at /home/user? Or perhaps chown user:root? Sorry for all the questions, I'm learning :)

Yes, you can use your SFTP client to write to /var/www if you chown it just like your user's home directory.  That works great if you are the only user.  If you have to share, you have to set the permissions up using groups.  That's easy too.

---

### Post by icebox83 on 2013-09-14
> **Lars Noodén said:**
> Yes, you can use your SFTP client to write to /var/www if you chown it just like your user's home directory.  That works great if you are the only user.  If you have to share, you have to set the permissions up using groups.  That's easy too.

That worked great! Except WordPress still can't write anything. I can get around the wp-config file by making my own, but how do I deal with WP not being able to install plugins, themes, upload media, etc. since I can't make www-data the group or user?

---

### Post by Lars Noodén on 2013-09-15
Does it identify which files it needs to write?  If so you could chown to www-data just those particular files to keep it at a minimum.

---

### Post by icebox83 on 2013-09-15
> **Lars Noodén said:**
> Does it identify which files it needs to write?  If so you could chown to www-data just those particular files to keep it at a minimum.

WordPress needs to write the entire wp-content directory. Why, again, can't I chown user:www-data? My current server is running that way by default. And in doing some looking online this is the only instance I've been recommended otherwise...

---

### Post by icebox83 on 2013-09-15
Even the Ubuntu guide for installing WordPress recommends chown user:www-data... [https://help.ubuntu.com/community/WordPress](https://help.ubuntu.com/community/WordPress)

---

### Post by Lars Noodén on 2013-09-15
I guess if it needs write access to just the one directory and there is no other way, then you can change the group permissions while retaining ownership of it.  chgrp www-data and chmod g=rwx for the directory.

What we are trying to maintain is W^X or Write XOR eXecute, where object can either be written or be run but not both.  With the web server, the same applies to publishing, ideally you don't want published directories to be writable.  Sticking with W^X makes the system a little harder to be exploited should something go wrong with the scripts and some outsider find their way in.

---

### Post by SeijiSensei on 2013-09-16
There's no way to run Wordpress without letting the server write into the directory tree.  You can take the path of only adding write privileges to directories like /wp-includes/ when you need to do something like add a plugin, install a theme or upgrade WordPress itself.  But you'll still have to leave directories like /wp-content/ writable by the server if you want to use WP's native tools for tasks like uploading images.  The textual content isn't an issue since it is all stored in the SQL database.

I have one non-root user that owns all my sites, with www-data a member of that user's group.  All the WP directories are 770 and the files are 660, and all of these directories are under /home/username/websites/. /home/username itself has 711 privileges.

---

