---
title: "Issues with Virtualbox after upgrading from 14.04 to 14.10"
date: 2014-11-23
forum: Virtualisation
---

### Post by cato4 on 2014-11-23
Hello,

After i did the upgrade my virtual box has stopped working.

I have tried re-installing it and also done the "purge" command both with apt-get and also with aptitude.

The error code i get is as following (with aptitude)


[HTML]Fetched 21.3 MB in 17min 47s (20.0 kB/s)                                        Selecting previously unselected package virtualbox.(Reading database ... 205441 files and directories currently installed.)Preparing to unpack .../virtualbox_4.3.18-dfsg-1_amd64.deb ...Unpacking virtualbox (4.3.18-dfsg-1) ...Selecting previously unselected package virtualbox-dkms.Preparing to unpack .../virtualbox-dkms_4.3.18-dfsg-1_all.deb ...Unpacking virtualbox-dkms (4.3.18-dfsg-1) ...Selecting previously unselected package virtualbox-qt.Preparing to unpack .../virtualbox-qt_4.3.18-dfsg-1_amd64.deb ...Unpacking virtualbox-qt (4.3.18-dfsg-1) ...Processing triggers for man-db (2.7.0.2-2) ...Processing triggers for ureadahead (0.100.0-16) ...Processing triggers for bamfdaemon (0.5.1+14.10.20140925-0ubuntu1) ...Rebuilding /usr/share/applications/bamf-2.index...Processing triggers for desktop-file-utils (0.22-1ubuntu2) ...Processing triggers for mime-support (3.55ubuntu1) ...Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...Processing triggers for shared-mime-info (1.2-0ubuntu3) ...Processing triggers for menu (2.1.47ubuntu1) ...Processing triggers for hicolor-icon-theme (0.13-1) ...Setting up virtualbox (4.3.18-dfsg-1) ...insserv: script virtualbox: service vboxdrv already provided!insserv: exiting now!update-rc.d: error: insserv rejected the script headerdpkg: error processing package virtualbox (--configure): subprocess installed post-installation script returned error exit status 1dpkg: dependency problems prevent configuration of virtualbox-dkms: virtualbox-dkms depends on virtualbox (>= 4.3.18-dfsg-1); however:  Package virtualbox is not configured yet.  Package virtualbox-4.3 which provides virtualbox is not installed.
dpkg: error processing package virtualbox-dkms (--configure): dependency problems - leaving unconfigureddpkg: dependency problems prevent configuration of virtualbox-qt: virtualbox-qt depends on virtualbox (= 4.3.18-dfsg-1); however:  Package virtualbox is not configured yet.  Package virtualbox-4.3 which provides virtualbox is not installed.
dpkg: error processing package virtualbox-qt (--configure): dependency problems - leaving unconfiguredProcessing triggers for ureadahead (0.100.0-16) ...No apport report written because the error message indicates its a followup error from a previous failure.                          No apport report written because the error message indicates its a followup error from a previous failure.                                                    Errors were encountered while processing: virtualbox virtualbox-dkms virtualbox-qtE: Sub-process /usr/bin/dpkg returned an error code (1)Failed to perform requested operation on package.  Trying to recover:Setting up virtualbox (4.3.18-dfsg-1) ...insserv: script virtualbox: service vboxdrv already provided!insserv: exiting now!update-rc.d: error: insserv rejected the script headerdpkg: error processing package virtualbox (--configure): subprocess installed post-installation script returned error exit status 1dpkg: dependency problems prevent configuration of virtualbox-dkms: virtualbox-dkms depends on virtualbox (>= 4.3.18-dfsg-1); however:  Package virtualbox is not configured yet.  Package virtualbox-4.3 which provides virtualbox is not installed.
dpkg: error processing package virtualbox-dkms (--configure): dependency problems - leaving unconfigureddpkg: dependency problems prevent configuration of virtualbox-qt: virtualbox-qt depends on virtualbox (= 4.3.18-dfsg-1); however:  Package virtualbox is not configured yet.  Package virtualbox-4.3 which provides virtualbox is not installed.
dpkg: error processing package virtualbox-qt (--configure): dependency problems - leaving unconfiguredErrors were encountered while processing: virtualbox virtualbox-dkms virtualbox-qt
[/HTML]

---

### Post by cato4 on 2014-11-23
The fault will perhaps be easier to read like this



```
Fetched 21.3 MB in 17min 47s (20.0 kB/s)                                        Selecting previously unselected package virtualbox.
(Reading database ... 205441 files and directories currently installed.)
Preparing to unpack .../virtualbox_4.3.18-dfsg-1_amd64.deb ...
Unpacking virtualbox (4.3.18-dfsg-1) ...
Selecting previously unselected package virtualbox-dkms.
Preparing to unpack .../virtualbox-dkms_4.3.18-dfsg-1_all.deb ...
Unpacking virtualbox-dkms (4.3.18-dfsg-1) ...
Selecting previously unselected package virtualbox-qt.
Preparing to unpack .../virtualbox-qt_4.3.18-dfsg-1_amd64.deb ...
Unpacking virtualbox-qt (4.3.18-dfsg-1) ...
Processing triggers for man-db (2.7.0.2-2) ...
Processing triggers for ureadahead (0.100.0-16) ...
Processing triggers for bamfdaemon (0.5.1+14.10.20140925-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu2) ...
Processing triggers for mime-support (3.55ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Processing triggers for menu (2.1.47ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Setting up virtualbox (4.3.18-dfsg-1) ...
insserv: script virtualbox: service vboxdrv already provided!
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package virtualbox (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of virtualbox-dkms:
 virtualbox-dkms depends on virtualbox (>= 4.3.18-dfsg-1); however:
  Package virtualbox is not configured yet.
  Package virtualbox-4.3 which provides virtualbox is not installed.


dpkg: error processing package virtualbox-dkms (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of virtualbox-qt:
 virtualbox-qt depends on virtualbox (= 4.3.18-dfsg-1); however:
  Package virtualbox is not configured yet.
  Package virtualbox-4.3 which provides virtualbox is not installed.


dpkg: error processing package virtualbox-qt (--configure):
 dependency problems - leaving unconfigured
Processing triggers for ureadahead (0.100.0-16) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 virtualbox
 virtualbox-dkms
 virtualbox-qt
E: Sub-process /usr/bin/dpkg returned an error code (1)
Failed to perform requested operation on package.  Trying to recover:
Setting up virtualbox (4.3.18-dfsg-1) ...
insserv: script virtualbox: service vboxdrv already provided!
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package virtualbox (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of virtualbox-dkms:
 virtualbox-dkms depends on virtualbox (>= 4.3.18-dfsg-1); however:
  Package virtualbox is not configured yet.
  Package virtualbox-4.3 which provides virtualbox is not installed.


dpkg: error processing package virtualbox-dkms (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of virtualbox-qt:
 virtualbox-qt depends on virtualbox (= 4.3.18-dfsg-1); however:
  Package virtualbox is not configured yet.
  Package virtualbox-4.3 which provides virtualbox is not installed.


dpkg: error processing package virtualbox-qt (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 virtualbox
 virtualbox-dkms
 virtualbox-qt



```

---

### Post by ibjsb4 on 2014-11-23
> Package virtualbox-4.3 which provides virtualbox is not installed.
Check to see if this package is available.
```
apt-cache policy virtualbox-4.3
```
Try fixing any pending configurations and repair broken packages.
```
sudo dpkg --configure -a && sudo apt-get -f install
```

---

### Post by cato4 on 2014-11-23
Hello,

here is what i got:

```
@bob:~$ apt-cache policy virtualbox-4.3virtualbox-4.3:
  Installed: (none)
  Candidate: (none)
  Version table:
     4.3.16-95972~Ubuntu~raring 0
        100 /var/lib/dpkg/status



```

I guess this means that the policy is not there.
If that is the case, how do i force the policy in there ?

```
@bob:~$ sudo dpkg --configure -a && sudo apt-get -f installSetting up virtualbox (4.3.18-dfsg-1) ...
insserv: script virtualbox: service vboxdrv already provided!
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package virtualbox (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of virtualbox-dkms:
 virtualbox-dkms depends on virtualbox (>= 4.3.18-dfsg-1); however:
  Package virtualbox is not configured yet.
  Package virtualbox-4.3 which provides virtualbox is not installed.


dpkg: error processing package virtualbox-dkms (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of virtualbox-qt:
 virtualbox-qt depends on virtualbox (= 4.3.18-dfsg-1); however:
  Package virtualbox is not configured yet.
  Package virtualbox-4.3 which provides virtualbox is not installed.


dpkg: error processing package virtualbox-qt (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 virtualbox
 virtualbox-dkms
 virtualbox-qt



```

---

### Post by ibjsb4 on 2014-11-23
```
sudo apt-get update
```
That command is needed durning the install process.
Then check 
```
apt-cache policy virtualbox-4.3
```
[B][I]Not
[/I][/B]```
apt-cache policy virtualbox-4.3-virtualbox-4.3:
```

EDIT
Also try
```
apt-cache policy virtualbox
```

---

### Post by cato4 on 2014-11-23
the command:  apt-cache policy virtualbox-4.3-virtualbox-4.3:

Yielded the folowing

```


bob:~$ apt-cache policy virtualbox-4.3
virtualbox-4.3:
  Installed: (none)
  Candidate: (none)
  Version table:
     4.3.16-95972~Ubuntu~raring 0
        100 /var/lib/dpkg/status




```

---

### Post by ibjsb4 on 2014-11-23
What about the last command

---

### Post by cato4 on 2014-11-23
The last command gave this:

```


@bob:~$ apt-cache policy virtualboxvirtualbox:
  Installed: 4.3.18-dfsg-1
  Candidate: 4.3.18-dfsg-1
  Version table:
 *** 4.3.18-dfsg-1 0
        500 http://archive.ubuntu.com/ubuntu/ utopic/multiverse amd64 Packages
        100 /var/lib/dpkg/status



```

---

### Post by cato4 on 2014-11-23
I tried starting the program in the command line and got this:

```

@bob:~$ virtualbox
WARNING: The character device /dev/vboxdrv does not exist.
     Please install the virtualbox-dkms package and the appropriate
     headers, most likely linux-headers-generic.


     You will not be able to start VMs until this problem is fixed.
Qt WARNING: void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "S&tart" under id 16 
Qt WARNING: void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "&Pause" under id 17 
Qt WARNING: void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "&Reset" under id 18 
Qt WARNING: void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "D&iscard saved state..." under id 24 
Qt WARNING: void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "Re&fresh..." under id 25 
Qt WARNING: void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "Show in File Manager" under id 27 
Qt WARNING: void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "Create Shortcut on Desktop" under id 28 



```

---

### Post by ibjsb4 on 2014-11-23
```
sudo apt-get install virtualbox
```
Does it come back stating already installed?

---

### Post by cato4 on 2014-11-23
When i run that command then it says:

```


@bob:~$ sudo apt-get install virtualboxReading package lists... Done
Building dependency tree       
Reading state information... Done
virtualbox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up virtualbox (4.3.18-dfsg-1) ...
insserv: script virtualbox: service vboxdrv already provided!
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package virtualbox (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of virtualbox-qt:
 virtualbox-qt depends on virtualbox (= 4.3.18-dfsg-1); however:
  Package virtualbox is not configured yet.
  Package virtualbox-4.3 which provides virtualbox is not installed.


dpkg: error processing package virtualbox-qt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of virtualbox-dkms:
 virtualbox-dkms depends on virtualbox (>= 4.3.18-dfsg-1); however:
  Package virtualbox is not configured yet.
  Package virtualbox-4.3 which provides virtualbox is not installed.


dpkg: error processing package virtualbox-dkms (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 virtualbox
 virtualbox-qt
 virtualbox-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by ibjsb4 on 2014-11-23
> and the appropriate headers, most likely linux-headers-generic.

Got them installed?

---

### Post by cato4 on 2014-11-23
The only header i could see from this was that the virtualbox-dkms was not installed.


So i did this:

```

@bob:~$ sudo apt-get install virtualbox-dkmsReading package lists... Done
Building dependency tree       
Reading state information... Done
virtualbox-dkms is already the newest version.
virtualbox-dkms set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up virtualbox (4.3.18-dfsg-1) ...
insserv: script virtualbox: service vboxdrv already provided!
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package virtualbox (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of virtualbox-qt:
 virtualbox-qt depends on virtualbox (= 4.3.18-dfsg-1); however:
  Package virtualbox is not configured yet.
  Package virtualbox-4.3 which provides virtualbox is not installed.


dpkg: error processing package virtualbox-qt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of virtualbox-dkms:
 virtualbox-dkms depends on virtualbox (>= 4.3.18-dfsg-1); however:
  Package virtualbox is not configured yet.
  Package virtualbox-4.3 which provides virtualbox is not installed.


dpkg: error processing package virtualbox-dkms (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                     Errors were encountered while processing:
 virtualbox
 virtualbox-qt
 virtualbox-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by ibjsb4 on 2014-11-23
```
sudo apt-get install linux-headers-generic
```
Then update
Not sure about aptitude, but to make sure the kernel is upgraded:
```
sudo apt-get dist-upgrade
```

---

### Post by cato4 on 2014-11-23
I did some further faultfinding.

After having started Virtualbox in the command line it did indeed start.

When i tried starting one of the Vboxes i got this message:

Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

[COLOR=#0000ff]'/etc/init.d/vboxdrv setup'[/COLOR]

as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

I did the command mentioned in blue and got this:

```

 sudo /etc/init.d/vboxdrv setup
Stopping VirtualBox kernel modules ...done.
Uninstalling old VirtualBox DKMS kernel modules/etc/init.d/vboxdrv: 302: /etc/init.d/vboxdrv: /usr/share/virtualbox/src/vboxhost/do_dkms: not found
 ...done.
Trying to register the VirtualBox kernel modules using DKMS/etc/init.d/vboxdrv: 327: /etc/init.d/vboxdrv: /usr/share/virtualbox/src/vboxhost/do_dkms: not found
 ...failed!
  (Failed, trying without DKMS)
Recompiling VirtualBox kernel modules ...failed!
  (Look at /var/log/vbox-install.log to find out what went wrong)



```


When i go to the log file mentioned here i get this:

```

/etc/init.d/vboxdrv: 334: /etc/init.d/vboxdrv: /usr/share/virtualbox/src/vboxhost/build_in_tmp: not found
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                                                                                                      
~                                                                               
~                                                                               
~                                                                               
"/var/log/vbox-install.log" [readonly] 1 line, 106 characters



```

---

### Post by cato4 on 2014-11-23
I did the two commands and they gave both much the same results


```

@bob:/$ sudo apt-get install linux-headers-genericReading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up virtualbox (4.3.18-dfsg-1) ...
insserv: script virtualbox: service vboxdrv already provided!
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package virtualbox (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of virtualbox-qt:
 virtualbox-qt depends on virtualbox (= 4.3.18-dfsg-1); however:
  Package virtualbox is not configured yet.
  Package virtualbox-4.3 which provides virtualbox is not installed.


dpkg: error processing package virtualbox-qt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of virtualbox-dkms:
 virtualbox-dkms depends on virtualbox (>= 4.3.18-dfsg-1); however:
  Package virtualbox is not configured yet.
  Package virtualbox-4.3 which provides virtualbox is not installed.


dpkg: error processing package virtualbox-dkms (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                     Errors were encountered while processing:
 virtualbox
 virtualbox-qt
 virtualbox-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)



```


```

@bob:/$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up virtualbox (4.3.18-dfsg-1) ...
insserv: script virtualbox: service vboxdrv already provided!
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package virtualbox (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of virtualbox-qt:
 virtualbox-qt depends on virtualbox (= 4.3.18-dfsg-1); however:
  Package virtualbox is not configured yet.
  Package virtualbox-4.3 which provides virtualbox is not installed.


dpkg: error processing package virtualbox-qt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of virtualbox-dkms:
 virtualbox-dkms depends on virtualbox (>= 4.3.18-dfsg-1); however:
  Package virtualbox is not configured yet.
  Package virtualbox-4.3 which provides virtualbox is not installed.


dpkg: error processing package virtualbox-dkms (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                     Errors were encountered while processing:
 virtualbox
 virtualbox-qt
 virtualbox-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by ibjsb4 on 2014-11-23
I think its time for a reinstall.
And before installing, open Nautilus as administrator.  Go to your FileSystem and do a search on virtualbox.  And remove any leftover packages.  With the exception of your virtual machines 'VirtualBox VMs' located in your Home directory.  No need to remove png's.
```
gksudo nautilus
```

---

### Post by cato4 on 2014-11-23
Thanks a milion ibjs4!

All works great now!

During the install after having deleted manually the files you mentioned apt-get spent some time generating the kernelmodule and now it is working!

---

### Post by ibjsb4 on 2014-11-23
Welcome :)

---

