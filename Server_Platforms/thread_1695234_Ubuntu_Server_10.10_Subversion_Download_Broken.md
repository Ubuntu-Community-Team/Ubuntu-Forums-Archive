---
title: "Ubuntu Server 10.10 Subversion Download Broken?"
date: 2011-02-25
forum: Server Platforms
---

### Post by dreamnoir on 2011-02-25
I'm trying to install Subversion on a fresh install of Ubuntu Server. When using apt-get I run into the following problem.

```
~$ sudo apt-get install subversion libapache2-svn            Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libapache2-svn : Depends: libsvn1 (>= 1.6) but it is not going to be installed
 subversion : Depends: libsvn1 (= 1.6.12dfsg-1ubuntu1.1) but it is not going to be installed
E: Broken packages

```

Is the repository missing pieces?

---

### Post by chadhs on 2011-02-28
What if you first:
sudo apt-get update
sudo apt-get upgrade
(reboot if necessary)

Second:
sudo apt-get install subversion subversion-tools db4.8-util

...and then:
sudo apt-get install libapache2-svn

?

Sorry if that doesn't help.

---

### Post by dreamnoir on 2011-02-28
Thanks that worked! I assume the first two lines are just updating anything already installed? Makes sense. I'm used to the graphical updater in Ubuntu and didn't think to do it with Ubuntu Server.

---

### Post by chadhs on 2011-02-28
no problem at all dreamnoir.  :cool:

...and you are exactly right.  the first line is updating your package list, and the second then is telling the system to go ahead and install any updates.

also, from the looks of your original post you were probably following the svn documentation to access your repositories via webdav etc.  that is absolutely fine and dandy, however I just wrote a blog entry on setting up a basic svn / subversion server on ubuntu server.  feel free to check that out and see if that is easy for you.

article: "how to set up a basic subversion (svn) server on ubuntu"
[http://www.chadstovern.com/how-to-set-up-a-basic-subversion-svn-server-on-ubuntu](http://www.chadstovern.com/how-to-set-up-a-basic-subversion-svn-server-on-ubuntu)

---

