---
title: "Setting up Django with mod_python and apache2 on Ubuntu 8.04"
date: 2008-06-12
forum: Server Platforms
---

### Post by blis102 on 2008-06-12
Hi all!

I have been developing on Django for a few months now and have a decent grasp of it, however, now I am trying to deploy an application to a Ubuntu 8.04 server (on a 256mb Slice @ SliceHost) with mod_python and apache2 and have been having a hell of a time getting it to work.

**What I've got so far:**
[LIST]
[*]apache2 is installed.
[*]phpmyadmin is installed.
[*]mysql-server is installed.
[*]mod_python is installed.
[*]I have a virtual host set up and working (serving a simple "hello world" html page).
[*]SVN version of Django setup and working.
[*]Other things like an SVN repository, SSH, FTP, etc...
[/LIST]

**What I have been struggling with:**
[LIST]
[*]How to structure my directories? I know there are many different ways to set up a directory structure, but what I've got right now is "/home/**username**/domains/example.com/" is where my site files are (e.g. directories for cgi-bin, backups, public, private, logs). I've put my media in "/home/**username**/media/example.com". What is an intelligent way to locate files (I know there probably are many!)? How scalable is the solution I am using now?
[*]Getting [dynamically configured mass virtual hosting]("http://httpd.apache.org/docs/2.0/vhosts/mass.html") set up. I would like to be able to create directories for domains and sub domains and have them automatically servered (like creating sub.example.com and putting a file in it and having it servered up). I know this is possible and my previous host (MediaTemple) has this set-up. How hard is this to do? Any advice or links? An example file for me to look at?
[*]Actually serving a Django app. Right now I have been trying to do it with the VirtualHost file, but I haven't been able to get anything to work. MediaTemple has a simple process for adding a new app that basically works by: 
1)SyncDB to create the DB tables 
2)Adding the application (naming it, its location in the directory tree, and where to host the file at, (e.g. example.com)) 
3)Generate an .htaccess file (I believe they do this because they use fastcgi and lighttpd?) 
4)Start the application. 
I know they created custom commands to do this easily, but what commands are they running behind the scenes to get this to work? I don't care if its more steps, but having the same result would be great! Also, if I could make my own commands like they did, that would be even better! Any ideas?
[/LIST]

**What I'd (ideally) like:**
To be able to have a directory for hosting my websites (/home/**username**/domains/) and within that a directory for each domain or subdomain (e.g. example.com/, sub.example.com/). The sites would automatically be served (via dynamically configured mass virtual hosting). If I want a particular site to be a Django site, I would put the application in a django directory (e.g. /home/**username**/containers/django/example.com) and then have it served in the /domains/ directory. I would serve media separate (as recommended by many people) either with another server with lighttpd or on Amazon's S3 or even just outside of a mod_python process. I want to host maybe 10 Django apps on my server (after I upgrade my slice), so the MassVirtual host would be awesome. This is basically how my old host (MeidaTemple) was set-up and if I could get something like this I would be in heaven. Also, if there is better or more simple solution, please let me know! 

Right now I am using VirtualHosts to server files from "/home/**username**/domains/public/" and that is working fine, but I can't seem to be able to get my Django files server to that location, and I'd like to not have to create a VH for each new site I add.

I have read the Django docs and a bunch of other docs around the net but with nothing really working well for me. I know this is a lot but I know you guys and gals out there really know your stuff!

Any help would be _greatly_ appreciated!

Thanks!
Dana

---

### Post by blis102 on 2008-06-16
Anyone?

---

### Post by airjaw on 2008-09-15
Try the django irc channel on irc.freenode.net

#django

a user there named Magnus is pretty knowledgeable and is around much of the time

---

### Post by pqrs541 on 2008-09-16
The Weather:[buy wow gold](http://www.mmoinn.com)  It's so dry, the trees are bribing the dogs. It's been hitter?s a goat's butt in a pepper patch.  Wintry roads are said to be "slicker than otter snot. [wow gold](http://wowus.mmoinn.com/index.do?PageModule=OrderForm_new)[wow gold](http://woweu.mmoinn.com/index.do?PageModule=OrderForm_new) [World of warcraft Gold](http://www.mmoinn.com)[wow gold](http://www.mmoinn.com)

---

### Post by alexisbellido on 2008-10-18
I guess the original poster already got it working but I still wanted to share an article I published about [setting up Django with Apache, mod_python, mod_proxy and Lighttpd]("http://ventanazul.com/webzine/tutorials/setup-apache-lighttpd-django-ubuntu") on Ubuntu 8.04.

I hope it helps other Django developers out there :)

---

### Post by alexisbellido on 2008-10-18
By the way, the article should help users of other distributions as well...

---

