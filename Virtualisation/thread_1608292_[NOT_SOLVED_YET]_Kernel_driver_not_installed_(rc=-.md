---
title: "[NOT SOLVED YET] Kernel driver not installed (rc=-1908) Ubuntu Lucid Lynx"
date: 2010-10-28
forum: Virtualisation
---

### Post by AlexanderDGreat on 2010-10-28
I know there's already a thread for this: [http://ubuntuforums.org/showthread.php?t=1163811]("http://ubuntuforums.org/showthread.php?t=1163811")

But this is what shows up for me:

[IMG]http://i365.photobucket.com/albums/oo91/whatupdawg_photos/kerneldrivernotinstalled.png[/IMG]

I've tried reinstalling my linux-headers, linux-images, 2.6.32-25-generic-pae, 2.6.32-25-generic, switching to 2.6.32.24, reinstall from there, what have you.

I've tried purging virtualbox-3.2, dkms, remove the folder /var/lib/dkms/

I've tried running what the picture says, sudo /etc/init.d/vboxdrv setup

ALL FAILED, everytime I run VirtualBox, it says this.

Help!

---

### Post by bpalone on 2010-10-28
Just a thought here.  Have you tried an older version of VB to see if the problem persists?  You can access older builds on the VirtualBox site, or at least you used to be able to.  Other than that, I do remember there being some dependencies mentioned in the manual, but I'm guessing that you had it running before and that should of been addressed already.

May not be of much help, but is worth exactly what was paid.:)

Good luck.

---

### Post by CharlesA on 2010-10-28
How did you install virtualbox, and which version is it?

I've got VirtualBox running on Lucid x64 without any problems.

---

### Post by AlexanderDGreat on 2010-10-28
Hi CharlesA.

I'm running **Ubuntu Lucid Lynx 32-bit, VirtualBox-3.2.10 r66523, installed from Synaptics,** followed Virtualbox website instructions, add source, and key, then install, not from .deb.

---

### Post by CharlesA on 2010-10-28
It's the "non-free" version then?

Here's the one I have installed:
```
ii  virtualbox-3.2                  3.2.10-66523~Ubuntu~lucid                       Oracle VM VirtualBox
```

Looks like you installed it correctly.

Can you do this:

```
sudo apt-get purge virtualbox-3.2
```

Reboot, then run this:

```
sudo apt-get install virtualbox-3.2
```

I've had to kill anything related to virtualbox if I needed to rebuild the kernel modules.

Did running /etc/init.d/vboxdrv setup return any error?

---

### Post by AlexanderDGreat on 2010-10-28
Yup it's the non-free version.

```


**art@lgv-server:~$ sudo apt-get purge virtualbox-3.2**
[sudo] password for art: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  virtualbox-3.2*
0 upgraded, 0 newly installed, 1 to remove and 26 not upgraded.
After this operation, 96.7MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 152152 files and directories currently installed.)
Removing virtualbox-3.2 ...
 * Stopping VirtualBox kernel modules                                            *  done.
Purging configuration files for virtualbox-3.2 ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for python-support ...
**art@lgv-server:~$ sudo apt-get install virtualbox-3.2**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  virtualbox-3.2
0 upgraded, 1 newly installed, 0 to remove and 26 not upgraded.
Need to get 0B/49.1MB of archives.
After this operation, 96.7MB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package virtualbox-3.2.
(Reading database ... 151633 files and directories currently installed.)
Unpacking virtualbox-3.2 (from .../virtualbox-3.2_3.2.10-66523~Ubuntu~lucid_i386.deb) ...
Processing triggers for ureadahead ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Setting up virtualbox-3.2 (3.2.10-66523~Ubuntu~lucid) ...
addgroup: The group `vboxusers' already exists as a system group. Exiting.
 * Stopping VirtualBox kernel modules                                            *  done.
 * Uninstalling old VirtualBox DKMS kernel modules                               *  done.
 * Trying to register the VirtualBox kernel modules using DKMS                   *  done.
 * Starting VirtualBox kernel modules                                            *  done.

Processing triggers for python-central ...
**art@lgv-server:~$ sudo /etc/init.d/vboxdrv setup**
 * Stopping VirtualBox kernel modules                                            *  done.
 * Uninstalling old VirtualBox DKMS kernel modules                               *  done.
 * Trying to register the VirtualBox kernel modules using DKMS                   *  done.
 * Starting VirtualBox kernel modules                                            *  done.
art@lgv-server:~$ 


```

---

### Post by CharlesA on 2010-10-28
It looks like it completely fine without any errors.

Does it still give you the same error when you try to start it up?

---

### Post by AlexanderDGreat on 2010-10-29
Hi CharlesA,

> Does it still give you the same error when you try to start it up?

Do you mean when I launch it via the menu? No errors.
Do you mean when I type VirtualBox from CLI? No errors.

BUT when I autostart it by launching System > Preferences > Startup Applications

VBoxManage startvm Microsoft\ Windows\ XP

This is where I get the error.

So to sum if I just launch it via the Virtualbox GUI, no errors, WinXP can start just fine.

But when I auto launch it at boot time, that's where the error comes up.

---

### Post by CharlesA on 2010-10-29
Oh gotcha.

It could be that something isn't loaded when it's trying to start it up.

Try adding something like s***leep 60 && VBoxManage startvm Microsoft\ Windows\ XP***

To see if it has the same problem.

I actually ran into a similar problems when I use cron and the @reboot condition to start a VM after a reboot. It failed to start the VM but the kernel module wasn't loaded when it was starting up.

I had to reinstall virtualbox to get it to work correctly.

Here's the error that I got:

```
charles@luna:~$ cat startvm.log
VBoxSVC: error: 0 bytes read from child process
VBoxHeadless: Error -1908 in suplibOsInit!
VBoxHeadless: Kernel driver not installed

VBoxHeadless: Tip! Make sure the kernel module is loaded. It may also help to reinstall VirtualBox.
VBoxSVC: error: 0 bytes read from child process
VBoxHeadless: Error -1908 in suplibOsInit!
VBoxHeadless: Kernel driver not installed

```

EDIT: Looks like it's the same error.

---

### Post by AlexanderDGreat on 2010-10-30
> Try adding something like sleep 60 && VBoxManage startvm Microsoft\ Windows\ XP

Yes, Finally it worked! I only have to put sleep 10.

Thank you so much CharlesA! Now, I'll lock my version of VirtualBox.

Coz it put me off my work for a while, I'll upgrade when I have time. Thanks :)

---

### Post by CharlesA on 2010-10-31
Glad you got it working. :)

---

### Post by AlexanderDGreat on 2010-11-01
> Glad you got it working. - ***Thank you! More Power to you! God bless.***

---

