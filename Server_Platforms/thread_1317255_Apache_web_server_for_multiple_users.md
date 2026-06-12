---
title: "Apache web server for multiple users"
date: 2009-11-06
forum: Server Platforms
---

### Post by makoReactor on 2009-11-06
I am trying to make a single web-server for multiple users to be able to log in and make their own sites, but not be able to log into anyone else's webspace.

For example, having something like [http://www.domain.com/~user_name](http://www.domain.com/~user_name) 

with their own FTP to access just the /var/www/user_name section

I have looked everywhere and cannot find a guide to help me!

---

### Post by volkswagner on 2009-11-06
You may find what you need with ISPconfig.

---

### Post by BQAggie2006 on 2009-11-06
Basically, you need to configure apache to allow for per user directories :
[http://httpd.apache.org/docs/2.0/howto/public_html.html](http://httpd.apache.org/docs/2.0/howto/public_html.html)
[http://ubuntuforums.org/showthread.php?t=734373](http://ubuntuforums.org/showthread.php?t=734373)

And then, configure the ftp server to allow local logins and chroot the users to their home dir: 
[https://help.ubuntu.com/9.10/serverguide/C/ftp-server.html](https://help.ubuntu.com/9.10/serverguide/C/ftp-server.html)

---

### Post by GCoffee on 2009-11-06
As I was going to say, Chroot (Jailing) users to there home directories would be step 1.

Alternatively you can chroot everyone in a certain group to their home directories, but not others.

This can be done in ProFTPD - I think its something like DefaultRoot in the config.

Sorry I cant be of more help.

---

### Post by Thirtysixway on 2009-11-06
> **GCoffee said:**
> As I was going to say, Chroot (Jailing) users to there home directories would be step 1.

Alternatively you can chroot everyone in a certain group to their home directories, but not others.

This can be done in ProFTPD - I think its something like DefaultRoot in the config.

Sorry I cant be of more help.

That's what I've done.  I setup apache to use mod_dir so that each user has a public_html folder they can put stuff in.  Then setup proftpd to jail each user to their home directory.

There may be some other security things to take into consideration such as php's ability to include another users files.  There are some php settings you can mess with to disable this (I can't recall which ones...) google could probably help with that step.

Also, using phpmyadmin you'll have to play around with the settings.  Have it so each user can access username_* databases only and then they have their own private databases.

---

### Post by Lars Noodén on 2009-11-07
> **Thirtysixway said:**
> That's what I've done.  I setup apache to use mod_dir so that each user has a public_html folder they can put stuff in.  Then setup proftpd to jail each user to their home directory.

There may be some other security things to take into consideration ...

Can I ask *if* FTP was selected on purpose?  If so, why?
Was there a document online that suggested using FTP to manage web server content?

If you are interested in improving security then you can rather painlessly chroot SFTP (not FTPS) users.  OpenSSH-server is probably already installed for you to manage the system administration, the sftp subsystem is built in.  

You can force everyone into sftp and chroot in their home directories, and the allow a few exceptions to run wild:

```

# add near end of /etc/ssh/sshd_config

# all users except members of adm get chrooted
# and must use sftp, no shell access
Match Group !adm
   ChrootDirectory /var/www
   ForceCommand internal-sftp

```

---

### Post by Thirtysixway on 2009-11-07
I selected FTP because that's what I had setup at the time. Since then I've stopped hosting for other people because of bandwidth reasons and actually I turned off port forwarding for FTP to be more secure (intranet access only for ftp.)

I may look into setting up sftp in the future, however.

---

