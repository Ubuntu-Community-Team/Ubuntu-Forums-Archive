---
title: "VirtualBox refuses to start up"
date: 2014-12-07
forum: Virtualisation
---

### Post by joe_blow2 on 2014-12-07
Hi,

When I try to start VirtualBox from the command line, I get this message:

> user@user:~$ virtualbox
/usr/bin/virtualbox: 1: /usr/bin/virtualbox: grep: Permission denied
/usr/bin/virtualbox: 1: /usr/bin/virtualbox: awk: Permission denied
/usr/bin/virtualbox: 1: /usr/bin/virtualbox: whoami: Permission denied
/usr/bin/virtualbox: 1: /usr/bin/virtualbox: ps: Permission denied
/usr/bin/virtualbox: 1: /usr/bin/virtualbox: basename: Permission denied
Unknown application - 



I think I might have deleted the /usr folder a while ago by accident when I was cleaning out unnecessary files.... What should I do to correct this? Uninstalling and reinstalling doesn't seem to help and I can't find any other solutions...

---

### Post by TheFu on 2014-12-07
What does
```
ls -al /usr/bin/virt*
```
show?

If you deleted /usr - time to reinstall.  /usr is like removing /windows/system32 -  bad.

---

### Post by ajgreeny on 2014-12-07
> I think I might have deleted the /usr folder a while ago by accident when I was cleaning out unnecessary files.
Do you mean the complete /usr folder, or just the /usr/lib/virtualbox folder, or even one of the various vb files in/usr/bin,  where there are about 13 various executables, scripts or links to other vb files.

There is no /usr/virtualbox folder to remove so it would be good to know exactly what you did.

---

### Post by joe_blow2 on 2014-12-07
> **TheFu said:**
> What does
```
ls -al /usr/bin/virt*
```
show?

If you deleted /usr - time to reinstall.  /usr is like removing /windows/system32 -  bad.

It shows me

> user@user:~$ ls -al /usr/bin/virt*
-rwxr-xr-x 1 root root   510168 sept 24  2013 /usr/bin/virt_mail
lrwxrwxrwx 1 root root       27 apr  7  2014 /usr/bin/virtualbox -> ../share/virtualbox/VBox.sh
-rwxr-xr-x 1 root root 12103400 sept 24  2013 /usr/bin/virtuoso-t


I think I deleted the entire /usr folder, hitting myself in the head right now........ There's no way to get it back I suppose?

---

### Post by TheFu on 2014-12-07
> **joe_blow2 said:**
> I think I deleted the entire /usr folder, hitting myself in the head right now........ There's no way to get it back I suppose?

Well, if that 'ls' command shows what you say, then you did NOT delete /usr.

However, this cannot be deleted by a normal userid accidentally - root or sudo is required to make that happen.  If you did remove it, I don't think the system would work very much.  Definitely no GUI would run.  If that happened, either reinstall or restoring from a backup would be the solution. You do have backups, right?

anyway - at this point we don't know what the issue is - follow the links to see what happened.
Could it be that you removed /bin?  This is the same, terrible issue.  Got backups?

I would probably just reinstall virtualbox and try again.

---

### Post by joe_blow2 on 2014-12-08
> **TheFu said:**
> Well, if that 'ls' command shows what you say, then you did NOT delete /usr.

However, this cannot be deleted by a normal userid accidentally - root or sudo is required to make that happen.  If you did remove it, I don't think the system would work very much.  Definitely no GUI would run.  If that happened, either reinstall or restoring from a backup would be the solution. You do have backups, right?

anyway - at this point we don't know what the issue is - follow the links to see what happened.
Could it be that you removed /bin?  This is the same, terrible issue.  Got backups?

I would probably just reinstall virtualbox and try again.

I checked whether I deleted those by seeing what  cd /usr    and cd /bin   showed me, and they do indeed exist on my computer so I guess I didn't delete them. I tried removing and installing again, it didn't change anything. I noticed a strange script when it was installing, take a look:

> user@user:~$ sudo apt-get install virtualbox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  virtualbox-dkms virtualbox-qt
Suggested packages:
  virtualbox-guest-additions-iso vde2
The following NEW packages will be installed:
  virtualbox virtualbox-dkms virtualbox-qt
0 upgraded, 3 newly installed, 0 to remove and 9 not upgraded.
Need to get 0 B/20,6 MB of archives.
After this operation, 84,1 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Selecting previously unselected package virtualbox.
(Reading database ... 250879 files and directories currently installed.)
Preparing to unpack .../virtualbox_4.3.10-dfsg-1_amd64.deb ...
Unpacking virtualbox (4.3.10-dfsg-1) ...
Selecting previously unselected package virtualbox-dkms.
Preparing to unpack .../virtualbox-dkms_4.3.10-dfsg-1_all.deb ...
Unpacking virtualbox-dkms (4.3.10-dfsg-1) ...
Selecting previously unselected package virtualbox-qt.
Preparing to unpack .../virtualbox-qt_4.3.10-dfsg-1_amd64.deb ...
Unpacking virtualbox-qt (4.3.10-dfsg-1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for ureadahead (0.100.0-16) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
**Unknown media type in type 'all/all'**
**Unknown media type in type 'all/allfiles'**
**Unknown media type in type 'uri/mms'**
**Unknown media type in type 'uri/mmst'**
**Unknown media type in type 'uri/mmsu'**
**Unknown media type in type 'uri/pnm'**
**Unknown media type in type 'uri/rtspt'**
**Unknown media type in type 'uri/rtspu'**
Processing triggers for menu (2.1.46ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1) ...
Setting up virtualbox (4.3.10-dfsg-1) ...
 * Stopping VirtualBox kernel modules                                                                                                    [ OK ] 
 * Starting VirtualBox kernel modules                                                                                                            
*** No suitable module for running kernel found**
**                                                                                                                                         [fail]**
**invoke-rc.d: initscript virtualbox, action "restart" failed.**
Setting up virtualbox-dkms (4.3.10-dfsg-1) ...
Loading new virtualbox-4.3.10 DKMS files...
First Installation: checking all kernels...
Building only for 3.13.0-40-generic
Building initial module for 3.13.0-40-generic
Done.


vboxdrv:
Running module version sanity check.
 - Original module
**   - No original module exists within this kernel**
 - Installation
   - Installing to /lib/modules/3.13.0-40-generic/updates/dkms/


vboxnetadp.ko:
Running module version sanity check.
 - Original module
**   - No original module exists within this kernel**
 - Installation
   - Installing to /lib/modules/3.13.0-40-generic/updates/dkms/


vboxnetflt.ko:
Running module version sanity check.
 - Original module
**   - No original module exists within this kernel**
 - Installation
   - Installing to /lib/modules/3.13.0-40-generic/updates/dkms/


vboxpci.ko:
Running module version sanity check.
 - Original module
**   - No original module exists within this kernel**
 - Installation
   - Installing to /lib/modules/3.13.0-40-generic/updates/dkms/


depmod.....................................


DKMS: install completed.
 * Stopping VirtualBox kernel modules                                                                                                    [ OK ] 
 * Starting VirtualBox kernel modules                                                                                                    [ OK ] 
Setting up virtualbox-qt (4.3.10-dfsg-1) ...
Processing triggers for menu (2.1.46ubuntu1) ...





I'm not sure what these mean, could you shed some light on it?

---

### Post by TheFu on 2014-12-08
I stopped using virtualbox a few years ago and never ran it under Linux, but I suspect the system is lacking the required prerequisites for the installation.  Did you follow the installation guides that are available on help.ubuntu.com for this?  I think **more** than apt-get install is required.  Lots of folks in this forum have suggested to others that the Oracle PPA be used to install virtualbox to gain access to current releases and the Oracle PPA instructions probably more clearly specify the dependencies (dkms-something, and a few others probably).

[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) - do not just download the .deb file - follow the instructions to use the PPA. This is 1000x better.
> Note: Ubuntu/Debian users might want to install the dkms package to ensure that the VirtualBox host kernel modules (vboxdrv, vboxnetflt and vboxnetadp) are properly updated

---

