---
title: "Help with apache and webdav setup"
date: 2009-08-21
forum: Server Platforms
---

### Post by munchi3s on 2009-08-21
Well, I have been working with apache and webdav all day and I have made some progress I have made a Vhost that correctly points to the folder I want it to and webdav that was able to allow a windows XP box with dreamweaver download the files in the server using webdav protocol. The only problem is that when I try to edit the files with dreamweaver and reupload them to the server acess is denied by the server(I think).
I'm just wondering if anyone else has had any similer problems and can help me.

I am using this [tutorial]("http://www.howtoforge.com/how-to-set-up-webdav-with-apache2-on-ubuntu-8.10") which is desinged for 8.10 I'm currently using 9.04. Everything seemed to be working.

If anyone could help me out I would appiciate very much.

---

### Post by VipX1 on 2009-08-21
Is it a Permission issue with the web server directory. Other users don't have write access so you can't upload from the XP machine.You need to go research the chmod command. I just did some chmod things on my web server before I posted as a test and it caused other problems so I'm not posting chmod commands..

---

### Post by munchi3s on 2009-08-21
I think its a permission issue but I thought I set up the permissions in the tutorial. Ill go look it up. Thanks Ill update to any change.

---

### Post by y@w on 2009-08-21
Looks like the tutorial you used has you chown the files to be owned by root with the group of www-data, then it has you chmod 640 the files. Since Apache runs as www-data by default, the web server won't have access to write the files, but can read.

---

### Post by munchi3s on 2009-08-21
Well I dont understand chown command yet or what "640" means but it seems that I can read the files fine. How do I change it so www-data can also write to the files. I created a webdav user and password in a file called "var/www/web1/passwd.dav" which created the webdav user. How do I give that webdav user permission to edit the files?

Edit > Well it seems that I need to use the chmod command to add premissions to the directory /var/www/web1/**web/** But the chown command gives the group "www-data" access to the directory but it also need permissions for the directory as well.
Tell me if I'm wrong or dont understand.

---

### Post by y@w on 2009-08-21
I think you've got it, but I'm not sure..

Anyway, you'll want to do something like:
```
chmod -R g+w /var/www/web1/web/
```

That will give the group www-data access to write to that directory as well as any files underneath.

---

### Post by munchi3s on 2009-08-21
I tried what you gave me, yet to no avail. Its frustrating being so close I can taste it.:confused:
I'm going to keep trying things if you come up with something else let me know :).

Edit> The chmod commands dont seem to do anything(unless its already done) but this is what I'm looking at. At this point dreamweaver still cannot write index.html to the server.

root@apache-webserver:/var/www/web1# ls -l
total 12
-rw-r----- 1 root     www-data   47 2009-08-21 09:41 passwd.dav
-rw-r----- 1 root     www-data   28 2009-08-20 18:39 passwd.dav~
drw-r----- 3 www-data root     4096 2009-08-20 20:09 web
root@apache-webserver:/var/www/web1# chmod -R g+w /var/www/web1/web/
root@apache-webserver:/var/www/web1# ls =l
ls: cannot access =l: No such file or directory
root@apache-webserver:/var/www/web1# ls -l
total 12
-rw-r----- 1 root     www-data   47 2009-08-21 09:41 passwd.dav
-rw-r----- 1 root     www-data   28 2009-08-20 18:39 passwd.dav~
drw-r----- 3 www-data root     4096 2009-08-20 20:09 web
root@apache-webserver:/var/www/web1#

---

### Post by munchi3s on 2009-08-21
It may be a lock issue. DAVlock has given other people issues.

---

### Post by y@w on 2009-08-21
> **munchi3s said:**
> It may be a lock issue. DAVlock has given other people issues.

Hmm.. Good point. Is "access denied" just the error in Dreamweaver?

Perhaps a tail of /var/log/apache/error.log would help.

---

### Post by munchi3s on 2009-08-21
Access denied is only in dreamweaver. ill look at the file you specified and see if there is anything there that could help me.

---

### Post by munchi3s on 2009-08-21
I'm getting a lot of errors. I dont know if thats normal but like 7 - 10 of these appear every second

[Thu Aug 20 16:53:06 2009] [notice] child pid 20512 exit signal Illegal instruction (4)
[Thu Aug 20 16:53:06 2009] [notice] child pid 20513 exit signal Illegal instruction (4)
[Thu Aug 20 16:53:06 2009] [notice] child pid 20514 exit signal Illegal instruction (4)

Edit> more like 20 - 25 every second

Edit> They stopped. But some lots of errors of denied 192.168.1.101 (My dreamweaver box) to index.html
Which is the file I'm trying to edit.

But, here is what I noticed. When connecting to my apache server in dreamweaver I have dreamweaver set up to look at "192.168.1.107:80/webdav/ I also noticed that when it was dening my dreamweaver machine it was .../webdav/index.html and some other stuff. But if I retrive the files from my apache server it give me the index file in .../web/

---

### Post by munchi3s on 2009-08-21
Heres a look at the last fraction of my error.log
(Sorry about how long it is)


[Fri Aug 21 09:38:49 2009] [error] [client 192.168.1.101] (13)Permission denied: access to /webdav/index.html denied
[Fri Aug 21 09:38:49 2009] [error] [client 192.168.1.101] (13)Permission denied: access to /webdav/index.cgi denied
[Fri Aug 21 09:38:49 2009] [error] [client 192.168.1.101] (13)Permission denied: access to /webdav/index.pl denied
[Fri Aug 21 09:38:49 2009] [error] [client 192.168.1.101] (13)Permission denied: access to /webdav/index.php denied
[Fri Aug 21 09:38:49 2009] [error] [client 192.168.1.101] (13)Permission denied: access to /webdav/index.xhtml denied
[Fri Aug 21 09:38:49 2009] [error] [client 192.168.1.101] (13)Permission denied: access to /webdav/index.htm denied
[Fri Aug 21 09:38:49 2009] [error] [client 192.168.1.101] Provider encountered an error while streaming a multistatus PROPFIND response.  [404, #0]
[Fri Aug 21 09:38:49 2009] [error] [client 192.168.1.101] (13)Permission denied: access to /webdav/index.html denied
[Fri Aug 21 09:38:49 2009] [error] [client 192.168.1.101] (13)Permission denied: access to /webdav/index.cgi denied
[Fri Aug 21 09:38:49 2009] [error] [client 192.168.1.101] (13)Permission denied: access to /webdav/index.pl denied
[Fri Aug 21 09:38:49 2009] [error] [client 192.168.1.101] (13)Permission denied: access to /webdav/index.php denied
[Fri Aug 21 09:38:49 2009] [error] [client 192.168.1.101] (13)Permission denied: access to /webdav/index.xhtml denied
[Fri Aug 21 09:38:49 2009] [error] [client 192.168.1.101] (13)Permission denied: access to /webdav/index.htm denied
[Fri Aug 21 09:38:49 2009] [error] [client 192.168.1.101] Provider encountered an error while streaming a multistatus PROPFIND response.  [404, #0]
[Fri Aug 21 09:42:06 2009] [crit] [client 192.168.1.101] (13)Permission denied: /var/www/web1/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable
[Fri Aug 21 09:43:10 2009] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Fri Aug 21 09:43:11 2009] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Fri Aug 21 09:43:11 2009] [warn] NameVirtualHost *:80 has no VirtualHosts
[Fri Aug 21 09:43:12 2009] [notice] Apache/2.2.11 (Ubuntu) DAV/2 PHP/5.2.9 configured -- resuming normal operations
[Fri Aug 21 09:43:18 2009] [crit] [client 192.168.1.101] (13)Permission denied: /var/www/web1/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable
[Fri Aug 21 09:43:20 2009] [crit] [client 192.168.1.101] (13)Permission denied: /var/www/web1/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable
[Fri Aug 21 09:45:15 2009] [notice] caught SIGTERM, shutting down
[Fri Aug 21 09:45:16 2009] [notice] Apache/2.2.11 (Ubuntu) DAV/2 PHP/5.2.9 configured -- resuming normal operations
[Fri Aug 21 09:45:22 2009] [crit] [client 192.168.1.101] (13)Permission denied: /var/www/web1/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable
[Fri Aug 21 09:54:28 2009] [error] [client 192.168.1.107] File does not exist: /var/www/web1/web/favicon.ico
[Fri Aug 21 09:54:31 2009] [error] [client 192.168.1.107] File does not exist: /var/www/web1/web/favicon.ico
[Fri Aug 21 09:54:52 2009] [error] [client 192.168.1.104] File does not exist: /var/www/web1/web/favicon.ico
[Fri Aug 21 09:54:55 2009] [error] [client 192.168.1.104] File does not exist: /var/www/web1/web/favicon.ico
[Fri Aug 21 09:57:52 2009] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Fri Aug 21 09:57:53 2009] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Fri Aug 21 09:57:53 2009] [warn] NameVirtualHost *:80 has no VirtualHosts
[Fri Aug 21 09:57:53 2009] [notice] Apache/2.2.11 (Ubuntu) DAV/2 PHP/5.2.9 configured -- resuming normal operations
[Fri Aug 21 09:58:35 2009] [error] [client 192.168.1.101] Could not fetch resource information.  [400, #0]
[Fri Aug 21 09:58:35 2009] [error] [client 192.168.1.101] (2)No such file or directory: The URL contains extraneous path components. The resource could not be identified.  [400, #0]
[Fri Aug 21 09:58:35 2009] [error] [client 192.168.1.101] Could not fetch resource information.  [400, #0]
[Fri Aug 21 09:58:35 2009] [error] [client 192.168.1.101] (2)No such file or directory: The URL contains extraneous path components. The resource could not be identified.  [400, #0]
**[Fri Aug 21 09:58:55 2009] [error] [client 192.168.1.101] Unable to PUT new contents for /webdav/index.htm.  [403, #0]**
**[Fri Aug 21 09:58:55 2009] [error] [client 192.168.1.101] (13)Permission denied: An error occurred while opening a resource.  [500, #0]**
[Fri Aug 21 10:01:20 2009] [error] [client 192.168.1.101] Unable to PUT new contents for /webdav/index.htm.  [403, #0]
[Fri Aug 21 10:01:20 2009] [error] [client 192.168.1.101] (13)Permission denied: An error occurred while opening a resource.  [500, #0]
[Fri Aug 21 10:04:12 2009] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Fri Aug 21 10:04:13 2009] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Fri Aug 21 10:04:13 2009] [warn] NameVirtualHost *:80 has no VirtualHosts
[Fri Aug 21 10:04:13 2009] [notice] Apache/2.2.11 (Ubuntu) DAV/2 PHP/5.2.9 configured -- resuming normal operations
[Fri Aug 21 10:04:16 2009] [notice] caught SIGTERM, shutting down
[Fri Aug 21 10:04:18 2009] [notice] Apache/2.2.11 (Ubuntu) DAV/2 PHP/5.2.9 configured -- resuming normal operations
[Fri Aug 21 10:04:38 2009] [error] [client 192.168.1.101] Unable to PUT new contents for /webdav/index.htm.  [403, #0]
[Fri Aug 21 10:04:38 2009] [error] [client 192.168.1.101] (13)Permission denied: An error occurred while opening a resource.  [500, #0]
[Fri Aug 21 10:07:48 2009] [notice] caught SIGTERM, shutting down
[Fri Aug 21 10:07:49 2009] [notice] Apache/2.2.11 (Ubuntu) DAV/2 PHP/5.2.9 configured -- resuming normal operations
[Fri Aug 21 10:07:55 2009] [error] [client 192.168.1.101] Unable to PUT new contents for /webdav/index.htm.  [403, #0]
[Fri Aug 21 10:07:55 2009] [error] [client 192.168.1.101] (13)Permission denied: An error occurred while opening a resource.  [500, #0]
[Fri Aug 21 10:08:17 2009] [error] [client 192.168.1.101] Could not fetch resource information.  [400, #0]
[Fri Aug 21 10:08:17 2009] [error] [client 192.168.1.101] (2)No such file or directory: The URL contains extraneous path components. The resource could not be identified.  [400, #0]
[Fri Aug 21 10:08:28 2009] [error] [client 192.168.1.101] Unable to PUT new contents for /webdav/index.htm.  [403, #0]
[Fri Aug 21 10:08:28 2009] [error] [client 192.168.1.101] (13)Permission denied: An error occurred while opening a resource.  [500, #0]
[Fri Aug 21 10:18:40 2009] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Fri Aug 21 10:18:40 2009] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Fri Aug 21 10:18:40 2009] [warn] NameVirtualHost *:80 has no VirtualHosts
[Fri Aug 21 10:18:40 2009] [notice] Apache/2.2.11 (Ubuntu) DAV/2 PHP/5.2.9 configured -- resuming normal operations
[Fri Aug 21 10:18:50 2009] [error] [client 192.168.1.101] Unable to PUT new contents for /webdav/index.htm.  [403, #0]
[Fri Aug 21 10:18:50 2009] [error] [client 192.168.1.101] (13)Permission denied: An error occurred while opening a resource.  [500, #0]
[Fri Aug 21 10:23:11 2009] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Fri Aug 21 10:23:11 2009] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Fri Aug 21 10:23:11 2009] [warn] NameVirtualHost *:80 has no VirtualHosts
[Fri Aug 21 10:23:11 2009] [notice] Apache/2.2.11 (Ubuntu) DAV/2 PHP/5.2.9 configured -- resuming normal operations
[Fri Aug 21 10:23:16 2009] [notice] caught SIGTERM, shutting down
[Fri Aug 21 10:23:17 2009] [notice] Apache/2.2.11 (Ubuntu) DAV/2 PHP/5.2.9 configured -- resuming normal operations
[Fri Aug 21 10:23:21 2009] [error] [client 192.168.1.101] Unable to PUT new contents for /webdav/index.htm.  [403, #0]
[Fri Aug 21 10:23:21 2009] [error] [client 192.168.1.101] (13)Permission denied: An error occurred while opening a resource.  [500, #0]

---

### Post by y@w on 2009-08-21
Yeah.. looks like a permissions issue. For some reason, the permissions that you listed before didn't have execute permissions on the directory.. I would start there. You'll want to do:

```
chmod -R +X /var/www/web
```


I'm not quite sure why it's owned by www-data with group root (the opposite that the how-to says), but that should be ok.. If that doesn't work, ls -l inside the /var/www/web directory so we can see the individual file permissions.

---

### Post by munchi3s on 2009-08-21
No such luck. Although I was able to add execute to the permissions of my "/var/www/web1/**web/** folder.

root@apache-webserver:/var/www/web1# ls -l
total 8
-rw-r----- 1 root     www-data   28 2009-08-21 09:56 passwd.dav
drwxrwxr-x 3 www-data root     4096 2009-08-21 10:47 web

 Thats what I'm looking at right now. I think there is an issue with the DAVlock system. I belive that my permissions would work if DAVlock system also worked. In this configuration. Do you know of a way to disable this feature of webdav or configur it to work? I may try to refollow the tutorial with a fresh install of ubuntu if I cannot get it to work.

---

### Post by volkswagner on 2009-08-21
I am not sure if you problem is the same as what I had.  Our error logs are different, but I was not using dreamweaver.

Here is my thread.

[http://ubuntuforums.org/showthread.php?t=1240886](http://ubuntuforums.org/showthread.php?t=1240886)

There is a link to a  better how-to in my solution post.

I must say I am a little jealous, as I had no response in one week to my thread, yet you had several in a few hours.  :(

---

### Post by munchi3s on 2009-08-21
When I was doing my research I checked yours out I'm going to reinstall ubuntu on this machine for a clean slate then I'm going to try the tutorial on your post. Our problems seem similar and it was your post that gave me the idea to check out the DAVlock system.
Thanks.

---

### Post by munchi3s on 2009-08-22
Well everything works well now. I combined [this tutorial]("http://www.howtoforge.com/how-to-set-up-webdav-with-apache2-on-ubuntu-8.10") that I found with [this tutorial ]("http://ubuntuforums.org/showthread.php?t=119228&highlight=howto+WebDAV")from volkswagner's post and it was the problem with DAVlock. This helped out a lot. When I recreated the server from the original tutorial and also created the DAVlock file of the 2nd one. I also edited the file paths where necessary. Thanks everyone who helped me with this problem.

---

