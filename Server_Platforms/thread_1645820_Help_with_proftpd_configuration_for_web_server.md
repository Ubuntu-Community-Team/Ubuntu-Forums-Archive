---
title: "Help with proftpd configuration for web server"
date: 2010-12-15
forum: Server Platforms
---

### Post by Invex09 on 2010-12-15
I'm using Ubuntu 10.10 to run a web server. I installed LAMP and have verified that it works without a problem. For an FTP server, I installed proftpd. Proftpd is currently working, but I'm looking for some help in getting it set the way I would like. 

My goal is to be able to add/edit multiple users that have read/write/execute permissions to the /var/www directory (and only that directory) that currently contains all of my websites. Currently, I can FTP into my machine with my ubuntu account credentials. This gives me access to the whole file system (as far as I can tell). I was able to download files from my linux /home directory as well as the /var/www directory. However, when I tried to upload files to the /var/www, I was unable to do so because of insufficient permission.

This made sense to me as the owner by default of the /var/www directory was root. Thus, I used the following command to change the owner and owner group of the folder

```
chown -R www-data:www-data /var/www
```

I used www-data as the user/group because from what I've read online this appears to be the user/group used by Apache2. I then made the following change to my /etc/proftpd/proftpd.conf file:

```
# Set the user and group that the server normally runs at.
#User             proftpd
#Group           nogroup
User                www-data
Group              www-data
```

I commend out the default values for the server to run at and changed them to www-data for both user and group. I thought this would mean that when I attempted to create a file in the directory, it would create it under www-data:www-data, or the owner of the /var/www directory. Obviously this was not the case. When I try to create the file, is it using my ubuntu account? This is the first bump in the road I've encountered when trying to reach my goal above (ability to add/edit multiple FTP users with full permissions to only /var/www folder). Thanks in advance for any help!

---

### Post by Invex09 on 2010-12-16
I actually was able to take a step in the right direction toward the functionality I desire using the "DefaultRoot" directive in the proftpd.conf file. Using this line:

```
DefaultRoot /var/www ftpusers
```

I set everyone in my ftpusers group to only have access to the var/www directory.

The information found at this link: *proftpd.org/docs/howto/Chroot.html* ended up being a great resource. I was able to learn a lot by going through that. 

The main problem I'm having now deals with permissions. I made a group called 'ftpusers' and set their default root to /var/www which correctly locks them to that folder when they login via FTP. Now however, they don't have permission to write/overwrite in this directory as well as make new directories. What is the best way to set this? Also, if an ftp user uploads a PHP script (or some other server-side script) that tries to modify the file system, what permissions are used for the script? Because ideally if a user has FTP access to the folder and can read/write/execute, I'd like any script that user uploads to have the same permissions as the user. Thanks in advance for any help!

---

