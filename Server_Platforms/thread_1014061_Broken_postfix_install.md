---
title: "Broken postfix install"
date: 2008-12-17
forum: Server Platforms
---

### Post by lancherider on 2008-12-17
While testing out different MTAs on 8.04, I inadvertently deleted a bunch of postfix files, which evidently broke the installation. Now, when I try to remove postfix, I get the following:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  postfix
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 2966kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 32574 files and directories currently installed.)
Removing postfix ...
invoke-rc.d: unknown initscript, /etc/init.d/postfix not found.
dpkg: error processing postfix (--remove):
 subprocess pre-removal script returned error exit status 100
.: 13: Can't open /usr/share/postfix/postinst.functions
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

When I try to run apt-get install postfix to try and repair the installation, I get:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
postfix is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up postfix (2.5.1-2ubuntu1.2) ...
.: 13: Can't open /usr/share/postfix/postinst.functions
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

How do I fix this?

---

### Post by lancherider on 2008-12-17
Just in case anyone is curious, I fixed this by copying /etc/init.d/postfix from another system and then used apt-get purge postfix. Everything seems OK now.

---

### Post by pqangel on 2008-12-17
hi, i have the same problem as you but with courier-imap

do you happen to have the courier-imap located in init.d??

would you be so kind of uploading it so i can use it and try to fix my problem??

thanks :D

---

