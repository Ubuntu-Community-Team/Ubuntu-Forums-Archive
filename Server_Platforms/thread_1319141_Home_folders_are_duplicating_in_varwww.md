---
title: "Home folders are duplicating in /var/www"
date: 2009-11-08
forum: Server Platforms
---

### Post by dalitso on 2009-11-08
I have setup postfix to deliver mail to Maildir/ and my apache site directory to /home/user/public_html. It works fine only recently I have noticed that every folder and file in /home/ is being duplicated in /var/www/
How can I stop this duplicating?

Another thing is that when I setup transparency proxy, I cannot access any remote servers via vpn or webmin. Is there a way to correct this or its just one of the disadvantages of transparent proxy?

Your help will be greately appreciated.

---

### Post by Lars Noodén on 2009-11-09
What method are you using to see that these folders are visible in /var/www? Your web browser?

---

### Post by dalitso on 2009-11-09
Using either ssh(putty) or webmin file manager or the command console itself. By the way, my box is running ubuntu server 8.04

---

### Post by Lars Noodén on 2009-11-09
If you look at www inside of /var or /var/www, do you see symlinks?

[INDENT][FONT="Courier New"]lrwxr-xr-x   1 root  wheel  10 Nov  8 21:55 home -> /var/www/

lrwxr-xr-x   1 root  wheel  10 Nov  8 21:55 /var/www -> /home[/FONT][/INDENT]

Do you have user directories turned on in apache?  That would allow you to access some part of the user home directory via the web:

[INDENT][http://myhost.example.com/~dalitso/](http://myhost.example.com/~dalitso/)[/INDENT]

What would be shown by the URL above for ~dalitso would be dependent on how UserDir was set in your Apache virtual host.

[INDENT][http://httpd.apache.org/docs/2.2/mod/mod_userdir.html](http://httpd.apache.org/docs/2.2/mod/mod_userdir.html)
[http://httpd.apache.org/docs/2.2/howto/public_html.html](http://httpd.apache.org/docs/2.2/howto/public_html.html)
[http://httpd.apache.org/docs/2.2/urlmapping.html](http://httpd.apache.org/docs/2.2/urlmapping.html)[/INDENT]

---

### Post by dalitso on 2009-11-09
Apache userDir is disabled by default. And there are no symlinks between /var/www and /home

---

### Post by Lars Noodén on 2009-11-10
Yes, default it is disabled.  But what is the current setting on your machines web server configuratoin?  How about the settings for ServerRoot and DocumentRoot?

Also please explain in more detail how you can see that the folders are duplicating in /var/www?

---

### Post by dalitso on 2009-11-10
Apache userdir is disabled. I have a number of virtual hosts heres their document roots

ServerRoot "/etc/apache2"

DocumentRoot /home/martin/public_html

DocumentRoot /home/dalitso/public_html

DocumentRoot /usr/share/squirrelmail


I have attached webmin file manager screen shots; that's one of the ways I can tell that the folders are duplicating.

Here is also the output from the terminal


```
root@wani:/home# ls -l
total 36
-rw------- 1 root                           root                              0 2009-09-07 20:36 aquota.user
drwxr-xr-x 4 dalitso                        users                          4096 2009-11-05 12:43 dalitso
drwxr-xr-x 3 demster                        users                          4096 2009-11-10 18:45 demster
drwxrwxrwx 3 ftp                            nogroup                        4096 2009-10-27 20:58 ftp
-rw-r--r-- 1 root                           root                             45 2009-09-07 18:37 index.html
drwxr-xr-x 9 martin                         martin                         4096 2009-11-10 18:45 martin
drwxr-xr-x 4 ngonie                         users                          4096 2009-11-10 18:45 ngonie
drwxr-xr-x 2 squid                          squid                          4096 2009-10-30 11:21 squid
drwxr-xr-x 2 root                           root                           4096 2009-11-02 06:45 webalizer
drwxr-xr-x 6 webmail-martinology.selfip.org webmail-martinology.selfip.org 4096 2009-11-07 23:41 webmail-martinology.selfip.org



root@wani:/var/www# ls -l
total 36
-rw------- 1 root                           root                              0 2009-09-07 20:36 aquota.user
drwxr-xr-x 4 dalitso                        users                          4096 2009-11-05 12:43 dalitso
drwxr-xr-x 3 demster                        users                          4096 2009-11-10 18:45 demster
drwxrwxrwx 3 ftp                            nogroup                        4096 2009-10-27 20:58 ftp
-rw-r--r-- 1 root                           root                             45 2009-09-07 18:37 index.html
drwxr-xr-x 9 martin                         martin                         4096 2009-11-10 18:45 martin
drwxr-xr-x 4 ngonie                         users                          4096 2009-11-10 18:45 ngonie
drwxr-xr-x 2 squid                          squid                          4096 2009-10-30 11:21 squid
drwxr-xr-x 2 root                           root                           4096 2009-11-02 06:45 webalizer
drwxr-xr-x 6 webmail-martinology.selfip.org webmail-martinology.selfip.org 4096 2009-11-07 23:41 webmail-martinology.selfip.org

```

---

### Post by yknivag on 2009-11-10
From the ls output above it seems that /var/www/ is a symlink to /home/

Can you post the output of ```
ls -l /var
``` please?

---

### Post by dalitso on 2009-11-10
Here's the output of ls -l /var

[HTML]root@wani:~# ls -l /var
total 48
drwxr-xr-x  2 root root  4096 2009-10-25 06:26 backups
drwxr-xr-x 14 root root  4096 2009-10-12 15:47 cache
drwxr-xr-x 45 root root  4096 2009-10-12 16:00 lib
drwxrwsr-x  2 root staff 4096 2008-06-13 22:40 local
drwxrwxrwt  3 root root    60 2009-11-10 15:32 lock
drwxr-xr-x 15 root root  4096 2009-11-10 15:32 log
drwxrwsr-x  2 root mail  4096 2009-09-07 22:11 mail
drwxr-xr-x  2 root root  4096 2009-09-07 18:14 opt
drwxr-xr-x 19 root root   640 2009-11-10 15:32 run
drwxr-xr-x  8 root root  4096 2009-09-24 20:18 spool
drwxrwxrwt  2 root root  4096 2008-06-13 22:40 tmp
drwxrwxrwt  2 root root  4096 2009-09-07 21:07 virtualmin-autoreply
drwx------  2 root bin   4096 2009-10-31 21:49 webmin
drwxr-xr-x 10 root root  4096 2009-11-07 23:41 www
[/HTML]

---

### Post by yknivag on 2009-11-10
OK so /var/www isn't a symlink of /home. Is /home a symlink of /var/www?

Or are there any jobs in cron that are synchronising the two directories? (You can see all of these at once in webmin)

---

### Post by dalitso on 2009-11-10
Thank you very much guys for all your help. It does seem there is some kind of link between /var/www and /home or the other way round.

This is what I found in fstab

[HTML]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8c30055e-5ee8-4d45-85cd-3842c307bbd5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=b64a58e9-207f-4268-9046-6f168ecf8728  /home  ext3  suid,resgid=1002,dev,relatime,exec  0  2
# /dev/sda5
UUID=67db335f-da38-40ee-b0cf-67e607bf5727 /share          ext3    relatime        0       2
# /dev/sda3
UUID=dd993637-3f4e-4074-9597-83cf8e812834 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/var/www /home none bind
[/HTML]


I have attached a disk and network filesystem screen shot of webmin. It does show like /home and /var/www are linked.

Now the only question is, how did this happen? Well, I also have virtualmin installed on the server. After googling, it turns out when virtualmin is installed as a module, it cannot use /home for mail and site but /var/www

However if installed using a script (virtualmin....sh) it can take care of such a problem ( I hope symlinking is not the solution) Mine was not installed using the script. I guess that explains alot.

Thank you again all you guys.

---

