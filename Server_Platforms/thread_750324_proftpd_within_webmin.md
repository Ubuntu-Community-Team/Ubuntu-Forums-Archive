---
title: "proftpd within webmin"
date: 2008-04-09
forum: Server Platforms
---

### Post by ianb72 on 2008-04-09
I am running dapper server with webmin and I installed proftpd as guide in [Lamp for Noobs]("http://www.cjfay.com/lamp.html")

I have added a new user called admin and a group called ftp, I added the user admin and the group ftp to the www-data group/user through the System/Administration menu on the desktop.

when I try to log on to the ftp through a proxy by [ftp://admin@myip](ftp://admin@myip) all I get is an FTP ERROR and a report saying 530 login incorrect.

what am I doing wrong??

I have just tried [ftp://admin@localhost](ftp://admin@localhost) and all is well it asks for my password and logs me in fine, but just not over the proxy, my IP address at the moment is 79.73.239.142 if that helps anyone

Ian

---

### Post by ianb72 on 2008-04-09
I've managed to sort the access problem but how do I restrict access to only certain files and folders, mainly my website content?

Ian

---

### Post by kebes on 2008-04-09
You can "chroot" FTP users, which basically means that the user, once logged-in, can only see the sub-section of the filesystem that you let him see.

To do this, use the "DefaultRoot" command in your proftp config file (which is probably located at "/etc/proftpd/proftpd.conf"). Details about this directive can be found [here]("http://www.proftpd.org/docs/directives/linked/config_ref_DefaultRoot.html").

As an example, if you have an FTP user "bob" and you only want him to be able to access "/var/www/bobsite/" then you would open "/etc/proftpd/proftpd.conf" and add a line like:

```

DefaultRoot /var/www/bobsite/ bob

```

Than save the file and restart the FTP server.

---

