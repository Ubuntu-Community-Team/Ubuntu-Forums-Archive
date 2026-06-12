---
title: "Installing Backuppc"
date: 2010-09-17
forum: Server Platforms
---

### Post by p2ranger on 2010-09-17
Running Ubuntu Server 10.04.1

I recently heard about the backup software backuppc and wanted to give it a try

[http://backuppc.sourceforge.net/]("http://backuppc.sourceforge.net/")

I am unable to get it to install. I've followed the directions in a couple of different tutorials and on the documentation site, but I'm not having any success. The first time I tried to install it, I wasn't able to get it to come up in the browser when I went to [http://ipaddress/backuppc](http://ipaddress/backuppc)

I removed it and tried installing it again. Now I get this when I try to install it:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  backuppc
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/561kB of archives.
After this operation, 2,433kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package backuppc.
(Reading database ... 79923 files and directories currently installed.)
Unpacking backuppc (from .../backuppc_3.1.0-9ubuntu1_all.deb) ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Setting up backuppc (3.1.0-9ubuntu1) ...
Module auth_basic already enabled
Module authz_groupfile already enabled
Module authn_file already enabled
Module authz_user already enabled
Module cgi already enabled
 * Starting backuppc...
2010-09-17 10:35:38 Can't create a test hardlink between a file in /var/lib/backuppc/pc and /var/lib/backuppc/cpool.  Either these are different file systems, or this file system doesn't support hardlinks, or these directories don't exist, or there is a permissions problem, or the file system is out of inodes or full.  Use df, df -i, and ls -ld to check each of these possibilities. Quitting...
invoke-rc.d: initscript backuppc, action "start" failed.
dpkg: error processing backuppc (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 backuppc
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I have tried deleting those directories, removing the backuppc user, uninstalling and reinstalling, creating the backuppc user before installing, nothing seems to work

Thanks for any help

Jason

---

### Post by p2ranger on 2010-09-20
I was able to completely remove backuppc and reinstall by using

```
sudo apt-get purge backuppc
```

I'm still not able to get backuppc to show up on the web interface.  It still shows a 404 page not found error when I go to [http://192.168.1.120/backuppc](http://192.168.1.120/backuppc)

Is it possible that it's located somewhere else? How do I find this page?

Thanks for any help

Jason

---

### Post by howwhi on 2010-09-20
Jason,

I've just started installing BackupPC after a long idle time away from the tool (a couple of years).  First time through, I did not pay close enough attention to the install scripts.  Did not see the assignment of a password for the user "backuppc."  Did an uninstall similar to yours and then re-installed via "aptitude install backuppc" this time watching carefully for the password assignment.  Also executed the htpasswd command to change this password.  Am able to bring up the application main page by the URL <http://192.168.???.???/backuppc> and then keying the user "backuppc" and "password" as above.

Your posting sounds like you are not getting this far.  My response is to encourage you to look for missing dependencies or some such.  My install is upon a desktop system as opposed to server.  [When | If] I install backuppc as a full time application, I will likely do so upon a server system.

Howard

---

### Post by p2ranger on 2010-09-20
I was able to get the screen that showed the assigned password and allow me to choose apache2 as my webserver.

I don't know if there is something misconfigured with my apache install or something. In my /var/www directory, there is no backuppc directory.

How do I go about looking for dependencies?

Thanks

Jason

---

### Post by p2ranger on 2010-09-21
Found a solution. Don't know why it doesn't do it automatically: 

```
sudo chmod 777 /etc/apache2/apache2.conf
sudo cat /etc/backuppc/apache.conf >> /etc/apache2/apache2.conf
sudo chmod 644 /etc/apache2/apache2.conf
sudo /etc/init.d/apache2 stop
sudo /etc/init.d/apache2 start
```

As per this thread:
[http://ubuntuforums.org/showthread.php?t=645984](http://ubuntuforums.org/showthread.php?t=645984)

---

### Post by brainstuff on 2011-02-11
> **p2ranger said:**
> Found a solution. Don't know why it doesn't do it automatically: 

```
sudo chmod 777 /etc/apache2/apache2.conf
sudo cat /etc/backuppc/apache.conf >> /etc/apache2/apache2.conf
sudo chmod 644 /etc/apache2/apache2.conf
sudo /etc/init.d/apache2 stop
sudo /etc/init.d/apache2 start
```

As per this thread:
[http://ubuntuforums.org/showthread.php?t=645984](http://ubuntuforums.org/showthread.php?t=645984)

Just wanted to say thanks for posting the solution, it worked for me (identical symptoms). For the record mine was on ubuntu server 10 LTS which I'd cloned and renamed from another box (which originally started life as a VBox virtual machine!).

Cheers

---

### Post by LiLoather on 2011-04-05
This didn't work for me on Ubuntu Server 10.04 LTS- I'm still getting the;

Error: Wrong user: my userid is 33, instead of 108(backuppc) 

&tc message in the web-page.

I'm assuming that the line:

sudo cat /etc/backuppc/apache.conf >> /etc/apache2/apache2.conf

given above should be ..../backuppc/apache2.conf... to match reality?

Studying several dozen forum threads on this problem delivered by Google (which shows that it's been a sort-the-men-from-the-boys problem since at least 2003 on practically every Linux distribution out there) makes me think that I need to make Apache run as user backuppc - which is what I thought the solution offered in this thread effected - but presumably I was wrong.

One forum thread did suggest that I change the user in Apache's httpd.conf file to backuppc, but my /etc/apache2/httpd.conf file consists of 0B which makes it difficult to change anything, there being nothing to change.

I've also been totally unable to find anywhere in the scripts the definition of $Conf{BackupPCUser}which the error message says sets the user to backuppc, and I'm also having to assume that the file the applciation says is /usr/share/backuppc/cgi-bin/BackupPC_Admin is in fact the one it installs as /usr/share/backuppc/cgi-bin/index.cgi - but regrettably I lack the telepathic skills required by the average Linux user which enables them to understand what the developers meant rather than what they said.

I won't even begin to wonder how if I set Apache to run as backuppc user, it will serve any other application - that being a philosophical problem for the Linux master of many years.

I'll admit that I've only been trying to get BackupPC to work for a mere two days, which is far too short a time for any Linux expert to regard as sufficient sacrifice to conquer the challenges, but I'm weary and have other things to do, and the temptations of backsliding to Windows Server and Veritas in order to get a working backup system without effort are getting hard to resist, so please help save me from this heresy by pointing the way.

---

### Post by 65 mustang on 2012-08-15
For my situation i had a LVM partition mounted at "/var/lib/backuppc".  The solution was to stop backuppc and then set the **sticky bit** on the mounted volume.
```
service backuppc stop
chown -R backuppc:backuppc /var/lib/backuppc
chmod g+s /var/lib/backuppc
service backuppc start
```

---

