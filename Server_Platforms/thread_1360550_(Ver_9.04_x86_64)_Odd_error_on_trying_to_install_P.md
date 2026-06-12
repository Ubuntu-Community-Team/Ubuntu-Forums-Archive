---
title: "(Ver: 9.04 x86_64) Odd error on trying to install PureFTPD"
date: 2009-12-21
forum: Server Platforms
---

### Post by RobbieThe1st on 2009-12-21
I have a bit of a problem. I have a new VPS from eukhost.com which is running Ubuntu 9.04(I've been using eukhost.com for several years now, and just had my VPS switched over to Ubuntu from CentOS - They don't have 9.10 yet, BTW).
After getting it, I started setting it up. I have been following [This]("http://www.howtoforge.com/perfect-server-ubuntu-9.04-ispconfig-3") tutorial, starting after the server-install part of it.
Everything seems to work fine, but PureFTPD. I can't install it. When I try, I get this:
```
root@vps****:~# apt-get install pure-ftpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libcrypt-openssl-rsa-perl libconvert-tnef-perl libio-stringy-perl
  libarchive-zip-perl libmime-tools-perl libnet-cidr-perl libnet-server-perl
  pax libmail-dkim-perl libconvert-uulib-perl libberkeleydb-perl
  libio-multiplex-perl libconvert-binhex-perl libunix-syslog-perl
  libcrypt-openssl-bignum-perl
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  pure-ftpd
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/169kB of archives.
After this operation, 528kB of additional disk space will be used.
Traceback (most recent call last):
  File "/usr/bin/apt-listchanges", line 33, in <module>
    from ALChacks import *
  File "/usr/share/apt-listchanges/ALChacks.py", line 32, in <module>
    sys.stderr.write(_("Can't set locale; make sure $LC_* and $LANG are correct!\n"))
NameError: name '_' is not defined
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Selecting previously deselected package pure-ftpd.
(Reading database ... 36079 files and directories currently installed.)
Unpacking pure-ftpd (from .../pure-ftpd_1.0.21-11.4ubuntu1_amd64.deb) ...
Setting up pure-ftpd (1.0.21-11.4ubuntu1) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Starting ftp server: perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Running: /usr/sbin/pure-ftpd -l pam -O clf:/var/log/pure-ftpd/transfer.log -u 1000 -E -B
invoke-rc.d: initscript pure-ftpd, action "start" failed.
dpkg: error processing pure-ftpd (--configure):
 subprocess post-installation script returned error exit status 252
Errors were encountered while processing:
 pure-ftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@vps****:~# 

```Theres a bunch of odd language error stuff, but I don't think thats causing the problem - Every single other thing I installed had those errors, and that stuff seems to work fine(I wouldn't mind finding a way to fix it though..).

The one thing I do see there is:
```

Running: /usr/sbin/pure-ftpd -l pam -O clf:/var/log/pure-ftpd/transfer.log -u 1000 -E -B
invoke-rc.d: initscript pure-ftpd, action "start" failed.

```That looks like its the problem. 
I did some googling, and found a couple solutions to the problem, involving recompiling the package after editing a certain file. However, upon extracting the source package, I can't find the file that needs to be edited!

My specs:
Virtualizer: Parallels/Virtuozzo.
Ram: 384MB
OS: ubuntu-9.04-x86_64, up-to-date updates-wise

What do I do? 

Thanks,
-RobbieThe1st

---

### Post by RobbieThe1st on 2009-12-21
I'm fairly new to this forum, and as such don't know the neuances of bumping posts/bringing topics to the top where they will be read. I looked in the forum code of conduct, but didn't see anything specific. I also looked for a specific bump tool, but didn't see one.
As such, let me know if I did wrong by bumping this topic from several pages down.

---

