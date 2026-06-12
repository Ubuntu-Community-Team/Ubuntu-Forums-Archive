---
title: "Apache2 Permission issue"
date: 2008-09-09
forum: Server Platforms
---

### Post by keatonvictor on 2008-09-09
Hi everyone

I recently switched from Fedora to Ubuntu as I found Ubuntu a lot easier to manage. However I have had one or two problems. The one I wish to resolve is with my apache web server.

I setup ftp using vsftpd and created a user called "web" which had its home directory mapped to /var/www so I could login and make changes to the root directory of the server via a client such as Filezilla.

However Ever since I did that I get the following error when going to my web address.

You don't have permission to access /index.html on this server.

I presumed this may be a issue as I have /etc/sudoers set to:

web ALL=(ALL) ALL

To allow modification of /var/www directory

Any ideas how I can resolve this issue ?

---

### Post by forger on 2008-09-09
Can you post the output of:
```
ls -l /var/www
ls -l /home/web
```

I'm not sure, but I think you have to allow a common group in which the user web is in.

Perhaps this is helpful:
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch20_:_The_Apache_Web_Server#Where_To_Put_Your_Web_Pages](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch20_:_The_Apache_Web_Server#Where_To_Put_Your_Web_Pages)
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch20_:_The_Apache_Web_Server#File_Permissions_And_Apache](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch20_:_The_Apache_Web_Server#File_Permissions_And_Apache)

[http://www.debian-administration.org/articles/412](http://www.debian-administration.org/articles/412)

---

