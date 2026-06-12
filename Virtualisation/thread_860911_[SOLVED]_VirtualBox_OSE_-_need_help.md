---
title: "[SOLVED] VirtualBox OSE - need help"
date: 2008-07-16
forum: Virtualisation
---

### Post by farkadenear on 2008-07-16
Okay load seemed to go well and I set up a new machine... when I started it up I get this message.
-----------------------
00:00:06.608 VirtualBox 1.5.6_OSE r28240 linux.x86 (Apr  9 2008 01:30:09) release log
00:00:06.608 Log opened 2008-07-16T06:13:48.638632000Z
00:00:06.609 ERROR [COM]: aRC=0x80004005 aIID={1dea5c4b-0753-4193-b909-22330f64ec45} aComponent={Console} aText={VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
00:00:06.609 VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED)} aPreserve=false
00:00:06.776 Power up failed (vrc=VERR_VM_DRIVER_NOT_INSTALLED, hrc=0x80004005)
----------------------

Anyway if anyone has seen this particular problem and knows the work around that would be awesome.

FKN

---

### Post by Canis familiaris on 2008-07-16
Go to Synaptic. Search for virtualbox-ose-modules-generic package. Install it. 
Also Add your user to vboxusers group.
Try Again.

---

### Post by farkadenear on 2008-07-16
Okay installed the generic package... seems to be the same error to me. But I will post it in case I am just not seeing the difference.

__

00:00:07.139 VirtualBox 1.5.6_OSE r28240 linux.x86 (Apr  9 2008 01:30:09) release log
00:00:07.139 Log opened 2008-07-16T05:25:51.340274000Z
00:00:07.140 ERROR [COM]: aRC=0x80004005 aIID={1dea5c4b-0753-4193-b909-22330f64ec45} aComponent={Console} aText={VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
00:00:07.140 VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED)} aPreserve=false
00:00:07.249 Power up failed (vrc=VERR_VM_DRIVER_NOT_INSTALLED, hrc=0x80004005)

__

[EDIT] Thought I would look at /dev/vboxdrv

farkadenear@farkadenear-desktop:~$ sudo /dev/vboxdrv
[sudo] password for farkadenear: 
sudo: /dev/vboxdrv: command not found



thanks
FKN

---

### Post by farkadenear on 2008-07-16
[link: Vbox Tutorial]("http://ubuntuforums.org/showthread.php?t=770745&highlight=virtualbox+won%27t+work&page=6")

Found someone in this thread with the same error and he fixed it with: ```
sudo /etc/init.d/vboxdrv setup
```

so that is what I will try when I get home from work today.

---

### Post by farkadenear on 2008-07-16
Okay so I got home and tried that command like I had mentioned.
___________

farkadenear@farkadenear-desktop:~$ sudo /etc/init.d/vboxdrv setup
[sudo] password for farkadenear: 
 * Usage: /etc/init.d/vboxdrv {start|stop|restart|status}
farkadenear@farkadenear-desktop:~$ sudo /etc/init.d/vboxdrv restart
 * Stopping VirtualBox kernel module vboxdrv                             [ OK ] 
 * Starting VirtualBox kernel module vboxdrv                                    
 * No suitable module for running kernel found.
farkadenear@farkadenear-desktop:~$ 

Running Status resulted in:

farkadenear@farkadenear-desktop:~$ sudo /etc/init.d/vboxdrv status
 * VirtualBox kernel module is not loaded.
farkadenear@farkadenear-desktop:~$ 

___________

And this is what I got.

Any ideas where to go from there?

---

### Post by raptor2552 on 2008-07-16
Hello

I had the same problem but it's easily fixed

Remove the OSE (Open Source Edition)  version of Virtualbox

Go to the Virtualbox website: [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)
and click on Binaries (all platforms) which will take you to Sun's website then select your platform and download.

Use Debian package manager to install and you should be all set.

If and when there is a kernel update you can then use```
sudo /etc/init.d/vboxdrv setup
``` to update your Virtual box for use with the new kernel. It takes only seconds to recompile.

---

### Post by farkadenear on 2008-07-18
> **raptor2552 said:**
> Hello

I had the same problem but it's easily fixed

Remove the OSE (Open Source Edition)  version of Virtualbox

Go to the Virtualbox website: [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)
and click on Binaries (all platforms) which will take you to Sun's website then select your platform and download.

Use Debian package manager to install and you should be all set.

If and when there is a kernel update you can then use```
sudo /etc/init.d/vboxdrv setup
``` to update your Virtual box for use with the new kernel. It takes only seconds to recompile.


thanks that worked great!

---

### Post by raptor2552 on 2008-07-19
Glad this fixed your troubles. There was one thing I forgot to mention and that is be sure to install the "guest additions". I don't know if you are aware they exist.

---

### Post by Eagleman11 on 2008-08-03
ummm...

Does Anyone Have Mandriva 2008.1 spring one?

Because In Konsole it said bash: sudo Command not found.

---

### Post by wxnker on 2008-08-04
Eagleman11--> Mandriva doesn't use sudo by default. Just type "su" and hit enter to become root. Then run the command you need (without sudo).

---

### Post by TheRoot on 2008-09-05
A temporary fix, until the package is updated:

sudo apt-get install virtualbox-ose-source
sudo module-assistant update
sudo module-assistant prepare
sudo module-assistant a-i virtualbox-ose
sudo /etc/init.d/vboxdrv restart

Launch VirtualBox, and it should work.

[Thanks to McB]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/237278/comments/12")

---

