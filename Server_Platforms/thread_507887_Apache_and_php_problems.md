---
title: "Apache and php problems"
date: 2007-07-23
forum: Server Platforms
---

### Post by Scaryclouds on 2007-07-23
Hi am having problems setting up my LAMP server. 

Recently I downloaded Ubuntu 7.04 Server edition went through the setup and select LAMP and DNS to be setup. However it appears my LAMP is not working properly, specifically Apache. 

I have uploaded .php files to my server but they do not parse, I have an "httpd.conf" file, but it is totally blank, and commands for restarting my server do not work. All together it seems I'm in a bit of a bind. I have tried uninstalling and reinstalling apache but they do not seem to accomplish the task. Anybody have any ideas on what the problems could be?

Couple of other notes:
I installed samba, and when I upload files they are stored in the "homes" folder

I am using openssh-client

I have run updates so everything is as current as it could be. 

Any help would be much appreciated :D

---

### Post by geeffland on 2007-07-30
I am a newbie to this as well... but on my maching I found the default apaches files in /var/www

I then went into the samba config file and added a source for the 'webroot' directory so I could push files there from a windows XP machine without using ftp.

I used 6.06 dapper drake but it should be similar... 

Greg

---

### Post by fuzz500 on 2007-10-15
Its a bit late, but the apache2 configuration file is located at
/etc/apache2/apache2.conf
good luck!

---

