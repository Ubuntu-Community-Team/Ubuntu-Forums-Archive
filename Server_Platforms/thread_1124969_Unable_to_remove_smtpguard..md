---
title: "Unable to remove smtpguard."
date: 2009-04-13
forum: Server Platforms
---

### Post by jms1989 on 2009-04-13
Hello, I am trying to remove smtpguard and its dependencies but I keep running into an error.

> 
jms1989@compaq-linux:~$ sudo apt-get remove smtpguard
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsmtpguard1 libdb4.3
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  smtpguard
0 upgraded, 0 newly installed, 1 to remove and 61 not upgraded.
After this operation, 184kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 57249 files and directories currently installed.)
Removing smtpguard ...
Stopping smtpguard: invoke-rc.d: initscript smtpguard, action "stop" failed.
dpkg: error processing smtpguard (--remove):
 subprocess pre-removal script returned error exit status 1
Starting smtpguard: smtpguard-daemon.
Errors were encountered while processing:
 smtpguard
E: Sub-process /usr/bin/dpkg returned an error code (1)


What am I missing? Btw, its running ubuntu server 8.04 32bit

I've tried with countless retries and end up with the same results.

---

### Post by brian_p on 2009-04-14
> **jms1989 said:**
> 

Removing smtpguard ...
Stopping smtpguard: invoke-rc.d: initscript smtpguard, action "stop" failed.

Try stopping smtpguard manually first:

```
sudo /etc/init.d/smtpguard stop
```

---

### Post by jms1989 on 2009-04-14
same error, no change.

---

### Post by brian_p on 2009-04-14
> **jms1989 said:**
> same error, no change.

Looks like a possible bug.

---

### Post by jms1989 on 2009-04-14
I really need to remove it, is there a way to find what files and directories are installed from the package from the command line so I can delete them and rebuild apt package list?

---

### Post by brian_p on 2009-04-14
> **jms1989 said:**
> I really need to remove it, is there a way to find what files and directories are installed from the package from the command line so I can delete them and rebuild apt package list?

```
dpkg -L smtpguard

```
for the files installed by the package. Remove manually.

You could try

```
dpkg -r smtpguard
```

beforehand, but I wouldn't hold out much hope for it if there is a bug in one of the removal scripts.

---

### Post by jms1989 on 2009-04-14
Alright, how do I get apt to see my manual changes? Refresh the installed package lists? not sources.

Nevermind, I got it to see the changes by running sudo dpkg -r smtpguard and then purge the config files by running sudo dpkg -P smtpguard

My problem is solved.

---

