---
title: "Ubuntu 10.04 Server - Tomcat?"
date: 2010-05-11
forum: Server Platforms
---

### Post by mixpix on 2010-05-11
I have installed a fresh install of Ubuntu Server 10.04 LTS (64-bit). I installed LAMP, SSH, Samba and Print Server during the installation.

I am having a problem trying to understand how Tomcat works on a default install of the server.

If I go to mydomain.com:8080 it shows that a Tomcat server is running, but I cannot find the process or any folders that actually hold Tomcat files.

I have no need for Tomcat and can't seem to find a way to uninstall it or just stop the service from running.

I've tried uninstalling it, but it says it's not installed and looking at the services list but there isn't anything relating to Tomcat. But it's running on port 8080, so it's got to be there!

I'm still learning when it comes to Linux, but this is driving me up the wall!

---

### Post by Magneus on 2010-05-11
> **mixpix said:**
> 

If I go to mydomain.com:8080 it shows that a Tomcat server is running, but I cannot find the process or any folders that actually hold Tomcat files.

I have no need for Tomcat and can't seem to find a way to uninstall it or just stop the service from running.

I've tried uninstalling it, but it says it's not installed and looking at the services list but there isn't anything relating to Tomcat. But it's running on port 8080, so it's got to be there!

I'm still learning when it comes to Linux, but this is driving me up the wall!

Quick disclaimer: I have experience with Gentoo and CentOS server installs, but only Ubuntu desktop installs. Presuming Ubuntu server is not a wholly different beast from Ubuntu desktop, this advice will be 100% spot-on.

Tomcat stores its applications in the webapps folder. webapps should be found by default in /usr/share/tomcat6/webapps. 

To see if it is, indeed running:
```
ps -ef | grep tomcat
``` 

To stop it, use:
```
sudo service tomcat6 stop
```

To uninstall, it should be:
```
sudo apt-get remove tomcat6
```

And then you can clean up any extra junk with:
```
sudo apt-get autoremove
```

I hope that helps. Let us know how it goes!

---

### Post by mixpix on 2010-05-12
Thanks for your reply. I've done the last two steps that you posted previously and the tomcat webpage on port 8080 was still there.

BUT, I have restarted the server and now there's nothing running on port 8080! I'm wondering if it was an Apache bug? I never installed the Tomcat option, so it shouldn't have been there to begin with.

Anyways, thanks for the help. Here are the results for my system when I did your steps, the last two were the same for me when I first tried them:

~$ ps -ef | grep tomcat
mixpix    7923  3692  0 20:12 pts/0    00:00:00 grep --color=auto tomcat

~$ sudo service tomcat6
tomcat6: unrecognized service

~$ sudo apt-get remove tomcat6
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package tomcat6 is not installed, so not removed

---

