---
title: "Virtualbox Kernal mismatch help"
date: 2012-10-05
forum: Virtualisation
---

### Post by swnedol on 2012-10-05
Hello,

I am running 12.04 32-bit ubuntu.  I need some help with the Virtualbox kernal.  Hopefully someone can help me or point me in the righ direction, google has been unhelpful.

I must of not typed it correctly into the package manager because I didn't find virtualbox.So, I downloaded virtualbox 4.2 from the website which was a *.deb file.  I ran the file and it seemed to install.  I setup a VM, but was having USB issues. 

I ran the sudo apt-get purge vitualbox-4.2 and it ran through.  I then checked the package manager again and found it this time.  So I installed via the ubuntu software manager.  I found out that the package manager has Virtualbox 4.1 version.  After opening Virtualbox (it still had my previous VM I created before uninstall) I deleted the VM and recreated it.

When I started the VM I got the error message
"RTR3Init failed with rc=-1912 (rc=-1912)

The VirtualBox kernel modules do not match this version of VirtualBox. The installation of VirtualBox was apparently not successful. Executing

'/etc/init.d/vboxdrv setup'

may correct this. Make sure that you do not mix the OSE version and the PUEL version of VirtualBox."

So after some googling, I ran the command "sudo apt-get --reinstall install virtualbox-dkms"

This is what echo'd to my terminal:
```
swnedol@swnedol:~$ sudo apt-get --reinstall install virtualbox-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  bochsbios par2 libwxgtk2.8-0 sabnzbdplus-theme-plush python-utidylib
  python-configobj libtidy-0.99-0 python-cheetah vgabios libwxbase2.8-0
  python-feedparser libjs-mochikit bximage libjs-excanvas libgtkspell0
  python-yenc
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/675 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 205495 files and directories currently installed.)
Preparing to replace virtualbox-dkms 4.1.12-dfsg-2ubuntu0.1 (using .../virtualbox-dkms_4.1.12-dfsg-2ubuntu0.1_all.deb) ...

-------- Uninstall Beginning --------
Module:  virtualbox
Version: 4.1.12
Kernel:  3.2.0-31-generic-pae (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-31-generic-pae/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-31-generic-pae/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-31-generic-pae/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-31-generic-pae/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.

------------------------------
Deleting module version: 4.1.12
completely from the DKMS tree.
------------------------------
Done.
Unpacking replacement virtualbox-dkms ...
Setting up virtualbox-dkms (4.1.12-dfsg-2ubuntu0.1) ...
Loading new virtualbox-4.1.12 DKMS files...
Building only for 3.2.0-31-generic-pae
Building initial module for 3.2.0-31-generic-pae
Done.

vboxdrv:
Running module version sanity check.
Error! Module version 4.1.12_Ubuntu for vboxdrv.ko
is not newer than what is already found in kernel 3.2.0-31-generic-pae (4.2.0).
You may override by specifying --force.

vboxnetadp.ko:
Running module version sanity check.
Error! Module version 4.1.12_Ubuntu for vboxnetadp.ko
is not newer than what is already found in kernel 3.2.0-31-generic-pae (4.2.0).
You may override by specifying --force.

vboxnetflt.ko:
Running module version sanity check.
Error! Module version 4.1.12_Ubuntu for vboxnetflt.ko
is not newer than what is already found in kernel 3.2.0-31-generic-pae (4.2.0).
You may override by specifying --force.

vboxpci.ko:
Running module version sanity check.
Error! Module version 4.1.12_Ubuntu for vboxpci.ko
is not newer than what is already found in kernel 3.2.0-31-generic-pae (4.2.0).
You may override by specifying --force.

depmod....

DKMS: install completed.
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Starting VirtualBox kernel modules                                    [ OK ]


```I can't seem to figure out how to remove the old(newest) kernal so I can install the 4.1 kernal.

How can I do a complete clean uninstall of Virtualbox including removing the kernal, so I can do a clean install of Virtualbox from the package manager?  Hopefully this makes sense.  I am at a loss any help would be GREATLY appreciated, I've been pulling my hair out for the last 3 hours.  I am pretty new to Linux.

Thank you,
SW

---

### Post by nothingspecial on 2012-10-06
*Thread moved to **Virtualization**.*

---

### Post by swnedol on 2012-10-06
Thanks for moving it to the appropriate forum.  I wasn't sure which forum to post the question in.

---

### Post by swnedol on 2012-10-06
One more thing I saw I forgot to post.  I ran /etc/init.d/vboxdrv setup as it suggested.  This is what came back.

swnedol@swnedol:~$ /etc/init.d/vboxdrv setup
bash: /etc/init.d/vboxdrv: No such file or directory

---

### Post by swnedol on 2012-10-07
So, I purged virtualbox-dkms from my system.  I then tried using:
swnedol@swnedol:~$ sudo apt-get -o dpkg::Options::= --force-bad-version -o dpkg::Options::= --force-overwrite  install virtualbox-dkms

in hopes that it would overwrite the new version with the old version.  It didn't work.  It showed me this after it was done installing with the above option passed:
swnedol@swnedol:~$ sudo apt-get -o dpkg::Options::= --force-bad-version -o dpkg::Options::= --force-overwrite  install virtualbox-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  bochsbios par2 libwxgtk2.8-0 sabnzbdplus-theme-plush python-utidylib
  python-configobj libtidy-0.99-0 python-cheetah vgabios libwxbase2.8-0
  python-feedparser libjs-mochikit bximage libjs-excanvas libgtkspell0
  python-yenc
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  virtualbox-dkms
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/675 kB of archives.
After this operation, 3,898 kB of additional disk space will be used.
Selecting previously unselected package virtualbox-dkms.
(Reading database ... 205242 files and directories currently installed.)
Unpacking virtualbox-dkms (from .../virtualbox-dkms_4.1.12-dfsg-2ubuntu0.1_all.deb) ...
Setting up virtualbox-dkms (4.1.12-dfsg-2ubuntu0.1) ...
Loading new virtualbox-4.1.12 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-31-generic-pae
Building initial module for 3.2.0-31-generic-pae
Done.

vboxdrv:
Running module version sanity check.
Error! Module version 4.1.12_Ubuntu for vboxdrv.ko
is not newer than what is already found in kernel 3.2.0-31-generic-pae (4.2.0).
You may override by specifying --force.

vboxnetadp.ko:
Running module version sanity check.
Error! Module version 4.1.12_Ubuntu for vboxnetadp.ko
is not newer than what is already found in kernel 3.2.0-31-generic-pae (4.2.0).
You may override by specifying --force.

vboxnetflt.ko:
Running module version sanity check.
Error! Module version 4.1.12_Ubuntu for vboxnetflt.ko
is not newer than what is already found in kernel 3.2.0-31-generic-pae (4.2.0).
You may override by specifying --force.

vboxpci.ko:
Running module version sanity check.
Error! Module version 4.1.12_Ubuntu for vboxpci.ko
is not newer than what is already found in kernel 3.2.0-31-generic-pae (4.2.0).
You may override by specifying --force.

depmod....

DKMS: install completed.
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Starting VirtualBox kernel modules                                    [ OK ]

---

### Post by swnedol on 2012-10-07
In my previous posting after it builds the modules it runs a "module sanity check."  After a few of the *.ko files fail the sanity check it says "You may override by specifying --force"

How would I specify the --force to override the problem?

I have already tried passing the -bad-version and -overwrite switches with the dpkg --force upon running the install.

Is there another way to pass a --force command?  How would I accomplish overriding by specifying --force as it suggests?

Thanks
SW

---

### Post by swnedol on 2012-10-07
Not sure if I should mark the problem "solved" or not because technically my original issue is not resolved.  I have no idea how to actually fix the modules issue with the kernal.

I do however have virtual box up and running now.  I found a way install virtualbox-4.2 package with the package manager.  And since I already had the 4.2 modules installed I had no trouble with the installation.

To add the repository key I used:
wget -q [http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc](http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc) -O- | sudo apt-key add -

Then to add the repository I used:
sudo sh -c 'echo "deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) precise contrib" >> /etc/apt/sources.list'

Then I ran:
sudo apt-get update && sudo apt-get install virtualbox-4.2

after that I had to add my username to the vboxusers group :
sudo usermod -aG vboxusers <your username>

and now I have virtualbox up and running.  Like I said my original issue is not solved, and I would love to know how I could of resolved that issue.  Any help on the original issue would be great. 

Thanks,
SW

---

### Post by CharlesA on 2012-10-07
Run this please:

```
dpkg -l | grep virtualbox
```

It should only list this (with 4.2 replacing 4.1, cuz I have 4.1 installed on my box):

```
ii  virtualbox-4.1                       4.1.22-80657~Ubuntu~precise         Oracle VM VirtualBox

```

If you needed USB support, you would need the version of virutalbox from the virtualbox website.

---

