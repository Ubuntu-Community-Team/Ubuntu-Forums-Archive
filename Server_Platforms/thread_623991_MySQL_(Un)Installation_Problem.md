---
title: "MySQL (Un)Installation Problem"
date: 2007-11-26
forum: Server Platforms
---

### Post by Shanebob on 2007-11-26
Well, I've Googled and Googled, but haven't found a solution for this problem I've encountered.

I've been trying to get a localhost server running on my PC (running Ubuntu 7,10 Home Edition), and so far I have Apache 2.2.4 and PHP 5.2.3 installed and working.  Last night I tried to install MySQL and something screwed up.  I'm not sure why, but it doesn't work at all, and I can't use 'apt-get', 'apt-remove', etc. any more, or open Synaptic Package Manager.  Here's an example of what happens whenever I try to use 'apt-get' or something similar.

```
shane@shane-desktop:~$ sudo apt-get autoremove
[sudo] password for shane:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up mysql-server-5.0 (5.0.45-1ubuntu3) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
 * Starting MySQL database server mysqld                                 [ OK ] 
/etc/init.d/mysql: line 122: /etc/mysql/debian-start: No such file or directory
invoke-rc.d: initscript mysql, action "start" failed.
```

I'm not really sure what this means...And I can't do anything from there except close Terminal.  If I try to open Synaptic, I get this:

'**Unable to get exclusive lock**
This usually means that another package management application (like apt-get or aptitude) already running. Please close that application first.'

Also, if I try 'sudo dpkg --configure -a', I get 'dpkg: status database area is locked by another process'.

Any ideas on how I can fix this?

---

### Post by Shanebob on 2007-11-26
Nevermind, I got this fixed...I had to download a my.cnf file and configure it myself.  Then I got into Synaptic and could completely remove all the MySQL-related stuff.  Things seem to be working now.

Sorry for the unnecessary thread.

---

### Post by koenn on 2007-11-26
there seems to be somethiing wrong with the install or startup scripts for the mysql package. They come from official Ubuntu repo's ? 

You can try
```
dpkg-reconfigure mysql-server
apt-get install -f
```
the first one attempts to complete the postinstall-configuration of mysql-server (check the package name, I'm not 100% sure). The second one installs and configures any missing or half-installed packages. You can change the order and run them several times. They both require sudo. 

You may have to remove the dpkg lock file, a file that indicates the dpkg directory is in use, before running the above commands. make sure synamptic or any other package manager is closed and you don't have any apt or dpkg commands running/hanging in terminals, then do
```
sudo rm /var/lib/dpkg/lock
```

*If you don't hear from me again, I'll have been banned for posting sudo rm commands  *  ;)

---

### Post by Shanebob on 2007-11-26
Well, I don't think any of those things were my problem.  I'm pretty sure it was just the my.conf file missing.  Once I downloaded that, it didn't take long to fix it.  I finally did get my server up and running, though.  It only took about 8 hours of work, haha.  Thanks for the help, though.

---

