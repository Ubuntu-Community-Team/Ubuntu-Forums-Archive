---
title: "what happens !!!!????"
date: 2009-07-09
forum: Server Platforms
---

### Post by wangfeng3769 on 2009-07-09
[SIZE=3][COLOR=Red]:KShlleo guys when I type
 the command at the terminal "sudo apt-get install subversion libapache2-svn[/COLOR][/SIZE][SIZE=3][COLOR=Red]"[/COLOR][/SIZE][SIZE=3]
wangfeng@wangfeng-desktop:~$ sudo apt-get install subversion libapache2-svn
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-genshi python-tz python-pygments
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libsvn1
Suggested packages:
  db4.6-util subversion-tools
The following NEW packages will be installed:
  libapache2-svn libsvn1 subversion
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1222kB of archives.
After this operation, 6337kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Selecting previously deselected package libsvn1.
(Reading database ... 169179 files and directories currently installed.)
Unpacking libsvn1 (from .../libsvn1_1.5.4dfsg1-1ubuntu2_i386.deb) ...
Selecting previously deselected package libapache2-svn.
Unpacking libapache2-svn (from .../libapache2-svn_1.5.4dfsg1-1ubuntu2_i386.deb) ...
Selecting previously deselected package subversion.
Unpacking subversion (from .../subversion_1.5.4dfsg1-1ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Setting up libsvn1 (1.5.4dfsg1-1ubuntu2) ...

Setting up libapache2-svn (1.5.4dfsg1-1ubuntu2) ...
ERROR: Module dav_svn does not exist!
dpkg: error processing libapache2-svn (--configure):
 subprocess post-installation script returned error exit status 1
Setting up subversion (1.5.4dfsg1-1ubuntu2) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
[/SIZE][SIZE=3][COLOR=Blue]Errors were encountered while processing:
 libapache2-svn
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR][/SIZE][SIZE=3]
how can I solve the problem?
thank you [/SIZE]

---

### Post by crazyone on 2009-07-09
have you tried entring in the terminal "sudo dpkg --configure -a"  hope that helps

---

### Post by paul555 on 2009-08-16
I run also into this problem lately.I solved it by removing libapache2-svn and then reinstalling all the apache related packages and after that installing again libapache2-svn.Hope it helps.

---

