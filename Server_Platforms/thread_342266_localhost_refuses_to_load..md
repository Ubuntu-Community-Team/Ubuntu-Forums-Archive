---
title: "localhost refuses to load."
date: 2007-01-19
forum: Server Platforms
---

### Post by bobleny on 2007-01-19
I just installed Apache2, MySQL, PHP5, and  phpMyAdmin according to this guide, "https://help.ubuntu.com/community/ApacheMySQLPHP".

My problem is though, "localhost" won't load. I tried adding this, "ServerName localhost", to this file, "/etc/apache2/apache2.conf", as instructed by the guide. Keep in mind though, I haven't received any errors. This fix worked until I restarted my computer...

Also, when I turn apache on with this command, "sudo /etc/init.d/apache2 start", I get no conformation of it starting. It simply jumps to the next line. I only bring this up because when I tell it to stop (sudo /etc/init.d/apache2 stop), I get a conformation.

What should I do?

Thanks!

Edit: Please note, if relevant, I am running kubuntu 6.10 edgy eft.

---

### Post by jtc on 2007-01-20
This might seem basic, but seen init.d/apache2 start won't give any respons, we can always check whatever apache2 is actually running.

```
ps aux |grep apache2
```

Then, the logs are always good way to look. Do you find any hint about what's wrong in /var/log/apache2/error.log

---

### Post by bobleny on 2007-01-20
I don't understand what that is exactly, but this is what I get when I run that command.:
```
bob@George:~$ ps aux |grep apache2
bob       4731  0.0  0.2   2800   752 pts/1    R+   07:51   0:00 grep apache2
```

---

### Post by jtc on 2007-01-20
This seems like a good time as any for some Unix-basics :-)

*ps* is a command which list running processes. If you invoke it is *psi aux* it displays all running processes, with some extra info about them. You can read more about it by running *man ps*
[SIZE="1"]
(Clarification: This is the way GNU ps, usually installed at Linux computers, behave. If you run ps on a unix system it uses diffrent flags.)
[/SIZE]
In this case we weren't interested in all processes, but simply whatever apache was not running or not. The | is called a pipe and is,  a bit simplified, used to direct output from one program to another. *grep* is used to test, line by line, for certain keywords och patterns.

What we did was to list all processes running on the system, direct the output to grep which then gave us all of those involving the word apache2, which happens to be the name of the binary for Apache 2. Since all we got in response was our own query we can assume apache isn't running.

By the way, did you find anything in /var/log/apache2/error.log ?

---

### Post by bobleny on 2007-01-20
There is nothing in "/var/log/apache2/error.log".

What should I do....

---

### Post by bobleny on 2007-01-20
How d I do a complete uninstall and reinstall of LAMP? When I unistalled it with Adept Manager, there where still files  left over. Then after I told it to install LAMP again, I checked the "/etc/apache2/apache2.conf" file and the "Servername localhost" thing is still at the bottom of the file. So, It's not uninstalling right.

How d I do a complete uninstall and reinstall of LAMP?

---

### Post by jtc on 2007-01-21
If nothing else, you can always completly remove a package using apt-get this way.

```
apt-get --purge remove apache2
```

---

### Post by bobleny on 2007-01-21
How do I see what what packages are installed on the computer?

---

### Post by jtc on 2007-01-21
```
dpkg --list
```

---

### Post by bobleny on 2007-01-21
```
root@George:/# apt-get autoremove apache
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package apache is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```


```
rc  apache                        1.3.34-4ubuntu1               versatile, high-performance HTTP server
rc  apache-common         1.3.34-4ubuntu1               support files for all Apache webservers
```

Why does it say that I don't have apache when I tell it to remove it, but it says I have it when I list the packages in my computer?

---

### Post by jtc on 2007-01-21
Note the two initial letter, rc? In short that means that the package is mainly removed, but there are configurationfiles, etc remaining.  Packages installed for real are marked ii.

To remove it completely, do the following.

```
dpkg --purge *packagename*
```

---

### Post by bobleny on 2007-01-21
Oh.... I like this! Way better than adept. Never go back to that.... lol This tells me what it is going to do before it does it and then asks me if I still want it to do what It is going to do. lol - wow that makes little since.

Going back to the "ii" and the "rc", what is "un" and "pn"?

---

### Post by jtc on 2007-01-21
> **bobleny said:**
> Going back to the "ii" and the "rc", what is "un" and "pn"?
Almost time for you to start doing your homework yourself :p If you look the the top of the listing, you'll find a listing of what the diffrent letter mean.

Getting anywhere with Apache? I did try to reproduce your problem, but the only way I could find having /etc/init.d/apache2 start do nothing (not starting nor giving any error message) would be if its binary ( /usr/sbin/apache2 ) was missing or not executable. In that case through /etc/init.d/apache2 stop shouldn't have given any output either, which I belive it did in your case.

Noticed that the packages you were trying to remove belonged to version 1.3 of apache. Something you tried when apache2 didn't work? Otherwise, if they were installed the entire time, perhaps there could have been some collition between the two versions?

---

### Post by bobleny on 2007-01-21
The first time I installed apache, I accidentally installed apache and not apache2. I told adept to unistall it. I also uninstalled every thing else but apparently it didn't help. I think what has happened is do in part to adept. I think files got crossed. This is why I want to wipe it all from my computer and start again....

I have no problem finding information on my own, until I can't find it. I often times don't know where to find the info...

And besides, this is all it says at the top of the list.... I don't see anything about ii or rc or pn or un....
```
root@George:/# dpkg -l
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                          Version                       Description
```

So, yeah, I have no idea what pn and un is....


Edit: Also, Ive been using this guide, "https://help.ubuntu.com/community/AptGetHowto" to help me out, but it doesn't explain things very well. None the less, I have looked for info on apt-get...

---

### Post by jtc on 2007-01-21
Those two-letter-combination are the Desired-value plus the Status-value.

pn would then translate into (p)urge and (n)ot.

Excatly how these turn into reality I'm not sure, since I don't have any of those myself and don't know what would have happened to cause them.

Good luck with the purge and start-over with apache!

---

### Post by jtc on 2007-01-21
> **jtc said:**
> Almost time for you to start doing your homework yourself :p
Perhaps that wasn't the best way to express myself. It was merely an introduction to the next sentence, which refered to some extra information on a specific question. I apologize if it came out the wrong way.

Ask as many question as you want and as you feel you need to!

---

### Post by bobleny on 2007-01-21
OK, so again, I am following this guide.
The problem is: the browser keeps asking me to download php files.

This is all the commands I fed the terminal....
I have highlighted the parts that I feel are of interest.
```
root@George:/# apt-get install apache2
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  apache2-common apache2-mpm-worker apache2-utils libapr0
Suggested packages:
  apache2-doc
The following NEW packages will be installed:
  apache2 apache2-common apache2-mpm-worker apache2-utils libapr0
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1282kB of archives.
After unpacking 4325kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Selecting previously deselected package libapr0.
(Reading database ... 84186 files and directories currently installed.)
Unpacking libapr0 (from .../libapr0_2.0.55-4ubuntu4_i386.deb) ...
Selecting previously deselected package apache2-utils.
Unpacking apache2-utils (from .../apache2-utils_2.0.55-4ubuntu4_i386.deb) ...
Selecting previously deselected package apache2-common.
Unpacking apache2-common (from .../apache2-common_2.0.55-4ubuntu4_i386.deb) ...
Selecting previously deselected package apache2-mpm-worker.
Unpacking apache2-mpm-worker (from .../apache2-mpm-worker_2.0.55-4ubuntu4_i386.deb) ...
Selecting previously deselected package apache2.
Unpacking apache2 (from .../apache2_2.0.55-4ubuntu4_i386.deb) ...
Setting up libapr0 (2.0.55-4ubuntu4) ...

Setting up apache2-utils (2.0.55-4ubuntu4) ...
Setting up apache2-common (2.0.55-4ubuntu4) ...
Setting Apache2 to Listen on port 80. If this is not desired, please edit /etc/apache2/ports.conf as desired. Note that the Port directive no longer works.
Module userdir installed; run /etc/init.d/apache2 force-reload to enable.

Setting up apache2-mpm-worker (2.0.55-4ubuntu4) ...
 * Starting apache 2.0 web server...                                                                                                          [COLOR="Red"]apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName[/COLOR]
                                                                                                                                       [ ok ]

Setting up apache2 (2.0.55-4ubuntu4) ...
```

This is where I did what the guide says...
> Troubleshooting

If you get this error:

apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName

then edit sudo gedit /etc/apache2/apache2.conf and add ServerName localhost at the end of the file

If Apache2 is pointing to the wrong directory then you need to edit the file /usr/share/apache2/default and any files in the directory /usr/share/apache2/allowed-sites/

Then I opened firefox and tested "localhost" It works! So I continued with the guide.

This is what I did next, again, interesting things highlighted...
```
root@George:/# apt-get install php5
Reading package lists... Done
Building dependency tree
Reading state information... Done
[COLOR="Red"]The following packages were automatically installed and are no longer required:
  apache2-mpm-worker
Use 'apt-get autoremove' to remove them.[/COLOR]
The following extra packages will be installed:
  apache2-mpm-prefork libapache2-mod-php5 php5-common
Suggested packages:
  php-pear
[COLOR="Red"]The following packages will be REMOVED:
  apache2-mpm-worker[/COLOR]
The following NEW packages will be installed:
  apache2-mpm-prefork libapache2-mod-php5 php5 php5-common
0 upgraded, 4 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B/2663kB of archives.
After unpacking 5652kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
[COLOR="Red"]dpkg: apache2-mpm-worker: dependency problems, but removing anyway as you request:
 apache2 depends on apache2-mpm-worker (= 2.0.55-4ubuntu4) | apache2-mpm-prefork (= 2.0.55-4ubuntu4) | apache2-mpm-perchild (= 2.0.55-4ubuntu4); however:
  Package apache2-mpm-worker is to be removed.
  Package apache2-mpm-prefork is not installed.
  Package apache2-mpm-perchild is not installed.[/COLOR]
(Reading database ... 84659 files and directories currently installed.)
[COLOR="Red"]Removing apache2-mpm-worker ...[/COLOR]
 * Stopping apache 2.0 web server...                                                                                                   [ ok ]
Selecting previously deselected package apache2-mpm-prefork.
(Reading database ... 84655 files and directories currently installed.)
Unpacking apache2-mpm-prefork (from .../apache2-mpm-prefork_2.0.55-4ubuntu4_i386.deb) ...
Selecting previously deselected package php5-common.
Unpacking php5-common (from .../php5-common_5.1.6-1ubuntu2.1_i386.deb) ...
Selecting previously deselected package libapache2-mod-php5.
Unpacking libapache2-mod-php5 (from .../libapache2-mod-php5_5.1.6-1ubuntu2.1_i386.deb) ...
Selecting previously deselected package php5.
Unpacking php5 (from .../php5_5.1.6-1ubuntu2.1_all.deb) ...
Setting up apache2-mpm-prefork (2.0.55-4ubuntu4) ...
 * Starting apache 2.0 web server...                                                                                                   [ ok ]

Setting up php5-common (5.1.6-1ubuntu2.1) ...
Setting up libapache2-mod-php5 (5.1.6-1ubuntu2.1) ...
 * Forcing reload of apache 2.0 web server...                                                                                          [ ok ]

Setting up php5 (5.1.6-1ubuntu2.1) ...
root@George:/# sudo /etc/init.d/apache2 restart
 * Forcing reload of apache 2.0 web server...                                                                                          [ ok ]
```

If apache needs that file that was deleted, then why would php delete the file? Maybe this is a problem? However, to my surprise, localhost sill works...


Next, since my browser keeps asking me to download the php files. the guide says:

> Does your browser ask if you want to download the php file instead of displaying it? If Apache is not actually parsing the php after you restarted it, install libapache2-mod-php5. It is installed when you install the php5 package, but may have been removed inadvertently by packages which need to run a different version of php. You may also need to actually enable it, by doing sudo a2enmod php5 followed by sudo /etc/init.d/apache2 restart

So, since, it said nothing about uninstalling the the libapache2-mod-php5, I simply tried to enable it, which also confirms that the file is installed and is already enabled, but I go ahead and tell it to install the package anyways.

```
root@George:/# a2enmod php5
This module is already enabled!
root@George:/# apt-get install libapache2-mod-php5
Reading package lists... Done
Building dependency tree
Reading state information... Done
libapache2-mod-php5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@George:/# a2enmod php5
This module is already enabled!
root@George:/#  root@George:/# sudo /etc/init.d/apache2 restart
 * Forcing reload of apache 2.0 web server... 
root@George:/# 
```

I also made sure apache was fresh, so I restarted it and yet again, the browser asks me to download the php files.

What should I do!?

---

### Post by bobleny on 2007-01-21
OK! never mind!!!!

WOOOW! I restarted my computer and it actually displays the php files.

Great, now I will install MySQL and phpMyAdmin and see if they work!...

---

### Post by bobleny on 2007-01-21
Yes!!!! It works! I am so happy! WOW! Its been over 3 months since I've had a working server!!

Thanks a lot to jtc!!! :biggrin:  =D>  YAY!

Thanks!

---

### Post by jtc on 2007-01-22
Wonderfull!

In case you'r curious.
mpm-worker does a better job serving static files
mpm-prefork are better suitable for php-pages, etc

Had you run apache2 and libapache2-mod-php5 in the same apt-get, it ought to have picked the right one right away.

In case you'r even more curious.
[http://httpd.apache.org/docs/2.0/mod/worker.html](http://httpd.apache.org/docs/2.0/mod/worker.html)
[http://httpd.apache.org/docs/2.0/mod/prefork.html](http://httpd.apache.org/docs/2.0/mod/prefork.html)

---

