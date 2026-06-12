---
title: "Hash Sum Mismatch error while trying to install Virtualbox 2.2 in Ubuntu 9.04"
date: 2009-05-20
forum: Virtualisation
---

### Post by diablo75 on 2009-05-20
Edit:  md5sum shows a mismatch on the deb file I've download many times.  I'm going to try and find a torrent for this to ensure a correct download.

I have two computers.  One was recently upgraded from 8.10 to 9.04 and the other had 9.04 installed fresh about 2 days ago.

The PC which was upgraded had Virtualbox 2.1 on it.  Attempting to install 2.2 via the deb caused some sort of package conflict error.  So I used sudo apt-get remove virtualbox-2.1 to remove.  I also used the tip from the virtualbox FAQ to unregister virtualbox from dkms (rm -rf /var/lib/dkms/vboxnetflt).  I did this after several attempts to install Vbox from a deb and running into an error where it said it was unable to compile the kernel.  It seemed to compile successfully after, but failed to show up in Applications>System menu as usual.  Checking with System>Preferences>Main Menu also does not show an otherwise hidden shortcut waiting to be enabled, so I uninstalled using apt-get purge.

Next (on both computers) I attempted to install virtualbox via third-party software sources and then using the command sudo apt-get install virtualbox-2.2.  Every time I do this the download seems to lock up for a long time midway through.  Regardless of whether or not it locks up, if it gets all the way through, it tells me there's a "hash sum mismatch" and that it was unable to successfully download all necessary packages.

From the sound of this, it would seem that there is some sort of problem with my connection.  This has never happened before.  I am on a cable connection with a WPA2 wireless connection.  I've even cut wireless out of the equation by taking the laptop (which is the second of the two computers, only running 9.04 since a couple days ago from a fresh install) strait to the router, and it still produces the same problem, even though on the most recent attempt to install there were no visible locks during the download.

So I'm stuck without virtualbox on both PCs and can't seem to figure out what's preventing me from installing it.

---

### Post by diablo75 on 2009-05-20
Here's what happens if I take the deb file from Sun's website and try to install it using dpkg -i in Terminal:

```
user@user-desktop:~/Desktop$ sudo dpkg -i virtualbox-2.2_2.2.2-46594_Ubuntu_jaunty_i386.deb 
Selecting previously deselected package virtualbox-2.2.
(Reading database ... 135331 files and directories currently installed.)
Unpacking virtualbox-2.2 (from virtualbox-2.2_2.2.2-46594_Ubuntu_jaunty_i386.deb) ...
Setting up virtualbox-2.2 (2.2.2-46594_Ubuntu_jaunty) ...
addgroup: The group `vboxusers' already exists as a system group. Exiting.
Messages emitted during module compilation will be logged to /var/log/vbox-install.log.
Success!
chmod: cannot access `/usr/lib/virtualbox/VirtualBox': No such file or directory
chmod: cannot access `/usr/lib/virtualbox/VBoxHeadless': No such file or directory
chmod: cannot access `/usr/lib/virtualbox/VBoxSDL': No such file or directory
chmod: cannot access `/usr/lib/virtualbox/VBoxNetDHCP': No such file or directory
chmod: cannot access `/usr/lib/virtualbox/VBoxNetAdpCtl': No such file or directory
 * Starting VirtualBox kernel module                                             *  done.

user@user-desktop:~/Desktop$ 

```

This happened after I did a sudo apt-get purge virtualbox-2.1 virtualbox-2.2

What else can I try?

---

