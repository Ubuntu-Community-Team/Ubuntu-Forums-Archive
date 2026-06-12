---
title: "Chroot with mod_sec ... ?"
date: 2005-10-29
forum: Server Platforms
---

### Post by dbee on 2005-10-29
Got a bit of a problem again 

[Sat Oct 29 16:00:27 2005] [notice] mod_security: chroot successful, path=/chroot/apache
[Sat Oct 29 16:00:27 2005] [error] (2)No such file or directory: could not create /var/run/apache2.pid
[Sat Oct 29 16:00:27 2005] [error] apache2: could not log pid to file /var/run/apache2.pid

mod_security for apache won't work, it's not a permissions issue as I've set the folder to 777

Help !!!

---

### Post by dbee on 2005-10-29
The whole thing has gone down the plug hole again,
I get this from the error log when I start apache

[Sat Oct 29 16:54:40 2005] [error] [client 127.0.0.1] File does not exist: /var/www

and when I try to restart apache 

root@ubuntu:/chroot # /etc/init.d/apache2 start
 * Starting web server (Apache2)...
(98)Address already in use: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
 *able to open logs      

Even if I kill apache by the all the apache processes on ps -aux , it doesn't make a difference

It can't be a permission problem as I've opened up the files

root@ubuntu:/chroot # stat /chroot/apache/var/www
  File: `/chroot/apache/var/www'
  Size: 4096            Blocks: 8          IO Block: 4096   directory
Device: 301h/769d       Inode: 686796      Links: 2
Access: (0755/drwxr-xr-x)  Uid: ( 1002/   httpd)   Gid: ( 1002/   httpd)
Access: 2005-10-29 17:03:49.525522808 +0900
Modify: 2005-10-29 16:55:40.257902792 +0900
Change: 2005-10-29 17:03:49.525522808 +0900

and apache runs ps -aux

httpd    13781  0.0  3.5  11648  4552 ?        S    16:59   0:00 /usr/sbin/apache2 -k start -DSSL

---

### Post by Glut on 2005-10-30
It looks like another process has already got that socket. It could be apache, as killing the child processes wont get rid of it. Check that first: **lsof -i:www**
if so, stop the process: **/etc/init.d/apache2 stop**, then try starting it again (If it is apache, you could simply **restart**, instead of stopping and starting.)
As for your first message: it looks like it has chroot'd then can't find a /var/run directory. Make sure that you have /chroot/apache/var/run, along with the correct permissions.

---

