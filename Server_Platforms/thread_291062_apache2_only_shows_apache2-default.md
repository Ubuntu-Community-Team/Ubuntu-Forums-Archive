---
title: "apache2 only shows apache2-default"
date: 2006-11-02
forum: Server Platforms
---

### Post by twigboy on 2006-11-02
In my /var/www I have 2 folders the apache2-default and htdocs.  Every file in htdocs has the 755 permissions the only difference is I have added a htaccess file.  When I go to localhost apache2 only shows the apache2-default folder.  Any ideas?
Thanx

---

### Post by Bachstelze on 2006-11-02
Is the directory itself also CHMODed to 755 ?

---

### Post by twigboy on 2006-11-02
No.  How do you chmod a directory?

---

### Post by DannyG on 2006-11-02
To CHMOD a directory, use: ```
chmod 755 directory
``` OR to CHMOD a directory and ALL its subfolders and files use: ```
chmod 755 directory -r
``` It might also be worth mentioning, that you don't need a .htaccess file to define the root of your webserver. You can add the line ```
DocumentRoot /folder/where/you/put/htdocs
``` in your /etc/apache2/apache2.conf, then restart your webserver.

Keep us informed.

Daniel.

---

### Post by twigboy on 2006-11-02
heres the ls -al output of my /var/www
drwxr-xr-x  4 root root 4096 2006-11-01 21:45 .
drwxr-xr-x 15 root root 4096 2006-10-30 19:47 ..
drwxr-xr-x  2 root root 4096 2006-10-30 19:47 apache2-default
drwxr-xr-x  2 root root 4096 2006-11-01 21:34 home
-rw-r--r--  1 root root   50 2006-11-01 18:02 index.html~

heres the of the home folder
drwxr-xr-x 2 root root   4096 2006-11-01 21:34 .
drwxr-xr-x 4 root root   4096 2006-11-01 21:45 ..
-rwxr-xr-x 1 root root 155423 2006-10-31 20:48 DSC01965.JPG
-rwxr-xr-x 1 root root 150253 2006-10-31 20:51 DSC02039.JPG
-rwxr-xr-x 1 root root    140 2006-11-01 18:09 .htaccess
-rwxr-xr-x 1 root root     24 2006-11-01 18:10 .htpasswd
-rwxr-xr-x 1 root root     43 2006-11-01 18:03 index.html
-rwxr-xr-x 1 root root     52 2006-11-01 17:43 index.html~

When I put the DocumentRoot in apache2.conf nothing changes, It still only showes the apache2-default dir.  When I change it in the /etc/apache2/sites-available/defaulf file to /var/www/home it showes the files in the home directory.

I should also note that the htaccess does not work when I go to this directory.

Thanks for the help everyone.

---

### Post by yanny on 2008-01-19
The solution is to type in the following in httpd.conf:

<virtualhost *:80>
ServerName example.com
DocumentRoot /var/www/example.com
</virtualhost>

---

