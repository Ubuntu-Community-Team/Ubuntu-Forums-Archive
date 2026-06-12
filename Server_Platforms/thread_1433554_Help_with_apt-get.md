---
title: "Help with apt-get"
date: 2010-03-19
forum: Server Platforms
---

### Post by ipng on 2010-03-19
Hello :)

I have tried to install the ProFTPd with MySQL, but when i run
```
sudo aptitude install proftpd-mysql
```
it won't install. 
The output lookes like this ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No candidate version found for proftpd-mysql
No candidate version found for proftpd-mysql
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

```
I really hope, that anyone can fix this for me.
Thanks in advance :)

---

### Post by wojox on 2010-03-19
That's just the module. Try:

```
sudo aptitude install proftpd proftpd-mysql
```

---

### Post by Drenriza on 2010-03-19
Why don't you use
sudo apt-get install proftpd-mysql

i dont get the
sudo aptitude install proftpd-mysql 
command

---

### Post by SlugSlug on 2010-03-19
you may need to update your repositries

sudo apt-get update

and then 

sudo apt-get install proftpd

---

### Post by dudumomo on 2010-03-19
Agree!
Seems to be a repository problem.
If sudo apt-get update then sudo apt-get install proftpd doesn't work, check your /etc/apt/sources.list

---

### Post by ipng on 2010-03-19
> **wojox said:**
> That's just the module. Try:

```
sudo aptitude install proftpd proftpd-mysql
```
 Many thanks :) that worked out just fine for me! :D

---

### Post by wojox on 2010-03-19
> **ipng said:**
> Many thanks :) that worked out just fine for me! :D

Your welcome. ;)

---

