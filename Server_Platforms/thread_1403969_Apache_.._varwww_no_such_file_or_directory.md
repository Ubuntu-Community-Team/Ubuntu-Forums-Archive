---
title: "Apache .. /var/www no such file or directory?"
date: 2010-02-10
forum: Server Platforms
---

### Post by Pres B on 2010-02-10
Hi everybody.  I recently installed XAMPP (lampp) on my Linux Mint Gloria (KDE).... I wanted to download Wordpress and mess around with that locally to play with some themes for sites, etc.  

Anyway, part of the tutorial I was trying to follow regarding installing Wordpress referred to extracting the tar file with the following command:

```
sudo tar zxvf wordpress-x.x.x.tar.gz --directory=/var/www/
```


I get the following output when I try to run that:
```
tar: /var/www: Cannot chdir: No such file or directory
tar: Error is not recoverable: exiting now

```

Isn't that directory supposed to have been setup when I installed Apache?  Can anybody point me in the right direction for making sure my local server is set up properly?

Thanks!!!

Pres b.

---

### Post by joberly on 2010-02-10
How exactly did you install Apache?

At a terminal do:

apache2 -v

ls -l /var/

---

### Post by Pres B on 2010-02-10
Hey, thanks for getting back to me.  I installed XAMPP and followed the instructions on the web site (apachefriends.org).  

```
$ apache2 -v                                                      
The program 'apache2' can be found in the following packages:
 * apache2-mpm-event
 * apache2-mpm-prefork
 * apache2-mpm-worker
 * apache2-mpm-itk
Try: sudo apt-get install <selected package>
bash: apache2: command not found

```


```
$ ls -l /var
total 40
drwxr-xr-x  2 root root  4096 2010-02-10 20:02 backups
drwxr-xr-x 17 root root  4096 2010-02-06 01:08 cache
drwxr-xr-x  2 root root  4096 2009-10-21 19:45 crash
drwxr-xr-x 56 root root  4096 2010-02-06 01:08 lib
drwxrwsr-x  2 root staff 4096 2009-04-13 05:33 local
drwxrwxrwt  2 root root    80 2010-02-10 20:54 lock
drwxr-xr-x 13 root root  4096 2010-02-10 20:02 log
drwxrwsr-x  2 root mail  4096 2009-04-20 10:27 mail
drwxr-xr-x  2 root root  4096 2009-04-20 10:27 opt
drwxr-xr-x 19 root root   740 2010-02-10 22:10 run
drwxr-xr-x  7 root root  4096 2009-04-26 10:24 spool
drwxrwxrwt  4 root root  4096 2010-02-09 23:21 tmp

```

---

### Post by Vegan on 2010-02-10
you need to install the LAMP stack, its not installed automatically.

```
sudo tasksel LAMP
```

Then you will be good to go.

---

### Post by Pres B on 2010-02-10
Thanks Vegan. I am installing the Lamp stack now. I'll leave my progression of how I got to this point (see below) just in case somebody as novice as myself reads these posts.  (Plus I'm sure it's funny for people who know what they are doing.) 

This is what I get when I try that... 

```
Usage:
tasksel install <task>
tasksel remove <task>
tasksel [options]
        -t, --test          test mode; don't really do anything
            --new-install   automatically install some tasks
            --list-tasks    list tasks that would be displayed and exit
            --task-packages list available packages in a task
            --task-desc     returns the description of a task

```


****edit
So, I did 
```
sudo tasksel
```

And then selected LAMP Server from the next screen that popped up.  But then I got this error:

```

tasksel: aptitude failed (100)

```

****2nd edit
It's installing now.  The reason it wasn't working before is because I had Synaptic open.

---

