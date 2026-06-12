---
title: "VirtualBox - How to get back to Oracle version"
date: 2013-12-13
forum: Virtualisation
---

### Post by satimis on 2013-12-13
Hi all,

Host   Ubuntu 12.04 64bit
Guest  Ubuntu 12.04  b4bit
Virtualbox, Oracle

Receently after upgrade Virtualbox it is discovered the version of VirtualBox changed to Ubuntu version NOT Oracle version resulting in unable installing Oracle GuestAddition on VM.  Please advise is there any way getting back to Oracle version rather than reinstall the PC.  Thanks

Rgds
satimis

---

### Post by mikewhatever on 2013-12-14
Well, remove whatever version of VBOX you have installed, then get [one from here]("https://www.virtualbox.org/wiki/Linux_Downloads"), and install it.
Note: All versions of Virtual Box are Oracle's, there is no such thing as an 'Ubuntu version'.

---

### Post by satimis on 2013-12-14
> **mikewhatever said:**
> Well, remove whatever version of VBOX you have installed, then get [one from here]("https://www.virtualbox.org/wiki/Linux_Downloads"), and install it.
Note: All versions of Virtual Box are Oracle's, there is no such thing as an 'Ubuntu version'.
Hi,

Thanks for your advice.

I have >25VMs running.  If removing the VBOX would it remove all VMs simutaneously?

On Oracle VM Virtual Manager
Help -> About Virtual Box
it displays```

virtualbox interface graphical user interface version 4.1.12_Ubuntu c77245

```

Rgds
satimis

---

### Post by mikewhatever on 2013-12-14
No, it should not remove the VMs.
Ubuntu in the name does not mean it's not Oracle's. Note, for example, what Oracle's installation file for 13.10 is called:
**virtualbox-4.3_4.3.4-91027~Ubuntu~raring_i386.deb**.

---

### Post by JKyleOKC on 2013-12-14
> **satimis said:**
> I have >25VMs running.  If removing the VBOX would it remove all VMs simutaneously?No it will not remove any of your VMs. However, be sure how have all of them in "powered off" state, not "saved" when you make the change. You will be moving up by not one, but two, minor revisions (4.1.x to 4.3.4) and Oracle made a few changes in the way "saved" state works during that interval. After I upgraded from 4.2 to 4.3, none of my "saved" VMs would load. However, using the "discard" button to drop the saved data made them work right once more, and all now save just as they did before the upgrade.

It's always disconcerting, though, to get error messages immediately after doing an upgrade, even when there's a simple fix for the errors and you know what it is!

---

### Post by satimis on 2013-12-17
Hi all,

I have a spare PC with following setup:

Host	Ubuntu 12.04 64bit
VirtualBox 4.2.20

Just started this PC and VirtualBox, following notice popup (see attached file) asking to download a new version of VirtualBox.  VBoxGuestAddition works on Ubuntu12043/Debian7.2/LinuxMint16(guests) without problem but unable to work on Fedora19/CentOS6.5(Guests)

Now I recall that I did it about 2 weeks ago on the daily working PC, installing the package download on Orcle website pushing the PC to present situation.

I further discover:
On the spare PC - ls /usr/share/virtualbox```

nls                    src                     VBoxSysInfo.sh
rdesktop-vrdp-keymaps  VBoxCreateUSBNode.sh
rdesktop-vrdp.tar.gz   VBoxGuestAdditions.iso

```

On the working PC there are 2 folders

/usr/share/virtualbox
/home/satimis/.VirtualBox (I suppose this directory was created at the time when I installed the download package)

$ ls /home/satimis/.VirtualBox/```

compreg.dat                                              VBoxSVC.log.2
Oracle_VM_VirtualBox_Extension_Pack-4.2.10.vbox-extpack  VBoxSVC.log.3
Oracle_VM_VirtualBox_Extension_Pack-4.2.12.vbox-extpack  VBoxSVC.log.4
Oracle_VM_VirtualBox_Extension_Pack-4.2.14.vbox-extpack  VBoxSVC.log.5
Oracle_VM_VirtualBox_Extension_Pack-4.2.16.vbox-extpack  VBoxSVC.log.6
Oracle_VM_VirtualBox_Extension_Pack-4.2.18.vbox-extpack  VBoxSVC.log.7
selectorwindow.log                                       VBoxSVC.log.8
selectorwindow.log.1                                     VBoxSVC.log.9
VBoxGuestAdditions_4.1.12.iso                            VirtualBox.xml
VBoxSVC.log                                              VirtualBox.xml-prev
VBoxSVC.log.1                                            xpti.dat
VBoxSVC.log.10

```

$ ls /usr/share/virtualbox/```

nls  VBox.sh  VBoxSysInfo.sh

```

$ ls /usr/share/virtualbox/nls```

qt_ar.qm     qt_ja.qm     VirtualBox_ar.qm     VirtualBox_ja.qm
qt_bg.qm     qt_km_KH.qm  VirtualBox_bg.qm     VirtualBox_km_KH.qm
qt_ca.qm     qt_ko.qm     VirtualBox_ca.qm     VirtualBox_ko.qm
qt_ca_VA.qm  qt_lt.qm     VirtualBox_ca_VA.qm  VirtualBox_lt.qm
qt_cs.qm     qt_nl.qm     VirtualBox_cs.qm     VirtualBox_nl.qm
qt_da.qm     qt_pl.qm     VirtualBox_da.qm     VirtualBox_pl.qm
qt_de.qm     qt_pt_BR.qm  VirtualBox_de.qm     VirtualBox_pt_BR.qm
qt_el.qm     qt_pt.qm     VirtualBox_el.qm     VirtualBox_pt.qm
qt_en.qm     qt_ro.qm     VirtualBox_en.qm     VirtualBox_ro.qm
qt_es.qm     qt_ru.qm     VirtualBox_es.qm     VirtualBox_ru.qm
qt_eu.qm     qt_sk.qm     VirtualBox_eu.qm     VirtualBox_sk.qm
qt_fi.qm     qt_sr.qm     VirtualBox_fi.qm     VirtualBox_sr.qm
qt_fr.qm     qt_sv.qm     VirtualBox_fr.qm     VirtualBox_sv.qm
qt_gl_ES.qm  qt_tr.qm     VirtualBox_gl_ES.qm  VirtualBox_tr.qm
qt_hu.qm     qt_uk.qm     VirtualBox_hu.qm     VirtualBox_uk.qm
qt_id.qm     qt_zh_CN.qm  VirtualBox_id.qm     VirtualBox_zh_CN.qm
qt_it.qm     qt_zh_TW.qm  VirtualBox_it.qm     VirtualBox_zh_TW.qm

```

In order to avoid further problem please advise is there any way getting back the VirtualBox on Ubuntu repo?  If YES please advise how?

Thanks in advance.

Rgds
satimis

---

### Post by CharlesA on 2013-12-17
How did you install virtualbox in the first place?

I've always added their repo to the sources.list file by following the instructions here:
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by satimis on 2013-12-20
> **CharlesA said:**
> How did you install virtualbox in the first place?

I've always added their repo to the sources.list file by following the instructions here:
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)
Hi,

At the beggining I installed VirturalBox on Ubuntu repo when I installed this PC.

VirtualBox repo is on source.list

$ cat /etc/apt/sources.list```

deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) precise main restricted

deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) precise-updates main restricted

deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) precise universe
deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) precise-updates universe

deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) precise-updates multiverse

deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) precise contrib

```

In one occasion when I started VirtualBox a reminder similar to the file attached popup.  I mistakenly thought it coming from Ubuntu and installed it.  Then it comes to present situation.  Now I expect getting back to version on VirtualBox repo.

Rgds
satimis

---

### Post by CharlesA on 2013-12-20
The version of virtualbox in the Ubuntu repos usually lags behind the one from virtualbox.org. If you want the most up-to-date one, use their repo and install it via apt-get.

---

### Post by satimis on 2013-12-20
> **CharlesA said:**
> The version of virtualbox in the Ubuntu repos usually lags behind the one from virtualbox.org. If you want the most up-to-date one, use their repo and install it via apt-get.

$ apt-cache policy virtualbox```

virtualbox:
  Installed: 4.1.12-dfsg-2ubuntu0.5
  Candidate: 4.1.12-dfsg-2ubuntu0.5
  Version table:
 *** 4.1.12-dfsg-2ubuntu0.5 0
        500 http://hk.archive.ubuntu.com/ubuntu/ precise-updates/universe amd64 Packages
        100 /var/lib/dpkg/status
     4.1.12-dfsg-2ubuntu0.2 0
        500 http://security.ubuntu.com/ubuntu/ precise-security/universe amd64 Packages
     4.1.12-dfsg-2 0
        500 http://hk.archive.ubuntu.com/ubuntu/ precise/universe amd64 Packages

```
Is it the up-to-date version?  


I have 2 folders for vituralbox.

ls /usr/share/virtualbox
```

nls                    src                     VBoxSysInfo.sh
rdesktop-vrdp-keymaps  VBoxCreateUSBNode.sh
rdesktop-vrdp.tar.gz   VBoxGuestAdditions.iso

```

and
/home/satimis/.VirtualBox (I suppose this directory was created at the time when I installed the download package)

$ ls /home/satimis/.VirtualBox/```

compreg.dat                                              VBoxSVC.log.2
Oracle_VM_VirtualBox_Extension_Pack-4.2.10.vbox-extpack  VBoxSVC.log.3
Oracle_VM_VirtualBox_Extension_Pack-4.2.12.vbox-extpack  VBoxSVC.log.4
Oracle_VM_VirtualBox_Extension_Pack-4.2.14.vbox-extpack  VBoxSVC.log.5
Oracle_VM_VirtualBox_Extension_Pack-4.2.16.vbox-extpack  VBoxSVC.log.6
Oracle_VM_VirtualBox_Extension_Pack-4.2.18.vbox-extpack  VBoxSVC.log.7
selectorwindow.log                                       VBoxSVC.log.8
selectorwindow.log.1                                     VBoxSVC.log.9
VBoxGuestAdditions_4.1.12.iso                            VirtualBox.xml
VBoxSVC.log                                              VirtualBox.xml-prev
VBoxSVC.log.1                                            xpti.dat
VBoxSVC.log.10

```

How to fix this problem?  I suppose it should be /usr/share/virtualbox

IIRC previsously when I download VirtualBox on their website and installed it.  The folder was /home/satimis/.VirtualBox

Rgds
satimis

---

### Post by CharlesA on 2013-12-20
No. That's the one from the Ubuntu repos. You need to purge that one before installing the one from the virtualbox repos.

VirtualBox stores information in ~/.VirtualBox but the guest additions ISO should be there or in /usr/share.

---

### Post by satimis on 2013-12-20
> **CharlesA said:**
> No. That's the one from the Ubuntu repos. You need to purge that one before installing the one from the virtualbox repos.

VirtualBox stores information in ~/.VirtualBox but the guest additions ISO should be there or in /usr/share.
Thanks

Whether run following commands on terminal?

To remove the running VirtualBox```

$ sudo apt-get purge virtualbox-4.1.12-dfsg-2ubuntu0.5

```

Would the installed VMs be affected?


To install the latest version of VirtualBox on their repo;

1)
To create VirtualBox repo on local PC
```

sudo sh -c 'echo "deb http://download.virtualbox.org/virtualbox/debian $(lsb_release -sc) contrib" >> /etc/apt/sources.list.d/virtualbox.list'

```

2)
To get the key:
```

wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -

```

3)
To update and install lastest Virtualbox:```

sudo apt-get update

```
```

sudo apt-get install virtualbox-4.3

```

Do I need to manually delete following repo on sourcs.list ?```

deb http://download.virtualbox.org/virtualbox/debian precise contrib

```

Rgds
satimis

---

### Post by CharlesA on 2013-12-20
You should be able to remove it via:

```
sudo apt-get purge virtualbox
```

It looks like you already have the virtualbox.org repo in your sources.list, at least according to the output in one of the posts above.

---

### Post by satimis on 2013-12-20
> **CharlesA said:**
> You should be able to remove it via:

```
sudo apt-get purge virtualbox
```

It looks like you already have the virtualbox.org repo in your sources.list, at least according to the output in one of the posts above.
Following repo is on sources.list of this PC
```

deb http://download.virtualbox.org/virtualbox/debian precise contrib

```
Whether just run;
1)
```

sudo apt-get purge virtualbox

```

2)
```

sudo apt-get install virtualbox-4.3

```
to install the latest version of VirturalBox ?

Thanks

satimis

---

### Post by CharlesA on 2013-12-20
Work on removing the current version of virtualbox first. If that purge command doesn't work, post what errors you get.

---

### Post by satimis on 2013-12-20
> **CharlesA said:**
> Work on removing the current version of virtualbox first. If that purge command doesn't work, post what errors you get.

Before removing virtualbox:-

$ ls /usr/share/virtualbox/```

nls  VBox.sh  VBoxSysInfo.sh

```

$ ls /usr/share/virtualbox/nls/```

qt_ar.qm     qt_ja.qm     VirtualBox_ar.qm     VirtualBox_ja.qm
qt_bg.qm     qt_km_KH.qm  VirtualBox_bg.qm     VirtualBox_km_KH.qm
qt_ca.qm     qt_ko.qm     VirtualBox_ca.qm     VirtualBox_ko.qm
qt_ca_VA.qm  qt_lt.qm     VirtualBox_ca_VA.qm  VirtualBox_lt.qm
qt_cs.qm     qt_nl.qm     VirtualBox_cs.qm     VirtualBox_nl.qm
qt_da.qm     qt_pl.qm     VirtualBox_da.qm     VirtualBox_pl.qm
qt_de.qm     qt_pt_BR.qm  VirtualBox_de.qm     VirtualBox_pt_BR.qm
qt_el.qm     qt_pt.qm     VirtualBox_el.qm     VirtualBox_pt.qm
qt_en.qm     qt_ro.qm     VirtualBox_en.qm     VirtualBox_ro.qm
qt_es.qm     qt_ru.qm     VirtualBox_es.qm     VirtualBox_ru.qm
qt_eu.qm     qt_sk.qm     VirtualBox_eu.qm     VirtualBox_sk.qm
qt_fi.qm     qt_sr.qm     VirtualBox_fi.qm     VirtualBox_sr.qm
qt_fr.qm     qt_sv.qm     VirtualBox_fr.qm     VirtualBox_sv.qm
qt_gl_ES.qm  qt_tr.qm     VirtualBox_gl_ES.qm  VirtualBox_tr.qm
qt_hu.qm     qt_uk.qm     VirtualBox_hu.qm     VirtualBox_uk.qm
qt_id.qm     qt_zh_CN.qm  VirtualBox_id.qm     VirtualBox_zh_CN.qm
qt_it.qm     qt_zh_TW.qm  VirtualBox_it.qm     VirtualBox_zh_TW.qm

```

$ ls /home/satimis/.VirtualBox/```

compreg.dat                                              VBoxSVC.log.2
Oracle_VM_VirtualBox_Extension_Pack-4.2.10.vbox-extpack  VBoxSVC.log.3
Oracle_VM_VirtualBox_Extension_Pack-4.2.12.vbox-extpack  VBoxSVC.log.4
Oracle_VM_VirtualBox_Extension_Pack-4.2.14.vbox-extpack  VBoxSVC.log.5
Oracle_VM_VirtualBox_Extension_Pack-4.2.16.vbox-extpack  VBoxSVC.log.6
Oracle_VM_VirtualBox_Extension_Pack-4.2.18.vbox-extpack  VBoxSVC.log.7
selectorwindow.log                                       VBoxSVC.log.8
selectorwindow.log.1                                     VBoxSVC.log.9
VBoxGuestAdditions_4.1.12.iso                            VirtualBox.xml
VBoxSVC.log                                              VirtualBox.xml-prev
VBoxSVC.log.1                                            xpti.dat
VBoxSVC.log.10

```

$ sudo apt-get purge virtualbox```

[sudo] password for satimis: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsdl-ttf2.0-0 linux-headers-3.2.0-38-lowlatency linux-headers-3.2.0-38
  dkms libgsoap1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  virtualbox* virtualbox-dkms* virtualbox-qt*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 68.6 MB disk space will be freed.
Do you want to continue [Y/n]? 
....
....
DKMS: uninstall completed.

------------------------------
Deleting module version: 4.1.12
completely from the DKMS tree.
------------------------------
Done.
Removing virtualbox ...
 * Stopping VirtualBox kernel modules
   ...done.
Purging configuration files for virtualbox ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for shared-mime-info ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot

```


Rebooted PC.

After removing virtualbox:-

$ ls /usr/share/virtualbox/```

ls: cannot access /usr/share/virtualbox/: No such file or directory

```

$ ls /home/satimis/.VirtualBox/```

compreg.dat                                              VBoxSVC.log.2
Oracle_VM_VirtualBox_Extension_Pack-4.2.10.vbox-extpack  VBoxSVC.log.3
Oracle_VM_VirtualBox_Extension_Pack-4.2.12.vbox-extpack  VBoxSVC.log.4
Oracle_VM_VirtualBox_Extension_Pack-4.2.14.vbox-extpack  VBoxSVC.log.5
Oracle_VM_VirtualBox_Extension_Pack-4.2.16.vbox-extpack  VBoxSVC.log.6
Oracle_VM_VirtualBox_Extension_Pack-4.2.18.vbox-extpack  VBoxSVC.log.7
selectorwindow.log                                       VBoxSVC.log.8
selectorwindow.log.1                                     VBoxSVC.log.9
VBoxGuestAdditions_4.1.12.iso                            VirtualBox.xml
VBoxSVC.log                                              VirtualBox.xml-prev
VBoxSVC.log.1                                            xpti.dat
VBoxSVC.log.10

```

The above folder with its contents is still there after removal of VirtualBox

Rgds
satimis

---

### Post by CharlesA on 2013-12-21
That's normal. Just install virtualbox from the instructions on the virtualbox.org site and you will be fine.

---

### Post by satimis on 2013-12-21
> **CharlesA said:**
> That's normal. Just install virtualbox from the instructions on the virtualbox.org site and you will be fine.

On 2.3. Installing on Linux hosts
[https://www.virtualbox.org/manual/ch02.html](https://www.virtualbox.org/manual/ch02.html)

there are several methods installing VirtualBox such as;```

2.3.3.1. Installing VirtualBox from a Debian/Ubuntu package
or
2.3.3.2. Using the alternative installer (VirtualBox.run)
or
2.3.3.3. Performing a manual installation
or
2.3.3.5. Automatic installation of Debian packages
or
2.3.3.6. Automatic installation of .rpm packages
etc

```

If I expect installing the package on repo:```

deb http://download.virtualbox.org/virtualbox/debian precise contrib

```
which method shall I follow?  I suppose the package on above repo is VirtualBox official package, the latest version?  Or I have to downlow the package on VirtualBox website and do manual installation?  Thanks

Rgds
satimis

---

### Post by CharlesA on 2013-12-21
This page:
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

It looks like you already have the repo enabled, so just install virtualbox-4.3.

---

### Post by satimis on 2013-12-21
> **CharlesA said:**
> This page:
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

It looks like you already have the repo enabled, so just install virtualbox-4.3.

Thanks.  I'll try later.

There is a spare SSD HD on this PC running Ubuntu 12.04 (upgrade from 10.04 LTS several times in the past)

Just followed below document to install VirtualBox on their website;

How to install Virtualbox 4.3 on Ubuntu 12.04, Linux Mint 13 and Elementary OS 0.2
[http://linuxg.net/how-to-install-virtualbox-4-3-on-ubuntu-13-04-12-10-12-04-linux-mint-15-14-13-pear-os-8-pear-os-7-and-elementary-os-0-2-via-the-official-virtualbox-repository/](http://linuxg.net/how-to-install-virtualbox-4-3-on-ubuntu-13-04-12-10-12-04-linux-mint-15-14-13-pear-os-8-pear-os-7-and-elementary-os-0-2-via-the-official-virtualbox-repository/)

running;```

$ wget -q -O - http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc | sudo apt-key add -
$ sudo sh -c 'echo "deb http://download.virtualbox.org/virtualbox/debian precise non-free contrib" >> /etc/apt/sources.list.d/virtualbox.org.list'
$ sudo apt-get update
$ sudo apt-get install virtualbox-4.3

```
(no repo on sources.list)

It worked.  

Folder
/usr/share/virtualbox

No
/home/satimis/.VirtualBox

I'll come back later.

Rgds
satimis

---

### Post by CharlesA on 2013-12-21
/home/satimis/.VirtualBox gets created when you run virtualbox the first time.

---

### Post by satimis on 2013-12-23
Performed following tests:-

1)
Installation of VirtualBox on 120G SSD completed with following VMs created;
Fedora 20 (GuestAddtion couldn't installed)
Ubuntu 12.04.3 (GuestAddition installed)
Debian 7.3 (GuestAddition installed)
LinuxMint 16 (GuestAddition installed

$ ls /usr/share/virtualbox/```

nls                    src                     VBoxSysInfo.sh
rdesktop-vrdp-keymaps  VBoxCreateUSBNode.sh
rdesktop-vrdp.tar.gz   VBoxGuestAdditions.iso

```

$ ls -al /home/satimis/```

total 312
drwxr-xr-x 42 satimis satimis  4096 Dec 23 11:39 .
drwxr-xr-x  3 root    root     4096 Jan  3  2013 ..
drwx------  3 satimis satimis  4096 Jan  3  2013 .adobe
-rw-------  1 satimis satimis 24499 Dec 23 00:16 .bash_history
-rw-r--r--  1 satimis satimis   220 Jan  3  2013 .bash_logout
-rw-r--r--  1 satimis satimis  3486 Jan  3  2013 .bashrc
drwxrwxr-x  3 satimis satimis  4096 Jan 25  2013 blackbird
drwxrwxr-x  3 satimis satimis  4096 Dec 21 23:08 .bluefish
drwxrwxr-x  2 satimis satimis  4096 Dec 23 11:37 .byobu
drwx------ 24 satimis satimis  4096 Dec 21 17:03 .cache
drwxrwxr-x  3 satimis satimis  4096 Jan  3  2013 .compiz-1
drwx------ 25 satimis satimis  4096 Dec 21 23:52 .config
drwx------  3 satimis satimis  4096 Jan  3  2013 .dbus
drwxr-xr-x  2 satimis satimis  4096 Jan  3  2013 Desktop
-rw-r--r--  1 satimis satimis    26 Dec 23 10:36 .dmrc
drwxr-xr-x  2 satimis satimis  4096 Dec 21 23:06 Documents
drwxr-xr-x  2 satimis satimis  4096 Dec 23 00:08 Downloads
drwxr-xr-x  2 satimis satimis  4096 Jan 23  2013 dwhelper
-rw-r--r--  1 satimis satimis  8445 Jan  3  2013 examples.desktop
drwxr-xr-x  2 satimis satimis  4096 Dec 21 16:31 .fontconfig
drwx------  2 satimis satimis  4096 Jan  7  2013 .freerdp
drwx------  4 satimis satimis  4096 Dec 23 10:36 .gconf
-rw-r-----  1 satimis satimis     0 Dec 22 23:59 .gksu.lock
drwx------  4 satimis satimis  4096 Jan  3  2013 .gnome2
drwx------  2 satimis satimis  4096 Jan 16  2013 .gnupg
-rw-------  1 satimis satimis     0 Jan  3  2013 .goutputstream-620BQW
-rw-------  1 satimis satimis    55 Jan 10  2013 .goutputstream-JAVLQW
-rw-------  1 satimis satimis    55 Jan 20  2013 .goutputstream-MMA5QW
-rw-------  1 satimis satimis    55 Jan  9  2013 .goutputstream-N585PW
drwxrwxr-x  2 satimis satimis  4096 Dec 23 11:10 .gstreamer-0.10
-rw-rw-r--  1 satimis satimis   190 Dec 23 10:36 .gtk-bookmarks
dr-x------  2 satimis satimis     0 Dec 23 10:36 .gvfs
-rw-------  1 satimis satimis 30706 Dec 23 10:36 .ICEauthority
drwxr-xr-x  3 satimis satimis  4096 Jan  3  2013 .local
drwx------  3 satimis satimis  4096 Jan  3  2013 .macromedia
drwx------  3 satimis satimis  4096 Jan  3  2013 .mission-control
drwx------  4 satimis satimis  4096 Jan  3  2013 .mozilla
drwxr-xr-x  2 satimis satimis  4096 Jan  3  2013 Music
-rw-------  1 satimis satimis   240 Jan 23  2013 .mysql_history
-rw-------  1 root    root       59 Jan 24  2013 .nano_history
drwxrwxr-x  8 satimis satimis  4096 Jan 21  2013 Old_n_New_Documents_20121228
drwxr-xr-x  2 satimis satimis  4096 Dec 21 23:08 Pictures
drwx------  3 satimis satimis  4096 Mar 11  2013 .pki
-rw-r--r--  1 satimis satimis   675 Jan  3  2013 .profile
drwxr-xr-x  2 satimis satimis  4096 Jan  3  2013 Public
drwx------  2 satimis satimis  4096 Dec 23 10:36 .pulse
-rw-------  1 satimis satimis   256 Jan  3  2013 .pulse-cookie
drwx------  2 satimis satimis  4096 Jan  8  2013 .remmina
-rw-rw-r--  1 satimis satimis     0 Jan  4  2013 .screenrc
drwx------  2 satimis satimis  4096 Jan 12  2013 .ssh
drwxr-xr-x  2 satimis satimis  4096 Jan  3  2013 Templates
drwxrwxr-x  4 satimis satimis  4096 Mar 11  2013 Temp_Storage
drwx------  4 satimis satimis  4096 Jan  3  2013 .thumbnails
drwx------  4 satimis satimis  4096 Jan 23  2013 .thunderbird
drwxrwxr-x  2 satimis satimis  4096 Jan 26  2013 Transfer_Directory
drwxrwxr-x  3 satimis satimis  4096 Nov 11 15:19 Ubuntu One
drwxr-xr-x  2 satimis satimis  4096 Jan  3  2013 Videos
-rw-rw-r--  1 satimis satimis  5492 Dec 22 00:02 virtualbox_install_on_ssd120g_20131221.txt
drwxrwxr-x  6 satimis satimis  4096 Dec 23 00:06 VirtualBox VMs
drwxrwxr-x  6 satimis satimis  4096 Jan 14  2013 Web_Documents_20130114
-rw-------  1 satimis satimis   109 Dec 23 10:36 .Xauthority
-rw-------  1 satimis satimis  5260 Dec 23 11:39 .xsession-errors
-rw-------  1 satimis satimis  5167 Dec 23 00:16 .xsession-errors.old

```

Couldn't find /home/satimis/.VirtualBox folder

$ ls /home/satimis/VirtualBox\ VMs/```

deb730dkssd00  fedora20dkssd00  mint16dkssd00  ub12043dkssd00

```
I think those are VM folders?  Snapshot of VM?

$ ls /home/satimis/VirtualBox\ VMs/ub12043dkssd00/```

Logs  ub12043dkssd00.vbox  ub12043dkssd00.vbox-prev  ub12043dkssd00

```
ub12043dkssd00.vbox - VM images ?


2)
Installation of VirtualBox on 2TB Hard drive, same PC.

Before installing VirtualBox
============================

$ sudo find / -name virtualbox -type d```

/usr/lib/virtualbox

```

$ ls /usr/lib/virtualbox/```

ExtensionPacks

```

$ ls /usr/lib/virtualbox/ExtensionPacks/```

Oracle_VM_VirtualBox_Extension_Pack

```

$ ls /usr/lib/virtualbox/ExtensionPacks/Oracle_VM_VirtualBox_Extension_Pack/```

darwin.amd64          ExtPack-license.txt  linux.amd64    solaris.x86
darwin.x86            ExtPack.manifest     linux.x86      win.amd64
ExtPack-license.html  ExtPack.signature    PXE-Intel.rom  win.x86
ExtPack-license.rtf   ExtPack.xml          solaris.amd64

```

$ sudo find / -name *VirtualBox* -type d```

/root/.VirtualBox
/usr/lib/virtualbox/ExtensionPacks/Oracle_VM_VirtualBox_Extension_Pack
/home/satimis/.VirtualBox
/data/home/satimis/.VirtualBox

```

# ls /root/.VirtualBox/```

compreg.dat  VBoxSVC.log  xpti.dat

```
What are those files for ?

# ls /home/satimis/.VirtualBox/```

compreg.dat                                              VBoxSVC.log.2
Oracle_VM_VirtualBox_Extension_Pack-4.2.10.vbox-extpack  VBoxSVC.log.3
Oracle_VM_VirtualBox_Extension_Pack-4.2.12.vbox-extpack  VBoxSVC.log.4
Oracle_VM_VirtualBox_Extension_Pack-4.2.14.vbox-extpack  VBoxSVC.log.5
Oracle_VM_VirtualBox_Extension_Pack-4.2.16.vbox-extpack  VBoxSVC.log.6
Oracle_VM_VirtualBox_Extension_Pack-4.2.18.vbox-extpack  VBoxSVC.log.7
selectorwindow.log                                       VBoxSVC.log.8
selectorwindow.log.1                                     VBoxSVC.log.9
VBoxGuestAdditions_4.1.12.iso                            VirtualBox.xml
VBoxSVC.log                                              VirtualBox.xml-prev
VBoxSVC.log.1                                            xpti.dat
VBoxSVC.log.10

```

# ls /data/home/satimis/.VirtualBox/```

compreg.dat                                              VBoxSVC.log.3
Oracle_VM_VirtualBox_Extension_Pack-4.2.10.vbox-extpack  VBoxSVC.log.4
Oracle_VM_VirtualBox_Extension_Pack-4.2.12.vbox-extpack  VBoxSVC.log.5
Oracle_VM_VirtualBox_Extension_Pack-4.2.14.vbox-extpack  VBoxSVC.log.6
Oracle_VM_VirtualBox_Extension_Pack-4.2.16.vbox-extpack  VBoxSVC.log.7
selectorwindow.log                                       VBoxSVC.log.8
selectorwindow.log.1                                     VBoxSVC.log.9
VBoxSVC.log                                              VirtualBox.xml
VBoxSVC.log.1                                            VirtualBox.xml-prev
VBoxSVC.log.10                                           xpti.dat
VBoxSVC.log.2

```

Where are the VM images (.vdi) stored?

Ran:-
$ sudo apt-get update && sudo apt-get upgrade

$ sudo apt-get install virtualbox-4.3```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libgsoap1
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  virtualbox-4.3
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 68.7 MB of archives.
After this operation, 154 MB of additional disk space will be used.
Get:1 http://download.virtualbox.org/virtualbox/debian/ precise/contrib virtualbox-4.3 amd64 4.3.6-91406~Ubuntu~precise [68.7 MB]
Fetched 68.7 MB in 3min 39s (313 kB/s)                                         
Preconfiguring packages ...
Selecting previously unselected package virtualbox-4.3.
(Reading database ... 
dpkg: warning: files list file for package `libdca0' missing, assuming package has no files currently installed.
(Reading database ... 516913 files and directories currently installed.)
Unpacking virtualbox-4.3 (from .../virtualbox-4.3_4.3.6-91406~Ubuntu~precise_amd64.deb) ...
Fetched 68.7 MB in 3min 39s (313 kB/s)                                         
Preconfiguring packages ...
Selecting previously unselected package virtualbox-4.3.
(Reading database ... 
dpkg: warning: files list file for package `libdca0' missing, assuming package has no files currently installed.
(Reading database ... 516913 files and directories currently installed.)
Unpacking virtualbox-4.3 (from .../virtualbox-4.3_4.3.6-91406~Ubuntu~precise_amd64.deb) ...
Fetched 68.7 MB in 3min 39s (313 kB/s)                                         
Preconfiguring packages ...
Selecting previously unselected package virtualbox-4.3.
(Reading database ... 
dpkg: warning: files list file for package `libdca0' missing, assuming package h
as no files currently installed.
(Reading database ... 516913 files and directories currently installed.)
Unpacking virtualbox-4.3 (from .../virtualbox-4.3_4.3.6-91406~Ubuntu~precise_amd
64.deb) ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for shared-mime-info ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Setting up virtualbox-4.3 (4.3.6-91406~Ubuntu~precise) ...
Installing new version of config file /etc/init.d/vboxdrv ...
Installing new version of config file /etc/init.d/vboxautostart-service ...
Installing new version of config file /etc/init.d/vboxweb-service ...
Installing new version of config file /etc/init.d/vboxballoonctrl-service ...
Adding group `vboxusers' (GID 125) ...
Done.
Stopping VirtualBox kernel modules ...done.
Uninstalling old VirtualBox DKMS kernel modulesError! Could not locate dkms.conf
 file.
File:  does not exist.
 ...done.
Trying to register the VirtualBox kernel modules using DKMS ...done.
Starting VirtualBox kernel modules ...done.

```


On terminal ran:-

$ VirtualBox```

Error opening file for reading: Permission denied
Qt WARNING: void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "S&tart" under id 16 
Qt WARNING: void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "&Pause" under id 17 
Qt WARNING: void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "&Reset" under id 18 
Qt WARNING: void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "D&iscard saved state..." under id 24 
Qt WARNING: void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "Re&fresh..." under id 25 
Qt WARNING: void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "Show in File Manager" under id 27 
Qt WARNING: void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "Create Shortcut on Desktop" under id 28 

```


Warning:
You have an old version (4.1.28) of the Oracle VM VirtualBox Extension Pack installed.
Do you wish to download latest one from the Internet?
(see attached file)

-> Download


After installing VirtualBox
$ sudo find / -name virtualbox -type d```

[sudo] password for satimis: 
/usr/lib/virtualbox
/usr/share/virtualbox

```

$ ls /usr/share/virtualbox/```

nls                    src                     VBoxSysInfo.sh
rdesktop-vrdp-keymaps  VBoxCreateUSBNode.sh
rdesktop-vrdp.tar.gz   VBoxGuestAdditions.iso

```

$ sudo find / -name *VirtualBox* -type d```

/root/.VirtualBox
/usr/lib/virtualbox/ExtensionPacks/Oracle_VM_VirtualBox_Extension_Pack
/home/satimis/.VirtualBox

```

$ ls /home/satimis/.VirtualBox/```

compreg.dat                                              VBoxSVC.log.10
Oracle_VM_VirtualBox_Extension_Pack-4.2.10.vbox-extpack  VBoxSVC.log.2
Oracle_VM_VirtualBox_Extension_Pack-4.2.12.vbox-extpack  VBoxSVC.log.3
Oracle_VM_VirtualBox_Extension_Pack-4.2.14.vbox-extpack  VBoxSVC.log.4
Oracle_VM_VirtualBox_Extension_Pack-4.2.16.vbox-extpack  VBoxSVC.log.5
Oracle_VM_VirtualBox_Extension_Pack-4.2.18.vbox-extpack  VBoxSVC.log.6
Oracle_VM_VirtualBox_Extension_Pack-4.3.6.vbox-extpack   VBoxSVC.log.7
selectorwindow.log                                       VBoxSVC.log.8
selectorwindow.log.1                                     VBoxSVC.log.9
VBoxGuestAdditions_4.1.12.iso                            VirtualBox.xml
vbox-ssl-cacertificate.crt                               VirtualBox.xml-prev
VBoxSVC.log                                              xpti.dat
VBoxSVC.log.1

```

Where are the VM images (.vdi) stored?

/root/.VirtualBox is still there
# ls /root/.VirtualBox/```

compreg.dat  VBoxSVC.log  xpti.dat

```

What are those files for?

Rgds
satimis

---

### Post by CharlesA on 2013-12-23
The only folders you need to worry about is the one located in ~/.VirtualBox and ~/VirtualBox VMs. The VDIs should be stored there, but as I haven't used VirtualBox for a long time now, you might get better results by asking over at [http://forums.virtualbox.org/](http://forums.virtualbox.org/)

---

### Post by satimis on 2013-12-23
> **CharlesA said:**
> The only folders you need to worry about is the one located in ~/.VirtualBox and ~/VirtualBox VMs. The VDIs should be stored there, but as I haven't used VirtualBox for a long time now, you might get better results by asking over at [http://forums.virtualbox.org/](http://forums.virtualbox.org/)

Thanks

Rgds
satimis

---

