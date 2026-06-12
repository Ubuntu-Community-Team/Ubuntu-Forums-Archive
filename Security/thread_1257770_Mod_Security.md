---
title: "Mod Security"
date: 2009-09-04
forum: Security
---

### Post by phillw on 2009-09-04
Hi folks,

I have just re-installed MySQL, Apache2 & PHP  (I got hacked - poorly setup SSH) ..  

This time I'm RTFM  VERY carefully !!

I've just followed Bodhi.Zazen's excellent article on putting mod-security onto apache2..

[http://blog.bodhizazen.net/linux/how-to-mod_security-ubuntu-904/](http://blog.bodhizazen.net/linux/how-to-mod_security-ubuntu-904/)

Something has not worked, and I'm stuck ....

everything went smoothly, no errors reported doing the install, wget, tar etc ....

Created and edited the various directories, links, and /etc/apache2/conf.d/modsecurity2.conf, with the required content.

But, when I restart apache2 I get this  :(

```

phillw@piglet:/etc/apache2/conf.d/modsecurity$ sudo /etc/init.d/apache2 restart

 * Restarting web server apache2                                                Syntax error on line 53 of /etc/apache2/conf.d/modsecurity/modsecurity_crs_10_config.conf:

Invalid command 'SecRuleEngine', perhaps misspelled or defined by a module not included in the server configuration

                                                                         [fail]


```

To check said file is where it is expected to be, I then did this ....

```

phillw@piglet:/etc/apache2/conf.d/modsecurity$ gksudo gedit /etc/apache2/conf.d/modsecurity/modsecurity_crs_10_config.conf


```

Gedit shows the area in question to be .....

```

## -- Configuration ----------------------------------------------------------

# Turn ModSecurity on ("On"), set to monitoring only 
# ("DetectionOnly") or turn off ("Off").
#
SecRuleEngine On

# Define which part of the HTTP transaction to inspect.
#


```

I'm stuck - any ideas anyone ?

Thanks,

Phill.

---

### Post by phillw on 2009-09-04
6 hours on .... Well, I've had a good look round - faced with ripping it all out & starting again - I've disabled (re-named) the file that fires up mod-security while I have a look at a couple of other apache hardening things - but I need my apache running to test them.  They are designed to run with apache mod-security. The ONLY thing I did before putting on mod-security was install OSSEC - HIDS, again according to the 'How-to', this seems to be running quite happily, and, tbh, I'd be really gutted to learn that it could interfere with the installation.

Phill.

:-k

---

### Post by bodhi.zazen on 2009-09-04
You need to enable mod-security:

```
sudo a2enmod mod-security
```

---

### Post by phillw on 2009-09-04
> **bodhi.zazen said:**
> You need to enable mod-security:

```
sudo a2enmod mod-security
```

Honest, I tried that .....

```


phillw@piglet:~$ sudo a2enmod mod-security
[sudo] password for phillw: 
ERROR: Module mod-security does not exist!


```It is not in /etc/apache2/mods-available  :confused:

If I'm supposed to have  modsecurity2.conf  in that directory - it has put itself into

/etc/apache2/conf.d

---

### Post by bodhi.zazen on 2009-09-04
Odd. I assume you missed a step along the way as I just went through the link :

[http://blog.bodhizazen.net/linux/how-to-mod_security-ubuntu-904/](http://blog.bodhizazen.net/linux/how-to-mod_security-ubuntu-904/)

setp-by-step.

Did you ```
sudo apt-get -y install libapache-mod-security
```On my box :

```
root@testing:/# ls /etc/apache2/mods-available/ | grep security
mod-security.load
root@testing:/#
``````
root@testing:/# a2enmod mod-security
Module mod-security already enabled
root@testing:/#
```

---

### Post by phillw on 2009-09-04
on piglet ......


```

phillw@piglet:/$ sudo apt-get -y install libapache-mod-security
[sudo] password for phillw: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libapache-mod-security is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.


```
```

cd /
phillw@piglet:/$ sudo find . | grep mod-security | grep -v common 

./var/lib/dpkg/info/libapache-mod-security.list
./var/lib/dpkg/info/libapache-mod-security.md5sums
./var/lib/dpkg/info/libapache-mod-security.prerm
./var/lib/dpkg/info/libapache-mod-security.postinst
./var/cache/apt/archives/libapache-mod-security_2.5.6-1_i386.deb
./usr/share/doc/libapache-mod-security


```As I read it, libapache-mod-security is there, and happily there. But, there is no file called *mod-security*  

BTW, I didn't get the .... is already the newest version the 1st time I did it.  :confused:

phillw@piglet:/etc/apache2/mods-available$ sudo find . | grep security
phillw@piglet:/etc/apache2/mods-available$ 

So, it's not in mods-available - in fact, It's not on my hard-drive anywhere  :-(

---

### Post by phillw on 2009-09-04
Spat dummy out of pram, in fact - I think I spat the whole pram out !!!!

sudo apt-get -purge remove libapache-mod-security
sudu dpkg --purge libapache-mod-security 

sudo apt-get -y install libapache-mod-security

Lo, and behold - the errant file is sat there, in the directory......

I'm still mystified as to why it didn't go there the 1st time, but - it's there now :D

and, more importantly - apache2 now starts hapilly..

:popcorn:

Once again, thanks for your help.

Phill

---

