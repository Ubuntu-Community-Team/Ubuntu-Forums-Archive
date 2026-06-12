---
title: "VirtualBox kernel driver not installed v 1.6.2"
date: 2008-07-08
forum: Virtualisation
---

### Post by sonicjosh on 2008-07-08
I can not start a vm on virtualbox; I get the this error
[img]http://farm4.static.flickr.com/3003/2649716645_690c68d727_o.png[/img]

So I run it and get this
```
sonicjosh@sonicjosh-desktop-ubuntu:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                             *  done.
 * Recompiling VirtualBox kernel module                                         
 [color="red"]*[/color] Look at /var/log/vbox-install.log to find out what went wrong

```

Open that up
```
Makefile:127: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.

```

So I do that
```
sonicjosh@sonicjosh-desktop-ubuntu:~$ sudo  KERN_DIR=/boot/ /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                             *  done.
 * Recompiling VirtualBox kernel module                                         
 [COLOR="Red"]*[/COLOR] Look at /var/log/vbox-install.log to find out what went wrong

```
Get a new err
```
Makefile:154: *** Error: unable to find the include directory for your current Linux kernel. Specify KERN_INCL=<directory> and run Make again.  Stop.

```

So I basically just need to know where the KERN_INCL dir should be. I am on Ubuntu 8.04 and have not changed the kernel (e.g. it is the default kernel).

---

### Post by HotShotDJ on 2008-07-08
Have you installed build-essential?```
sudo apt-get install build-essential
```Once you install that, you should be all set.  Do NOT use the "KERN_INCL=<path>" directive.  After build-essential is installed, simply issue the command ```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by sonicjosh on 2008-07-09
> **HotShotDJ said:**
> Have you installed build-essential?```
sudo apt-get install build-essential
```Once you install that, you should be all set.  Do NOT use the "KERN_INCL=<path>" directive.  After build-essential is installed, simply issue the command ```
sudo /etc/init.d/vboxdrv setup
```

I get this again
```
Makefile:127: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.

```

I also specified the kernel dir but still got the error.

---

### Post by HotShotDJ on 2008-07-09
> **sonicjosh said:**
> I get this again
```
Makefile:127: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.

```

I also specified the kernel dir but still got the error.Did you specify /boot like you did before?  If so, don't do that.  vboxdrv setup is looking for the kernel SOURCES, not the kernel itself.

You should not have to specify KERN_DIR at all -- I'm at a loss as to why it is giving you this problem.  Perhaps a reboot after installing build-essential (perhaps you've done that already, I don't know).  You can TRY KERN_DIR=/usr/src/linux -- but again, I don't know why you are getting that error if you've properly installed build-essential.

---

### Post by Wharf Rat on 2008-07-09
I had virtualbox running for the past two weeks. Bam! It stopped with the same errors.  I followed the instructions above to work around the problem and I am back to the beginning.

I have removed Vbox, removed the Group Vbox users and reinstalled.  Still the same.

---

### Post by sonicjosh on 2008-07-09
> **HotShotDJ said:**
> Did you specify /boot like you did before?  If so, don't do that.  vboxdrv setup is looking for the kernel SOURCES, not the kernel itself.

You should not have to specify KERN_DIR at all -- I'm at a loss as to why it is giving you this problem.  Perhaps a reboot after installing build-essential (perhaps you've done that already, I don't know).  You can TRY KERN_DIR=/usr/src/linux -- but again, I don't know why you are getting that error if you've properly installed build-essential.

To the first question: yes, tried it both ways
Yes I have rebooted (this computer gets shut off every night).
And no, KERN_DIR=/usr/src/linux did not work.

---

### Post by Nikayah on 2008-07-09
I'm having the same issue!:( I have build essential, and I've specified KERN_DIR=/usr/src/linux but it wont work for me either. I'm running UbuntuStudio x64.

---

### Post by HotShotDJ on 2008-07-10
> **sonicjosh said:**
> To the first question: yes, tried it both ways
Yes I have rebooted (this computer gets shut off every night).
And no, KERN_DIR=/usr/src/linux did not work.I'm honestly stumped.  Obviously, the problem is real... I just don't know what is causing it.  I've got Virtualbox 1.6.2 installed on two machines... and I'm having no trouble running Windows 2000 and Vista Home Premium.

Let's try something... there are a few things I suspect.  First of all, I'd like you to go to System --> Administration --> Synaptic Package Manager and then search for virtualbox.  Check to see if there are still some modules from the OSE version installed.  If so, remove everything EXCEPT virtualbox 1.6.2 (and make sure it is the version for Hardy!) and then run "sudo /etc/init.d/vboxdrv setup"

If that is not the problem, then open a terminal and completely remove virtualbox -- "sudo apt-get autoremove virtualbox --purge"

Now you can reinstall virtualbox by simply double-clicking on the file.  The reinstall SHOULD go smoothly, including building the kernel module.

Other than these two things, I'm out of ideas.

---

### Post by ubtutu on 2008-07-10
I had a similar problem.... I fixed it after suspecting that my Gutsy kernel upgrade was interfering with the kernel module:

```

user@ubuntu:~$ sudo /etc/init.d/vboxdrv start
 * Starting VirtualBox kernel module vboxdrv
FATAL: Module vboxdrv not found.

```

So I tried to find the module, wondering where it had gone:
```

user@ubuntu:~$ find / -mount -iname vboxdrv.ko 2>/dev/null /lib/modules/2.6.22-14-generic/misc/vboxdrv.ko

```

Found it, but it's not installed in the correct place due to a kernel upgrade:
```

user@ubuntu:~$ uname -r
2.6.22-15-generic

```

I wasn't sure if the old existing module would still be compatible with my new kernel. Modprobe only seems to like already-installed modules, but insmod seems happy to inset the module.
```

user@ubuntu:~$ sudo insmod /lib/modules/2.6.22-14-generic/misc/vboxdrv.ko
user@ubuntu:~$ sudo /etc/init.d/vboxdrv start
 * Starting VirtualBox kernel module vboxdrv
   ...done.

```

After this, virtualbox seemed to run ok again! I would imagine that you can just copy the module to the correct place so that modprobe finds it upon bootup.

---

### Post by ceelow on 2008-07-10
I'm having this same problem, I understand what happened I just don't know how to correct it.  I went from the generic kernel to realtime (when upgrading from Ubuntu to Ubuntu Studio by installing the missing packages) and now VBox won't recreate the new module.  I cannot insmod the old vboxdrv.ko because of the difference in the kernels.  

Should I set KERN_DIR=2.6.24-19-rt/ or something to that effect?

I'll try, but if there's any other way, or is this the way, etc.  Guess I'll try first.:confused:

EDIT: Nope, set the env var didn't help, trying to load the generic built vboxdrv.ko didn't work either.

---

### Post by Ice_Stovo on 2008-07-22
I just uninstall VirtualBox ran 

sudo apt-get install linux-headers-`uname -r` 

and installed virtualbox again, Now everything works OK.

---

### Post by Enshin on 2008-07-24
> **Ice_Stovo said:**
> I just uninstall VirtualBox ran 

sudo apt-get install linux-headers-`uname -r` 

and installed virtualbox again, Now everything works OK.

Thanks for this post. .

Now the driver compiled..

---

### Post by Fiste788 on 2008-07-25
i solved with this command
sudo KERN_DIR=/usr/src/linux-2.6.26-k8 /etc/init.d/vboxdrv setup

---

### Post by lmcfadden on 2008-07-25
[QUOTE
Found it, but it's not installed in the correct place due to a kernel upgrade:
```

user@ubuntu:~$ uname -r
2.6.22-15-generic

```

I wasn't sure if the old existing module would still be compatible with my new kernel. Modprobe only seems to like already-installed modules, but insmod seems happy to inset the module.
```

user@ubuntu:~$ sudo insmod /lib/modules/2.6.22-14-generic/misc/vboxdrv.ko
user@ubuntu:~$ sudo /etc/init.d/vboxdrv start
 * Starting VirtualBox kernel module vboxdrv
   ...done.

```

After this, virtualbox seemed to run ok again! I would imagine that you can just copy the module to the correct place so that modprobe finds it upon bootup.[/QUOTE]

  Thanks for this, excellent tip.  I have been going through the same thing every kernel upgrade, and generally I could find a VBOX for the latest kernel in Synaptic.  I checked this time with no luck, but this article worked.

LM.

---

### Post by Dyffo on 2008-07-28
> **sonicjosh said:**
> I can not start a vm on virtualbox; I get the this error
[img]http://farm4.static.flickr.com/3003/2649716645_690c68d727_o.png[/img]

So I run it and get this
```
sonicjosh@sonicjosh-desktop-ubuntu:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                             *  done.
 * Recompiling VirtualBox kernel module                                         
 [color="red"]*[/color] Look at /var/log/vbox-install.log to find out what went wrong

```

Open that up
```
Makefile:127: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.

```

So I do that
```
sonicjosh@sonicjosh-desktop-ubuntu:~$ sudo  KERN_DIR=/boot/ /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                             *  done.
 * Recompiling VirtualBox kernel module                                         
 [COLOR="Red"]*[/COLOR] Look at /var/log/vbox-install.log to find out what went wrong

```
Get a new err
```
Makefile:154: *** Error: unable to find the include directory for your current Linux kernel. Specify KERN_INCL=<directory> and run Make again.  Stop.

```

So I basically just need to know where the KERN_INCL dir should be. I am on Ubuntu 8.04 and have not changed the kernel (e.g. it is the default kernel).
Hi did anyone resolve this problem - I am having the same - I have tried out all these suggestions - but nothing !!!

---

### Post by heatpumpcontrol on 2008-09-05
> **Ice_Stovo said:**
> I just uninstall VirtualBox ran 

sudo apt-get install linux-headers-`uname -r` 

and installed virtualbox again, Now everything works OK.

This FIXED IT!!!:popcorn:

---

### Post by ugutugut on 2008-10-16
No need to uninstall Virtualbox 
1) sudo apt-get install linux-headers-`uname -r` 
2) sudo /etc/init.d/vboxdrv setup

That's fix my problem....

---

### Post by anibalismo on 2009-09-09
Dude, got the same problem, but what i needed was:
> sudo apt-get install build-essential linux-headers-generic
and for some unknown reason, I also needed to restart my computer. That fix my problem!!!
note: this link [http://forums.virtualbox.org/viewtopic.php?f=3&t=15679](http://forums.virtualbox.org/viewtopic.php?f=3&t=15679) helpme ALOT

---

### Post by V_gra on 2009-11-26
Had the same problem; but sugestion worked out well.

No need to uninstall Virtualbox 
1) sudo apt-get install linux-headers-`uname -r` 
2) sudo /etc/init.d/vboxdrv setup

Now Vbox is runn OK Thanks to ugutugut

---

