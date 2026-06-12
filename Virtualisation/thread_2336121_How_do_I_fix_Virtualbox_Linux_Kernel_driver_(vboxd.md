---
title: "How do I fix Virtualbox Linux Kernel driver (vboxdrv) problem?"
date: 2016-09-04
forum: Virtualisation
---

### Post by AbleTassie on 2016-09-04
After I open Oracle VM Virtualbox Manager, when I try to start a new Windows machine, I get the following error message (see attached screenshot):

[I]The Virtualbox Linus Kernel Driver (vboxdrv) is either not loaded or there is a permission problem with dev/vboxdrv. Please reinstall the kernel module by executing:

[COLOR=#0000cd]'/etc/init.d/vboxdrv setup'
[/COLOR][COLOR=#000000]
as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.
[/COLOR][/I][COLOR=#000000]
Can somebody tell me how to do this simply?

Thank you,

A.
[/COLOR]

---

### Post by ajgreeny on 2016-09-05
Install dkms in your host with ```
sudo apt-get install dkms
```
Run command ```
sudo /etc/init.d/vboxdrv setup
```
Make sure you have installed the correct version of the [Virtualbox Extension Pack]("https://www.virtualbox.org/wiki/Downloads")

---

### Post by AbleTassie on 2016-09-05
Thank you ajgreeny,

The version of Virtualbox that I have is Virtualbox 5.0.2 r102096. The link in your reply takes me to Virtualbox 5.1.4 as well the the Virtualbox Extension Pack for 5.1.4 as well. Should I uninstall Virtualbox 5.0.2 r102096 and then install Virtualbox 5.1.4? Would such an updating of Virtualbox likely cure the problem? Or should I run the terminal commands in your post after installing the updated (5.1.4) version of Virtualbox?

Thanks again,

A.

---

### Post by &amp;KyT$0P# on 2016-09-05
What version of Ubuntu is your host on?

VirtualBox 5.0.2 runs nicely on 14.04, I'm running it right now in fact.  If your host is 16.04 you'll need newer VirtualBox.
Try the [latest 5.0]("https://www.virtualbox.org/wiki/Download_Old_Builds_5_0") first, only if that can't or don't work then try 5.1.x as people have reported all kinds of weird issues with 5.1.x.

Whatever version you end up running, make sure Extension Pack is of exactly the same version to ensure compatibility and stability.

---

### Post by AbleTassie on 2016-09-06
Hi halogen,

I am running Lubuntu -Distribution Ubuntu 14.04.5 LTS. So it sounds like I probably already have the correct Virtualbox extension pack (although I do not know how to check this specifically). It sounds like I should probably just run the terminal commands in ajgreeny's post, correct?

Able

---

### Post by howefield on 2016-09-06
> **AbleTassie said:**
> So it sounds like I probably already have the correct Virtualbox extension pack (although I do not know how to check this specifically).

```
apt-cache policy virtualbox-ext-pack
```

might do it or Virtualbox > Preference > Extensions will tell you.

> It sounds like I should probably just run the terminal commands in ajgreeny's post, correct?

Indeed :)

---

### Post by AbleTassie on 2016-09-07
> **halogen2 said:**
> 

Whatever version you end up running, make sure Extension Pack is of exactly the same version to ensure compatibility and stability.

The Virtualbox Extension Pack is 5.0.4r102546; and as I said above,  Virtualbox is 5.0.2 r102096. So there is an apparent difference between  Virtualbox and the Extension Pack. Should I change one or the other?

Thank you,

A.

---

### Post by ajgreeny on 2016-09-07
Yes, you should download the extension pack of that version direct from [http://download.virtualbox.org/virtualbox/5.0.2/Oracle_VM_VirtualBox_Extension_Pack-5.0.2-102096.vbox-extpack](http://download.virtualbox.org/virtualbox/5.0.2/Oracle_VM_VirtualBox_Extension_Pack-5.0.2-102096.vbox-extpack) and double click to install it; it should automatically be installed into your VBox.

I am running VBox version 5.0.26 and the extension pack of the same version also in 14.04 and it is running perfectly, so you could consider upgrading to that version but I would not personally recommend going to 5.1.## version at the moment; it seems to have a number of difficulties for several users and certainly caused me a load of problems related to the extensions pack.

---

### Post by AbleTassie on 2016-09-08
I downloaded Oracle_VM_VirtualBox_Extension_Pack-5.0.2-102096 and tried to install it by double clicking on it. That did not seem to work, because Virtualbox Preferences still showed the same Virtualbox Extension Pack as 5.0.4r102546 . So I opened Virtualbox, went to File>Preferences>Extensions and added the extension pack using the drop down menu. After that, the Extension Pack in Preferences was listed as 5.0.2-102096.

Then I attempted to execute the Terminal Commands in ajgreeny's post. **But this apparently failed to work.** I still get the same error message when trying to open a new machine in VirtualBox And I got the following, which seems to indicate failure:

   ```
rob@RobNotebook:~$ sudo apt-get install dkms 
 [sudo] password for rob:  
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 dkms is already the newest version. 
 The following packages were automatically installed and are no longer required: 
   abiword-common apturl apturl-common encfs evolution-data-server-common 
   gecko-mediaplayer gnome-mplayer kde-l10n-engb language-selector-gnome 
   libabiword-3.0 libappindicator1 libboost-serialization1.54.0 libcamel-1.2-45 
   libchamplain-0.12-0 libchamplain-gtk-0.12-0 libcryptui0a libdiscid0 
   libebook-contacts-1.2-0 libedataserver-1.2-18 libfs6 libgda-5.0-4 
   libgda-5.0-common libgmlib1 libgmtk1 libgmtk1-data libical1 libllvm3.6 
   libmusicbrainz3-6 libntdb1 libots0 librlog5 libwv-1.2-4 lubuntu-core 
   python-ntdb seahorse seahorse-daemon x11-apps x11-session-utils 
   x11-xfs-utils xinit xorg 
 Use 'apt-get autoremove' to remove them. 
 0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded. 
 rob@RobNotebook:~$ sudo /etc/init.d/vboxdrv setup 
 Stopping VirtualBox kernel modules ...done. 
 Uninstalling old VirtualBox DKMS kernel modulesrmdir: failed to remove &#8216;&#8217;: No such file or directory 
 rmdir: failed to remove &#8216;&#8217;: No such file or directory 
 rmdir: failed to remove &#8216;&#8217;: No such file or directory 
 rmdir: failed to remove &#8216;&#8217;: No such file or directory 
 rmdir: failed to remove &#8216;&#8217;: No such file or directory 
 rmdir: failed to remove &#8216;&#8217;: No such file or directory 
 rmdir: failed to remove &#8216;&#8217;: No such file or directory 
 rmdir: failed to remove &#8216;&#8217;: No such file or directory 
 rmdir: failed to remove &#8216;&#8217;: No such file or directory 
 rmdir: failed to remove &#8216;&#8217;: No such file or directory 
 rmdir: failed to remove &#8216;&#8217;: No such file or directory 
 rmdir: failed to remove &#8216;&#8217;: No such file or directory 
 rmdir: failed to remove &#8216;&#8217;: No such file or directory 
 rmdir: failed to remove &#8216;&#8217;: No such file or directory 
 rmdir: failed to remove &#8216;&#8217;: No such file or directory 
 rmdir: failed to remove &#8216;&#8217;: No such file or directory 
 rmdir: failed to remove &#8216;&#8217;: No such file or directory 
 rmdir: failed to remove &#8216;&#8217;: No such file or directory 
 Error! There are no instances of module: vboxhost 
 5.0.2 located in the DKMS tree. 
 Error! There are no instances of module: vboxhost 
 5.0.2 located in the DKMS tree. 
 Error! There are no instances of module: vboxhost 
 5.0.2 located in the DKMS tree. 
 Error! There are no instances of module: vboxhost 
 5.0.2 located in the DKMS tree. 
 Error! There are no instances of module: vboxhost 
 5.0.2 located in the DKMS tree. 
 Error! There are no instances of module: vboxhost 
 5.0.2 located in the DKMS tree. 
 Error! There are no instances of module: vboxhost 
 5.0.2 located in the DKMS tree. 
 Error! There are no instances of module: vboxhost 
 5.0.2 located in the DKMS tree. 
 Error! There are no instances of module: vboxhost 
 5.0.2 located in the DKMS tree. 
 Error! There are no instances of module: vboxhost 
 5.0.2 located in the DKMS tree. 
 Error! There are no instances of module: vboxhost 
 5.0.2 located in the DKMS tree. 
 Error! There are no instances of module: vboxhost 
 5.0.2 located in the DKMS tree. 
 Error! There are no instances of module: vboxhost 
 5.0.2 located in the DKMS tree. 
 Error! There are no instances of module: vboxhost 
 5.0.2 located in the DKMS tree. 
 Error! There are no instances of module: vboxhost 
 5.0.2 located in the DKMS tree. 
  ...done. 
 Trying to register the VirtualBox kernel modules using DKMScp: cannot stat &#8216;/var/lib/dkms/vboxhost/5.0.2/source/&#8217;: No such file or directory 
 /usr/sbin/dkms: line 1183: cd: /var/lib/dkms/vboxhost/5.0.2/build: No such file or directory 
 ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/virtualbox-5.0.0.crash' 
 Error! Bad return status for module build on kernel: 4.4.0-36-generic (x86_64) 
 Consult /var/lib/dkms/vboxhost/5.0.2/build/make.log for more information. 
  ...failed! 
   (Failed, trying without DKMS) 
 Recompiling VirtualBox kernel modules ...failed! 
   (Look at /var/log/vbox-install.log to find out what went wrong) 
 rob@RobNotebook:~$
```

---

### Post by &amp;KyT$0P# on 2016-09-08
> **AbleTassie said:**
>    (Look at /var/log/vbox-install.log to find out what went wrong) 
Well? ;)

That information would help, but it maybe won't be the whole story -
> The following packages were automatically installed and are no longer required:
abiword-common apturl apturl-common encfs evolution-data-server-common
gecko-mediaplayer gnome-mplayer kde-l10n-engb language-selector-gnome
libabiword-3.0 libappindicator1 libboost-serialization1.54.0 libcamel-1.2-45
libchamplain-0.12-0 libchamplain-gtk-0.12-0 libcryptui0a libdiscid0
libebook-contacts-1.2-0 libedataserver-1.2-18 libfs6 libgda-5.0-4
libgda-5.0-common libgmlib1 libgmtk1 libgmtk1-data libical1 libllvm3.6
libmusicbrainz3-6 libntdb1 libots0 librlog5 libwv-1.2-4 [COLOR="#FF0000"]lubuntu-core[/COLOR]
python-ntdb seahorse seahorse-daemon [B][COLOR="#FF0000"]x11-apps x11-session-utils
x11-xfs-utils xinit xorg[/COLOR][/B]
Use 'apt-get autoremove' to remove them. 
Why are those packages I highlighted in red seen by apt as auto-removable?
lubuntu-core is a meta-package which does nothing by itself, but the others are **critical** to the GUI and something "manually-installed" should depend on them.

(Manually installing those packages would be only a band-aid, not a real fix for that issue.  So best not to do that, at least not without hearing from someone better versed in this than me.)

---

### Post by ajgreeny on 2016-09-08
Have you installed the Guest additions .iso file into your VM then running the VboxLinux.run file?

In your running VM go to the **Devices -> Insert Guest Additions CD image** which should insert that iso file for you, then open a terminal and run command ```
sudo /media/<*user*>/VBOXADDITIONS_5.0.2-102096/VBoxLinuxAdditions.run
```using your own username of course where I show <*user*>.

---

### Post by &amp;KyT$0P# on 2016-09-08
> **ajgreeny said:**
> Have you installed the Guest additions .iso file into your VM then running the VboxLinux.run file?

In your running VM g
I would imagine this to be currently quite difficult given that their guest is Windows and right now they can't start any VMs at all.

:)

---

### Post by AbleTassie on 2016-09-09
> **halogen2 said:**
> Well? ;)

That information would help, but it maybe won't be the whole story -

Why are those packages I highlighted in red seen by apt as auto-removable?
lubuntu-core is a meta-package which does nothing by itself, but the others are **critical** to the GUI and something "manually-installed" should depend on them.

(Manually installing those packages would be only a band-aid, not a real fix for that issue.  So best not to do that, at least not without hearing from someone better versed in this than me.)

Hello halogen, thanks for your response.

The vbox-install.log is below under my name. It is pretty long.

ajgreeny, thanks for your response, but I do not see how to do what you suggest given that I cannot start a virtual machine at all.

I am wondering if my problem could have been due to an installation of some kind. For example, I installed (or attempted installation) of Adobe-flashplayer, which was not installed from the Lubuntu software center, but from another site. I wanted to watch the Olympic Gold medal soccer/football game, but was unsuccessful. I am not sure how to uninstall Adobe-flashplayer.

Able

**vbox-install.log:**


```
Uninstalling modules from DKMS
  removing old DKMS module vboxhost version  5.0.2

-------- Uninstall Beginning --------
Module:  vboxhost
Version: 5.0.2
Kernel:  3.19.0-33-generic (x86_64)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod.........

DKMS: uninstall completed.

-------- Uninstall Beginning --------
Module:  vboxhost
Version: 5.0.2
Kernel:  3.19.0-37-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-37-generic/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-37-generic/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-37-generic/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-37-generic/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod...........

DKMS: uninstall completed.

-------- Uninstall Beginning --------
Module:  vboxhost
Version: 5.0.2
Kernel:  3.19.0-41-generic (x86_64)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod...........

DKMS: uninstall completed.

-------- Uninstall Beginning --------
Module:  vboxhost
Version: 5.0.2
Kernel:  3.19.0-42-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-42-generic/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-42-generic/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-42-generic/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-42-generic/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod............

DKMS: uninstall completed.

-------- Uninstall Beginning --------
Module:  vboxhost
Version: 5.0.2
Kernel:  3.19.0-43-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-43-generic/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-43-generic/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-43-generic/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-43-generic/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod............

DKMS: uninstall completed.

-------- Uninstall Beginning --------
Module:  vboxhost
Version: 5.0.2
Kernel:  3.19.0-47-generic (x86_64)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod...........

DKMS: uninstall completed.

-------- Uninstall Beginning --------
Module:  vboxhost
Version: 5.0.2
Kernel:  3.19.0-49-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-49-generic/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-49-generic/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-49-generic/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-49-generic/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod............(bad exit status: 1)

DKMS: uninstall completed.

-------- Uninstall Beginning --------
Module:  vboxhost
Version: 5.0.2
Kernel:  3.19.0-51-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-51-generic/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-51-generic/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-51-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-51-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod............(bad exit status: 1)

DKMS: uninstall completed.

-------- Uninstall Beginning --------
Module:  vboxhost
Version: 5.0.2
Kernel:  3.19.0-56-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-56-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-56-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-56-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-56-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod...........

DKMS: uninstall completed.

-------- Uninstall Beginning --------
Module:  vboxhost
Version: 5.0.2
Kernel:  3.19.0-58-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-58-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-58-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-58-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-58-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod..........

DKMS: uninstall completed.

-------- Uninstall Beginning --------
Module:  vboxhost
Version: 5.0.2
Kernel:  3.19.0-59-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-59-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-59-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-59-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-59-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod............

DKMS: uninstall completed.

-------- Uninstall Beginning --------
Module:  vboxhost
Version: 5.0.2
Kernel:  3.19.0-61-generic (x86_64)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod...........(bad exit status: 1)

DKMS: uninstall completed.

-------- Uninstall Beginning --------
Module:  vboxhost
Version: 5.0.2
Kernel:  3.19.0-64-generic (x86_64)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod...........(bad exit status: 1)

DKMS: uninstall completed.

-------- Uninstall Beginning --------
Module:  vboxhost
Version: 5.0.2
Kernel:  3.19.0-65-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-65-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-65-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-65-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-65-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod...........(bad exit status: 1)

DKMS: uninstall completed.

-------- Uninstall Beginning --------
Module:  vboxhost
Version: 5.0.2
Kernel:  3.19.0-66-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-66-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-66-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-66-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-66-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod.................(bad exit status: 1)

DKMS: uninstall completed.

-------- Uninstall Beginning --------
Module:  vboxhost
Version: 5.0.2
Kernel:  3.19.0-68-generic (x86_64)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod...........(bad exit status: 1)

DKMS: uninstall completed.

------------------------------
Deleting module version: 5.0.2
completely from the DKMS tree.
------------------------------
Done.
  removing old DKMS module vboxhost version  5.0.2
  removing old DKMS module vboxhost version  5.0.2
  removing old DKMS module vboxhost version  5.0.2
  removing old DKMS module vboxhost version  5.0.2
  removing old DKMS module vboxhost version  5.0.2
  removing old DKMS module vboxhost version  5.0.2
  removing old DKMS module vboxhost version  5.0.2
  removing old DKMS module vboxhost version  5.0.2
  removing old DKMS module vboxhost version  5.0.2
  removing old DKMS module vboxhost version  5.0.2
  removing old DKMS module vboxhost version  5.0.2
  removing old DKMS module vboxhost version  5.0.2
  removing old DKMS module vboxhost version  5.0.2
  removing old DKMS module vboxhost version  5.0.2
  removing old DKMS module vboxhost version  5.0.2
```

---

### Post by &amp;KyT$0P# on 2016-09-09
This is making no sense.  You somehow have an obsolete HWE stack installed on your system but the "normal" X Windows System for trusty... and you further have way more installed kernels than normal.

If you don't have a specific reason for running the HWE stack, try installing the 14.04.1 kernel (which is what I'm running).  It's still supported unlike your current running kernel.
I think you should just be able to install it without affecting your current setup, but in case there's more to it than that, **back up your system before proceeding**.

This command should do the trick, but pay very careful attention to what it wants to do.  It should NOT want to remove anything.
```
sudo apt-get install linux-firmware linux-generic linux-headers-generic linux-image-generic linux-libc-dev
```
Then, reboot and select the 3.13 kernel in the GRUB menu.

I don't know if that'd be enough on its own for VirtualBox to work, or if you'll need to re-run the commands ajgreeny suggested earlier while running under the 3.13 kernel.

---

### Post by AbleTassie on 2016-09-09
> **halogen2 said:**
> This is making no sense.  You somehow have an obsolete HWE stack installed on your system but the "normal" X Windows System for trusty... and you further have way more installed kernels than normal.

If you don't have a specific reason for running the HWE stack, try installing the 14.04.1 kernel (which is what I'm running).  It's still supported unlike your current running kernel.
I think you should just be able to install it without affecting your current setup, but in case there's more to it than that, **back up your system before proceeding**.

This command should do the trick, but pay very careful attention to what it wants to do.  It should NOT want to remove anything.
```
sudo apt-get install linux-firmware linux-generic linux-headers-generic linux-image-generic linux-libc-dev
```
Then, reboot and select the 3.13 kernel in the GRUB menu.

I don't know if that'd be enough on its own for VirtualBox to work, or if you'll need to re-run the commands ajgreeny suggested earlier while running under the 3.13 kernel.

OK halogen, thank you. It sounds like it is a pretty fundamental problem if it involves kernels. It's getting late here and I'll see if others concur with your advice. I'll probably go further with this tomorrow.

A.[B]

Does anybody else have anything else to add at this point? Thank you, A.[/B]

---

### Post by AbleTassie on 2016-09-13
i'm waiting to get some external memory backup before trying the new kernel.

thanks,

A

---

