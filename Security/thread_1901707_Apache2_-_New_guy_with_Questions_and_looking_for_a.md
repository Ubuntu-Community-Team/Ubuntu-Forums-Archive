---
title: "Apache2 - New guy with Questions and looking for advice."
date: 2011-12-29
forum: Security
---

### Post by kristiaan_d on 2011-12-29
Hi Guys,
I am after a little advice regarding Apache2 and keeping it secure, So i started to read this article on the Apache website relating to [security tips]("http://httpd.apache.org/docs/2.2/misc/security_tips.html") 

and it mentioned that Apache2 initially starts as the root user and then switches to a user defined in the apache2.conf file, however when i do 

```
ps aux | grep apache
```

I get the following results, am i to presume the apache2 process still running as root is normal?

```
root      2127  0.0  0.2   5420  2576 ?        Ss   16:03   0:00 /usr/sbin/apache2 -k start
www-data  2129  0.0  0.1   5192  1760 ?        S    16:03   0:00 /usr/sbin/apache2 -k start
www-data  2130  0.0  0.2 226836  2180 ?        Sl   16:03   0:00 /usr/sbin/apache2 -k start
www-data  2131  0.0  0.2 226836  2184 ?        Sl   16:03   0:00 /usr/sbin/apache2 -k start
```

I may be mis-understanding the wording in the Apache link as well but it does mention that folders the apache software accesses for serving user content should belong to the user apache is running as, in my case www-data however a quick listing of the /var/www/ folder shows the owner is root.

```
me@myserver:/var$ ls -la www
total 12
drwxr-xr-x  2 root root 4096 2011-12-28 15:30 .
drwxr-xr-x 15 root root 4096 2011-12-28 15:30 ..
-rw-r--r--  1 root root  177 2011-12-28 15:30 index.html
```

again is this a normal? or should i be chown'ing the folders to www-data ?

If anyone happens to have any good reference material on securing an apache box, setting one up etc i would appreciate some links etc as our companie is looking to start using Linux and Apache2 more and more in the next 12 months, initially internally but eventually public facing, so i would like to brush up on the subject and get my head around the do's and don't way before they decide to start running production servers and they end up getting done over due to poor security practices.

---

### Post by SeijiSensei on 2011-12-29
The first Apache instance with root privileges is the "parent" of the "children" running as the www-data user.  The children handle the requests; the parent manages them.

Since /var/www and /var/www/index.html have world-readable permissions, the ownership of the directory doesn't really matter here.  However if you wrote a script that needs to write files, you'd have to place them in a directory owned by the www-data user.  

The bigger issue concerns how files will be written to the /var/www directory.  If you want ordinary users to place files there, you'd need to adjust the permissions.  This is a more complicated issue and has been addressed here from time to time.

---

### Post by kristiaan_d on 2011-12-29
> **SeijiSensei said:**
> The first Apache instance with root privileges is the "parent" of the "children" running as the www-data user.  The children handle the requests; the parent manages them.

Since /var/www and /var/www/index.html have world-readable permissions, the ownership of the directory doesn't really matter here.  However if you wrote a script that needs to write files, you'd have to place them in a directory owned by the www-data user.  

The bigger issue concerns how files will be written to the /var/www directory.  If you want ordinary users to place files there, you'd need to adjust the permissions.  This is a more complicated issue and has been addressed here from time to time.

thanks for the response, i kinda had the feeling the one root apache instance was going to be some sort of "child management" but i wanted to double check as there was no clear yes or no that i could find, as most of the pages i had read, all mentioned that apache would start as root and switch to the alternate user, there was no mention that it would maintain a root presense for this.

with regards to /var/www/ it will mainly be hosting static content with a mix of php where needed, any data that needs to be stored will be pushed through to a MYSQL DB on another system. I was more concerned about the directory being owned by root incase this posed a security risk / hazard that would normally be resolved by chown'ing the folder before bringing the server into production, but if its not a concern then i will happily leave the folders owner as-is for now.

Thanks again
Kris

---

