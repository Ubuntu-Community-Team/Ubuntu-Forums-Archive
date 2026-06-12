---
title: "Apache2 problem"
date: 2011-07-23
forum: Server Platforms
---

### Post by atom94 on 2011-07-23
Hi,

I am trying to set up a home web server for my personal site using Ubuntu 11.04 and Apache. I have set up a user called www and given it FTP access to its home area (/home/www) using vsftpd. I then edited /etc/apache2/sites-available/default and set the DocumentRoot directive to /home/www. When I made a test index.html file in that directory it worked fine. Then I FTP'd to the server (as www) from another PC and uploaded the site files. Now when I try to access the site I get an error 403 (forbidden).

Obviously I'm doing something wrong here but I'm not sure what. What should I do to fix this.

Thanks

---

### Post by brighty22 on 2011-07-23
The permissions on the file you "FTP'd" will be such that apache cannot read them. Run ls -al in the www folder to see. From there you can chown the file so the owner/group is www, or for a more permanent solution, find out the group owner of the offending file (ls -al will tell you), and add your www user to that group. That will enable apache to server any files you transfer to the server in the future without doing any permissions editing after each transfer before you can see them.

---

### Post by atom94 on 2011-07-23
Problem solved. I uncommented the following line in vsftpd.conf
```
local_umask=022
```

apparently the default in vsftpd (if you don't uncomment this line) is 077, which means only the www user was getting read permissions on the uploading files. apache, running under a different user, wasn't.

thanks

---

