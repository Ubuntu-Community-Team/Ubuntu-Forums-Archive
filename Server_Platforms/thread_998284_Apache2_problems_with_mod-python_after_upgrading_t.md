---
title: "Apache2 problems with mod-python after upgrading to 8.10"
date: 2008-11-30
forum: Server Platforms
---

### Post by arandall on 2008-11-30
Hey guys,

I just upgraded to Ibex and I started having problems with Apache2. When I try to start the server, I get the following error:

"apache2: Syntax error on line 185 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/mods-enabled/mod-python.load: No such file or directory"

When I go to the directory in the terminal, I run ls and the file appears, but it's in red font with a black background. I'm assuming this means that something is wrong... When I run cat on the file to print its contents, it says "No such file or directory." 

With this, I went ahead and try to reinstall apache2 and libapache2-mod-python, but alas, nothing helped. 

Is there something else I need to do? 

Thanks

---

### Post by cariboo on 2008-11-30
Reinstalling something because it doesn't work as expected will not fix your problem. Why waste the time you could spent on fixing the problem doing something useless like reinstalling. Remember Linux is not Windows.

It it looks like you either have a permissions problem or a symbolic link problem. This is what my /etc/Apache2 on my server looks:

```
ls -l
total 40
-rw-r--r-- 1 root root 10104 2008-09-19 06:42 apache2.conf
drwxr-xr-x 2 root root  4096 2008-11-09 14:06 conf.d
-rw-r--r-- 1 root root   378 2008-09-19 06:42 envvars
-rw-r--r-- 1 root root     0 2008-11-05 14:01 httpd.conf
drwxr-xr-x 2 root root  4096 2008-11-07 20:42 mods-available
drwxr-xr-x 2 root root  4096 2008-11-07 20:43 mods-enabled
-rw-r--r-- 1 root root   351 2008-09-19 06:42 ports.conf
drwxr-xr-x 2 root root  4096 2008-11-05 14:01 sites-available
drwxr-xr-x 2 root root  4096 2008-11-05 14:01 sites-enabled
```

Check to see if your file and directory permissions match mine.

Jim

---

### Post by arandall on 2008-11-30
Thanks for the response, Jim. The reason I reinstalled is because the error I was getting was that a file was missing, so (with my limited knowledge of Linux) it made sense to try a reinstall that could possibly just copy the file again and solve the problem... I'm relatively new to Linux, so honestly, it's more just experimenting with the OS rather than taking a "Windows" approach to solving the problem. And through using the apt-get commands in the terminal, the time I wasted trying this was quite literally around one minute, with which I was running some MATLAB code on another computer, so it was downtime anyway. 

The file and directory permissions match yours: 
```
adrian@adrian-server:/etc/apache2$ ls -l
total 48
-rw-r--r-- 1 root root 10104 2008-09-19 09:42 apache2.conf
drwxr-xr-x 2 root root  4096 2008-11-30 13:41 conf.d
-rw-r--r-- 1 root root   378 2008-06-25 09:50 envvars
-rw-r--r-- 1 root root     0 2008-10-27 20:48 httpd.conf
drwxr-xr-x 2 root root 12288 2008-11-30 16:39 mods-available
drwxr-xr-x 2 root root  4096 2008-11-30 16:39 mods-enabled
-rw-r--r-- 1 root root   351 2008-09-19 09:42 ports.conf
drwxr-xr-x 2 root root  4096 2008-11-30 16:37 sites-available
drwxr-xr-x 2 root root  4096 2008-10-27 20:48 sites-enabled

```

-Adrian

---

### Post by arandall on 2008-12-04
Nothing?

---

### Post by Vanadaar on 2009-05-01
A few months after the fact, but I had the same problem, after upgrading from intrepid to jaunty, fixed it with:

```
sudo apt-get purge libapache2-mod-python
sudo apt-get install libapache2-mod-python
```

---

