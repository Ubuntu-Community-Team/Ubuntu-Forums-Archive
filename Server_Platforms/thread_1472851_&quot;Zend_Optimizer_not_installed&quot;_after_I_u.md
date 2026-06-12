---
title: "&quot;Zend Optimizer not installed&quot; after I updated to 10.04"
date: 2010-05-04
forum: Server Platforms
---

### Post by Eugene_Bondarenko on 2010-05-04
Hi guys,

I've just updated from 9.10 to 10.04. Everything seems to run fine except for zend optimizer which is throwing "Zend Optimizer not installed" error. I went to php.ini and the following line is still there
```
zend_extension=/etc/php5/ZendOptimizer.so
```
Also I checked that the file does exist and that the php.ini I am looking at is in fact the php.ini file that is being used by the server. Please let me know if you have any ideas about how to fix or debug this.

Thanks,
Eugene

---

### Post by Eugene_Bondarenko on 2010-05-04
Update:

I've just managed to get this from apache logs
```
Zend Optimizer requires Zend Engine API version 220060519. 
The Zend Engine API version 220090626 which is installed, is newer. 
Contact Zend Technologies at zend.com for a later version of Zend Optimizer.
```

---

### Post by Eugene_Bondarenko on 2010-05-04
Well, it turns out that zend optimizer does not yet support php 5.3 which is provided under ubuntu 10.04. So basically the problem is solved and I have a new problem - to downgrade php
[http://ubuntuforums.org/showthread.php?p=9237689](http://ubuntuforums.org/showthread.php?p=9237689)

---

### Post by kumarldh on 2010-08-10
Hi,

I dont remember the thread from where I copied this but the following script will help you downgrade your PHP from 5.3.x to 5.2.10
```
#!/bin/bash
# by Ruben Barkow (rubo77) http://www.entikey.z11.de/

# Originally Posted by Bachstelze http://ubuntuforums.org/showthread.php?p=9080474#post9080474
# OK, here's how to do the Apt magic to get PHP packages from the karmic repositories:

echo "Am I root?  "
if [ "$(whoami &2>/dev/null)" != "root" ] && [ "$(id -un &2>/dev/null)" != "root" ] ; then
  echo "  NO!

Error: You must be root to run this script.
Enter
sudo su
"
  exit 1
fi
echo "  OK";


# finish all apt-problems:
apt-get -f install

# remove all your existing PHP packages. You can list them with dpkg -l| grep php
PHPLIST=$(for i in $(dpkg -l | grep php|awk '{ print $2 }' ); do echo $i; done)
echo these pachets will be removed: $PHPLIST 
# you need not to purge, if you have upgraded from karmic:
aptitude remove $PHPLIST
# on a fresh install, you need purge:
# aptitude remove --purge $PHPLIST


#Create a file each in /etc/apt/preferences.d like this (call it for example /etc/apt/preferences.d/php5_2);
#
#Package: php5
#Pin: release a=karmic
#Pin-Priority: 991
#
#The big problem is that wildcards don't work, so you will need one such stanza for each PHP package you want to pull from karmic:

echo ''>/etc/apt/preferences.d/php5_2
for i in $PHPLIST ; do echo "Package: $i
Pin: release a=karmic
Pin-Priority: 991
">>/etc/apt/preferences.d/php5_2; done

# duplicate your existing sources.list replacing lucid with karmic and save it in sources.list.d:
#sed s/lucid/karmic/g /etc/apt/sources.list | sudo tee /etc/apt/sources.list.d/karmic.list

# better exactly only the needed sources, cause otherwise you can get a cachsize problem:
echo "# needed sources vor php5.2:
deb http://de.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ karmic main restricted

deb http://de.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

deb http://de.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://de.archive.ubuntu.com/ubuntu/ karmic universe
deb http://de.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://de.archive.ubuntu.com/ubuntu/ karmic-updates universe

deb http://de.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://de.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse
" >> /etc/apt/sources.list.d/karmic.list

aptitude update

apache2ctl restart

echo install new from karmic:
aptitude -t karmic install $PHPLIST

# at the end retry the modul libapache2-mod-php5 in case it didn't work the first time:
aptitude -t karmic install libapache2-mod-php5

apache2ctl restart
```

---

