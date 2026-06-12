---
title: "virtualbox install error ubuntu 18.04.1"
date: 2019-01-03
forum: Virtualisation
---

### Post by peteraj2 on 2019-01-03
Cannot install virtualbox in ubuntu 18.04.0, get the following error:
E: py3 compile:183: cannot create directory    /usr/share/hplip/ui5/--pycache--
On checking I have     hplip/ui4/ 

terminal output, first part to error:



peteraj@peteraj-System-Product-Name:~$ sudo apt-get install virtualbox
[sudo] password for peteraj: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
virtualbox is already the newest version (5.2.18-dfsg-2~ubuntu18.04.1).
virtualbox set to manually installed.
The following packages were automatically installed and are no longer required:
  libcompfaceg1 libgmime-2.6-0 libgtkspell0 libpisock9 libusb-0.1-4
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 5 not to upgrade.
26 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up python3 (3.6.7-1~18.04) ...
running python rtupdate hooks for python3.6...
E: py3compile:183: cannot create directory /usr/share/hplip/ui5/__pycache__: FileNotFoundError(2, 'No such file or directory')
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/aboutdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/aboutdialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/aligndialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/aligndialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/cleandialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/cleandialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/colorcaldialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/colorcaldialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/devicesetupdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/devicesetupdialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/deviceuricombobox.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/devmgr5.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/devmgr5_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/devmgr_ext.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/fabgrouptable.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/fabnametable.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/fabwindow.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/fabwindow_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/faxsetupdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/faxsetupdialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/filetable.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/firmwaredialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/firmwaredialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/infodialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/infodialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/linefeedcaldialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/linefeedcaldialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/loadpapergroupbox.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/makecopiesdialog.py'


Can post the rest if needed
Peter

---

### Post by peteraj2 on 2019-01-04
All fixed, updated hplip & was able to install virtualbox.

---

