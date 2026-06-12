---
title: "useradd -d /var/www -G www-data - ProFTPD Login 530"
date: 2014-09-19
forum: Server Platforms
---

### Post by 3kynox2 on 2014-09-19
Hello folks,

All is in the title, I try to create a user with apache directory as default folder, and when I try to log in with ftp, got 530 error.

When creating a normal user (in home directory), proftpd is working correctly.

Any help possible please ?

---

### Post by Lars Noodén on 2014-09-19
There are two or three issues here.  

One is that the group www-data should generally not have any other members besides the web server itself.  Nor should it be able to write, in general, to any directory which the web server can read.  The reason for the www-data user and group is to provide an unprivileged user/group for the web server.  

Another is that in order to write to the directory, you need to set the permissions.  If you are the only user of /var/www/ then you can simply take ownership of it with [chown](http://manpages.ubuntu.com/manpages/trusty/en/man1/chown.1.html).  If you are not the only user then you need to share it via a group, so in that case make a new group, e.g. webmasters, set the group ownership of that directory to that group, add your users to that group, and set write permissions plus sgid.  These permissions are probably what will answer your question.

Lastly, are you sure your case really requires actual FTP and not SFTP? If you are looking for a way to transfer files, then you should do it securely and [abandon FTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp) for SFTP.  Support  for SFTP is built into all the regular file managers as well as tools like FileZilla.

---

### Post by 3kynox2 on 2014-09-19
Hello and thanks for your answer.

1. I can try with another group name or user creation (that I chown to /var/www/html in addition of its /home/user directory) without any changes. For example, I created user ekynox with home directory at /home/ekynox and chowned to /var/www/html, I log in that user using filezilla with success, but when moving to /var/www folder, I got no permissions inside (write, chmod, ...)

2. sudo chmod -R g+rw /var/www/html in and makes no changes too. As I said in #1, chown do no changes too.

3. Yes, I would like proftpd support in that folder, and not only sftp.

Still stuck.

---

### Post by Lars Noodén on 2014-09-19
> **3kynox2 said:**
> 
2. sudo chmod -R g+rw /var/www/html in and makes no changes too. As I said in #1, chown do no changes too.

If you go with groups, make a special group for the sharing, and be sure to set the set-group-ID bit on the directories themselves:

```

# do once
sudo addgroup webmasters
sudo chgrp -R webmasters /var/www

sudo find /var/www -type d -exec chmod g=rwx**s** "{}" \;
sudo find /var/www -type f -exec chmod g=rws "{}" \;

# repeat for each user:
sudo gpasswd --add ekynox webmasters

```

The files don't need that bit set.

---

