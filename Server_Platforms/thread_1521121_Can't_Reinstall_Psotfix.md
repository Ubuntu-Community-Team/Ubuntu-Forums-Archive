---
title: "Can't Reinstall Psotfix"
date: 2010-06-30
forum: Server Platforms
---

### Post by Devin82m on 2010-06-30
Hey everyone,

I can't seem to reinstall Postfix. I followed a guide and couldn't get it to work. After I retried a few times I gave up and deleted all files and folders I could find related to Postfix. Well I realized what the issue was and now that I want to try reinstalling Postfix it won't allow me. 

When I type: 
```
sudo apt-get install postfix
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
postfix is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up postfix (2.7.0-1) ...
update-rc.d: /etc/init.d/postfix: file does not exist
dpkg: error processing postfix (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 postfix
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)


When I try:
```
sudo apt-get install -f
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up postfix (2.7.0-1) ...
update-rc.d: /etc/init.d/postfix: file does not exist
dpkg: error processing postfix (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 postfix
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)


When I try:
```
sudo apt-get purge
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up postfix (2.7.0-1) ...
update-rc.d: /etc/init.d/postfix: file does not exist
dpkg: error processing postfix (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 postfix
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)


When I try :
```
sudo apt-get autoclean
```
devin@server:/var/www$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree
Reading state information... Done


If you can offer any help I would appreciate it. Thanks! :p

---

### Post by Ichido on 2010-07-01
Try:
sudo apt-get --purge remove Postfix 	
(To Remove/Delete everything including configuration files.)

Then:
sudo apt-get install Postfix		
(To Install program.)

APT Commands:
1) sudo apt-get update {package} 		To Update program.	
2) sudo apt-get upgrade {package}		To Upgrade program. 	 
3) sudo apt-get install {package}		To Install program.
4) sudo apt-get remove {package}		To Remove program.
4) sudo apt-get --purge remove {package} 	To Remove/Delete everything including configuration files!
5) sudo apt-get install -f			To FIX Broken Packages:

[http://202.203.132.242/cgi-bin/dwww/usr/share/doc/Debian/apt-howto/apt-howto.en.html](http://202.203.132.242/cgi-bin/dwww/usr/share/doc/Debian/apt-howto/apt-howto.en.html)

---

### Post by Devin82m on 2010-07-01
This is what I get when I tried
```
sudo apt-get --purge remove postfix 
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  postfix*
0 upgraded, 0 newly installed, 1 to remove and 3 not upgraded.
1 not fully installed or removed.
After this operation, 3,273kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ...
dpkg: warning: files list file for package `postfix' missing, assuming package has no files currently installed.
(Reading database ... 66331 files and directories currently installed.)
Removing postfix ...
invoke-rc.d: unknown initscript, /etc/init.d/postfix not found.
dpkg: error processing postfix (--purge):
 subprocess installed pre-removal script returned error exit status 100
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Devin82m on 2010-07-01
This is what I get when I tried
```
sudo apt-get --purge remove postfix 
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  postfix*
0 upgraded, 0 newly installed, 1 to remove and 3 not upgraded.
1 not fully installed or removed.
After this operation, 3,273kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ...
dpkg: warning: files list file for package `postfix' missing, assuming package has no files currently installed.
(Reading database ... 66331 files and directories currently installed.)
Removing postfix ...
invoke-rc.d: unknown initscript, /etc/init.d/postfix not found.
dpkg: error processing postfix (--purge):
 subprocess installed pre-removal script returned error exit status 100
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Ichido on 2010-07-01
Better web site:
[http://202.203.132.242/cgi-bin/dwww/usr/share/doc/Debian/apt-howto/apt-howto.en.html](http://202.203.132.242/cgi-bin/dwww/usr/share/doc/Debian/apt-howto/apt-howto.en.html)

---

### Post by Ichido on 2010-07-01
I would try this:
1) sudo apt-get install {package} To Install program.
2) sudo apt-get update {package} To Update program.
Then test.

If still having trouble, then:
3) sudo apt-get upgrade {package} To Upgrade program.

This is about my limits.

---

### Post by Devin82m on 2010-07-05
Nothing seems to work. I have tried all sorts of commands suggested. I even tried downloading the source and install Postfix manually without any success. When I tried installing an alternative MTA (Sendmail) it wouldn't even install because of the Postfix errors. PLEASE help. I wish I could undelete all those Postfix config files I deleted! :)

---

### Post by s1gnAl on 2010-07-05
Try this: (disclaimer: no guarantee it will work :P)

```
sudo touch /etc/init.d/postfix
```

run apt-get install postfix, cross fingers. 

Still not working? Let's try something else: 

```

mkdir $HOME/postfix-files
cd $HOME/postfix-files
wget http://us.archive.ubuntu.com/ubuntu/pool/main/p/postfix/postfix_2.7.0-1_i386.deb
sudo dpkg -x postfix_2.7.0-1_i386.deb .

```

What this will do is download the .deb and just unpack it only, the idea is to "pluck" files from it as apt complains. 

Again... this is off the cuff hack so I have no idea if it will work, but if I was to have this problem this is how I would probably attack it. 

Hope that helps and good luck.... :)

---

### Post by Devin82m on 2010-07-05
THANKS! That first command fixed it right away! What is that command used for?

---

### Post by s1gnAl on 2010-07-05
Awesome! Glad it worked :) 

Basically in a nutshell touch modifies the access time of a file and creates it if it doesn't exist, among other things. 

When you ran the command it created the file which satisfied apt. 

Take a look at the man page if you want to learn more:

```
man touch
```

---

### Post by Ichido on 2010-07-15
> **s1gnAl said:**
> Try this: (disclaimer: no guarantee it will work :P)

```
sudo touch /etc/init.d/postfix
```

run apt-get install postfix, cross fingers. 

Still not working? Let's try something else: 

```

mkdir $HOME/postfix-files
cd $HOME/postfix-files
wget http://us.archive.ubuntu.com/ubuntu/pool/main/p/postfix/postfix_2.7.0-1_i386.deb
sudo dpkg -x postfix_2.7.0-1_i386.deb .

```

What this will do is download the .deb and just unpack it only, the idea is to "pluck" files from it as apt complains. 

Again... this is off the cuff hack so I have no idea if it will work, but if I was to have this problem this is how I would probably attack it. 

Hope that helps and good luck.... :)

I tried your commands.
First one did nothing.
The second one gives me the Error: 
"dpkg-deb: --extract needs a target directory.
Perhaps you should be using dpkg --install ?"

What can I try next?

---

### Post by Ichido on 2010-07-21
I fixed my "Postfix" Errors by Removing Postfix;)

---

### Post by diverbelow on 2010-10-11
> **s1gnAl said:**
> Try this: (disclaimer: no guarantee it will work :P)

```
sudo touch /etc/init.d/postfix
```

run apt-get install postfix, cross fingers. 

Still not working? Let's try something else: 

```

mkdir $HOME/postfix-files
cd $HOME/postfix-files
wget http://us.archive.ubuntu.com/ubuntu/pool/main/p/postfix/postfix_2.7.0-1_i386.deb
sudo dpkg -x postfix_2.7.0-1_i386.deb .

```

What this will do is download the .deb and just unpack it only, the idea is to "pluck" files from it as apt complains. 

Again... this is off the cuff hack so I have no idea if it will work, but if I was to have this problem this is how I would probably attack it. 

Hope that helps and good luck.... :)

I have tried both of those steps and it did not work on Ubuntu 10.04.1 32-bit. Here is how I fixed my issue with mod step 2:
```

cd /
wget http://us.archive.ubuntu.com/ubuntu/pool/main/p/postfix/postfix_2.7.0-1_i386.deb
sudo dpkg -x postfix_2.7.0-1_i386.deb .

```
Then I did apt-get install postfix and I got no errors and postfix installed just fine.

---

