---
title: "Error message upgrading v-box.  Probably simple solution"
date: 2010-02-14
forum: Virtualisation
---

### Post by azitizz on 2010-02-14
Hi There. I just tried upgrading my Virtual box version 3.1.2 to 3.1.4 which appeared as an automatic install (just click the link). It seemed to download the packages and then at the end of installing I got an error message mentioning there may be permission problems. 
 Now whenI open virtual box and click on my Win XP machine and the massage that comes up is:
"[B]Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.[/B]" 

Ive tried doing this (Below) but still get an error message. I know this is probably a no brainer for an experienced linux user but Im still a beginner. any pointers would be appreciated:
```
mikepanc@mikepanc-laptop:~$ /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                             *  done.
 * Recompiling VirtualBox kernel module                                         /etc/init.d/vboxdrv: 377: cannot create /var/log/vbox-install.log: Permission denied

 * Look at /var/log/vbox-install.log to find out what went wrong
mikepanc@mikepanc-laptop:~$ /var/log/vbox-install.log
bash: /var/log/vbox-install.log: Permission denied
mikepanc@mikepanc-laptop:~$ sudo/var/log/vbox-install.log
bash: sudo/var/log/vbox-install.log: No such file or directory
mikepanc@mikepanc-laptop:~$ sudo /var/log/vbox-install.log
[sudo] password for mikepanc: 
sudo: /var/log/vbox-install.log: command not found
```

---

### Post by mandyb on 2010-02-14
That "as root" part of the instructions means you will need to preface the /etc/init.d/vboxdrv setup with sudo.  To look at the log, open with a text editor.  One way you could do that:  nano /var/log/vbox-install.log

If you are using Windows guest I will be interested to know if guest additions will install.  that's where my 3.1.2 -> 3.1.4 fell down & now looking for answers.  I KNOW better than to be first! ha

Another note: I think you will be better off turning off the virtualbox update and using your package manager instead.

---

### Post by azitizz on 2010-02-14
I see. So I ran the command you suggested to read the log file. Heres what it says. I cant seem to see anything that tells me something went terribly wrong but also much of this is an alien language t me still:

```
** Compiling vboxdrv
Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxdrv/3.1.2/source ->
                 /usr/src/vboxdrv-3.1.2

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
su nobody -c "make KERNELRELEASE=2.6.31-17-generic -C /lib/modules/2.6.31-17-generic/build M=/var/lib/dkms/vboxdrv/3.1.2/build"..............

Running the post_build script:
cleaning build area....

DKMS: build Completed.

vboxdrv.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.31-17-generic/updates/dkms/

depmod....

DKMS: install Completed.
** Compiling vboxnetflt
Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxnetflt/3.1.2/source ->
                 /usr/src/vboxnetflt-3.1.2

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Running the pre_build script:

Building module:
cleaning build area....
su nobody -c "make KERNELRELEASE=2.6.31-17-generic -C /lib/modules/2.6.31-17-generic/build M=/var/lib/dkms/vboxnetflt/3.1.2/build"....
cleaning build area....

DKMS: build Completed.

vboxnetflt.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.31-17-generic/updates/dkms/

depmod....

DKMS: install Completed.
** Compiling vboxnetadp
Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxnetadp/3.1.2/source ->
                 /usr/src/vboxnetadp-3.1.2

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Running the pre_build script:

Building module:
cleaning build area....
su nobody -c "make KERNELRELEASE=2.6.31-17-generic -C /lib/modules/2.6.31-17-generic/build M=/var/lib/dkms/vboxnetadp/3.1.2/build"....
cleaning build area....

DKMS: build Completed.

vboxnetadp.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.31-17-generic/updates/dkms/

depmod....

DKMS: install Completed.
```

Is there any simply way to revert back to the original version without loosing the installed windows? I do have windows with guest additions by the way. Yes I will be curious to see if they remain intact.

---

### Post by mandyb on 2010-02-15
I'm too ignorant to give you advice going forward from where you are at, plus don't like that log's references to 3.1.2 when you were updating to 3.1.4...(?)  So I'll just say what I would do:
copy your {windowsname}.vdi file  just make a blood & guts copy
stop the vboxdrv service (something like sudo /etc/init.d/vboxdrv stop that's close but you might have to google it)
however you installed virtualbox in the first place, use that to uninstall it,  synaptic  or command line apt-get remove or dpkg --purge
Now reinstall the way you did to begin with, turn off checking for updates.

Wish I could be better help.. I think you can tell my advice is more back yourself up & something to try.  I can reassure you the xxxx.vdi your virtual machine will still be there when you get the update backed off.

---

### Post by mandyb on 2010-02-16
Upgrading 3.1.2 to 3.1.4 I lost the ability to install Windows Guest Additions, getting "file not found".  Probably every Windows person knows that means registry key RunOnce is missing, but it took me a couple of days to find that answer here
[http://forums.virtualbox.org/viewtopic.php?f=2&t=25796&start=0](http://forums.virtualbox.org/viewtopic.php?f=2&t=25796&start=0)

Happy now.

---

