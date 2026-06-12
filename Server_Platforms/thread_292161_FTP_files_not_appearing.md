---
title: "FTP files not appearing"
date: 2006-11-03
forum: Server Platforms
---

### Post by dolbex on 2006-11-03
Howdy,

I apologize for the massive amount of n00b that I am probably bleeding out right now, but this is my first true Linux experience, and so far a very good one.  I have installed Apache, PHP, and mySQL successfully (I found afterwards I should have just installed the server, heh).  I also have proftpd up and running.

Ok, so here's the problem.  If I create files in my /var/www folder on the Ubuntu machine everything works peachy.  However, if I FTP in via proftpd and upload those files Apache fails to serve them.  It's not a permission problem - I have chmod'ed them to 777 and still nothing...  Anything I might have missed in the install / config that would cause this to happen?

Thanks in advance!

---

### Post by dolbex on 2006-11-03
One quick note:

proftpd's default location was my home folder.  I created what I thought was a shortcut to '/var/www/' and found that it seemed to work.  Now, when I ftp in I see the files that I have uploaded.  However, If I navigate directly to '/var/www/' on the Ubuntu machine I don't see the files I have uploaded.  However, if I go to my home folder and click on the shortcut I do see the files.  What am I doing wrong?

---

