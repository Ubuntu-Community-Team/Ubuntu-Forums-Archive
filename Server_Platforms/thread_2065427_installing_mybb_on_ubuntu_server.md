---
title: "installing mybb on ubuntu server"
date: 2012-10-01
forum: Server Platforms
---

### Post by micahpage on 2012-10-01
I tried going through this tutorial
[http://www.upubuntu.com/2012/03/how-to-install-latest-version-of-mybb.html]("http://www.upubuntu.com/2012/03/how-to-install-latest-version-of-mybb.html")

to get this set up, but when i go to the link 
```
http://localhost/forums/install/
```
that the tutorial shows to go to, i get a 403 Forbidden error saying i do not have permission

i did this command and still got no luck
```
sudo chmod 755 /var/www/mybb
```

Is this the correct permissions for it? OR do I have to add something to the apache config file?

---

### Post by lisati on 2012-10-01
*Thread moved to **Server Platforms**.*

A "quick and nasty" alternative to the chmod method that is commonly recommended is something like this:
```
sudo chown www-data /var/www/mybb
```

Note: from a security perspective, doing this for the entire mybb directory might not be advisable.

---

### Post by micahpage on 2012-10-01
```
sudo chown www-data /var/www/forums

```

i did this and i still get a 403

> doing this for the entire mybb directory might not be advisable.
what exactly would be advisable?


i am kind of confused on how to get this forum working



EDIT:
whoops sorry i was looking at another directory for the 403 error, when i try the mybb i get a 500 error```

The website encountered an error while retrieving http://www.metulburr.com/forums/index.php. It may be down for maintenance or configured incorrectly.
```

---

### Post by hasan.akgoz on 2012-10-02
Can you try again above command ?
 
sudo chown -R www-data /var/www/forums and also Can you give me output ?
 
1- tail -f  /var/log/apache2/error.log
2- ls -hla /var/www

---

### Post by micahpage on 2012-10-02
here are all those cmds ran, with outputs, 

```
metulburr@ubuntu:~$ ls -hla /var/www
total 39M
drwxr-xr-x  4 root     root 4.0K Oct  2 02:52 .
drwxr-xr-x 14 root     root 4.0K Sep 16 23:34 ..
-rw-r--r--  1 root     root 7.3K Oct  1 09:00 alchemy.zip
-rw-rw-r--  1 root     root 162K Aug  2  2011 bg1.jpg
-rw-r--r--  1 root     root  510 Oct  1 09:00 change_root.zip
-rw-r--r--  1 root     root 3.0K Oct  1 09:00 codesnip.zip
-rw-r--r--  1 root     root  199 Oct  2 01:48 contact.html
-rw-r--r--  1 root     root  196 Oct  2 01:48 contact.html~
-rw-r--r--  1 root     root 6.9K Oct  1 09:01 crapdealer.zip
-rw-rw-r--  1 root     root 5.5K Oct  1 09:29 Debugging.html
-rw-rw-r--  1 root     root 5.5K Oct  1 07:12 Debugging.html~
-rw-r--r--  1 root     root 1.1K Oct  1 09:01 dirsearch.zip
-rw-r--r--  1 root     root 3.1K Oct  2 00:31 donate.html
-rw-r--r--  1 root     root 3.1K Oct  2 00:31 donate.html~
-rw-r--r--  1 root     root  854 Sep 29 02:27 down.gif
drwxr-xr-x  2 root     root 4.0K Oct  1 09:10 download
-rw-r--r--  1 root     root  535 Oct  1 09:27 downloads.html
-rw-r--r--  1 root     root  530 Oct  1 09:26 downloads.html~
-rw-rw-r--  1 root     root 5.0K Oct  1 23:40 Executing.html
-rw-rw-r--  1 root     root 5.1K Oct  1 09:30 Executing.html~
-rw-r--r--  1 root     root 1.7K Oct  1 09:01 extcopy.zip
-rw-r--r--  1 root     root  24K Sep 28 17:10 forum_logo.png
drwxr-xr-x 10 www-data root 4.0K Oct  1 04:37 forums
-rw-r--r--  1 root     root    0 Sep 30 17:32 header.html~
-rw-r--r--  1 root     root 1.3K Oct  2 02:52 header.shtml
-rw-r--r--  1 root     root 1.3K Oct  2 02:51 header.shtml~
-rw-r--r--  1 root     root 5.7K Oct  1 07:45 html_test.html
-rw-r--r--  1 root     root 5.7K Oct  1 07:32 html_test.html~
-rw-r--r--  1 root     root  29K Oct  1 20:47 htop.jpg
-rw-r--r--  1 root     root  283 Oct  1 09:30 index2.html
-rw-r--r--  1 root     root  234 Sep 28 18:57 index2.html~
-rw-r--r--  1 root     root  961 Oct  2 02:23 index.html
-rw-r--r--  1 root     root 2.2K Oct  2 02:22 index.html~
-rw-r--r--  1 root     root 1.7K Sep 29 02:27 jqueryslidemenu.css
-rw-r--r--  1 root     root 2.5K Sep 29 02:28 jqueryslidemenu.js
-rw-r--r--  1 root     root  11K Oct  1 08:24 linux_header_crop.jpg
-rw-r--r--  1 root     root   54 Oct  1 20:31 linux.html
-rw-r--r--  1 root     root    0 Oct  1 20:30 linux.html~
-rw-r--r--  1 root     root  21M Sep 30 03:03 megadeth3.mp4
-rw-r--r--  1 root     root  18M Sep 30 02:58 megadeth.mp4
-rw-r--r--  1 root     root 6.4K Oct  1 09:01 metulbot.zip
-rw-r--r--  1 root     root 312K Sep 28 23:25 movie.mp4
-rw-r--r--  1 root     root 5.3K Sep 29 00:25 outdoor.jpg
-rw-rw-r--  1 root     root  113 Oct  1 09:30 python_index.html
-rw-rw-r--  1 root     root  111 Oct  1 07:11 python_index.html~
-rw-r--r--  1 root     root 4.6K Oct  1 09:01 quitsmoking.zip
-rw-r--r--  1 root     root 1.7K Oct  1 23:46 Resources.html
-rw-r--r--  1 root     root 1.6K Oct  1 19:23 Resources.html~
-rw-r--r--  1 root     root  860 Sep 29 02:27 right.gif
-rw-rw-r--  1 root     root 2.7K Oct  1 09:30 String.html
-rw-rw-r--  1 root     root 2.7K Oct  1 07:13 String.html~
-rw-r--r--  1 root     root  900 Oct  1 09:01 syscheck.zip
-rw-r--r--  1 root     root 2.4K Sep 29 01:35 tetris50l.py
-rw-r--r--  1 root     root 1.9K Sep 28 08:36 tux.jpg
metulburr@ubuntu:~$ 

```

```
metulburr@ubuntu:~$ tail -f /var/log/apache2/error.log
[Tue Oct 02 02:50:32 2012] [error] [client 69.205.234.41] File does not exist: /var/www/favicon.ico
[Tue Oct 02 02:50:37 2012] [error] [client 69.205.234.41] File does not exist: /var/www/favicon.ico
[Tue Oct 02 02:51:49 2012] [error] [client 69.205.234.41] File does not exist: /var/www/favicon.ico
[Tue Oct 02 02:52:04 2012] [error] [client 69.205.234.41] File does not exist: /var/www/favicon.ico
[Tue Oct 02 02:52:12 2012] [error] [client 69.205.234.41] File does not exist: /var/www/favicon.ico
[Tue Oct 02 02:52:14 2012] [error] [client 69.205.234.41] File does not exist: /var/www/favicon.ico
[Tue Oct 02 02:52:16 2012] [error] [client 69.205.234.41] File does not exist: /var/www/favicon.ico
[Tue Oct 02 02:52:24 2012] [error] [client 69.205.234.41] File does not exist: /var/www/favicon.ico
[Tue Oct 02 02:52:27 2012] [error] [client 69.205.234.41] File does not exist: /var/www/favicon.ico
[Tue Oct 02 02:52:29 2012] [error] [client 69.205.234.41] File does not exist: /var/www/favicon.ico



```


```
metulburr@ubuntu:~$ sudo chown -R www-data /var/www/forums
[sudo] password for metulburr: 
metulburr@ubuntu:~$
```

---

### Post by hasan.akgoz on 2012-10-02
Would you please try again enter the following console commands?
- sudo chown -R www-data /var/www
-sudo chmod -R 777 /var/www/forum

---

### Post by micahpage on 2012-10-03
oh sorry i must not have posted the edit.

It did finally work, i think it was your code
```
sudo chown -R www-data /var/www/forums
```
I am not sure why it didn't work the first time and now it did

thanks for all your help

---

### Post by usalug on 2012-10-03
The -R made the chown recursive and changed all the files from the top level /var/www/forums down, including subfolders, the orginal command didn't have that.

---

