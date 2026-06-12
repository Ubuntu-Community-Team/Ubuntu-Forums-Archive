---
title: "tor confusion"
date: 2010-07-28
forum: Security
---

### Post by machinanoctua on 2010-07-28
i am relatively new Here and my dilemma is that  i have attempted to install tor and polipo altering the config file like the tor site said but it still says polipo isnt working and when i goto check if tor is running it says it isnt i am at a total loss and i love ubuntu so far if i can get some help on this it would b great thank u!:(

here is my terminal history for what i have doine i have tor button installed everything went fine but it asks me if polipo is turned on when i test it in firefox

joshua@Euclid:~$ apt-get remove privoxy
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
joshua@Euclid:~$ su root 
Password: 
root@Euclid:/home/joshua# apt-get remove privoxy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package privoxy is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libswt-cairo-gtk-3.5-jni libswt-mozilla-gtk-3.5-jni libswt-gnome-gtk-3.5-jni
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@Euclid:/home/joshua# su joshua
joshua@Euclid:~$ sudo ps -A | grep -i privoxy
[sudo] password for joshua: 
joshua@Euclid:~$ sudo ps -A | grep -i privoxy
joshua@Euclid:~$ sudo echo 'deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) lucid main' > /etc/apt/sources.list && gpg --keyserver keys.gnupg.net --recv 886DDD89 && gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add - && sudo aptitude update && sudo aptitude install tor tor-geoipdb polipo
bash: /etc/apt/sources.list: Permission denied
joshua@Euclid:~$ su root
Password: 
root@Euclid:/home/joshua# sudo echo 'deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) lucid main' > /etc/apt/sources.list && gpg --keyserver keys.gnupg.net --recv 886DDD89 && gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add - && sudo aptitude update && sudo aptitude install tor tor-geoipdb polipo
gpg: requesting key 886DDD89 from hkp server keys.gnupg.net
gpg: key 886DDD89: "deb.torproject.org archive signing key" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
OK
Writing extended state information... Done
Get:1 [http://deb.torproject.org](http://deb.torproject.org) lucid Release.gpg [489B]
Ign [http://deb.torproject.org/torproject.org/](http://deb.torproject.org/torproject.org/) lucid/main Translation-en_US
Get:2 [http://deb.torproject.org](http://deb.torproject.org) lucid Release [2,224B]
Ign [http://deb.torproject.org](http://deb.torproject.org) lucid/main Packages                               
Ign [http://deb.torproject.org](http://deb.torproject.org) lucid/main Packages                               
Get:3 [http://deb.torproject.org](http://deb.torproject.org) lucid/main Packages [3,898B]                    
Fetched 6,611B in 13s (484B/s)  
Reading package lists... Done             

Current status: 1 update [+1], 5 new [+5].
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages are BROKEN:
  tor 
The following NEW packages will be installed:
  tor-geoipdb 
The following packages will be REMOVED:
  libswt-cairo-gtk-3.5-jni{u} libswt-gnome-gtk-3.5-jni{u} 
  libswt-mozilla-gtk-3.5-jni{u} 
The following packages will be upgraded:
  polipo 
1 packages upgraded, 2 newly installed, 3 to remove and 0 not upgraded.
Need to get 2,458kB of archives. After unpacking 4,899kB will be used.
The following packages have unmet dependencies:
  tor: Depends: tsocks which is a virtual package.
The following actions will resolve these dependencies:

Keep the following packages at their current version:
tor [Not Installed]
tor-geoipdb [Not Installed]

Score is -19810

Accept this solution? [Y/n/q/?] y
The following packages will be REMOVED:
  libswt-cairo-gtk-3.5-jni{u} libswt-gnome-gtk-3.5-jni{u} 
  libswt-mozilla-gtk-3.5-jni{u} 
The following packages will be upgraded:
  polipo 
1 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 185kB of archives. After unpacking 569kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://deb.torproject.org/torproject.org/](http://deb.torproject.org/torproject.org/) lucid/main polipo 1.0.4.1-1.1~lucid1 [185kB]
Fetched 185kB in 7s (23.5kB/s)                                                  
(Reading database ... 186311 files and directories currently installed.)
Removing libswt-cairo-gtk-3.5-jni ...
Removing libswt-gnome-gtk-3.5-jni ...
Removing libswt-mozilla-gtk-3.5-jni ...
(Reading database ... 186298 files and directories currently installed.)
Preparing to replace polipo 1.0.4-3 (using .../polipo_1.0.4.1-1.1~lucid1_i386.deb) ...
Stopping polipo: polipo.
Removing obsolete conffile /etc/ppp/ip-up.d/1polipo ...
Removing obsolete conffile /etc/ppp/ip-down.d/1polipo ...
Removing obsolete conffile /etc/network/if-up.d/01polipo ...
Removing obsolete conffile /etc/network/if-down.d/01polipo ...
Unpacking replacement polipo ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for doc-base ...
Processing 1 changed doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for install-info ...
Processing triggers for man-db ...
Setting up polipo (1.0.4.1-1.1~lucid1) ...
Installing new version of config file /etc/init.d/polipo ...
Starting polipo: polipo.

Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

Current status: 0 updates [-1].
root@Euclid:/home/joshua# sudo gedit /etc/polipo/config
root@Euclid:/home/joshua# sudo service tor restart && sudo service polipo restart
tor: unrecognized service
root@Euclid:/home/joshua# sudo service tor restart & sudo service polipo restart[1] 23552
tor: unrecognized service
Restarting polipo: polipo.
[1]+  Exit 1                  sudo service tor restart
root@Euclid:/home/joshua#

---

### Post by Bachstelze on 2010-07-29
It doesn't work because your sources.list now contains *only* the tor repository.  Here's a correct one, replace your current sources.list with it and try again.

```
deb http://archive.ubuntu.com/ubuntu/ lucid main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ lucid main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ lucid-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ lucid-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu lucid-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

deb http://deb.torproject.org/torproject.org lucid main

```

---

### Post by machinanoctua on 2010-07-29
i did as you advised and afterwards it gave me this error message thank you for your patience i am taking notes by the way !:p


Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.




Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release)  Unable to find expected entry  lucid-backports/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/Release](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/Release)  Unable to find expected entry  lucid-backports/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/Release](http://archive.ubuntu.com/ubuntu/dists/lucid/Release)  Unable to find expected entry  deb-src/binary-i386/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

---

