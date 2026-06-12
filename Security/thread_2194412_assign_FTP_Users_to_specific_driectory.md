---
title: "assign FTP Users to specific driectory"
date: 2013-12-18
forum: Security
---

### Post by singhsukhwinder4143 on 2013-12-18
I have installed vsftpd in ubuntu server 12.04 LTS and i want to restrict ftp users restricted to there respective directories
 for e.g.  i have /var/www/folder1 and /var/www/folder2 and two ftp users ftpuser1 and ftpuser2 

ftpuser1 is assigned to /var/www/folder1
ftpuser2 is assigned to /var/www/folder2

But when i connect it thru Filezilla then ftpuser1 and ftpuser2 can access all files of server. 



i want these users restricted to assigned folders.

Please help me :(

---

### Post by tfrue on 2013-12-18
I'm not too sure on how to use vsftpd, but I know that Samba handles being a file server just fine. It's easy to set up, super secure, and can be accessed from your Window's machine.

---

### Post by tfrue on 2013-12-18
In Samba, you define shares like:```

[share]
comment= Simple Share
path= path/to/share
valid users= chris #So here is your users restricted to certain folders.
read only= no
```
That a general idea of how you use Samba, and then you can access that folder from the network and provide the proper credentials. If you're interested I'll show you more configurations you can use.

---

### Post by renebarbosa on 2013-12-18
Hello, 

You can enable userDir in your web server[1] and then, enable user chroot[2] in your FTP server. It will make each user to store your files in /home/$USR/public_html and access that directory using FTP.

I hope it helps. :)

[1] [http://httpd.apache.org/docs/trunk/howto/public_html.html](http://httpd.apache.org/docs/trunk/howto/public_html.html)
[2] [http://www.cyberciti.biz/tips/vsftp-chroot-users-limit-to-only-their-home-directory.html](http://www.cyberciti.biz/tips/vsftp-chroot-users-limit-to-only-their-home-directory.html)

---

### Post by leftyleo on 2014-02-26
I believe there is a vsftp.config file that you can edit to chroot users (lock them into their own directory tree) and there is also then an option to enable to check against a chroot list file too 

(be sure to make a backup of the original before making  changes)

---

