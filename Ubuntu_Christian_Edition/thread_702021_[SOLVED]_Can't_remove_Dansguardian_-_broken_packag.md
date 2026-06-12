---
title: "[SOLVED] Can't remove Dansguardian - broken package"
date: 2008-02-19
forum: Ubuntu Christian Edition
---

### Post by alingham on 2008-02-19
Hi there. 
So I made the mistake of installing the "install_dansguardian_gui_gutsy" over the top of itself in Ubuntu 7.10 Gutsy...
Now the package dansguardian seems to be broken and will not remove.

When I type sudo apt-get remove dansguardian the following happens:
```

The following packages will be REMOVED:
  dansguardian
0 upgraded, 0 newly installed, 1 to remove and 9 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 1536kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 101158 files and directories currently installed.)
Removing dansguardian ...
Stopping DansGuardian: dansguardian.
/etc/init.d/dansguardian: 71: /usr/local/apps/parental-control/./dansguardian_log.pl: not found
invoke-rc.d: initscript dansguardian, action "stop" failed.
dpkg: error processing dansguardian (--remove):
 subprocess pre-removal script returned error exit status 127
Starting DansGuardian: /usr/sbin/dansguardian: error while loading shared libraries: libesmtp.so.5: cannot open shared object file: No such file or directory
invoke-rc.d: initscript dansguardian, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 dansguardian
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Similar happens using aptitude and synaptic manager, and apt-get install -f doesn't fix anything either...

I'm not sure if this is a dansguardian issue or whether its ubuntu.

Help Anyone!?

---

### Post by theophile on 2008-02-19
Couple ideas:

Assuming the Dansguardian process is called "dansguardian," try:
```
sudo killall dansguardian
``` then try again.

If that doesn't work, try:
```
sudo touch /usr/local/apps/parental-control/./dansguardian_log.pl
```

and then try again. If that doesn't work, see if:
```
sudo apt-get purge dansguardian
```
does any better.

---

### Post by alingham on 2008-02-19
Thanks for your reply - however no success...
The results for the aforementioned are:
```

sudo killall dansguardian
dansguardian: no process killed

```
```

sudo touch /usr/local/apps/parental-control/./dansguardian_log.pl
touch: cannot touch `/usr/local/apps/parental-control/./dansguardian_log.pl': No such file or directory

```
```

sudo apt-get purge dansguardian
Removing dansguardian ...
Stopping DansGuardian: dansguardian.
/etc/init.d/dansguardian: 71: /usr/local/apps/parental-control/./dansguardian_log.pl: not found
invoke-rc.d: initscript dansguardian, action "stop" failed.
dpkg: error processing dansguardian (--purge):
 subprocess pre-removal script returned error exit status 127
Starting DansGuardian: /usr/sbin/dansguardian: error while loading shared libraries: libesmtp.so.5: cannot open shared object file: No such file or directory
invoke-rc.d: initscript dansguardian, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 dansguardian
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Same old story...
Any other thoughts anyone?

---

### Post by alingham on 2008-02-19
Went searching for the dpkg error and found this thread:

[http://ubuntuforums.org/showthread.php?t=421971]("http://ubuntuforums.org/showthread.php?t=421971")


I deleted the dansguardian file from /etc/init.d/  (dpkg-dansguardian wasn't there)
```
 sudo rm /etc/init.d/dansguardian 
```

and then removed dansguardian via apt-get..
```
 sudo apt-get remove dansguardian 
```

Seems to have fixed the problem!!!

---

### Post by theophile on 2008-02-19
Try:
```
sudo apt-get install libesmtp
```
Then:
```
sudo /etc/init.d/dansguardian start
```
If that is successful, then try removing dansguardian again with:
```
apt-get remove dansguardian
```
If that doesn't work, let me ssh into your box. ;-)

---

### Post by theophile on 2008-02-19
OK, glad you found a solution. Though I never would have told you to delete the init script!

---

