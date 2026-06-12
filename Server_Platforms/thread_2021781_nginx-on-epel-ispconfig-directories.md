---
title: "nginx-on-epel-ispconfig-directories"
date: 2012-07-09
forum: Server Platforms
---

### Post by poolet on 2012-07-09
Hello guys, I have build a dedicated server with centOS and I need a point since I have a small problem..  The server is running as host and I have pointed my domain address on it. It also runs nginx on epel with ispconfig , php5,mysql database, fail2ban, e.g., and a sort of other services.. Everything works perfect.
**My first question is:** I need opinions of type, where to point forum.php, I have two possible ways, even with nginx on epel or to set the forum directly on ispconfig. All I need is cons and pros of using nginx instead of ispconfig. Has nothing to do with advertising since all of service are open source so, please answer if you have any kind of experience....   
**My second and final problem: **is that the website/forum is not respond proper. To be clear, when I reach the address [www.mydomain.com]("http://www.mydomain.com") I get the default web page of nginx "/usr/shares/nginx/html/index.html" if I try now to display the forum.php ([www.mydomain.com/forum.php]("http://www.mydomain.com/forum.php")) Instead of executing the php and display the forum, it's pop up a downloaded window for downloading the file. Now I make a research on google and a lot of other forums, but unfortunately I get nothing with nginx, any references and post are only with apache2 and the two of them are extremely difference at least for the path directories, so since I have a bunch of services installed I can't determine the path that I should configuring the file, and even that I don't know which file to edit and how to edited proper/correctly, in addition, all thread have different configurations and references into a lot of problem that may occur. So if anyone's knows something I will appreciated any kind of help..!!! 

Thank you in advance!!!!!!

---

### Post by poolet on 2012-07-10
/*SOLVED*/

Solution:: 

if your running nginx on epel and php-fpm following below::

```
 vi /etc/nginx/conf.d/default.conf 
```then::
```
server {
listen 80;
server_name _;
...
..
.
location / { 
 root /usr/share/nginx/html;  //*or whatever is your path of nginx*//
 index index.php index.htm;
}
...
..
.
location ~\.php${
 root /usr/shares/nginx/html;
.....
....
...   (uncomment any elements  on these brackets )
..
..
and add this line:::  fastcgi_param SCRIPT_FILENAME $ document_root$fastcgi_script_name;
}
```save end restart nginx and php-fpm..

**NOTE: these records are working only with php-fpm!!! **

---

