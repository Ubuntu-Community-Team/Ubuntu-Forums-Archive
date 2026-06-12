---
title: "Permission issues: access file via Apache that were loaded via FTP"
date: 2018-01-19
forum: Server Platforms
---

### Post by drieske2 on 2018-01-19
Hi all,

I must admit, I'm quiet new to Ubuntu. So my apologies if my question is a bit too easy.
I've already spend quiet some time on tutorials setting up Ubuntu, LAMP, and an FTP client. This has gone pretty well.

However, I can't figure out the following.

I've set up Apache, and all the files I put in /var/html/webserver/.../ are accessible via HTTP. So that runs fine. I used [this tutorial]("https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-16-04").
I've also installed and configured VSFTPD. I used [this tutorial]("https://www.digitalocean.com/community/tutorials/how-to-set-up-vsftpd-for-a-user-s-directory-on-ubuntu-16-04").
I created a user (let's call it "apache_dries"), and I'm able to connect to my Ubuntu installation using FTP and put files in it's home directory.

I was looking for a way to allow this ftp user also put files on /var/html/. I've found [this tutorial]("http://www.ducea.com/2006/07/27/allowing-ftp-access-to-files-outside-the-home-directory-chroot/"). Basically, I had to "bind" the two folders together. So I did this:
```
mount --bind /var/www/html/webserver /home/apache_dries/ftp/files
```

That seemed to work. I am now able to see files in /var/www/html/webserver via FTP directory listing.

However, I noticed that:
* Files that are created by my administrative user (using ssh) in /var/www/html/webserver can not be removed/modified using FTP;
* Files that are uploaded via ftp (with user apache_dries) can not be accessed using my administrative user (unless I sudo). Also, Apache gives a "permission denied" when I try to access these files.
* I tried "sudo chmod -R go+rx /var/www/html/webserver/", that made sure that all current files in the directory were accessible via Apache. But when new files are loaded via FTP, they are not accessible. I want to avoid running chmod-commands after every load of files;
* And somehow I broke the write-access of my FTP user to the /var/html/... folder. It is able to see, but not create/modify files anymore.

So what I want is that:
* My FTP user (apache_dries) has read/write access to /var/html/...;
* Any file that has been loaded by apache_dries needs to be accessible by my apache server;

What am I doing wrong?

---

### Post by TheFu on 2018-01-19
Welcome to the forums.

Unix and Linux are multi-user operating systems.  This means that every file, directory and process runs with a specific userid and a specific groupid.  Management of users and groups is a fundamental skill for Unix security and running any server.

There are tutorials for learning directory and file permissions, but really the best way to learn them is to create 3 userids and 3 groups then mix and match which users are in which groups.  Then create a temporary set of files and directories and spend 45 minutes using chmod and chgrp trying every possible combination of permissions, groups on the files, directories and files inside the directories.

Until you take the time to do that stuff, owners, groups and permissions will always seem a mystery.  Hours, days, weeks, months of frustration will happen until you learn it.  It is central to everything on a server.  Practice is the only way, but until you get the 'ah ha'  moment, it won't stick.  Unix permissions are very elegant.

I wouldn't use bind-mounts when something as simple as proper group management is all that you need.  In 25 yrs as a Unix admin, I've used bind-mounts less than 5 times and not at all right now.  They are a dangerous hack, IMHO.  Heck, I'd rather see ACLs used instead of bind-mounts.

Working together on Unix:
*    Put everyone into the same group (perhaps www-data is what you want?).
*    Create a directory where they can share files (somewhere for apache?).
*    Make the group on that empty directory have rws permissions
```

           $ sudo gpasswd -M  user1,user2,user3  ourgroup
           $ mkdir -p /tmp/Workspace
           $ cd /tmp/
           $ chmod g=rwxs Workspace
           $ ls -Fl Workspace
              drwxrws---   owner    group    Workspace/ 
           $ chgrp ourgroup Workspace
           $ ls -Fl Workspace
              drwxrws---   owner    ourgroup    Workspace/ 
```
Obviously, you'll want to learn this in a temporary place and see that it works fine.

If you want to make getting from a HOME directory to an apache static files directory easy, use a symbolic link.```

           $ cd ; ln -s /tmp/Workspace 
``` That will make a ~/Workspace link.

And my last piece of advice is to remove and purge any plain FTP server from your system. Use ssh and sftp instead.  sftp provides an FTP-like interface, but doesn't transmit logins or data unencrypted.  Plain FTP should have died out by 2000 and if the webhost doesn't support sftp, then you should fire them.  There are many other reasons NOT to use plain FTP.  Google will find those.

IMHO.

Good luck.

---

### Post by drieske2 on 2018-01-20
Hi!

Thank you for your support.
I've been reading about users/groups/chmod/chown and stuff yesterday and today. I think I understand the basics.
What I have done now:
* I've made sure that all current files in var/www/html are owned by the group www-data (that wasn't the case);
* I've added the ftp-user to the group www-data. I also made sure that www-data is now the primary group of my ftp user. So if it is uploading new files, those files will be part of www-data group;
* I've change the umask settings so that all new files uploaded via ftp now have read-rights to www-data;

It now works, but with the bind-workaround. I haven't found another solution. The problem is that you are chrooted when you log on via vsftp. That means that usr/home/ftpuser is the root folder and you aren't allowed to "break out" of that root. Hence the bind-workaround. 

And I fully agree with your remarks on FTP security. Unfortunately, I have some legacy software here that is only able to exchange files via FTP (not even SFTP). I think the security implications are minimal, since both servers are on an internal network and the data is not really sensitive.

Thanks!

---

### Post by TheFu on 2018-01-20
If the legacy software is calling out to an FTP program, you can trick it into using sftp with an alias.  That would remove many of the security problems that plain FTP forces.

Of course, it isn't always possible.  We haven't used plain FTP in 15+ yrs anywhere I worked, so for plain FTP security, you'll need to follow some respected guides from reputable sources.  We've always been able to use an alias for ftp as sftp and that worked.

Making the ftp user primary group be www-data isn't something I would do.  It should be a secondary group and that really shouldn't matter if you setup the directories correctly.  Actually, I would never allow any uploads to go directly into a website.  Always upload somewhere else and have a script test for bad files, reencode videos and images (to prevent embedded hacking), and only then move things over to where I want them.  Might also want to make a backup of the source files for legal reasons which are kept 30+ days, so if anything bad happens, there is traceability.

Internal servers do limit risks, provided the people with access are limited and trusted.  I've seen some huge abuse of internal servers in corporate environments, however.

---

### Post by drieske2 on 2018-01-22
Hi,
Thanks for your advice. I'll review the setup of my permissions, and I'll see if I can use SFTP with an alias.

And the script approach is a good idea, that way I don't need the "mount --bind" approach (and I'm even more flexible with my permissions). All the files that will be uploaded have a specific naming convention, so using the script I can make sure only the relevant files are copied. I didn't consider that, thanks!

---

