---
title: "Issues with Apache / PHP setup"
date: 2009-08-28
forum: Server Platforms
---

### Post by rosarch on 2009-08-28
I have just installed the latest version of mythbuntu on a server, I am using it is a backend and front end, I have set up hellanzb and hellaworld (great program) and am also using hellavcr (excellent program)

The issue I am having seems to be with php, hellaworld uses php and I normaly browse to it using [http://ip/hellaworld](http://ip/hellaworld), however this is only displaying the directory index and I have to click on the index.php file to load the page. This is only a bit annoying and I could have lived with it, however hellavcr is also written in php, this needs php as it uses simple xml and the page doesn't work as expected.

One confusing thing is that mythweb works and that is also php
although it is symlinked to another directory

root@rosarch-desktop:/var/www# ls -al
total 28
drwxr-xr-x  6 root root 4096 2009-08-28 00:13 .
drwxr-xr-x 15 root root 4096 2009-04-20 16:20 ..
drwxr-xr-x  7 root root 4096 2009-08-28 14:41 hellavcr
drwxr-xr-x  8 root root 4096 2009-08-27 20:31 hellaworld
-rw-r--r--  1 root root   45 2009-04-20 16:22 index.html
drwxr-xr-x  3 root root 4096 2009-08-28 00:13 monitorix
lrwxrwxrwx  1 root root   25 2009-08-27 03:03 mythweb -> /usr/share/mythtv/mythweb

I have updated with the latest apache2 and php 5

Anyone got any ideas?  :confused:

---

### Post by rosarch on 2009-08-29
(apologies for the double post but thought this question would be more appropriate in this section of the forum)

I have just installed the latest version of mythbuntu on a server, I am using it is a backend and front end, I have set up hellanzb and hellaworld  and am also using hellavcr 

The issue I am having seems to be with php, hellaworld uses php and I normaly browse to it using [http://ip/hellaworld](http://ip/hellaworld), however this is only displaying the directory index and I have to click on the index.php file to load the page. This is only a bit annoying and I could have lived with it, however hellavcr is also written in php, this needs php as it uses simple xml and the page doesn't work as expected.

One confusing thing is that mythweb works and that is also php
although it is symlinked to another directory

root@rosarch-desktop:/var/www# ls -al
total 28
drwxr-xr-x 6 root root 4096 2009-08-28 00:13 .
drwxr-xr-x 15 root root 4096 2009-04-20 16:20 ..
drwxr-xr-x 7 root root 4096 2009-08-28 14:41 hellavcr
drwxr-xr-x 8 root root 4096 2009-08-27 20:31 hellaworld
-rw-r--r-- 1 root root 45 2009-04-20 16:22 index.html
drwxr-xr-x 3 root root 4096 2009-08-28 00:13 monitorix
lrwxrwxrwx 1 root root 25 2009-08-27 03:03 mythweb -> /usr/share/mythtv/mythweb

I have updated with the latest apache2 and php 5

I have tested with a basic php test page as well with the same results.

Anyone got any ideas?

---

### Post by rosarch on 2009-08-29
Made some progress using:

sudo apt-get purge libapache2-mod-php5
sudo apt-get install libapache2-mod-php5

Both hellaworld and hellavcr are now working but mythweb has disappeared it was symlinked in the /var/www directory to /usr/share/mythtv/mythweb but I cant find it anymore....

Never mind I never used it anyway and use the other progams on a daily basis so am happy.

---

### Post by rosarch on 2009-08-29
Resolved (sort of) by doing the following:

sudo apt-get purge libapache2-mod-php5
sudo apt-get install libapache2-mod-php5

---

