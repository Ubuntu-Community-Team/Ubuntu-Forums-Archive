---
title: "Django project on server 12.04 LTS ubuntu"
date: 2013-01-28
forum: Server Platforms
---

### Post by Raafat1991 on 2013-01-28
Hi guys...i (as usual) followed this guide [http://jeffbaier.com/articles/installing-django-on-an-ubuntu-linux-server/](http://jeffbaier.com/articles/installing-django-on-an-ubuntu-linux-server/)  for installing a django project .
 and (Also as usual) i got a problem .

my problem is : when visiting 192.168.1.4 (where ubuntu server ) all what i got apache server's default page .

my ubuntu server is on a oracle VMBox .

any an idea ?

thank you  .

---

### Post by volkswagner on 2013-01-28
After quickly skimming the how-to it seems your Django install should be located at
```
http://192.168.1.4/media
```

I have not used symlinks for directing apache to different directories.  I usually just modify/create a virtual host file and use the DocumentRoot directive.

---

### Post by Raafat1991 on 2013-01-29
> **volkswagner said:**
> After quickly skimming the how-to it seems your Django install should be located at
```
http://192.168.1.4/media
```I have not used symlinks for directing apache to different directories.  I usually just modify/create a virtual host file and use the DocumentRoot directive.

Hi...there is no URL with [http://192.168.1.4/media/admin](http://192.168.1.4/media/admin) or [http://192.168.1.4/media/Recording](http://192.168.1.4/media/Recording) (my project)

but with [http://192.168.1.4/media](http://192.168.1.4/media) i got a page like ftp pages with filezilla .

---

### Post by volkswagner on 2013-01-29
Can you determine the actual directory you have landed at? Compare the listings to your webroot.

Can you post a screenshot?

---

### Post by Raafat1991 on 2013-01-30
> **volkswagner said:**
> Can you determine the actual directory you have landed at? Compare the listings to your webroot.

Can you post a screenshot?

I'm sorry but where is webroot ? (/var/www/  ?)

Also i did't understand your question : Can you determine the actual directory you have landed at ? 

Also

[IMG]http://i.cubeupload.com/tCvYuM.png[/IMG]

thank you....

---

### Post by volkswagner on 2013-01-30
Sorry for the poorly worded question.  "Landed" meaning from the screenshot above, can you navigate to /var/www/media and see an empty directory?


```
ls -alt /var/www
```

```
ls -alt /var/www/media
```


Either /var/www/media is empty, the symbolic link is not working, or Apache2 does not have permission to follow the link.


A side note:  I'm not sure how much time you have invested in this server, or if you have an available Virtual Machine host (hypervisor)... check out TurnkeyLinux for a [prebuilt image]("http://www.turnkeylinux.org/django") you can deploy with Django already setup.

---

### Post by Raafat1991 on 2013-01-31
> **volkswagner said:**
> Sorry for the poorly worded question.  "Landed" meaning from the screenshot above, can you navigate to /var/www/media and see an empty directory?


```
ls -alt /var/www
``````
ls -alt /var/www/media
```
Either /var/www/media is empty, the symbolic link is not working, or Apache2 does not have permission to follow the link.


A side note:  I'm not sure how much time you have invested in this server, or if you have an available Virtual Machine host (hypervisor)... check out TurnkeyLinux for a [prebuilt image]("http://www.turnkeylinux.org/django") you can deploy with Django already setup.

Yes it's empty .

```
ls -alt /var/www
```

its output :

```
drwxr-xr-x  2 root root 4096 Jan 31 13:52 .
drwxr-xr-x 13 root root 4096 Jan 30 15:25 ..
lrwxrwxrwx  1 root root   50 Jan 23 21:45 admin_media -> /home/raafat/django_src/django/contrib/admin/media
lrwxrwxrwx  1 root root   18 Jan 23 21:45 media -> /home/raafat/media
-rw-r--r--  1 root root  177 Jan  5 23:01 index.html
```


```
ls -alt /var/www/media
```

its output :

```
lrwxrwxrwx 1 root root 18 Jan 23 21:45 /var/www/media -> /home/raafat/media

```

i will check your side note . 

thank you .

---

### Post by Raafat1991 on 2013-02-01
Guys i'm waiting you...please .

---

### Post by volkswagner on 2013-02-01
It seems the how to you used is incomplete.  It assumes you know how to configure apache2 for mod_python.

I suggest you look for a better how to specific to Debian or Ubuntu.

Take a look at this [how-to]("http://freshtutorial.com/install-configure-apache2-modpython-debian-ubuntu/"), specifically look at /etc/apache2/sites-available/default edits.

I'm sorry I've never used mod_python.

Perhaps you should post your vhost file.

---

### Post by Raafat1991 on 2013-02-06
> **volkswagner said:**
> It seems the how to you used is incomplete.  It assumes you know how to configure apache2 for mod_python.

I suggest you look for a better how to specific to Debian or Ubuntu.

Take a look at this [how-to]("http://freshtutorial.com/install-configure-apache2-modpython-debian-ubuntu/"), specifically look at /etc/apache2/sites-available/default edits.

I'm sorry I've never used mod_python.

Perhaps you should post your vhost file.

Many thanks...thank you everyone .

---

