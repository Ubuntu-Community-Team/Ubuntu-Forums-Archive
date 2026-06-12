---
title: "Drupal won't install, access denied"
date: 2009-09-17
forum: Server Platforms
---

### Post by fela on 2009-09-17
I'm trying to install drupal on my server and I keep getting this frustrating error message:

Warning: include_once(./sites/default/settings.php) [function.include-once]: failed to open stream: Permission denied in /var/www/includes/bootstrap.inc on line 322

It avalanches into other error messages but I figured I'd better sort this one first.

I've temporarily chmodded the whole www folder as 777 (no need for security, I'm behind a NAT and this server isn't critical). Yet I still get the error message so something else must be wrong...I can't figure out what it is though.

Drupal also spits out: > The Drupal installer requires write permissions to ./sites/default/settings.php during the installation process. If you are unsure how to grant file permissions, please consult the on-line handbook.
The directory sites/default/files is not writable. An automated attempt to create this directory failed, possibly due to a permissions problem. To proceed with the installation, either create the directory and modify its permissions manually, or ensure that the installer has the permissions to create it automatically. For more information, please see INSTALL.txt or the on-line handbook.

But it must have access surely, because it's all at 777 permissions?

Thanks in advance

EDIT: nvm, I worked it out. Seems like I wasn't issuing the chmod command correctly or something. And I also found out that you HAVE to have 777 permissions? At least I do on my torrentflux folder and most of drupal...anyway it's fixed so yeah :)

---

### Post by BMWolf on 2010-04-13
I know you've figured this out quite some time ago, but I thought I'd chime in with what works for me and is safer than using 777 for your folders and files. I still don't know if it's the ideal way of doing things so I'm always looking for a safer solution.

My Situation:
I run Drupal at home on my server for testing purposes only and it is only available to my local network. Once settings have been checked and everything is working, I either re-do the steps on the live server(managed by my host) or sync everything with my ftp client and append the database changes. I have zero problems on the live site, I assume this is because my host's admins know what they are doing! :P

The Problem:
Apache runs as the user 'www-data' and if I've created the files/folders, they have MY_USERNAME as the owner, so Apache can't write to them. This is really only a problem for the '../defaults/files' folder and 'settings.php' file. Also, I can't change permissions, or save edits with my FTP client unless I'm the owner. 

My Solution:

Make sure I'm in the group 'www-data', not really needed but I do it anyway:
```
sudo usermod -a -G www-data MY_USERNAME
```

Make myself the owner of all the files in Drupal's install directory and set the group to 'www-data':
```
sudo chown -R MY_USERNAME:www-data DRUPAL_DIRECTORY

```


Then just change the files that need to be writable by apache to 775. I usually just do this in the ftp client since I'm logged in as the owner above, but you can do it via the shell too:
```
sudo chmod 775 DRUPAL_DIRECTORY/sites/default/files
sudo chmod 775 DRUPAL_DIRECTORY/sites/default/settings.php

```

Install Drupal, then change settings.php to 444 for protection:
```
sudo chmod 444 DRUPAL_DIRECTORY/sites/default/settings.php
```

Anyway, maybe that will work for someone else running a similar setup to myself. If this is your live server and it's accessible by the outside world, don't trust me and find someone that really knows what they are doing! I don't see any problems with the above setup in the wild, but you never know.

---

