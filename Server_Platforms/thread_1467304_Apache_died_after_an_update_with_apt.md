---
title: "Apache died after an update with apt"
date: 2010-04-30
forum: Server Platforms
---

### Post by das7002 on 2010-04-30
Well more of it complains about php and then says something about libxml and I have tried reinstalling apache and php and I cant see anything in my php.ini that would disable it so only thing I can think of is libxml getting updated and breaking everything on me :( 

Here is the error I get

```
root@*********:~# /etc/init.d/apache2 start
 * Starting web server apache2                                                  apache2: Syntax error on line 203 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/mods-enabled/php5.load: Cannot load /usr/lib/apache2/modules/libphp5.so into server: /usr/lib/apache2/modules/libphp5.so: symbol xmlTextReaderSchemaValidate, version LIBXML2_2.6.20 not defined in file libxml2.so.2 with link time reference
```

Please help, already tried on #httpd and ##php on freenode and I was ignored

EDIT: Forgot to mention its 9.10

---

### Post by tekknokrat on 2010-09-03
did you ever get a solution to your problem? Have the same on a karmic-pae server.

---

### Post by tekknokrat on 2010-09-04
Solution:

1. Pinning package libxml2 back to karmic (not karmic-update):

```
Package: libxml2
Pin: release a=karmic
Pin-Priority: 1001
```

2. Downgrade of packages to karmic
3. remove /lib/libxml2.so.2 manually
4. Reinstall package libxml2

```

$ aptitude reinstall libxml2 
```

---

### Post by noodl on 2010-10-31
Hi,

im having the same problem at Ubuntu Server 9.10.....

Wanted to fix it with your solution but dont know what to do in Step 1

> 1. Pinning package libxml2 back to karmic (not karmic-update):

 	Code:
 	Package: libxml2
Pin: release a=karmic
Pin-Priority: 1001 


hope someone could help me =)

mfg. noodl

---

### Post by tekknokrat on 2010-11-01
> **noodl said:**
> Hi,

im having the same problem at Ubuntu Server 9.10.....

Wanted to fix it with your solution but dont know what to do in Step 1



hope someone could help me =)

mfg. noodl

Put the code part from 1. into */etc/apt/preferences*. 
Then perform step 2. Let me know if there's an issue with that solution.

---

### Post by zaap01 on 2012-11-22
Success here, i solved the problem in my pc ^^ now my "http://ipadress/phpmyadmin" works fine :D
If anymore having trouble, enter in consol terminal an type:
rm /lib/libxml2.so.2; aptitude reinstall libxml2

maybe this will solve ur problens too ^^ (I'm using Ubuntu 11.04, tested on Mint and OpenSuse)

---

### Post by sandyd on 2012-11-23
**Necromancing - as per the Ubuntu forums code of conduct, please do not post in threads more than one year old**

Thanks!

---

