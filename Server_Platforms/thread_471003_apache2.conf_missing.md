---
title: "apache2.conf missing"
date: 2007-06-11
forum: Server Platforms
---

### Post by jocsch on 2007-06-11
Hi all,
hopefully somebody can tell me how to reconfigure apache2 to install all files that were originally included.
During a removal of apache2 I also removed the /etc/apache2 directory (by hand).
As I now need apache2 again, I installed it again. But obviously not everything that was installed last time is installed again. I get the following message:

apache2: Could not open configuration file /etc/apache2/apache2.conf: No such file or

And it's true. The directory /etc/apache2 was recreated with a few files in it, but the apache2.conf file is missing.

is there any trick how to get it again?

Thanks,
 Markus

---

### Post by dfreer on 2007-06-11
Hmmm. You could try removing apache with the purge command, cleaning your apt cache, and then try reinstalling apache. So:
```
sudo apt-get remove --purge apache2
sudo apt-get clean
sudo apt-get install apache2
```
Hopefully this helps.

---

### Post by jocsch on 2007-06-11
Thanks defreer,
it worked after I did a apt-get remove --purge apache2-common and reinstalled as described.

Cool ...

---

### Post by dfreer on 2007-06-11
basically, debian packages maintain certian files as configuration files. These are only removed when using the --purge command. This way you can reinstall programs without losing your settings. Glad it worked for you!

---

### Post by conza on 2007-06-14
hiya,
just wanted to say "thanks", since this thread solved my problem :) 

with one exception: I had to "sudo apt-get remove --purge apache2.2-common" for it to work, instead of 'just' apache2-common.

just if there are any more newbies like myself out there getting themselves in trouble..... ;-)

---

### Post by asmeetkumar on 2008-01-03
Thanks,
           This post solved my problem.:)

---

### Post by zoltansoos on 2008-05-07
You guys are great. Thank you so much for your help and sharing this info.:KS

---

### Post by sacrosancttayyar on 2008-06-11
iam using hardy, i have the same problem.
i deleted the whole /etc/apache2 directory

i used that reinstallation commands. Here is the output:
You will see the fail action in last rows.

```
root@hasantayyar-desktop:/home/hasantayyar# sudo apt-get remove --purge apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package apache2 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 20 not upgraded.
root@hasantayyar-desktop:/home/hasantayyar# sudo apt-get clean
root@hasantayyar-desktop:/home/hasantayyar# sudo apt-get install apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  apache2-mpm-worker apache2-utils apache2.2-common
Suggested packages:
  apache2-doc
The following NEW packages will be installed:
  apache2 apache2-mpm-worker apache2-utils apache2.2-common
0 upgraded, 4 newly installed, 0 to remove and 20 not upgraded.
Need to get 1171kB of archives.
After this operation, 4436kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) hardy-updates/main apache2-utils 2.2.8-1ubuntu0.2 [139kB]
Get:2 [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) hardy-updates/main apache2.2-common 2.2.8-1ubuntu0.2 [753kB]
Get:3 [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) hardy-updates/main apache2-mpm-worker 2.2.8-1ubuntu0.2 [234kB]
Get:4 [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) hardy-updates/main apache2 2.2.8-1ubuntu0.2 [44,4kB]
Fetched 1171kB in 4s (287kB/s)
Selecting previously deselected package apache2-utils.
(Reading database ... 161885 files and directories currently installed.)
Unpacking apache2-utils (from .../apache2-utils_2.2.8-1ubuntu0.2_i386.deb) ...
Selecting previously deselected package apache2.2-common.
Unpacking apache2.2-common (from .../apache2.2-common_2.2.8-1ubuntu0.2_i386.deb) ...
Selecting previously deselected package apache2-mpm-worker.
Unpacking apache2-mpm-worker (from .../apache2-mpm-worker_2.2.8-1ubuntu0.2_i386.deb) ...
Selecting previously deselected package apache2.
Unpacking apache2 (from .../apache2_2.2.8-1ubuntu0.2_all.deb) ...
Setting up apache2-utils (2.2.8-1ubuntu0.2) ...
Setting up apache2.2-common (2.2.8-1ubuntu0.2) ...

Setting up apache2-mpm-worker (2.2.8-1ubuntu0.2) ...
grep: /etc/apache2/mods-enabled/*.load: No such file or directory
Module cgi does not exist!
This module does not exist!
It looks like you've deleted /etc/apache2/mods-available/cgid.load, so mod_cgid cannot be enabled.  To fix this, please purge and reinstall apache2.2-common.
 * Starting web server apache2                                                           apache2: Could not open configuration file /etc/apache2/apache2.conf: No such file or directory
                                                                                  [[COLOR="Red"]fail[/COLOR]]
invoke-rc.d: initscript apache2, action "start" failed.

Setting up apache2 (2.2.8-1ubuntu0.2) ...
```

---

### Post by dfreer on 2008-06-11
> It looks like you've deleted /etc/apache2/mods-available/cgid.load, so mod_cgid cannot be enabled.  To fix this, please purge and reinstall apache2.2-common.

Try:
```
sudo apt-get remove --purge apache2.2-common
sudo apt-get install apache2.2-common
```

---

