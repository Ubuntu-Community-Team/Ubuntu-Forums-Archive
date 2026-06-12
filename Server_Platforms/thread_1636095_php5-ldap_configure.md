---
title: "php5-ldap configure"
date: 2010-12-02
forum: Server Platforms
---

### Post by bobwdn on 2010-12-02
I have for months been searching to solve this issue and keep failing. Therefore I need some help.

I was attempting to install and configure ldap onto my file server to allow the clients to share user info. During the setup (back weeks or months ago and I forgot what I did) I did a system security upgrade and began seeing the following code:
```
dpkg: warning: files list file for package `libelf1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `hddtemp' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libfile-rsyncp-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `debconf' missing, assuming package has no files currently installed.
```

Now, not just these four files are listed, rather there are so many that I cannot scroll back up to the top of them in a terminal.

System upgrades usually go okay. I mean the upgrade files are installed and the server seems to be working okay. But, most upgrade conclude with the following:
```
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 grub-pc
 libapache2-mod-php5
 php5-cgi
 php5
 php5-ldap
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up php5-cgi (5.3.2-1ubuntu4.5) ...
dpkg: error processing php5-cgi (--configure):
 subprocess installed post-installation script returned error exit status 10
Setting up grub-pc (1.98-1ubuntu8) ...
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 10
Setting up libapache2-mod-php5 (5.3.2-1ubuntu4.5) ...
dpkg: error processing libapache2-mod-php5 (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of php5:
 php5 depends on libapache2-mod-php5 (>= 5.3.2-1ubuntu4.5) | libapache2-mod-php5filter (>= 5.3.2-1ubuntu4.5) | php5-cgi (>= 5.3.2-1ubuntu4.5); however:
  Package libapache2-mod-php5 is not configured yet.
  Package libapache2-mod-php5filter is not installed.
  Package php5-cgi is not configured yet.
dpkg: error processing php5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php5-ldap:
 php5-ldap depends on phpapi-20090626+lfs; however:
  Package phpapi-20090626+lfs is not installed.
  Package libapache2-mod-php5filter which provides phpapi-20090626+lfs is not installed.
  Package libapache2-mod-php5 which provides phpapi-20090626+lfs is not configured yet.
  Package php5-cli which provides phpapi-20090626+lfs is not installed.
  Package php5-cgi which provides phpapi-20090626+lfs is not configured yet.
dpkg: error processing php5-ldap (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 php5-cgi
 grub-pc
 libapache2-mod-php5
 php5
 php5-ldap
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

Current status: 0 updates [-8].
```
As you can see the last upgrade status closes with 0 updates [-8]. Indicating to me, anyway, that all installed correctly. Except for those "Errors where encountered . . . . " at the end. A similar output is at the end of any aptitude or apt-get installations.

I have become confused and cannot tell if I have compound unrelated issues or just one simple configuration issue. That being ```
dpkg: dependency problems prevent configuration of php5:
 php5 depends on libapache2-mod-php5 (>= 5.3.2-1ubuntu4.5) | libapache2-mod-php5filter (>= 5.3.2-1ubuntu4.5) | php5-cgi (>= 5.3.2-1ubuntu4.5); however:
  Package libapache2-mod-php5 is not configured yet.
  Package libapache2-mod-php5filter is not installed.
  Package php5-cgi is not configured yet.
```

I am open to suggestions. If these mods need to be re-configured and are related to php5 somehow . . . well, any ideas where to start?

---

### Post by bobwdn on 2010-12-03
So, thirteen hours after I posted my initial post, no responds and that's okay. I have an out of control, do not remember details, type of problem. (Lesson number 1 - do not leave the problem to fix itself, duh!!):redface:

So, this morning I purged php5-cgi, libapache2-mod-php5, php5, php5-ldap and php5-common. And will start all over with that some other time. 

Last night I remembered that I think (lesson number 2 - don't wait so long to fix) my problem began when I upgraded to 10.04 server (from 9.10.)

(Lesson number 3 - take copious notes, and keep them!!):oops:

So, I am down to: ```
server:~$ sudo aptitude full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following partially installed packages will be configured:
  grub-pc 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up grub-pc (1.98-1ubuntu8) ...
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up grub-pc (1.98-1ubuntu8) ...
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
```
I have purged grub-pc. Changed my /etc/apt/sources.list server to a different (non-US) repository mirror. And still grub-pc will not re-install correctly. I get the above listed error. (I did cross my fingers and reboot the server and it restarted okay.)

What do I try now?:confused:

---

### Post by bobwdn on 2010-12-04
I'm still working on this.

This morning an upgrade to grub-pc and grub-common was released. And I have completed, said upgrade and this is the result:
```
Preparing to replace grub-pc 1.98-1ubuntu8 (using .../grub-pc_1.98-1ubuntu9_i386.deb) ...
Unpacking replacement grub-pc ...
Preparing to replace grub-common 1.98-1ubuntu8 (using .../grub-common_1.98-1ubuntu9_i386.deb) ...
Unpacking replacement grub-common ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Setting up grub-common (1.98-1ubuntu9) ...
Installing new version of config file /etc/grub.d/10_linux ...

Setting up grub-pc (1.98-1ubuntu9) ...
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 10
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up grub-pc (1.98-1ubuntu9) ...
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 10
[COLOR="Navy"]Errors were encountered while processing:
 grub-pc[/COLOR]
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

Current status: 0 updates [-2].
```

Yes, I have tried apt-get -f install.

Yes, I have tried *sudo dpkg --configure grub-pc* and I get these errors:
```
server:~$ sudo dpkg --configure grub-pc
Setting up grub-pc (1.98-1ubuntu9) ...
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 grub-pc
```

Yes, I tried *sudo dpkg -f install* and I get these results:
```
dpkg-deb: failed to read archive `install': No such file or directory
```

Now I have *sudo apt-get --purge remove grub-pc* and did *sudo aptitude update* and finally reinstalled grub-pb with *sudo aptitude install grub-pc* and the final code I get is:
```
Unpacking grub-pc (from .../grub-pc_1.98-1ubuntu9_i386.deb) ...
Processing triggers for man-db ...
Setting up grub-pc (1.98-1ubuntu9) ...
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up grub-pc (1.98-1ubuntu9) ...
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 grub-pc
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
```

So, I would still greatly appreciate anyones help with what I should try next. Any ideas?

---

### Post by bobwdn on 2010-12-04
I have just spent that last hour following this post:

[http://ubuntuforums.org/showthread.php?t=12737](http://ubuntuforums.org/showthread.php?t=12737)

And installing grub-pc went like this:
```
Unpacking grub-common (from .../grub-common_1.98-1ubuntu9_i386.deb) ...
Selecting previously deselected package grub-pc.
Unpacking grub-pc (from .../grub-pc_1.98-1ubuntu9_i386.deb) ...
Processing triggers for install-info ...
Processing triggers for man-db ...
Setting up grub-common (1.98-1ubuntu9) ...

Setting up grub-pc (1.98-1ubuntu9) ...
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Today, I stop with frustration. Tomorrow or Monday, I may try again.

In the mean time I am open to suggestions. Please help! ](*,)

---

### Post by bobwdn on 2010-12-07
At this time, I am unable to locate any alternative information pertaining to my problem. Therefore, for me, this issue remains unresolved.

---

