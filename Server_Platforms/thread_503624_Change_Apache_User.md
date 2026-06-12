---
title: "Change Apache User"
date: 2007-07-18
forum: Server Platforms
---

### Post by wilkesalex on 2007-07-18
Hello, my current apache setup is like this (please ,any recommendations!)

I have the /var/www folder which serves my personal html

i have created a linux user for each of my family. this means that they can access thier own website

[http://domain/~user/](http://domain/~user/)


tI have a problem with php scripts however - they cant do chmod or mkdir etc. this is the case if i run scripts form a /home/user/ dir or the /var/www dir


i don't really understand apache user and group permissions. my understanding is that i will need to set every folder to www-data 777 in all my /home/user/public_html and my /var/www/ folders. is that correct?

it's really annoying because I cant run any scripts any where on my server that require system operations (like mkdir)


is there an easy way to just make my apache run as root so it can do whatever?

---

### Post by crashie on 2007-07-18
It's a bad idea to run apache as root. If it is and it (or a PHP script) gets broken into the intruder will get full access to your computer.

Change the permissions on the directories where PHP needs write access instead. Set the group to www-data and give it write access. Note that if your PHP scripts create directories and create files inside them you won't be able to delete them as a normal user (they will be owned by the www-data user), you will have to be root then (of course they can be deleted from PHP).

For example, to change permissions on /home/user/public_html, type:
```
chmod 775 /home/user/public_html
sudo chgrp www-data /home/user/public_html
```

---

### Post by peterx14 on 2007-07-19
Not wishing to derail the thread at all, but how can you change what user Apache logs in as? I have Apache installed on Feisty using a standard Ubuntu repository install but I have the following processes:
```
$ ps -FA | grep apache
root      5326     1  0  2793   596   0 Jul19 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  5327  5326  0  2736   396   0 Jul19 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  5328  5326  0 58336  3172   0 Jul19 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  5330  5326  0 58435  3592   0 Jul19 ?        00:00:00 /usr/sbin/apache2 -k start
```
I would've expected *all* the Apache processes to be logged in as www-data.

---

### Post by jtc on 2007-07-20
Take a look at suPHP.

It is not exactly what you are asking for, but probably what you are looking for :-)

---

