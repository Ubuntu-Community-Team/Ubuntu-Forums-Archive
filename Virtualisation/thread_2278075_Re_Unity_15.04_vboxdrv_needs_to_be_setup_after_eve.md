---
title: "Re: Unity 15.04 vboxdrv needs to be setup after every reboot"
date: 2015-05-13
forum: Virtualisation
---

### Post by gwm on 2015-05-13
I am not sure when this started happening. I could have been after an update or perhaps even when I upgraded from 14.10 15.04
Each time I reboot, I need to run the suggested command. Then all is well until the next time I restart Ubuntu.
```
Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.
```
I run a windows client under vbox in Ubuntu. each time I reboot the computer, I have to run the setup again manually.
Please can someone help me fix this?

Once the setup has been run, I can restart the client OS, take down vbox and restart it with no problem.

---

### Post by ajgreeny on 2015-05-13
Do you have dkms installed in your host machine as that error tells you you should have?

Mind you, I also get this error occasionally with the most recent version of VBox, even though I do have dkms installed.  It does not happen every time I boot, however, perhaps because I am using 14.04 Xubuntu 64bit, not 15.04.

---

### Post by gwm on 2015-05-14
The setup command that one is asked to execute, removes the existing drivers and then uses dkms to reinstall / register them. Then all is well. Then when one reboots, they aren't registered anylonger.
In short, I believe that dkms is installed. Why would an update remove it?

---

### Post by entw on 2015-05-14
Yeah, doesn't work for me too. But i switched to Upstart recently where everything works just fine.

Well it seems there's no bug report on Launchpad for this issue. Can you create one?

---

### Post by SeijiSensei on 2015-05-14
Install the version of VirtualBox from Oracle's repository: [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

That has always worked better for me than using the Ubuntu version.

---

### Post by gwm on 2015-05-14
That is the version I use.
I've just applied a new update on vbox but the problem persists.
My guess is that one of the updates has caused something to change so the driver is not setup at boot time.
With the old Ubuntu GUI I could work out how to do stuff because it worked sort of like all the other operating systems I've worked on over the years. Now, in Unity, everything feels hidden.
Where do I go to find how to get things to run automatically when Ubuntu Unity starts up. Then I can force this command```
sudo /etc/init.d/vboxdrv setup
```to execute each time I reboot.
What a disgusting kludge solution but it will work (I hope the sudo bit works if I run it outside of a terminal environment).

Perhaps I should just reinstall vbox.

---

### Post by gwm on 2015-05-14
Oh, I have just realized that my description is incomplete.
The Virtual Box Manager starts up okay, It is when I try to start my Windows7 client that I get the error message.
I tried updating the client setup by changing the system memory slightly, to see if that would maybe recreate the client startup script, if there is one. When I clicked OK the VBox Manager grabbed the CPU so that my mouse was struggling along, the keyboard locked up and I had to hit the power switch to regain control of the PC.

---

### Post by SeijiSensei on 2015-05-14
The module is placed in /lib/modules/$(uname -r)/updates/dkms/vboxdrv.ko when it is compiled.  After you've run setup, can you see it there?  (The uname -r command returns the current kernel version, so on my system the appropriate directory is /lib/modules/3.16.0-33-generic/updates/dkms/.)

---

### Post by gwm on 2015-05-19
Sorry for long delay. Was deeply involved with other things.

Thank you for your response. The results you asked for are as follows.

First I rebooted Ubuntu then I tried to run my Windows client and I got the error telling me to run```
sudo /etc/init.d/vboxdrv setup
```
At this stage I opened a terminal and did the following```
gwm@puer:~$ uname -r
3.19.0-15-generic
gwm@puer:~$ ls -l /lib/modules/3.19.0-15-generic/updates/dkms
total 620
-rw-r--r-- 1 root root 539920 May 18 14:06 vboxdrv.ko
-rw-r--r-- 1 root root  15072 May 18 14:06 vboxnetadp.ko
-rw-r--r-- 1 root root  37936 May 18 14:06 vboxnetflt.ko
-rw-r--r-- 1 root root  36576 May 18 14:06 vboxpci.ko
gwm@puer:~$ sudo /etc/init.d/vboxdrv setup
[sudo] password for gwm: 
Stopping VirtualBox kernel modules ...done.
Uninstalling old VirtualBox DKMS kernel modules ...done.
Trying to register the VirtualBox kernel modules using DKMS ...done.
Starting VirtualBox kernel modules ...done.
gwm@puer:~$ ls -l /lib/modules/3.19.0-15-generic/updates/dkms
total 620
-rw-r--r-- 1 root root 539920 May 19 18:45 vboxdrv.ko
-rw-r--r-- 1 root root  15072 May 19 18:45 vboxnetadp.ko
-rw-r--r-- 1 root root  37936 May 19 18:45 vboxnetflt.ko
-rw-r--r-- 1 root root  36576 May 19 18:45 vboxpci.ko
gwm@puer:~$
```
After this the client starts just fine, as discussed earlier in this post.
This is necessary after each reboot of Ubuntu.

---

### Post by gwm on 2015-05-19
I looked in the setup script and it seemed to be logging its progress, so I include the log file below.
It doesn't seem to have any errors. Yet it must be re-executed each time.
I don't understand. reinstalling dkms has made no difference.```
cat /var/log/vbox-install.log
Uninstalling modules from DKMS
  removing old DKMS module vboxhost version  4.3.28

-------- Uninstall Beginning --------
Module:  vboxhost
Version: 4.3.28
Kernel:  3.19.0-15-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-15-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-15-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-15-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-15-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.

------------------------------
Deleting module version: 4.3.28
completely from the DKMS tree.
------------------------------
Done.
Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxhost/4.3.28/source ->
                 /usr/src/vboxhost-4.3.28

DKMS: add completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=3.19.0-15-generic -C /lib/modules/3.19.0-15-generic/build M=/var/lib/dkms/vboxhost/4.3.28/build.............
cleaning build area....

DKMS: build completed.

vboxdrv:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.19.0-15-generic/updates/dkms/

vboxnetflt.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.19.0-15-generic/updates/dkms/

vboxnetadp.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.19.0-15-generic/updates/dkms/

vboxpci.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.19.0-15-generic/updates/dkms/

depmod....

DKMS: install completed.
gwm@puer:~$ 
```

---

### Post by amgelinux on 2015-05-30
Hi!!

Same problem. Not needed to setup again and again (too slow). I realized that my problem is that the vboxdrv is not automatically starting with the operating system.
I write:

service vboxdrv start 

and I can use VirtualBox.
Maybe the problem is with upstart script??

---

### Post by gwm on 2015-06-01
Thank you Amgelinux!
I was looking into somehow modifying the vboxdrv initialization script since the compile simply produced exactly what was there already.
That means that dkms somehow starts something when it registers the modules.
I don't think I would have got to your solution. So, BRAVO!

---

### Post by gwm on 2015-06-01
Now I am looking into how to make it happen each time I reboot.
I found something called **Startup Applications** in the Head Up Display and I have added your command there. **service** needs super user privileges so I am now going to discover how it works by rebooting my machine.

---

### Post by gwm on 2015-06-01
It works!
Once the Graphic User Interface starts up, I get asked for a password again and after that I can use vbox.
I opened a command line window and executed the command repeatedly to see if this does any damage but it doesn't seem to hurt anything. So I am going to leave it in my Startup Applications until maybe the Oracle guys fix their client startup script and maybe tell us about it.

Thank you  once again Amgelinux!

---

### Post by ajgreeny on 2015-06-01
To avoid the password request at boot add the command to /etc/rc.local (no sudo needed) and it should be executed when the OS starts.

---

### Post by gwm on 2015-06-11
Thanks for the suggestion ajgtreeny.

I think I'll leave it where it is though, because it keeps reminding me that I have this cludge fix in there. If I put it away down in the start up sequence, while we are still running as root, I'll forget about it and I hate that.
Littering my system with commands that shouldn't be needed and that get forgotten just grates my developer sense of tidiness. We're applying a bandage to a wounded system.

My senses want to find what happened that it ceased to be started. That is actually what needs correction. Hopefully, one day, that will be fixed and then my reminder mechanism will remind me to remove the bandage.

It could be that the update to some other package overwrote a module that both packages have in common and thus wiped the service start command. If I try reinstalling Virtual Box, it might fix this issue but that other package will then start breaking and we won't know why. If one of us knew where, when and how in the boot sequence, this driver is supposed to be started, I would feel better about going to that module and fixing it.

Thanks again for all your help.

---

### Post by dan188 on 2015-08-09
I had the exact same problem, the error when launching a Windows VM. It turns out that "This can be simply solved by adding the line "vboxdrv" to /etc/modules" per [http://binbashblog.blogspot.com/2010/01/virtualbox-module-needs-recompiling.html](http://binbashblog.blogspot.com/2010/01/virtualbox-module-needs-recompiling.html)

---

### Post by sicvolo on 2015-09-10
To anyone stumbling here - this problem is caused by the vboxdrv not starting on boot. In my case the reason for it not starting on boot it was a collision between the /etc/init.d/virtualbox from the opensource distro and the Oracle vboxdrv. 
You can start it manually after each boot per the posts above, or fix the autostart issue by removing virtualbox remnants and reenabling vboxdrv in systemd:

```
sudo /usr/sbin/update-rc.d -f virtualbox remove 
sudo rm /etc/init.d/virtualbox
sudo systemctl enable vboxdrv
```

---

### Post by Mac_Huang on 2015-09-19
Hey guys, this solution worked for my Ubuntu 15.04:  [http://binbashblog.blogspot.com/2010/01/virtualbox-module-needs-recompiling.html](http://binbashblog.blogspot.com/2010/01/virtualbox-module-needs-recompiling.html)

---

### Post by frans-duijnhouwer on 2015-09-22
Hi,
I have the same problem. Just reinstalled the vboxdrv modules yesterday with the suggested command and today the same message popped up.
However, the driver modules are present in the /lib/modules/$(uname -r)/updates/dkms directory, so I guess the problem is not absence, but rather omitting to load them. You can load the modules into the kernel with the commands:
```

sudo modprobe vboxdrv
sudo modprobe vboxnetadp
sudo modprobe vboxnetflt
sudo modprobe vboxpci

```

This worked for me and is faster than reinstalling the modules.
A proper solution should load the modules automatically at boot time. On Ubuntu 15.04 this should be hooked into systemd somehow.

Cheers,
Frans

---

### Post by Rajnish_kumar on 2016-02-13
did u got the solution?
i am also facing the same problem........plzzzzz reply me

---

