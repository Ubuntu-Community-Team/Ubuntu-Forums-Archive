---
title: "HowTo: Installing and using KernelCheck"
date: 2007-09-21
forum: Tutorials
---

### Post by master_kernel on 2007-09-21
[FONT="Arial"]
[CENTER][[IMG]http://kcheck.sf.net/images/Lumen.png[/IMG]]("http://kcheck.sf.net")[/CENTER]

**[COLOR="Red"]NOTE: TWO CHANGES IN THE STRUCTURE OF KERNEL.ORG HAVE UNLEASHED TWO BUGS IN KERNELCHECK LUMEN. FOR THE COMPLETE PATCHED VERSION, PLEASE FOLLOW THE DEVELOPMENT METHOD STATED BELOW.[/COLOR]**

**Check out the blog: **[http://kernelcheck.blogspot.com/](http://kernelcheck.blogspot.com/)

*The purpose of this thread is to help KernelCheck users to install, use, and/or hack KernelCheck, a program written by myself. If you do not want to install KernelCheck, an automated kernel builder, please visit the [Master Kernel Thread]("http://ubuntuforums.org/showthread.php?t=311158") instead. Now, a short description. KernelCheck is a project that is designed to automatically build any 2.6 kernel from the upstream source. KernelCheck can help users fix hardware problems and improve boot time by customising the kernel configuration. KernelCheck is currently under the GNU Public License.*

Questions can also be asked via IRC on the #kernelcheck channel on irc.freenode.net or sent to [email]team-kcheck@lists.launchpad.net[/email].

KernelCheck can be used for several purposes:
[LIST=1]
[*]Fixing hardware issues
[*]Speeding up your computer with a shiny new kernel
[*]Automatically downloading, compiling, and installing the latest kernel
[/LIST]
*KernelCheck can install any stable 2.6 kernel, the latest stable patch, the latest stable development prepatch, the latest mm patch, a custom patch, or none at all. Usually the prepatch is less stable than the normal performance patch, but it is still widely used.*

**So, you want to install KernelCheck?** There are two versions available:
[LIST]
[*]Stable - 1.2.5 "Lumen"
[*]Development - 1.5.0 "Delta"
[/LIST]
*What's the difference? Well, the stable version of KernelCheck is a "tried and true" version, a version that has been tested over and over to get rid of as many bugs as possible before going public. The development version contains new features, but is often buggier than the stable version. The development installation method is the last described method on this post. Certain features may not work, such as proprietary video driver installation in the development version.*

These two methods do not work - please use the development method shown below.
[COLOR="Silver"]**_Recommended Installation Method (Stable)_**
[LIST=1]
[*]Download the Ubuntu package for KernelCheck [here]("http://sourceforge.net/project/showfiles.php?group_id=199755").
[*]Install KernelCheck
```
cd *location of package*
sudo dpkg -i kernelcheck_1.2.5-3_all.deb
```
[*]Use it: Go to *Application > System Tools > KernelCheck* and read the usage instructions below.
[/LIST]

**_Advanced/Manual Installation Method (Stable)_**
[LIST=1]
[*]Download the KernelCheck source [here]("http://sourceforge.net/project/showfiles.php?group_id=199755").
[*]Unpack the archive
```
tar -xzf kernelcheck-*.tar.gz
```
[*]Install KernelCheck
```
cd kernelcheck-*
```
```
sudo python setup.py install
```
[*]Use it
```
sudo kernelcheck
```
[/LIST][/COLOR]

**_Advanced/Manual Installation Method (Development)_**
[LIST=1]
[*]Download the KernelCheck source from LaunchPad:
```
bzr branch lp:kernelcheck
```
[*]Enter the directory:
```
cd kernelcheck
```
[*]Install KernelCheck
```
sudo python setup.py install
```
[*]Use it
```
sudo kernelcheck
```
[/LIST]

**_Usage_**
Full documentation for the stable version is available at [http://kcheck.sourceforge.net/pool/Documentation-Lumen.pdf]("http://kcheck.sourceforge.net/pool/Documentation-Lumen.pdf"). Note that usage may vary if you use the development version of KernelCheck.

KernelCheck can be opened in a variety of ways, either by going to *Application > System Tools > KernelCheck*, or by opening a terminal and typing in:
```
sudo kernelcheck
```

If you don't use sudo (or some other method of authentication, the program will show an error telling you to run it as root. If it does open, the first thing to do is download the kernel information. After doing that, the information the program shows should update.

The basic things the program will show you are:
[LIST=1]
[*]Your running kernel
[*]The latest kernel
[*]The latest kernel patch
[/LIST]

Now on to building the kernel. Under *Kernel Patch Options*, select the option that you wish to use. Unless you know what you're doing, I strongly recommend using the default selected. Under *Advanced Options*, you can choose whether you want to configure the kernel options, reconfigure the X server,  and install an nVidia module. **The nVidia option will remove any nVidia-related packages, any binary version installed, and install the latest one.** This will remove nVidia support for older kernels until you run the binary file in /usr/src with the -K option with every new kernel you use, not compiled with KernelCheck. It is strongly recommended that you configure the kernel options yourself, mainly to make sure your hardware is supported. Now to build the kernel, all you have to do is go to *Program > Build New Kernel*.

**_Hacking_**
**KernelCheck Lumen Hack #1: Change the name of the kernel**
[LIST=1]
[*]Open up a terminal and type:
```
sudo nano /usr/lib/python2.5/site-packages/KernelCheck/library/kscript.sh
```
[*]Find the line that says: KERNELNAME="Candela"
[*]Change the word "Candela" to whatever you want to name your kernel.
[*]Use CTRL+Q to quit and save the changes.
[*]Profit!
[/LIST]


[COLOR="Red"]Post your questions, comments, requests, etc. here.[/COLOR]


KernelCheck Delta is currently under active development.
[/FONT]

---

### Post by master_kernel on 2007-09-25
There number of KernelCheck downloads has doubled since I posted this topic. Thank you for your support.

---

### Post by FRuMMaGe on 2007-09-25
Compiling as I type this.

+ 1 for hacking section

What theme are you using?  The metallic black looks great on the screenshots :lolflag:

---

### Post by az_s_za on 2007-09-25
> KernelCheck is a project that is designed to easily build the latest kernel for your distribution
Sounds self-explanatory, but I have to check... can I use KernelCheck (or the instructions in your Master Kernel Thread for that matter) on a different (not Ubuntu) debian-based distro?  

I have not compiled a kernel before, but want to try this on another distro which uses an older kernel.

Thanks.

---

### Post by master_kernel on 2007-09-25
> **az_s_za said:**
> Sounds self-explanatory, but I have to check... can I use KernelCheck (or the instructions in your Master Kernel Thread for that matter) on a different (not Ubuntu) debian-based distro?  

I have not compiled a kernel before, but want to try this on another distro which uses an older kernel.

Thanks.
I don't see why not. I believe all debian-based system use APT, so it should work. However, I do not know if it will work on a RPM system, but I haven't tried.

---

### Post by master_kernel on 2007-09-25
> **FRuMMaGe said:**
> Compiling as I type this.

+ 1 for hacking section

What theme are you using?  The metallic black looks great on the screenshots :lolflag:
You're the second person to ask. I'll add which icon theme and GTK theme I'm using to the Howto.

---

### Post by az_s_za on 2007-09-28
Following the steps above, when I run kernelcheck, I get the following error message:
> Traceback (most recent call last):
  File "/usr/bin/kernelcheck-stage2", line 23, in ?
    pygtk.require('2.0')
  File "/var/lib/python-support/python2.4/pygtk.py", line 69, in require
    assert not sys.modules.has_key('gtk'), \
AssertionError: pygtk.require() must be called before importing gtk
???

---

### Post by master_kernel on 2007-09-28
Are you using Ubuntu?

It should work, this was tested on a fresh install of Feisty, and Gutsy.

However, if you continue to receive this error do the following:

Open a terminal and enter:
```
sudo gedit /usr/bin/kernelcheck-stage2
```
Find the line the reads 'pygtk.require('2.0')'
Remove that line, save, and run kernelcheck

---

### Post by master_kernel on 2007-09-29
[COLOR="Blue"]**Coming in the next release (1.0.6) of KernelCheck:**[/COLOR]

[LIST]
[*]New security update method
[*]Support for installing several proprietary drivers for the new kernel including, but not limited to:
[INDENT][LIST]
[*]FGLRX
[*]nVidia
[*]ndiswrapper
[/LIST][/INDENT]
[*]Reconfigure X Server option
[/LIST]

You can preview (test) these features in KernelCheck Codename HYDRA, KernelCheck 1.0.6 Alpha. Download it from the download page at the KernelCheck website.

[COLOR="Red"]Any requests can be posted here.[/COLOR]

---

### Post by az_s_za on 2007-09-30
No, I am compiling this new kernel for Elive (debian with Enlightenment desktop).

Since my last post, I used the instructions on your Master Kernel Thread which worked splendidly.
Thank you.

Next time I'll try kernelcheck again, using your instructions.  Thanks.

---

### Post by risidoro on 2007-10-01
Hi,
this program looks very promising and cool. I'm guessing which config is used when user press the Build Latest Kernel button. Does it run make oldconfig and then choose the defaults for the new options?

I would like the possibility to run make xconfig to customize all the options (i.e. disable generic x86 support and choose my processor family; build all the drivers i need inside the kernel instead of as modules; etc). Is it already possible to do this or can you add a small checkbox for this?

thanks, bye

---

### Post by master_kernel on 2007-10-01
> **risidoro said:**
> Hi,
this program looks very promising and cool. I'm guessing which config is used when user press the Build Latest Kernel button. Does it run make oldconfig and then choose the defaults for the new options?

I would like the possibility to run make xconfig to customize all the options (i.e. disable generic x86 support and choose my processor family; build all the drivers i need inside the kernel instead of as modules; etc). Is it already possible to do this or can you add a small checkbox for this?

thanks, bye
Hi, thank you for considering my program.

1. It does run make oldconfig, but it does not automatically choose the default options. You can choose the default options by holding down ENTER when make oldconfig is run.

2. It does automatically run make xconfig for customization.

master_kernel

---

### Post by OffHand on 2007-10-03
So your application makes and installs a deb file (kernel) which can be removed with Synaptic? It will respect the kernels that are installed already?

---

### Post by master_kernel on 2007-10-03
> **OffHand said:**
> So your application makes and install a deb file (kernel) which can be removed with Synaptic? It will respect the kernels that are installed already?
Of course! :)

master_kernel

---

### Post by risidoro on 2007-10-04
Hi Master_kernel,
can you pls tell me what's the difference between:
Latest kernel patch and Posted kernel patch? Or Latest kernel prepatch and Posted kernel prepatch? 

Actually, i've found the difference by looking in kernelcheck-stage2 file, Posted kernel is the one listed in master kernel thread, right? But i don't quite understand why this information should be useful...

Moreover: why do you compare posted kernel ver (from the forum) with latest kernel ver (from kernel.org)? Why should i need such an information?

Finally: there is a problem when you compare latest kernel ver (from kernel.org) with installed-kernel ver (with uname -r) to see whether my kernel is up to date or not: the problem is that in gutsy (at least in my system), 'uname -r' returns "2.6.22-12-generic" but the kernel version you get from kernel.org, the latest one, will never contain the tailing string '-generic' so installed kernel version and latest kernel version will never match even if my system is actually up to date. I hope i've been clear enough, my english is not so good.

Anyway, i really like your program, i hope you'll continue developing and improving it!

BTW, before i forget, add me to the list of people asking for hacking features in next version. +1 for me! :)

---

### Post by master_kernel on 2007-10-04
1. The posted kernel patch is just useless information, primarily for me to know when to update the thread. :)
2. In the next release, I will add support for parsing the 2.6.**-generic to read 2.6.**
3. There will be hacking support in the new version, codenamed HYDRA because of the many new features that will be included. This hacking support will only be available to those who put a certain file in a certain folder with a certain line in it, so others who don't want this feature will not have it.

**ANNOUNCEMENT:**
The next version of KernelCheck (Codename HYDRA) is scheduled to be released by November 1 with MANY new features. Please post any requests for HYDRA to this thread.

---

### Post by OffHand on 2007-10-04
I just used your application to build and install the latest kernel. It worked great! There we still a lot of questions which needed to be answered. Can you recommend a good guide for the options that a not answered by default?

---

### Post by master_kernel on 2007-10-04
> **OffHand said:**
> I just used your application to build and install the latest kernel. It worked great! There we still a lot of questions which needed to be answered. Can you recommend a good guide for the options that a not answered by default?
I am currently trying to find a way to eliminate those questions. You can usually press and hold Enter to select the defaults for it. Those are part of 'make oldconfig' which uses your current kernel configuration to build the new kernel. The questions to be answered are new options not specified in the old kernel. If you know a way to somehow send the 'Enter' keyboard signal to the terminal, please share it. This would be a great help.

---

### Post by risidoro on 2007-10-05
> I am currently trying to find a way to eliminate those questions. You can usually press and hold Enter to select the defaults for it.

I've found this two commands but i've not tested them:

**make silentoldconfig**  OR
**make ARCH=i386 nonint_oldconfig**

----

A good addition to your next version would be this script i've found on kernel mailing list: [http://www.ussg.iu.edu/hypermail/linux/kernel/0503.1/1248.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0503.1/1248.html)

The script will automatically disable in the config all the drivers that you're currently not using. To do so it checks the loaded modules (lsmod) and then disable in the confg all the modules that are not loaded in the pc (probably because they're not needed).

With a little change to the perl code you can have a even more useful feature: you set the config so that all the modules you're currently using (lsmod) will be compiled inside the kernel instead of as modules. Usually this is what i manually do when i compile a new kernel: i include all the drivers i need inside the kernel and not as modules.

Bye

---

### Post by master_kernel on 2007-10-07
> **risidoro said:**
> I've found this two commands but i've not tested them:

**make silentoldconfig**  OR
**make ARCH=i386 nonint_oldconfig**

----

A good addition to your next version would be this script i've found on kernel mailing list: [http://www.ussg.iu.edu/hypermail/linux/kernel/0503.1/1248.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0503.1/1248.html)

The script will automatically disable in the config all the drivers that you're currently not using. To do so it checks the loaded modules (lsmod) and then disable in the confg all the modules that are not loaded in the pc (probably because they're not needed).

With a little change to the perl code you can have a even more useful feature: you set the config so that all the modules you're currently using (lsmod) will be compiled inside the kernel instead of as modules. Usually this is what i manually do when i compile a new kernel: i include all the drivers i need inside the kernel and not as modules.

Bye
Wow! This was a great help! I'll test out the make silentoldconfig later, and if it works, I'll include in the HYDRA release. I might add an option to use the script you mentioned if that works too. The downside of this is that if you need hardware support later that is not compiled into the kernel, it won't work. I'll have to do some playing around since I don't know PERL.

Thank you!
master_kernel

---

### Post by OffHand on 2007-10-08
> **master_kernel said:**
> Wow! This was a great help! I'll test out the make silentoldconfig later, and if it works, I'll include in the HYDRA release. I might add an option to use the script you mentioned if that works too. The downside of this is that if you need hardware support later that is not compiled into the kernel, it won't work. I'll have to do some playing around since I don't know PERL.

Thank you!
master_kernel

Might want to make silent mode optional then....

---

### Post by master_kernel on 2007-10-08
> **OffHand said:**
> Might want to make silent mode optional then....
Of course, if it works.

---

### Post by pek on 2007-10-10
download of the latest kernel source fails. if i download manually it works. is there a way to tell this program to use the sources i have downloaded if the versions are the same?

---

### Post by master_kernel on 2007-10-10
> **pek said:**
> download of the latest kernel source fails. if i download manually it works. is there a way to tell this program to use the sources i have downloaded if the versions are the same?
It works for me running KernelCheck 1.0.5. Can you post the output of the program? It may have something to do with the latest kernel release.

---

### Post by master_kernel on 2007-10-10
I ran into a wall with the development KernelCheck. Apparently, the fglrx-kernel-source package in the Ubuntu Gutsy repo has a different filename than the onee in Feisty. Any help in resolving this is appreciated.

---

### Post by plun on 2007-10-11
Thanks for this script...:)

Hydra is up and running and Gutsy seems to have late trouble with
its kernel...  Hydra is a Ferrari... :)

-Free disk space must be included or written in the script, as I can see
at least 2.5 GB is needed.

- nVidia driver was broken...I must manually install it.

plun@dunder:~$ uname -r
2.6.23-hydra

:)

---

### Post by master_kernel on 2007-10-13
> **plun said:**
> Thanks for this script...:)

Hydra is up and running and Gutsy seems to have late trouble with
its kernel...  Hydra is a Ferrari... :)

-Free disk space must be included or written in the script, as I can see
at least 2.5 GB is needed.

- nVidia driver was broken...I must manually install it.

plun@dunder:~$ uname -r
2.6.23-hydra

:)

I'm working on the nVidia and ATi drivers... since I don't have an nVidia machine I will need testers. You're right about the disk space: I'll try to add something to the script. Thanks for using KernelCheck!

---

### Post by Frak on 2007-10-14
Thanks for this, its teh roxxors\\:D/

:lolflag:

---

### Post by jaeqladore on 2007-10-14
Hi!

I just installed KernelCheck 1.0.5 on Kubuntu Feisty following this howto, but when it starts it skips the dialog box  and i receive the following error:

> /usr/bin/kernelcheck: line 434: zenity: command not found

After this the program runs, connects to the internet and diplays the appropriate information about the kernels. However, it doesn't diplay the new kernel options.

Can anyone tell me what this means? Thanks!

---

### Post by Frak on 2007-10-14
> **jaeqladore said:**
> Hi!

I just installed KernelCheck 1.0.5 on Kubuntu Feisty following this howto, but when it starts it skips the dialog box  and i receive the following error:



After this the program runs, connects to the internet and diplays the appropriate information about the kernels. However, it doesn't diplay the new kernel options.

Can anyone tell me what this means? Thanks!
```
sudo aptitude install zenity
```

---

### Post by jaeqladore on 2007-10-15
I figured it was someting obvious that i had missed :D

So, I installed zenity and KernelCheck boots up without errors. It still doesn't diplay the kernel options choice, but i just noticed that there's no prepatch found so I suppose that's why.

I'm still quite new to linux when it comes to all this kernel-stuff but i'm slowly learning... (i hope) :) Thanks for the help Frak!

---

### Post by plun on 2007-10-15
> **master_kernel said:**
> I'm working on the nVidia and ATi drivers... since I don't have an nVidia machine I will need testers. You're right about the disk space: I'll try to add something to the script. Thanks for using KernelCheck!

OK...great little application, I switched to Debian Sid and it works nicely..:)

2.6.23-1-hydra is running, magic speed also with all "bling" running. 

Thanks !

Just make a note if nVidia testers are needed...

---

### Post by master_kernel on 2007-10-15
**KernelCheck HYDRA Beta is scheduled to be released by Friday, October 19, 2007.**

There will be major changes in this version, and it will be the first version where _beta testers will be needed_. There will be a separate thread for the beta testers, and the link will be posted on the main post and the webpage. Any suggestions for HYDRA must be submitted by Wednesday, October 17, 2007.

---

### Post by colo505 on 2007-10-16
If for any reason you wish to uninstall, how do you do it?

---

### Post by OffHand on 2007-10-16
> **colo505 said:**
> If for any reason you wish to uninstall, how do you do it?

The application or the kernel?

---

### Post by colo505 on 2007-10-16
the kernel

---

### Post by OffHand on 2007-10-16
> **colo505 said:**
> the kernel

Launch synaptic package manager and do a search for 'linux image'. Find the latest kernel and uninstall it.

---

### Post by Frak on 2007-10-16
> **OffHand said:**
> Launch synaptic package manager and do a search for 'linux image'. Find the latest kernel and uninstall it.
I think you mean, find the latest kernel and **install** it. It will then overwrite the one you installed.

EDIT
Also, to the OP Master_Kernel, you need to list [xterm]("apt:xterm") as a dependency.

---

### Post by master_kernel on 2007-10-16
> **Frak said:**
> I think you mean, find the latest kernel and **install** it. It will then overwrite the one you installed.

EDIT
Also, to the OP Master_Kernel, you need to list [xterm]("apt:xterm") as a dependency.
Thanks, I forgot about this. It will be added in the next release. I am currently debating what the HYDRA release will be: 1.0.6 or 1.1.0. It will be a great milestone for KernelCheck. All the kernels built with it will be 2.6.xx.xx-hydra. I never did find a way to silently make oldconfig, so I guess it won't be included. The speed of information retrieval will also be improved--a whopping 1 second (cable/dsl) versus the old 10 seconds (partly due to the removal of Master Kernel Thread information).

---

### Post by Sayers on 2007-10-16
You should change to the menu, this yes no thing is very annoying.

---

### Post by aktiwers on 2007-10-16
Very Nice work! 
+1 for the hacking part :)

---

### Post by Faer on 2007-10-17
I've come across a snag when attempting to build the latest kernel with KernelCheck. As it doesn't want to let me copy and paste the exact log of what it was doing (or maybe it would if I wasn't such a newbie :P), I'll do my best to explain the problem in as concise a manner as possible.

```
KernelCheck starts installing the latest dependencies.
<long list of Hit's and Ign's here>
KernelCheck finishes reading package lists.
E: Some index files failed to download, they have been ignored, or old ones were used instead.
Unkown Error. Aborting now.
```

And that's all she wrote. KernelCheck is up to date, and doesn't have any issues until I attempt to build the latest kernel. I'm running the 64bit Feisty Fawn release, with an AMD64 4200+ X2 CPU, an nVidia card, and installed KernelCheck from the terminal (no idea if all that information is relevant, but I figured I'd provide it just in case).

EDIT: I've started compiling the kernel manually via the directions in the Master Kernel Thread (awesome resource), and everything is going fine so far. Maybe it's just a problem with the way I installed KernelCheck.

---

### Post by OffHand on 2007-10-17
You might want to implement that KernelCheck cleans up the source after it has been compiled. It takes up a lot of space and most people do not have a huge /

---

### Post by Sunflower1970 on 2007-10-17
This is a great program. Thanks for writing it :D

Installed my very first compiled kernel this morning.

---

### Post by master_kernel on 2007-10-17
> **Sayers said:**
> You should change to the menu, this yes no thing is very annoying.
What do you mean?

---

### Post by master_kernel on 2007-10-17
> **Faer said:**
> I've come across a snag when attempting to build the latest kernel with KernelCheck. As it doesn't want to let me copy and paste the exact log of what it was doing (or maybe it would if I wasn't such a newbie :P), I'll do my best to explain the problem in as concise a manner as possible.

```
KernelCheck starts installing the latest dependencies.
<long list of Hit's and Ign's here>
KernelCheck finishes reading package lists.
E: Some index files failed to download, they have been ignored, or old ones were used instead.
Unkown Error. Aborting now.
```

And that's all she wrote. KernelCheck is up to date, and doesn't have any issues until I attempt to build the latest kernel. I'm running the 64bit Feisty Fawn release, with an AMD64 4200+ X2 CPU, an nVidia card, and installed KernelCheck from the terminal (no idea if all that information is relevant, but I figured I'd provide it just in case).

EDIT: I've started compiling the kernel manually via the directions in the Master Kernel Thread (awesome resource), and everything is going fine so far. Maybe it's just a problem with the way I installed KernelCheck.
The problem is that one of the repositories in your /etc/apt/sources.list is not working. Remove this bad entry and try it again. This error comes up because KernelCheck checks to see if there was an error with one command before it goes on to the next one. There is a way to hack around this, I can give it to you if you want it.

---

### Post by master_kernel on 2007-10-17
> **OffHand said:**
> You might want to implement that KernelCheck cleans up the source after it has been compiled. It takes up a lot of space and most people do not have a huge /
I think I'll add this as an option in HYDRA.

---

### Post by barbro on 2007-10-20
I tried compile the kernel with ipw2200 i followed ipw2000 guide ([http://ubuntuforums.org/showthread.php?p=2599422&highlight=ipw2200#post2599422](http://ubuntuforums.org/showthread.php?p=2599422&highlight=ipw2200#post2599422)). 
I used  (firmware version 3.0).
when i boot with 2.6.23.1 i get the following error;

ipw2200: ipw2200:bss-fw request_firmware failed: Reason -2
ipw2200: Unable to load firmware: -2
ipw2200: failed to register network device

Anyone else noticed this problem? Any solution?

and when boot is ready i try to do sudo modprobe ipw2200 i get: FATAL: Module ipw220 not found?
how come? I know i compiled kernel with ipw2200 and put the fireware in /lib/firmware/2.6.23.1/

---

### Post by ravenon on 2007-10-21
I have compiled a custom kernel using KernelCheck (2.6.23) and using the process described on the Master Kernel thread (2.6.22) and am running Gutsy. My reason to turning to a custom built kernel is that in Gutsy, the developers decided to switch to the SLUB allocator, SLAB was used in the past. I have a laptop with ATI 200 Express chipset and X700 graphics card, hence must us the proprietary fglrx drivers for functional use. However, with SLUB a bug appears in these drivers; the machine will no longer suspend or hibernate. This is described in Launchpad bug [https://bugs.launchpad.net/bugs/121653](https://bugs.launchpad.net/bugs/121653)

So building a custom kernel with SLAB, I then build the fglrx kernel module and poof, suspend and resume work again as they did in Fiesty.

Now the glitch. My laptop uses Intel Pro 3945 wireless card and the driver for that is provided by Ubuntu as a kernel module in the package linux-ubuntu-modules. My question is if I ge the source for this package, if there a way to build this module as I build the kernel? Or, should I use the source code for iwp3945 with module assistant and build the module? Whats the best approach?

---

### Post by master_kernel on 2007-10-21
> **ravenon said:**
> I have compiled a custom kernel using KernelCheck (2.6.23) and using the process described on the Master Kernel thread (2.6.22) and am running Gutsy. My reason to turning to a custom built kernel is that in Gutsy, the developers decided to switch to the SLUB allocator, SLAB was used in the past. I have a laptop with ATI 200 Express chipset and X700 graphics card, hence must us the proprietary fglrx drivers for functional use. However, with SLUB a bug appears in these drivers; the machine will no longer suspend or hibernate. This is described in Launchpad bug [https://bugs.launchpad.net/bugs/121653](https://bugs.launchpad.net/bugs/121653)

So building a custom kernel with SLAB, I then build the fglrx kernel module and poof, suspend and resume work again as they did in Fiesty.

Now the glitch. My laptop uses Intel Pro 3945 wireless card and the driver for that is provided by Ubuntu as a kernel module in the package linux-ubuntu-modules. My question is if I ge the source for this package, if there a way to build this module as I build the kernel? Or, should I use the source code for iwp3945 with module assistant and build the module? Whats the best approach?
I know that there are patches for this, but there may be an easier approach. I downloaded the source for linux-ubuntu-modules and when I untar-ed it I saw a ubuntu-firmware directory. I think if you copy the contents of the ipw3495 firmware folder to /lib/firmware/2.6.23/ the kernel should detect the firmware on reboot.

Hope this works!
master_kernel

---

### Post by master_kernel on 2007-10-21
> **barbro said:**
> I tried compile the kernel with ipw2200 i followed ipw2000 guide ([http://ubuntuforums.org/showthread.php?p=2599422&highlight=ipw2200#post2599422](http://ubuntuforums.org/showthread.php?p=2599422&highlight=ipw2200#post2599422)). 
I used  (firmware version 3.0).
when i boot with 2.6.23.1 i get the following error;

ipw2200: ipw2200:bss-fw request_firmware failed: Reason -2
ipw2200: Unable to load firmware: -2
ipw2200: failed to register network device

Anyone else noticed this problem? Any solution?

and when boot is ready i try to do sudo modprobe ipw2200 i get: FATAL: Module ipw220 not found?
how come? I know i compiled kernel with ipw2200 and put the fireware in /lib/firmware/2.6.23.1/
Odd. These wireless problems are popping up all over the place now because the mainstream kernel has switched wireless configurations. Try searching (ctrl +f) in the xconfig for ipw2200 and check anything that comes up. I don't know if this will work, but it's a start.

---

### Post by master_kernel on 2007-10-24
**MAJOR NOTE**: KERNELCHECK DEVELOPMENT WITH INCLUSION OF PROPRIETARY DRIVERS HAS COME TO A HALT WITH BECAUSE OF THE NEW API IN THE 2.6.23 KERNEL. THIS KERNEL CONTAINS TWO MAJOR CHANGES THAT PREVENT THE PROGRAM TO FUNCTION WITHOUT THE USE OF KERNEL PATCHES. BECAUSE OF THIS, THE RELEASE OF KERNELCHECK IS UNDECIDED. THE SCHEDULED RELEASE FOR NOVEMBER 7, 2007 IS NOW INVALID. THOUGH THIS MAY BE SO, KERNELCHECK HYDRA BETA IS STILL ON SCHEDULE FOR ITS RELEASE TODAY. THE CHANGES TO THE SCRIPT WITH THE INCLUSION OF PATCHES WILL BE INTEGRATED ASAP.

Sorry for the inconvenience.
master_kernel

---

### Post by Frak on 2007-10-24
Thanks for the notice :)

I am really starting to dislike all the big changes to the kernel though, a little heads up (some three months) warning from the kernel devs would be great. I'm going to suggest it on the mailing list.

---

### Post by master_kernel on 2007-10-24
> **Frak said:**
> Thanks for the notice :)

I am really starting to dislike all the big changes to the kernel though, a little heads up (some three months) warning from the kernel devs would be great. I'm going to suggest it on the mailing list.
I agree. There are two major changes in the 2.6.23 kernel ABI that do not allow some proprietary video drivers to be compiled into the kernel (including mine!). Looks like I'll have to check how the Ubuntu team works around this problem.

---

### Post by rustybronco on 2007-10-26
What the heck... i've got a spare h.d., a 7.10 iso and they released 2.6.24 rc1, time to give kernel check a go!

---

### Post by master_kernel on 2007-10-29
This would be an option... but the ck patchset ended with the 2.6.22 kernel. Maybe I'll add support for the kamikaze patchset.

---

### Post by master_kernel on 2007-10-29
Good news for fglrx(at least on 64bit)! I have found 3 patches that work together to help the driver compile into the kernel!

---

### Post by DemonBob on 2007-11-11
How about support for the -mm patch. Also was wondering does it copy your current .config to the new kernel and loads it by defualt, for the xconfig

---

### Post by master_kernel on 2007-11-11
> **DemonBob said:**
> How about support for the -mm patch. Also was wondering does it copy your current .config to the new kernel and loads it by defualt, for the xconfig
It does copy the config to the new kernel for default. I will add support for mm patches to HYDRA.

Thanks for your support,
master_kernel

---

### Post by master_kernel on 2007-11-11
If you would like to see a screenshot preview of KernelCheck HYDRA, just say the word. I'm still working on the nVidia drivers. If you can offer any help with this, please contact me.

---

### Post by master_kernel on 2007-11-11
**[COLOR="Blue"]Features to be included in KernelCheck 1.1.0 HYDRA:[/COLOR]**
[SIZE="2"]*[COLOR="Orange"]As of 11/11/2007, straight from the changelog[/COLOR]*[/SIZE]

[LIST]
[*]Added radio buttons for selecting patch
[*]Added mm patch support***
[*]Added more signal trapping to Python script
[*]Added error identification to script
[*]Added KernelCheck to Applications > System [Tools] and icon
[*]Added help option to script, and majorly updated script
[*]Added Master Kernel Thread button
[*]Added to running kernel checker so 2.6.xx-xxxx is recognized
[*]Added caching support to GREATLY enhance speed (~1.5 sec. vs. ~10 sec. for Cable/DSL)***
[*]Added support for installing the fglrx driver 8.40.1***
[*]Added support for installing the nVidia driver (not legacy)***
[*]Added support for reconfiguring the x server***
[*]Switched internet servers for kernel.org and ubuntuforums.org to speed up script
[*]New, improved, VERY fast network test (thanks to walkerk)
[*]Changed variable names for better understanding
[/LIST]
*** - Feature requests integrated

[COLOR="Red"]
Your opinion matters! Test the new KernelCheck HYDRA Beta and help support KernelCheck![/COLOR]

---

### Post by DemonBob on 2007-11-12
Let me know where to get the latest version. I have a vm i can test it on, and a laptop.

---

### Post by master_kernel on 2007-11-12
[CENTER]**[COLOR="RoyalBlue"]Mini HOWTO: Install KernelCheck Testing versions[/COLOR]**
*Use these versions at your own risk. They may or may not work.*[/CENTER]

[LIST=1]
[*]Download KernelCheck Testing
```
wget http://kcheck.sourceforge.net/pool/testing-git/kernelcheck-testing.tar.gz
```
[*]Untar the archive
```
tar -xzf kernelcheck-testing.tar.gz
```
[*]Install KernelCheck Testing
```
cd kernelcheck-testing && sudo python setup.py install
```
[*]Run KernelCheck Testing
```
kernelcheck
```
OR
Menu [Bar] > Applications > System Tools > KernelCheck
[*][COLOR="Red"]Post feedback at this thread[/COLOR]
[/LIST]

---

### Post by master_kernel on 2007-11-12
**KernelCheck is in dire need of a logo. If you can help, please contact me.**

---

### Post by DemonBob on 2007-11-12
Ran the instructions above, ran kernelcheck. It will not build selecting any patch. It seems to not even attempt to build, not poping up an xterm window at all. 

Running: 2.6.22-14-generic, Clean install

Laptop: Acer Aspire 5315

---

### Post by funpop on 2007-11-13
hey master kernel!

just want to say thanks for your work! kernelcheck 1.05 worked great with gutsy, in the qtconfig i just changed some stuff like selecting my cpu, that 1000 hz latency (?), disabled some stuff i dont need like wireless. for the nvidia drivers i just used the envy script.

kernelcheck and envy create debs, so its easy to manage those.

im not sure if my desktop is now snappier of faster, might be placebo effect :)

but i got rid of an old annoyance: when i play openarena and amarok switches the track in the background the game was hanging for ~3 seconds. now it doesnt do that anymore, which is great. i think the CFS of 2.6.23 cured this problem :popcorn:

---

### Post by master_kernel on 2007-11-13
> **DemonBob said:**
> Ran the instructions above, ran kernelcheck. It will not build selecting any patch. It seems to not even attempt to build, not poping up an xterm window at all. 

Running: 2.6.22-14-generic, Clean install

Laptop: Acer Aspire 5315
Bug fixed. Thanks for the notice.

---

### Post by master_kernel on 2007-11-13
> **funpop said:**
> hey master kernel!

just want to say thanks for your work! kernelcheck 1.05 worked great with gutsy, in the qtconfig i just changed some stuff like selecting my cpu, that 1000 hz latency (?), disabled some stuff i dont need like wireless. for the nvidia drivers i just used the envy script.

kernelcheck and envy create debs, so its easy to manage those.

im not sure if my desktop is now snappier of faster, might be placebo effect :)

but i got rid of an old annoyance: when i play openarena and amarok switches the track in the background the game was hanging for ~3 seconds. now it doesnt do that anymore, which is great. i think the CFS of 2.6.23 cured this problem :popcorn:
You're welcome. I'm glad to know my work is appreciated.

master_kernel

---

### Post by lime4x4 on 2007-11-13
this is the error i'm getting with the latest version (hydra). I'm running gutsy by the way

john@john-feisty:~$ kernelcheck

Initiating KernelCheck Codename HYDRA
Success.


Testing your network connection...
Test was successful, you are connected to the internet

Begin data retrival. Please be patient as this may take some time.
Traceback (most recent call last):
  File "/usr/bin/kernelcheck-stage2", line 942, in <module>
    KernelCheck()
  File "/usr/bin/kernelcheck-stage2", line 694, in __init__
    label.set_text("Latest Kamikaze patchset: "+km_releasedate)
NameError: global name 'km_releasedate' is not defined
john@john-feisty:~$

---

### Post by master_kernel on 2007-11-13
> **lime4x4 said:**
> this is the error i'm getting with the latest version (hydra). I'm running gutsy by the way

john@john-feisty:~$ kernelcheck

Initiating KernelCheck Codename HYDRA
Success.


Testing your network connection...
Test was successful, you are connected to the internet

Begin data retrival. Please be patient as this may take some time.
Traceback (most recent call last):
  File "/usr/bin/kernelcheck-stage2", line 942, in <module>
    KernelCheck()
  File "/usr/bin/kernelcheck-stage2", line 694, in __init__
    label.set_text("Latest Kamikaze patchset: "+km_releasedate)
NameError: global name 'km_releasedate' is not defined
john@john-feisty:~$
Fixed. The current version of HYDRA is extremely unstable. I have started massive work with the patches, and currently kamikaze is broken. Tomorrow at the end of the day it should be reletively stable. I have not tested the HYDRA release since I changed the patches around.

master_kernel

---

### Post by DemonBob on 2007-11-14
Latest Build: 

MM Patch might be a problem. When i select it to build, it pulles in the latest version witch is for the 2.6.24 Kernel, but it pulls in the stable kernel 6.2.23, and tryes to build againts that. It either needs to automaticly download the latest 2.6.24 or (which i know my be more difficult) have an options for 

Build MM against latest prepatch kernel
Build MM against latest stable kernel. 

I also suggest that since this is a "beta" running the script command first before all the other xterm get/building is initiated, saving the file to ~home directory, or tmp. at the end kill the script, be easier to see where it screwed up, in case the xterm window closes out.

Thanks
DemonBob.

---

### Post by master_kernel on 2007-11-14
> **DemonBob said:**
> Latest Build: 

MM Patch might be a problem. When i select it to build, it pulles in the latest version witch is for the 2.6.24 Kernel, but it pulls in the stable kernel 6.2.23, and tryes to build againts that. It either needs to automaticly download the latest 2.6.24 or (which i know my be more difficult) have an options for 

Build MM against latest prepatch kernel
Build MM against latest stable kernel. 

I also suggest that since this is a "beta" running the script command first before all the other xterm get/building is initiated, saving the file to ~home directory, or tmp. at the end kill the script, be easier to see where it screwed up, in case the xterm window closes out.

Thanks
DemonBob.
I have to figure out a way to program this. It might take a few days...

For now the mm and kamikaze patches don't work.

---

### Post by master_kernel on 2007-11-14
ANNOUNCEMENT: Kamikaze patchset works and is in KernelCheck HYDRA.

---

### Post by corbcox on 2007-11-15
I successfully compiled a new kernel utilizing the kamikaze patch. A big improvement over the gutsy kernel I was using.   A thousand thanks for the work that you do.

---

### Post by master_kernel on 2007-11-15
> **corbcox said:**
> I successfully compiled a new kernel utilizing the kamikaze patch. A big improvement over the gutsy kernel I was using.   A thousand thanks for the work that you do.
Always glad to hear from a happy user. Glad to know my work is appreciated.

master_kernel

---

### Post by colo505 on 2007-11-15
> **corbcox said:**
> I successfully compiled a new kernel utilizing the kamikaze patch. A big improvement over the gutsy kernel I was using.   A thousand thanks for the work that you do.

Can you post a step-by-step how to? Thanks

---

### Post by jaakan on 2007-11-16
a command line version of Kernelcheck would be nice.or even a boot disc version for cases like what i'm and a lot of people are running in to where we'd like to try a newer kernel but our system has a good case of locking up before the new kernel will even finsh compiling running under the 2.6.22 kernel.

[http://ubuntuforums.org/showthread.php?p=3782362&posted=1#post3782362](http://ubuntuforums.org/showthread.php?p=3782362&posted=1#post3782362)

the main screen is too long, if someone boots up with 800x600 vesa driver they can't even click the build kernel build on the beta

---

### Post by aldeby on 2007-11-16
I just wanted to drop a thank you to the developer of KernelCheck, since it is really a very easy-to-use script which eases a lot the process of upgrading a kernel. Thank you!

As a side note like jaakan said the main windows of the development branch of KernelCheck is a bit too long and needs a vertical scrollbar. In my widescreen with 800pt vertical I barely see the "check for updates" button. 
Also if one has issues with accelerated drivers and the screen falls back to low-res mode the application becomes unusable.

---

### Post by DemonBob on 2007-11-16
I agree that something needs to be done. When i was testing it on my virtual machines, i had the same issues, the resolution would only go up to 800x600 at the time. Which meant the last three buttons were cut off. I did a little photoshop mock up, of how this problem could be resolved, and still have room to grow with out going to "page" type program. 
[IMG]http://systemoverload.net/images/Screenshot-Kernel-Information-Test.png[/IMG]

---

### Post by master_kernel on 2007-11-16
> **aldeby said:**
> I just wanted to drop a thank you to the developer of KernelCheck, since it is really a very easy-to-use script which eases a lot the process of upgrading a kernel. Thank you!

As a side note like jaakan said the main windows of the development branch of KernelCheck is a bit too long and needs a vertical scrollbar. In my widescreen with 800pt vertical I barely see the "check for updates" button. 
Also if one has issues with accelerated drivers and the screen falls back to low-res mode the application becomes unusable.
I'll try to add the scrollbar; no guarantees though.

---

### Post by lime4x4 on 2007-11-16
I tried it and still getting the same error i redownloaded it as posted in your prior thread
 wget [http://kcheck.sourceforge.net/pool/testing-git/kernelcheck-testing.tar.gz](http://kcheck.sourceforge.net/pool/testing-git/kernelcheck-testing.tar.gz)

john@john-feisty:~/kernelcheck-testing$ kernelcheck

Initiating KernelCheck Codename HYDRA
Success.


Testing your network connection...
Test was successful, you are connected to the internet

Begin data retrival. Please be patient as this may take some time.
Traceback (most recent call last):
  File "/usr/bin/kernelcheck-stage2", line 942, in <module>
    KernelCheck()
  File "/usr/bin/kernelcheck-stage2", line 694, in __init__
    label.set_text("Latest Kamikaze patchset: "+km_releasedate)
NameError: global name 'km_releasedate' is not defined
john@john-feisty:~/kernelcheck-testing$

---

### Post by corbcox on 2007-11-16
> **colo505 said:**
> Can you post a step-by-step how to? Thanks

The KernelCheck Hydra program did all the work for me.  I just selected the Kamakize patch and followed the prompts.  I have followed Master Kernels thread over the past few months and have made several kernels.  I have also had several failures but that is the fun of it.  Gutsy is so stable it is almost boring. (Haven't broke it in over a week)

---

### Post by plun on 2007-11-18
Using Kernelcheck Beta and installed prepatch RC3

Works just fine....:)

Virtualbox refuses to build a new driver  :confused:

```
Makefile:76: *** Error: /usr/src/linux (version 2.6.24-rc3) does not match the current kernel (version 2.6.24-rc3-greenhydra).  Stop.
```

Where comes "greenhydra" from... ?

Also is it possible to use more then 1 patch...  prepatch and Kamikaze for example.

Thanks !

---

### Post by n00bek on 2007-11-18
i need install linux-restricted-modules-2.6.23.8-greenhydra. How build this?

---

### Post by master_kernel on 2007-11-18
> **n00bek said:**
> i need install linux-restricted-modules-2.6.23.8-greenhydra. How build this?
I tested the new version I just uploaded and it works fine.

---

### Post by master_kernel on 2007-11-18
> **n00bek said:**
> i need install linux-restricted-modules-2.6.23.8-greenhydra. How build this?
You have to compile the restricted mods yourself. I hope to implement an auto-build of this by KC2.

---

### Post by master_kernel on 2007-11-18
> **plun said:**
> Using Kernelcheck Beta and installed prepatch RC3

Works just fine....:)

Virtualbox refuses to build a new driver  :confused:

```
Makefile:76: *** Error: /usr/src/linux (version 2.6.24-rc3) does not match the current kernel (version 2.6.24-rc3-greenhydra).  Stop.
```

Where comes "greenhydra" from... ?

Also is it possible to use more then 1 patch...  prepatch and Kamikaze for example.

Thanks !
It is, but I doubt I'll have that in by HYDRA on Dec. 1. I'll try to do that by 1.1.1 sometime around Christmas. I'm still having problems with the proprietary drivers and the mm patch.

---

### Post by kalpik on 2007-11-18
> **master_kernel said:**
> You have to compile the restricted mods yourself. I hope to implement an auto-build of this by KC2.
How to build those?

BTW, a BIG thanks for kernelcheck. Just built myself 2.6.23.8 :)

---

### Post by tarasbulba on 2007-11-19
Hi. I have installed kernelcheck on kubuntu 7.10, but i couldn't get it to work.When i selected apply normal patch, reconfigure x server,nVidia option and pressed built latest kernel and pressed ok button but nothing happens.Console says:
> Panic option passed, attempt safe halt...
Exiting.

Please help...

---

### Post by kalpik on 2007-11-19
Even I had the same problem.. First select any of the options, other than normal patch (the recommended one) then select back the recommended one, then press build kernel. Then it will start.. And you dont have to press OK..

---

### Post by tarasbulba on 2007-11-19
Thank you very mush this did the trick :D

---

### Post by master_kernel on 2007-11-19
> **tarasbulba said:**
> Thank you very mush this did the trick :D
Hmmm... odd. Are you using 1.0.5? I would very much like to reproduce this error so I can fix it.

---

### Post by master_kernel on 2007-11-19
**ANNOUNCEMENT:** Vote for the KernelCheck logo here: [http://ubuntuforums.org/showthread.php?t=617680](http://ubuntuforums.org/showthread.php?t=617680)

---

### Post by kalpik on 2007-11-19
> Hmmm... odd. Are you using 1.0.5? I would very much like to reproduce this error so I can fix it.
Im on hydra.. And the same thing happens to me too.

---

### Post by tarasbulba on 2007-11-20
I have the same issue on both stable version of kernelcheck and Hydra.Thanks to kalpik, saved my life :)

---

### Post by master_kernel on 2007-11-20
Thank you, aysiu.

OK, now that KC is separated again, I need to find out why you're having that error with HYDRA.

---

### Post by Billy_McBong on 2007-11-20
kernelcheck.is awesome

but sound doesn't work, it says cant find GStreamer plugins
EDIT:fixed it, just had to enable the HD sound

---

### Post by funpop on 2007-11-21
i used kernelcheck 1.0.5 and im happy with my new kernel as i told here before.
but now i have only 400 mb left on my / partition.

would you please  explain, how to remove the unnecessary files left from compilation ? (sources or whatever)

michael

---

### Post by fatmcgav on 2007-11-22
HI there, 

I'm having some issues with the latest KCheck version...

When I try to build the latest prepatch kernel and compile nvidia, it gives me the following error when trying to configure Xserver during Nvidia compile...
> /usr/*bin/kernelcheck: line 348: 11997 Segmentation fault	(core dumped) sudo nvidia-xconfig

Any ideas?

Cheers
Gavin W

---

### Post by Maulwuff on 2007-11-22
tried to build a 23 kernel with:
 normal performance patch
reconfigure x-server
build nvidia

and it gives me this during install of the nvidia driver:
/usr/bin/kernelcheck: 348 : 8989 segmentation fault (core dumped). sudo nvidia-xconfig

hmmm it's going on. pressed enter once in console, then the ok button was enabled in the small nvidia window, now it is downloading the kernel src.

I don't think this will be of any success?

---

### Post by fatmcgav on 2007-11-23
> **Maulwuff said:**
> tried to build a 23 kernel with:
 normal performance patch
reconfigure x-server
build nvidia

and it gives me this during install of the nvidia driver:
/usr/bin/kernelcheck: 348 : 8989 segmentation fault (core dumped). sudo nvidia-xconfig

hmmm it's going on. pressed enter once in console, then the ok button was enabled in the small nvidia window, now it is downloading the kernel src.

I don't think this will be of any success?
No, it builds the kernel and appears to work fine, but when it boots in, the nvidia drivers aren't being used, and get the following error when trying to use restricted drivers manager... > "You need to install: 
Linux-restricted-modules-2.6.23.8-greenhydra
for this program to work" 

Any ideas people???

Cheers
Gav

---

### Post by Maulwuff on 2007-11-23
seems as there is a bug in hydra: if I don't recheck the options  to compile with (ie. compile with recommended patch), building won't start.


hint: don't download the src everytime a build is started. check wether it is present already.

It finally compiled the greenhydra-kernel.
At the end I got stuck with a full /boot -partition and kernelcheck went on as if everything went well.
see attached screenshot. (I don't know how to copy text out of the kernelcheck console)

---

### Post by Benji86 on 2007-11-23
I'm having the same porblem than Maulwuff. It'started after updating KernelCheck :S

---

### Post by elec999 on 2007-11-24
Same problem here. Linux-restricted-modules needed.
Thanks

---

### Post by master_kernel on 2007-11-25
Right now the nvidia driver option does not work. I will fix this by the mainstream release next week. You get the restricted driver error because it needs the nvidia driver.

Note: the mm- patchset will not be included in the HYDRA release due to time restrictions.

---

### Post by funpop on 2007-11-26
probably you missed my post..

my root partition went down from ~ 1,8 gig to 800 mb free disk space. could you please explain how to free up some space again ? cant imagine that the new kernel needs the 1 gig it took away..

---

### Post by master_kernel on 2007-11-26
> **funpop said:**
> probably you missed my post..

my root partition went down from ~ 1,8 gig to 800 mb free disk space. could you please explain how to free up some space again ? cant imagine that the new kernel needs the 1 gig it took away..
Sorry, I did miss your post.

Usually compiling the kernel takes up 3G, so you must be lucky :).

Anyway, there isn't much you can delete, except for /usr/src/linux-VERSION (i.e. /usr/src/linux-2.6.24-rc3). That should free up some space.

master_kernel

---

### Post by master_kernel on 2007-11-26
Well, lucky me. This is setback #15. The kamikaze patchset has been discontinued. This may affect the release date of KC significantly.

EDIT: The Zen project has replaced Kamikaze. These patches will be integrated into KernelCheck. The earliest release date for KernelCheck HYDRA will be a week after the stable release of the 2.6.24 kernel.

master_kernel

---

### Post by master_kernel on 2007-11-26
KernelCheck has a new face! The winning logo has been attached.

---

### Post by master_kernel on 2007-11-26
> **Billy_McBong said:**
> kernelcheck.is awesome

but sound doesn't work, it says cant find GStreamer plugins
EDIT:fixed it, just had to enable the HD sound
Yeah, it took me a while to figure this out.

---

### Post by kalpik on 2007-11-27
Just one suggestion, why dont you use "wget -c" instead of plain "wget" inside your script? That way we wont have to re-download the entire kernel source again if we just need to apply a new patch!

---

### Post by master_kernel on 2007-11-27
> **kalpik said:**
> Just one suggestion, why dont you use "wget -c" instead of plain "wget" inside your script? That way we wont have to re-download the entire kernel source again if we just need to apply a new patch!
This has been implemented into the current HYDRA. Thanks for this suggestion!

---

### Post by fatmcgav on 2007-11-28
> **master_kernel said:**
> Right now the nvidia driver option does not work. I will fix this by the mainstream release next week. You get the restricted driver error because it needs the nvidia driver.

Note: the mm- patchset will not be included in the HYDRA release due to time restrictions.

So whats the easiest way of getting a working nvidia install atm???

Cheers
Gav

---

### Post by funpop on 2007-11-28
envy did the job for me after compiling the kernel with kernelcheck!
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by kalpik on 2007-11-28
> **master_kernel said:**
> This has been implemented into the current HYDRA. Thanks for this suggestion!
Thanks! Im also assuming you have removed the "rm -rf" line to remove the downloaded kernel source? Cause otherwise the "wget -c" doesnt make any sense :p

---

### Post by master_kernel on 2007-11-28
> **kalpik said:**
> Thanks! Im also assuming you have removed the "rm -rf" line to remove the downloaded kernel source? Cause otherwise the "wget -c" doesnt make any sense :p

Why doesn't it make sense? "wget -c" continues downloading the source, but if it is already downloaded, it continues with the script. See below.

```
me@my-desktop:/usr/src$ wget -c [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.23.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.23.tar.bz2)
--14:48:11--  [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.23.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.23.tar.bz2)
           => `linux-2.6.23.tar.bz2'
Resolving [www.kernel.org](www.kernel.org)... 204.152.191.37, 204.152.191.5
Connecting to www.kernel.org|204.152.191.37|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do
```

Am I missing something?

---

### Post by master_kernel on 2007-11-28
> **fatmcgav said:**
> So whats the easiest way of getting a working nvidia install atm???

Cheers
Gav

Like funpop suggested above, try using Envy.

EDIT (below):

**BUGFIX:** I have updated and hopefully fixed the nVidia driver problem. It will use the nvidia-glx packages in the repos. Also, the bug that caused the kernel not to build unless you recheck the option is now fixed. Thank you for your feedback.

---

### Post by fatmcgav on 2007-11-28
> **master_kernel said:**
> Like funpop suggested above, try using Envy.

EDIT (below):

**BUGFIX:** I have updated and hopefully fixed the nVidia driver problem. It will use the nvidia-glx packages in the repos. Also, the bug that caused the kernel not to build unless you recheck the option is now fixed. Thank you for your feedback.

Envy did the job first time - cheers for the tip.

Shall give the new KC a try when the next updates out... :)

Cheers
Gavin

---

### Post by xinix on 2007-11-28
I got this error:
```
E: Opening configuration file libncurses5 - ifstream::ifstream (2 No such file or directory)
Error [500]: apt-get returned exit status 1. Aborting now.
```

Edit 1:
I found the error.  Lines 215 and 573 are apt-get commands that call to install "wget -c" instead of "wget".

Edit 2:
Now I'm getting this error after it does its apt-get stuff:```

Please type your password [if asked] to continue:
Performance (normal) patch selected.
E: Broken packages

```
This happens if I select the nvidia option.

Edit 3:
I don't get this error after reselecting the nvidia option and running the scripts again.

---

### Post by master_kernel on 2007-11-28
> **xinix said:**
> I got this error:
```
E: Opening configuration file libncurses5 - ifstream::ifstream (2 No such file or directory)
Error [500]: apt-get returned exit status 1. Aborting now.
```

Edit 1:
I found the error.  Lines 215 and 573 are apt-get commands that call to install "wget -c" instead of "wget".

Edit 2:
Now I'm getting this error after it does its apt-get stuff:```

Please type your password [if asked] to continue:
Performance (normal) patch selected.
E: Broken packages

```
This happens if I select the nvidia option.

Edit 3:
I don't get this error after reselecting the nvidia option and running the scripts again.
What do you mean by reselecting the nvidia option?

---

### Post by glotz on 2007-11-28
Why do I want the latest kernel if you please? I'm currently on Linux version 2.6.15-29-k7 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Mon Sep 24 17:31:22 UTC 2007

---

### Post by Frak on 2007-11-28
> **glotz said:**
> Why do I want the latest kernel if you please? I'm currently on Linux version 2.6.15-29-k7 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Mon Sep 24 17:31:22 UTC 2007
If you don't know, then you don't want it.

---

### Post by kalpik on 2007-11-29
> **master_kernel said:**
> Why doesn't it make sense? "wget -c" continues downloading the source, but if it is already downloaded, it continues with the script. See below.

```
me@my-desktop:/usr/src$ wget -c [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.23.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.23.tar.bz2)
--14:48:11--  [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.23.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.23.tar.bz2)
           => `linux-2.6.23.tar.bz2'
Resolving [www.kernel.org](www.kernel.org)... 204.152.191.37, 204.152.191.5
Connecting to www.kernel.org|204.152.191.37|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do
```

Am I missing something?
If you do "rm -rf", it will delete the downloaded source archive! So wget cannot continue.. It will download again!

---

### Post by xinix on 2007-11-29
> **master_kernel said:**
> 
**BUGFIX:** I have updated and hopefully fixed the nVidia driver problem. It will use the nvidia-glx packages in the repos. Also, the bug that caused the kernel not to build unless you recheck the option is now fixed. Thank you for your feedback.

I got it to build the kernel but had no luck with nVidia. This should install when the kernel installs, right?
 Just to be sure, where would one download the version of KC with this bug fix?  I got mine from [http://kcheck.sourceforge.net/pool/testing-git/]("http://kcheck.sourceforge.net/pool/testing-git/")

---

### Post by master_kernel on 2007-11-29
> **xinix said:**
> I got it to build the kernel but had no luck with nVidia. This should install when the kernel installs, right?
 Just to be sure, where would one download the version of KC with this bug fix?  I got mine from [http://kcheck.sourceforge.net/pool/testing-git/]("http://kcheck.sourceforge.net/pool/testing-git/")
Did you reupdate KernelCheck after I posted the update?

EDIT: That is the right link. Also, I pinpointed and fixed the problem. If you update KernelCheck again, it should work.

---

### Post by master_kernel on 2007-11-29
> **kalpik said:**
> If you do "rm -rf", it will delete the downloaded source archive! So wget cannot continue.. It will download again!
Sorry, I misunderstood your first post. I thought you asking me to ADD the rm -rf option. Anyway, I fixed it and uploaded the fix.

---

### Post by kalpik on 2007-11-29
Thanks a LOT! You are doing a lot of us here a BIG favour! Keep up the good work :)

---

### Post by master_kernel on 2007-11-29
**ANNOUNCEMENT:** There are over 1000 KernelCheck users worldwide. This project has expanded greatly after I posted this topic. Thank you for your feedback and support!

---

### Post by xinix on 2007-11-29
I had luck building the kernel and nvidia debs but the driver still doesn't seem to work.  When I boot with the new kernel X won't load because it doesn't find the driver.  Is there anything special that needs to be done, or should this be a normal install, reboot and go type of thing?

---

### Post by master_kernel on 2007-11-29
> **xinix said:**
> I had luck building the kernel and nvidia debs but the driver still doesn't seem to work.  When I boot with the new kernel X won't load because it doesn't find the driver.  Is there anything special that needs to be done, or should this be a normal install, reboot and go type of thing?
Hmmm... I'll look at Envy and hopefully this will be fixed by tomorrow. At least the debs were built though, thats the main part. Try sudo modprobe nvidia in the new kernel and restart X.

---

### Post by xinix on 2007-11-30
> **master_kernel said:**
> Try sudo modprobe nvidia in the new kernel and restart X.

I did but that failed too.
```
FATAL: Error running install command for nvidia

```

---

### Post by master_kernel on 2007-11-30
> **xinix said:**
> I did but that failed too.
```
FATAL: Error running install command for nvidia

```
**Can you post the names of the files KernelCheck created in your /usr/src directory?** This will help me greatly in determining what KernelCheck should install.
Also, try running "sudo depmod -a" and then "sudo modprobe nvidia".

---

### Post by xinix on 2007-11-30
here's what KernelCheck added to my /usr/src/

```

linux
linux-2.6.23
linux-2.6.23.tar.bz2
linux-headers-2.6.23.9-greenhydra
linux-headers-2.6.23.9-greenhydra_2.6.23.9-greenhydra-10.00.Custom_i386.deb
linux-image-2.6.23.9-greenhydra_2.6.23.9-greenhydra-10.00.Custom_i386.deb
modules
nvidia-kernel-2.6.23.9-greenhydra_100.14.19-0ubuntu3+2.6.23.9-greenhydra-10.00.Custom_i386.deb
nvidia-new-kernel-source.tar.gz
rpm
```

Tried  'depmod -a' but I got the same error.

---

### Post by master_kernel on 2007-11-30
> **xinix said:**
> here's what KernelCheck added to my /usr/src/

```

linux
linux-2.6.23
linux-2.6.23.tar.bz2
linux-headers-2.6.23.9-greenhydra
linux-headers-2.6.23.9-greenhydra_2.6.23.9-greenhydra-10.00.Custom_i386.deb
linux-image-2.6.23.9-greenhydra_2.6.23.9-greenhydra-10.00.Custom_i386.deb
modules
nvidia-kernel-2.6.23.9-greenhydra_100.14.19-0ubuntu3+2.6.23.9-greenhydra-10.00.Custom_i386.deb
nvidia-new-kernel-source.tar.gz
rpm
```

Tried  'depmod -a' but I got the same error.
Try to see if the nVidia package is installed. Do sudo dpkg -i nvidia-kernel-2.6.23.9-greenhydra_100.14.19-0ubuntu3+2.6.23.9-greenhydra-10.00.Custom_i386.deb to see if it is installed. If it is, reinstall it and tell me if you get the same error.

---

### Post by xinix on 2007-11-30
It is installed and I reinstalled it a couple times.  I've even used "kernelcheck -nvidiamod" to rebuild the package while running the greenhydra kernel.  In the end I still get the same error.

---

### Post by master_kernel on 2007-11-30
> **xinix said:**
> It is installed and I reinstalled it a couple times.  I've even used "kernelcheck -nvidiamod" to rebuild the package while running the greenhydra kernel.  In the end I still get the same error.
Took this off another site:

**Nvidia kernel package**

```
apt-get install nvidia-kernel-source
cd /usr/src
tar -zxf nvidia-kernel-source.tar.gz
cd linux
make-kpkg modules_image
cd /usr/src
dpkg -i nvidia-kernel-KVER*.deb
```

The debian package also creates a bunch of /dev/nvidia* devices which have a gid of video. You will need to add yourself to the video group. This will also require you to log out and log back in again to gain the new group permissions.

```
addgroup username video
```

EDIT: It's pretty much the one command above that's different.

---

### Post by Heazky on 2007-12-01
Also, please use/include the nvidia-glx-new (100.14.19) driver, as most newer cards won't work well with the old driver (96.39). Further more, if I remember correctly, the old driver doesn't even work on 2.6.23 (That might be xinix's problem).
Compiling the newest nvidia driver by hand works like a charm.
The source package is nvidia-new-source.

KernelCheck's has become a nice piece of soft.
Nice work master_kernel!

---

### Post by master_kernel on 2007-12-01
> **Heazky said:**
> Also, please use/include the nvidia-glx-new (100.14.19) driver, as most newer cards won't work well with the old driver (96.39). Further more, if I remember correctly, the old driver doesn't even work on 2.6.23 (That might be xinix's problem).
Compiling the newest nvidia driver by hand works like a charm.
The source package is nvidia-new-source.

KernelCheck's has become a nice piece of soft.
Nice work master_kernel!
KernelCheck uses both nvidia-glx-new and nvidia-new-source.

Thanks for your support,
master_kernel

---

### Post by master_kernel on 2007-12-01
> **xinix said:**
> It is installed and I reinstalled it a couple times.  I've even used "kernelcheck -nvidiamod" to rebuild the package while running the greenhydra kernel.  In the end I still get the same error.
Edit:

While searching the internet and the modprobe man page, I decided on the following:

Check if the nvidia module is loaded with
```
lsmod | grep nv
```

To find out what is causing the problem, post the output of:
```
sudo modprobe -nv nvidia
```

As a last resort, run this command that overrides the install:
```
sudo modprobe -i nvidia
```

---

### Post by Brando569 on 2007-12-02
> **risidoro said:**
> I've found this two commands but i've not tested them:

**make silentoldconfig**  OR
**make ARCH=i386 nonint_oldconfig**

i just tried to use make silentoldconfig in a script i wrote and it still asked me all of the questions :( 

as for kernelcheck its a great program and has a ton of potential but as another user noted if you want to recompile the kernel it either does **everything** over again or you have to do it all yourself (i didnt get this far, i just used my own script) for example, after kernercheck was finished compiling my kernel i tested it out and the kernel would work (probably a problem with my config) so i ran kernelcheck again and it proceeded to download the kernel all over again even though the tarball was in the exact location as it was before! i would suggest that you include some code that would check to see if stuff is already there so i doesnt have to re-download everything each time.

keep up the good work, im looking forward to future versions :)

---

### Post by master_kernel on 2007-12-03
> **Brando569 said:**
> i just tried to use make silentoldconfig in a script i wrote and it still asked me all of the questions :( 

as for kernelcheck its a great program and has a ton of potential but as another user noted if you want to recompile the kernel it either does **everything** over again or you have to do it all yourself (i didnt get this far, i just used my own script) for example, after kernercheck was finished compiling my kernel i tested it out and the kernel would work (probably a problem with my config) so i ran kernelcheck again and it proceeded to download the kernel all over again even though the tarball was in the exact location as it was before! i would suggest that you include some code that would check to see if stuff is already there so i doesnt have to re-download everything each time.

keep up the good work, im looking forward to future versions :)
Thanks, I hope you continue to use it!

**ANNOUNCEMENT:** RPM-based systems are planned to be supported by KernelCheck 2.0.

---

### Post by wolfprintAG on 2007-12-03
Well not sure why but I did... install.... now wish I didn't in a way, can not seem to get my display right and going through the posts do not seem to give me what I am after unless I am missing something (I have your stable version) Ubuntu 7.10 a HP 19" wide, a nVidia GeForce 6150 LE - and I am lost.... should I just try and go back to my old kernel... or ?? thanks


All this cause i wanted to get the other stuff on my tablet to work.... site says make sure you have latest kernel :( found out I didn't so I try updated it now I am stuck with a 800x600 screen :(( any help of any sort would be greatful or just maybe point me in the right direction to get my kernel to the old one before the install of kernelcheck - thanks - would be good prog. if I knew what I was doing

Well problem solved temporary until I figure how to actually solve it... just boot into
Ubuntu 7.10, kernel 2.6.22-14-generic

**Please though, tell me how to fix it, remove it, or go back to original... cause even in this "Ubuntu 7.10, kernel 2.6.22-14-generic" is different then what I had. THANKS**

Like I said, good program, it just I really not understanding the kernel, and or drivers are giving me headache thanks though.

---

### Post by Frak on 2007-12-03
Remember that sometimes the newest versions are the most stable.

Also, when Grub appears on boot, choose the option before the latest and you will be back to your old kernel.

@master_kernel
Looking forward to the rpm version :)

---

### Post by wolfprintAG on 2007-12-03
> **Frak said:**
> Remember that sometimes the newest versions are the most stable.

Also, when Grub appears on boot, choose the option before the latest and you will be back to your old kernel.

@master_kernel
Looking forward to the rpm version :)

Yea thanks... heh I almost experienced nightmare but took the chance (hose system) but I didnt... but yea grub can do wonders I think I will leave things as is for now lol dont have time or patience to play wannabe geek ;) -

Thanks again though for the help

---

### Post by master_kernel on 2007-12-04
> **wolfprintAG said:**
> Well not sure why but I did... install.... now wish I didn't in a way, can not seem to get my display right and going through the posts do not seem to give me what I am after unless I am missing something (I have your stable version) Ubuntu 7.10 a HP 19" wide, a nVidia GeForce 6150 LE - and I am lost.... should I just try and go back to my old kernel... or ?? thanks


All this cause i wanted to get the other stuff on my tablet to work.... site says make sure you have latest kernel :( found out I didn't so I try updated it now I am stuck with a 800x600 screen :(( any help of any sort would be greatful or just maybe point me in the right direction to get my kernel to the old one before the install of kernelcheck - thanks - would be good prog. if I knew what I was doing

Well problem solved temporary until I figure how to actually solve it... just boot into
Ubuntu 7.10, kernel 2.6.22-14-generic

**Please though, tell me how to fix it, remove it, or go back to original... cause even in this "Ubuntu 7.10, kernel 2.6.22-14-generic" is different then what I had. THANKS**

Like I said, good program, it just I really not understanding the kernel, and or drivers are giving me headache thanks though.
I recently found out that PCLinuxOS has APT, so that should make it easier.

---

### Post by master_kernel on 2007-12-04
[http://kcheck.wiki.sourceforge.net/](http://kcheck.wiki.sourceforge.net/)

**ANNOUNCEMENT:**The KernelCheck Wiki is up.

---

### Post by Maulwuff on 2007-12-04
I think I messed something up, while deleting the greenhydra stuff, because of missing nvidia-stuff.
Synaptic tells me to run  sudo dpkg --configure -a

and this gives me:
> Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.23.8-greenhydra
Cannot find /lib/modules/2.6.23.8-greenhydra
update-initramfs: failed for /boot/initrd.img-2.6.23.8-greenhydra


so, now I can't (un)/install anything. What should I do? Thx for help in advance.

---

### Post by ottoman on 2007-12-04
wow it has been a while since the last post. I too used the kernelcheck and loved it. I am still a newbie in Ubuntu.
Well everything went very smooth during the upgrade and got the new kernel system up and running, but with one problem. When using the old kernel, my wireless was perfectly fine, but with the new one, it is not workign at all. I cannot see wireless option in the network mannager, but I ca see the card in the hardware information under System->pref. ANy thoughts??

Oh btw my card is the intel 3495....

---

### Post by xinix on 2007-12-04
Here are the results of the commands you asked me to try.  sorry it took me so long to get to them.

```
xinix@Vampiro:~$ lsmod | grep nv
xinix@Vampiro:~$ sudo modprobe -nv nvidia
[sudo] password for xinix:
install /sbin/lrm-video nvidia
xinix@Vampiro:~$ sudo modprobe -i nvidia
FATAL: Module nvidia not found.
```

---

### Post by master_kernel on 2007-12-04
> **Maulwuff said:**
> I think I messed something up, while deleting the greenhydra stuff, because of missing nvidia-stuff.
Synaptic tells me to run  sudo dpkg --configure -a

and this gives me:


so, now I can't (un)/install anything. What should I do? Thx for help in advance.
If you still have the deb files, you should be able to install those and then uninstall them.

---

### Post by master_kernel on 2007-12-04
> **ottoman said:**
> wow it has been a while since the last post. I too used the kernelcheck and loved it. I am still a newbie in Ubuntu.
Well everything went very smooth during the upgrade and got the new kernel system up and running, but with one problem. When using the old kernel, my wireless was perfectly fine, but with the new one, it is not workign at all. I cannot see wireless option in the network mannager, but I ca see the card in the hardware information under System->pref. ANy thoughts??

Oh btw my card is the intel 3495....
They removed the 3495 drivers in the 2.6.23 kernels but I can't remember the name of the replacement. Try asking about this on the Master Kernel Thread. I'll try to google for some info.

---

### Post by master_kernel on 2007-12-04
> **xinix said:**
> Here are the results of the commands you asked me to try.  sorry it took me so long to get to them.

```
xinix@Vampiro:~$ lsmod | grep nv
xinix@Vampiro:~$ sudo modprobe -nv nvidia
[sudo] password for xinix:
install /sbin/lrm-video nvidia
xinix@Vampiro:~$ sudo modprobe -i nvidia
FATAL: Module nvidia not found.
```

This is the program that is run when you run the modprobe:
```
#!/bin/sh

PATH=/sbin:/bin

MODULE="$1"
shift

if [ "$MODULE" = "nvidia" ]; then
        if [ -e /lib/linux-restricted-modules/.nvidia_legacy_installed ]; then
                MODULE="nvidia_legacy"
        fi
        if [ -e /lib/linux-restricted-modules/.nvidia_new_installed ]; then
                MODULE="nvidia_new"
        fi
        XORG="nvidia";
elif [ "$MODULE" = "nvidia_legacy" -o "$MODULE" = "nvidia_new" ]; then
        XORG="nvidia";
elif [ "$MODULE" = "fglrx" ]; then
        XORG="fglrx";
fi

if cat /etc/X11/xorg.conf 2>/dev/null | \
  sed -n -e '/^[ \t]*section[ \\t]*"device"/I,/^[ \t]*endsection/I{/^[ \t]*driver[ \t]*/I{s/^[ \t]*driver[ \t]*"*//I;s/"*[ \t]*$//;p}}' | \
  grep -q -w $XORG; then
        modprobe --ignore-install -Qb $@ $MODULE
else
        echo "Not loading $MODULE module; not used in /etc/X11/xorg.conf" 1>&2
fi

```

For some reason, it is failing at one of these steps. To figure out where, edit it with root and change the #!/bin/sh line at the beginning to ```
#!/bin/sh -x
```
**This will make it verbose. Please post the output of this.** I have a hunch, but it may not be correct. The only thing I can think of is that it isn't configured correctly. Try the following commands:
```
sudo dpkg-reconfigure xserver-xorg
```
**and use the VESA driver; then do:**
```
sudo nvidia-xconfig
```

I hope this works,
master_kernel

---

### Post by xinix on 2007-12-05
I didn't try the configuration steps because I know that I have X configured properly to work with the nvidia kernel.  I think the key lies in the previously requested inclusion of nvidia-glx.  I Just used Envy to make a driver for my KernelCheck kernel and everything is working just fine.  
     The one thing I can see it does that KC isn't doing is updating nvidia-glx.  If you look at the versions the package is tied to kernel versions.  So If you are using the stock Ubuntu stuff the version would be : 100.14.19+2.6.22.4-14.10 .  This is also the package version that is used when you install the driver with KernelCheck.  Envy generates a new nvidia-glx package that replaces the one in the repositories with a version number of: 1:100.14.23+2.6.23.9.
     Both KernelCheck and Envy seem to create the same nvidia.ko module,  but I haven't compared them in depth.

---

### Post by master_kernel on 2007-12-05
> **xinix said:**
> I didn't try the configuration steps because I know that I have X configured properly to work with the nvidia kernel.  I think the key lies in the previously requested inclusion of nvidia-glx.  I Just used Envy to make a driver for my KernelCheck kernel and everything is working just fine.  
     The one thing I can see it does that KC isn't doing is updating nvidia-glx.  If you look at the versions the package is tied to kernel versions.  So If you are using the stock Ubuntu stuff the version would be : 100.14.19+2.6.22.4-14.10 .  This is also the package version that is used when you install the driver with KernelCheck.  Envy generates a new nvidia-glx package that replaces the one in the repositories with a version number of: 1:100.14.23+2.6.23.9.
     Both KernelCheck and Envy seem to create the same nvidia.ko module,  but I haven't compared them in depth.
This must be it. I'll have to look at how Envy compiles the driver and use that to compile it for KernelCheck.

EDIT: I've downloaded the latest version of the nVidia driver (100.14.23) and took a look at some of the options. This is what I have come up with to run after the kernel is installed:
```
sudo sh NVIDIA-Linux-x86-100.14.23-pkg2.run -a -X --no-x-check --kernel-name=$KERNELNAME
```

---

### Post by EisenPM on 2007-12-05
I am using encrypted root, home and swap partitions with cryptsetup and LUKS and the generic kernel.

When I update it with KernelCheck, will the modules for the encryption be still there? I dont' know, if it has something to do with the kernel, but I think so.

The most important thing is that the menu.list is modified. Will these modifications stay? I guess, since they are at:

# kopt

and 

# defoptions

And another question: The speed increase comes only with the HYDRA version, if you select it, right? Just updating the kernel doesn't mean a speed increase, or are there any modifications in the 1.0.5 version as well?

---

### Post by EisenPM on 2007-12-06
I have another question concerning the timer frequency in the kernel CPU configuration.

What is the timing for best responsiveness with an dual core CPU?

With single core CPUs it's 1000 Hz. But concerning SMP CPUs the info says the other three settings would be better.

Any ideas? Or how I can find out myself?

---

### Post by master_kernel on 2007-12-06
> **EisenPM said:**
> I am using encrypted root, home and swap partitions with cryptsetup and LUKS and the generic kernel.

When I update it with KernelCheck, will the modules for the encryption be still there? I dont' know, if it has something to do with the kernel, but I think so.

The most important thing is that the menu.list is modified. Will these modifications stay? I guess, since they are at:

# kopt

and 

# defoptions

And another question: The speed increase comes only with the HYDRA version, if you select it, right? Just updating the kernel doesn't mean a speed increase, or are there any modifications in the 1.0.5 version as well?
1. Is the encryption program embedded in your kernel?

2. You are correct. Kopt and Defoptions will stay in your menu.lst.

3. Someone in the Master Kernel Thread created a patch for the kernel that sets the best timing for SMP CPUs. I was not sure if it was right so I didn't use it. Here is the link to the post: [http://ubuntuforums.org/showpost.php?p=3463403&postcount=629](http://ubuntuforums.org/showpost.php?p=3463403&postcount=629)

---

### Post by xinix on 2007-12-07
> **master_kernel said:**
> 
3. Someone in the Master Kernel Thread created a patch for the kernel that sets the best timing for SMP CPUs. I was not sure if it was right so I didn't use it. Here is the link to the post: [http://ubuntuforums.org/showpost.php?p=3463403&postcount=629](http://ubuntuforums.org/showpost.php?p=3463403&postcount=629)

Is is possible to use this patch while using KernelCheck?  I'm trying it out now but I manually built the kernel.

---

### Post by flipfone on 2007-12-07
I ran this and all went well i now have the latest kernel. (GREAT JOB!) then i tried it again with the prepatch option however i didnt know it was going to write out the same kernel i just booted into. oooops! so i hit ctrl-c and aborted it. now my package manager is complaining. i tried to remove the new kernel but:

jim@jim-desktop:~/kernelcheck-1.0.5$ sudo apt-get remove linux-image-2.6.23.9 --purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package linux-image-2.6.23.9 needs to be reinstalled, but I can't find an archive for it.


help?!   thank you.

---

### Post by master_kernel on 2007-12-07
> **flipfone said:**
> I ran this and all went well i now have the latest kernel. (GREAT JOB!) then i tried it again with the prepatch option however i didnt know it was going to write out the same kernel i just booted into. oooops! so i hit ctrl-c and aborted it. now my package manager is complaining. i tried to remove the new kernel but:

jim@jim-desktop:~/kernelcheck-1.0.5$ sudo apt-get remove linux-image-2.6.23.9 --purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package linux-image-2.6.23.9 needs to be reinstalled, but I can't find an archive for it.


help?!   thank you.
I think you'll have to recompile the 2.6.23.9 kernel (sorry!). I'll have to do some testing with KC over the weekend because this shouldn't happen if you selected prepatch.

---

### Post by master_kernel on 2007-12-07
> **xinix said:**
> Is is possible to use this patch while using KernelCheck?  I'm trying it out now but I manually built the kernel.
I'll add support for custom patching in HYDRA.

---

### Post by flipfone on 2007-12-08
E: The package linux-image-2.6.23.9 needs to be reinstalled, but I can't find an archive for it.
Unknown Error. Aborting now.


Tried to rebuild it and i get this error.

---

### Post by of_darkness on 2007-12-10
> **master_kernel said:**
> You have to compile the restricted mods yourself. I hope to implement an auto-build of this by KC2.
but they dont exist.. i have googeld for it.. but only questions asking where/howto find and install them.. or are you suposed to youse the ones for the ubuntu kernel version?

---

### Post by Gourgi on 2007-12-11
i just installed kernel 2.6.23.9 using KC 
and i installed nvidia drivers using envy
everything looks just fine for the moment

it was tha first time compiling the kernel so i tried to have general module support and i didn't removed much 

so I have just a question : 
After compiling - instaling the kernel i ended with about 0% of free space at root partition, i freed as much as i could when i realised that
now i see that there is about 3.1GB at /usr/src/linux-2.6.23
and 620MB at /lib/modules
i obviously want to free some space so can i safely remove some of these dirs?
also is there something related to the kernel that i can remove using synaptic ?

@master kernel : i'd propose you to include a big big warning at the first post  of this thread saying that at least 4 gigs of freespace is required for compiling the new kernel 

P.S. i like the KC screelet a lot ! i already using it  
thanks for the KC project , you :guitar:   :)

---

### Post by funpop on 2007-12-11
you can delete /usr/src/linux-VERSION (/usr/src/linux-2.6.23)

i asked this qustion some posts earlier :popcorn:

---

### Post by EisenPM on 2007-12-11
> **master_kernel said:**
> 1. Is the encryption program embedded in your kernel?



well, I added the needed modules in:

/etc/initramfs-tools/modules

So they are not embedded in the kernel, right?

Does it make any sense to include these in the kernel?

aes_i586
dm-crypt
dm-mod
sha256

---

### Post by Gourgi on 2007-12-12
> **funpop said:**
> you can delete /usr/src/linux-VERSION (/usr/src/linux-2.6.23)

i asked this qustion some posts earlier :popcorn:

thanks for replying and apologize for double-asking 
i did read the hole thread but i missed that    ](*,)

---

### Post by Brando569 on 2007-12-12
another request for the kernel hacking section.

---

### Post by plun on 2007-12-13
2.6.24-RC5 up and running  :)

nVidia manual install

Virtualbox also works again from trunk
[http://www.virtualbox.org/wiki/Linux%20build%20instructions](http://www.virtualbox.org/wiki/Linux%20build%20instructions)

---

### Post by of_darkness on 2007-12-14
> ~/truecrypt-4.3a-source-code/Linux ]$ sudo ./build.sh
[sudo] password for blutengel:
Checking build requirements...
Linux kernel (2.6.23.9-greenhydra) source directory [/usr/src/linux]:
Error: Kernel source version in /usr/src/linux is not 2.6.23.9-greenhydra

have tried 2 change linux 2 point 2 linux-2.6.23 and 2 copy linux-2.6.23 to linux-source-2.6.23 and linking linux 2 it.. but no luck.. tried 2 look for some file in the 2.6.23 directory that would be specyfing the version but no luck..

---

### Post by flipfone on 2007-12-15
> **flipfone said:**
> E: The package linux-image-2.6.23.9 needs to be reinstalled, but I can't find an archive for it.
Unknown Error. Aborting now.


Tried to rebuild it and i get this error.

Anyone please?

---

### Post by flamelab on 2007-12-15
Hello , your program is reaaaaaaaly good .

But ! I really had a problem with the restricted drivers and especially my ATI card !Where can I download the restricted modules ?
Or is there a hack for that ?

---

### Post by Gourgi on 2007-12-15
> **flamelab said:**
> Hello , your program is reaaaaaaaly good .

But ! I really had a problem with the restricted drivers and especially my ATI card !Where can I download the restricted modules ?
Or is there a hack for that ?

you could try the envy package
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
it says it works for ati drivers too

---

### Post by flamelab on 2007-12-15
> **Gourgi said:**
> you could try the envy package
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
it says it works for ati drivers too

Oh no no , I don't want THAT driver (8.43 for now ) because it is too slow . I prefer 8.37 that is stable .
Can I install that without problem ?

---

### Post by master_kernel on 2007-12-16
Massive project due -- cannot respond to any questions until Tuesday afternoon.

Sorry,
master_kernel

---

### Post by flipfone on 2007-12-17
> **flipfone said:**
> Anyone please?

ok i found the solution.

sudo dpkg --remove --force-remove-reinstreq linux-image-2.6.23.9

---

### Post by kalpik on 2007-12-19
Kernel [2.6.23.12](http://kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.23.12) released!

---

### Post by master_kernel on 2007-12-31
Sadly, the HYDRA release will be delayed again. Since I have no deadline, I will announce it's release one week in advance.

Sorry,
master_kernel

---

### Post by happycheng on 2007-12-31
hello,
after i use 1.05 kernelcheck to build the new kernel(2.6.23.12), i found there is a error. Every time I boot with the new kernel , there is no sound,  the Volume Applet show the red cross , and says no volume control GStreamer plugins and/or devices found." however, when i use the "old" kernel" ( Linux -image-2.6.22.14-generic), everything turn right! what's wrong ? Does someone can help me?

I've already sudo update-modules, but there is still the error!?

I'm using linuxmint 4.0 

thanks in advance.

---

### Post by master_kernel on 2008-01-02
> **happycheng said:**
> hello,
after i use 1.05 kernelcheck to build the new kernel(2.6.23.12), i found there is a error. Every time I boot with the new kernel , there is no sound,  the Volume Applet show the red cross , and says no volume control GStreamer plugins and/or devices found." however, when i use the "old" kernel" ( Linux -image-2.6.22.14-generic), everything turn right! what's wrong ? Does someone can help me?

I've already sudo update-modules, but there is still the error!?

I'm using linuxmint 4.0 

thanks in advance.
You have to enable Intel HD Sound in the xconfig.

---

### Post by happycheng on 2008-01-03
sorry, I'm a newbie.
How to  enable Intel HD Sound in the xconfig. 
thx

---

### Post by ~LoKe on 2008-01-03
Your other thread worked for me, so I'll give this one a shot!

---

### Post by master_kernel on 2008-01-05
> **happycheng said:**
> sorry, I'm a newbie.
How to  enable Intel HD Sound in the xconfig. 
thx
This is what you have to do:

Run KernelCheck -- and when the xconfig window comes up, go to Sound > Advanced Linux Sound Architecture > PCI Devices and make Intel HD Sound a module by highlighting it and pressing "m". There should be a dot in the box beside it when you do this.

---

### Post by shifty2 on 2008-01-05
argh nightmare. Computer crashed whilst compiling the new kernel. This means that I don't have the new kernel but still have an extra 2 gig of space being used up on my system. How do I get rid of this before starting to compile again?

---

### Post by master_kernel on 2008-01-06
> **shifty2 said:**
> argh nightmare. Computer crashed whilst compiling the new kernel. This means that I don't have the new kernel but still have an extra 2 gig of space being used up on my system. How do I get rid of this before starting to compile again?
```
sudo rm -rf /usr/src/linux-2.6.23
```
Most people, particularly on this forum, are afraid of rm -rf commands, so if you need an alternative that might not delete everything, here it is:
```
rm -r /usr/src/linux-2.6.23
```
Note that you must be root to run either of these commands.

master_kernel

---

### Post by Colin The Grey on 2008-01-09
Excellent utility, and the information in this thread has been most useful to a Linux newb like me.

Have managed to update to the latest Kernel with no problems using KernelCheck - very pleased indeed :)

Many thanks.

---

### Post by Washer on 2008-01-13
Does this do a custom patch? That's a deal breaker for me. Shouldn't be too hard to add it using --dry-run or whatever.


Edit:
> **master_kernel said:**
> I'll add support for custom patching in HYDRA.

I see. Any chance you could support some common patches? I recently had some trouble adding reiser4 then truecrypt to gutsy. I could probably contribute a bit if you added a hacking section

---

### Post by happycheng on 2008-01-14
hi, 
I have already make the new kernel , but I found some mistakes (forget to add some codepage), and need to  remake the kernel manully, 
what can I do without doing from the very beginning?(I have save the .config file in my /home directory, and the kernel source and patch haven't deleted)

kernel check 1.05
kernel 2.6.23.-13

thx in advance.

---

### Post by taekr on 2008-01-20
Thanks Zillion!!! 

For a user like me....  you are the savior!!

---

### Post by jithin1987 on 2008-01-24
I am not able to run kernel checkit gives me following error

/usr/bin/kernelcheck: line 434: zenity: command not found
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py:72: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)

Testing your network connection...
Test was successful, you are connected to the internet
/usr/bin/kernelcheck-stage2:288: Warning: invalid (NULL) pointer instance
  self.window=gtk.Window(gtk.WINDOW_TOPLEVEL)
/usr/bin/kernelcheck-stage2:288: Warning: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
  self.window=gtk.Window(gtk.WINDOW_TOPLEVEL)
/usr/bin/kernelcheck-stage2:291: GtkWarning: gtk_icon_theme_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
  gtk.ICON_SIZE_DIALOG)
/usr/bin/kernelcheck-stage2:291: GtkWarning: gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
  gtk.ICON_SIZE_DIALOG)
/usr/bin/kernelcheck-stage2:291: GtkWarning: gtk_icon_size_lookup_for_settings: assertion `GTK_IS_SETTINGS (settings)' failed
  gtk.ICON_SIZE_DIALOG)
/usr/bin/kernelcheck-stage2:291: GtkWarning: Invalid icon size 6

  gtk.ICON_SIZE_DIALOG)
/usr/bin/kernelcheck-stage2:291: GtkWarning: gtk_icon_theme_load_icon: assertion `GTK_IS_ICON_THEME (icon_theme)' failed
  gtk.ICON_SIZE_DIALOG)
/usr/bin/kernelcheck: line 444:  9732 Segmentation fault      (core dumped) kernelcheck-stage2

---

### Post by master_kernel on 2008-01-27
You have to install zenity.

**sudo apt-get install zenity**

---

### Post by master_kernel on 2008-01-27
**ANNOUNCEMENT:** Too many new features are being integrated into KernelCheck HYDRA. Also, I have failed the deadline several times. For these and several other reasons, I am continuing on to KernelCheck 2 -- Silver.

---

### Post by costis on 2008-01-28
Hello to all from the windy Greece: wind speed reaches 70km/h :guitar:

Well, I am using http_proxy. While using kernelcheck-1.0.5 kernelcheck works and finds internet connection, in kernelcheck-testing, this doesn't happen. 
What should I do for the recovery of the issue?

---

### Post by Washer on 2008-01-30
master_kernel; I've been reading through the code & I got some ideas I wanted to bounce off you. Is there any way to contact you other than gmail? IM or IRC?

---

### Post by Washer on 2008-02-10
Or you could just ignore the post, yeah that works too.

---

### Post by Nirevus on 2008-02-11
Washer, there have been several times that master_kernel has been unable to reply for a week or several weeks at a time in this thread. It's likely that he's working on a project or otherwise busy. 

He may not have email notification turned on for this thread, so I'd suggest sending a PM from the forums to him in the hope it will notify him by email.

---

### Post by Fred_E _krugar on 2008-02-18
> **Washer said:**
> Or you could just ignore the post, yeah that works too.

LOL dude that is freaking funny. LOL

---

### Post by master_kernel on 2008-02-23
sorry for not replying for so long, ive been incredibly busy with school

---

### Post by master_kernel on 2008-02-23
Washer: Gmail is [email]master.kernel.contact@gmail.com[/email]

**ANNOUNCEMENT:** I was contacted by a Debian maintainer who wanted to package KernelCheck for the repositories. He said it will eventually make it into Ubuntu repositories. I just wanted to let everyone know the great progress KernelCheck is making even though my development of it has almost completely stopped at the moment. I will try to continue development and a completely revamped version will be released this summer.

---

### Post by master_kernel on 2008-03-15
**ANNOUNCEMENT:** KernelCheck HopeStar. 06.30.08.

---

### Post by la5zl on 2008-03-30
Thanks !

Having just installed 2.6.24.4, Ubuntu 7.10,
works perfect!

Had to compile ndiswrapper for my wlan card - rt2500pci -
but becoming used to it since the kernel driver almost
stopped working since kernel introduced around august
2007 - can't remember version though.
Well - it works, but very s l o w .., so ndiswrapper (1.52)is the
only solution. 

Again - Thanks!

Bjorn

---

### Post by master_kernel on 2008-03-30
**DEVELOPMENT ANNOUNCEMENT:** KernelCheck 06.30.08 is being developed using Anjuta.

---

### Post by larryfroot on 2008-04-06
thank you so much for all the hard work you are putting into this as it enables newbies like me the opportunity to enjoy the benefits of recompiling without the time investment needed to achieve this goal by other means. 

I have downloaded and used version 1.0.5 to really good effect, but I do have one question. Back last year there was a perl script drawn to your attention that removed unused modules from the kernel. Did you ever include this feature in kernelcheck, or should I give the instructions on the link to the script a go?

Mind you, they are instructions from someone in the know to others in the know! And a little knowledge can be a dangerous thing! Just that I am running gutsy on an old laptop with low specs. Anything that can increase performance is very, very welcome. At the moment it is just about OK...but only just.

well, thank you once again for a great tool and dedicated follow up with all the feedback you get.

---

### Post by master_kernel on 2008-04-07
> **larryfroot said:**
> thank you so much for all the hard work you are putting into this as it enables newbies like me the opportunity to enjoy the benefits of recompiling without the time investment needed to achieve this goal by other means. 

I have downloaded and used version 1.0.5 to really good effect, but I do have one question. Back last year there was a perl script drawn to your attention that removed unused modules from the kernel. Did you ever include this feature in kernelcheck, or should I give the instructions on the link to the script a go?

Mind you, they are instructions from someone in the know to others in the know! And a little knowledge can be a dangerous thing! Just that I am running gutsy on an old laptop with low specs. Anything that can increase performance is very, very welcome. At the moment it is just about OK...but only just.

well, thank you once again for a great tool and dedicated follow up with all the feedback you get.
I did not include this in 1.0.5, but it is planned in HopeStar.

---

### Post by master_kernel on 2008-04-07
**Annoucement:** Check out the [new website]("http://kcheck.sourceforge.net").

---

### Post by Kaohuz on 2008-04-21
I've just wanted to say that it is thanks to people like you that make Ubuntu and this community such a wonderfull place to be part of.
You guys always "pushing it to the next level" in order to people like me trough a few clicks can enjoy the power and goods of a new kernel.

Thank You!

---

### Post by traxk on 2008-04-27
Hi,
I am running ubuntu 8.04-rc. 
I have today run the kernelcheck to latest kernel 2.6.25 (5 hours to build)
Every thing seems to be ok except for sound no plug-ins found. Is there a quick way to fix this issue? Dell dimension 2400.
Suggestions welcome.
Thanks
Ps.:With above new kernel firefox 3.0 is not hunting anymore for memory and is low on cpu load. Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9pre) Gecko/2008042704 Minefield/3.0pre

---

### Post by master_kernel on 2008-04-28
> **traxk said:**
> Hi,
I am running ubuntu 8.04-rc. 
I have today run the kernelcheck to latest kernel 2.6.25 (5 hours to build)
Every thing seems to be ok except for sound no plug-ins found. Is there a quick way to fix this issue? Dell dimension 2400.
Suggestions welcome.
Thanks
Ps.:With above new kernel firefox 3.0 is not hunting anymore for memory and is low on cpu load. Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9pre) Gecko/2008042704 Minefield/3.0pre

In xconfig (where you configure the kernel), go to Sound > Advanced Linux Sound Architecture (press M to make it a module) > PCI Devices > Intel HD Audio (press M to make it a module, there should be a dot inside the box) and then let KernelCheck continue.

---

### Post by traxk on 2008-04-30
Thanks for your reply,
I cannot wake-up xconfig on my Pc, have tried all commands i found on the web no success. Boot time [2.6.25] is 310 and boot screen shows three progress bars instead of one. Printing does not work either cd/dvd do.
Besides the above kernel 2.6.25 feels great and swift at handling tasks. I will have to wait for an update. Any other suggestion welcome, thanks.

I am using kernel 2.6.24-16 in case of...
Thanks.
Iakop

---

### Post by jonlowe on 2008-04-30
> **master_kernel said:**
> In xconfig (where you configure the kernel), go to Sound > Advanced Linux Sound Architecture (press M to make it a module) > PCI Devices > Intel HD Audio (press M to make it a module, there should be a dot inside the box) and then let KernelCheck continue.


Does this mean I need to do a complete rebuild of the kernel if I forgot something?  Or is there a way to start xconfig and just build that portion?  Fi so, how?  Ubuntu 8.04 has the drivers for my Syntek webcam built in, but the kernelcheck script doesn't build them automatically.  It doesn't do the drivers for my Intel 3945 wireless card either, but I coaght that one before I built the kernel.

Also, the firmware libraries for things such as my wireless card didn't get created for 2.6.25.  I copied the one I have for 2.6.24-16 and renamed them to 2.6.25, and got it started.  However I had to find and manually add the firmware for my TV card.  Is there a way that kernelcheck can do this automagically?

Finally, I am getting a bios bug report on booting with 2.6.25 that I don't get with 2.6.24-16.  something about a pci memory reservation problem.  Any ideas why this would happen with 2.6.25?  It does boot up ok.

Thanks!

Jon

---

### Post by traxk on 2008-05-03
Hi,
Have updated to 2.6.25.1 see attachment copy conf.
Sound still down no gstreamer plug-in found . Boot time now 190 seconds, printer works now. Good sound with 2.6.24-16 kernel don`t know where it stalls in 2.6.25.1. Maybe you can give me a hint, thanks.
Iakop

---

### Post by Adahn on 2008-05-20
I have folders in usr/src for old kernels taking up  over 6GB of space on my hdd.
How do I purge these?

---

### Post by sdm_cacto on 2008-05-22
sudo nautilus

then you go to /usr/src/ and delete everything

---

### Post by gimmic on 2008-05-23
Thank you for making this process painless

---

### Post by defconoii on 2008-06-01
I compiled my own 2.6.25 kernel in hardy heron and noticed pulseaudio didnt work, does kernelcheck somehow fix this?

---

### Post by Adahn on 2008-06-01
> **sdm_cacto said:**
> sudo nautilus

then you go to /usr/src/ and delete everything

I did this and things were fine for a while, even through several updates.
Yesterday, update and synaptic stopped working.
Update tries to do a partial update; synaptic tells me to sudo dpkg --configure -a
 which gives me:

Setting up initramfs-tools (0.85eubuntu39) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.25.2
Cannot find /lib/modules/2.6.25.2
update-initramfs: failed for /boot/initrd.img-2.6.25.2
dpkg: subprocess post-installation script returned error exit status 1

I had deleted that /lib folder to save space.
Suggestions?

---

### Post by ForksHolder on 2008-06-01
Hello master-kernel,

The main problem i had with your longer How-to, is to configure the kernel to my computer (You know, the one i need to say what Pentium i have and stuff).

I thouth that in this Kernel-Check it will do it itself by seeking my computer information, but if i have to configure it myself again, i prefer using this kernel.

If you can make an update with will auto-configure itself, it'll be great. :)

Thanks,
Forks Holder

---

### Post by ukripper on 2008-06-06
Compilation and installation worked great but looks like i have to load ATI drivers by myself.

Thanks for this great app saved me some compilation and installtion time as i dont have to sit in front of my machine when it is compiling.

10/10 for this app from me!:KS

---

### Post by master_kernel on 2008-06-12
> **Adahn said:**
> I did this and things were fine for a while, even through several updates.
Yesterday, update and synaptic stopped working.
Update tries to do a partial update; synaptic tells me to sudo dpkg --configure -a
 which gives me:

Setting up initramfs-tools (0.85eubuntu39) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.25.2
Cannot find /lib/modules/2.6.25.2
update-initramfs: failed for /boot/initrd.img-2.6.25.2
dpkg: subprocess post-installation script returned error exit status 1

I had deleted that /lib folder to save space.
Suggestions?

1. Did you uninstall the 2.6.25.6 kernel?

---

### Post by master_kernel on 2008-06-12
> **ForksHolder said:**
> Hello master-kernel,

The main problem i had with your longer How-to, is to configure the kernel to my computer (You know, the one i need to say what Pentium i have and stuff).

I thouth that in this Kernel-Check it will do it itself by seeking my computer information, but if i have to configure it myself again, i prefer using this kernel.

If you can make an update with will auto-configure itself, it'll be great. :)

Thanks,
Forks Holder
This will be integrated by 2.0.

---

### Post by master_kernel on 2008-06-12
> **ukripper said:**
> Compilation and installation worked great but looks like i have to load ATI drivers by myself.

Thanks for this great app saved me some compilation and installtion time as i dont have to sit in front of my machine when it is compiling.

10/10 for this app from me!:KS
Thanks for the rating; It seems that since ATI is never up-to-date with the latest kernel, I won't be able to integrate support for it in HopeStar. I'll try to add an option for users to install Envy since it's in the repos now.

---

### Post by Adahn on 2008-06-12
> **master_kernel said:**
> 1. Did you uninstall the 2.6.25.6 kernel?

I solved this last week.  I had forgotten to delete the file in /var/lib/initramfs-tools associated with 2.6.25.6

---

### Post by ukripper on 2008-06-13
> **master_kernel said:**
> Thanks for the rating; It seems that since ATI is never up-to-date with the latest kernel, I won't be able to integrate support for it in HopeStar. I'll try to add an option for users to install Envy since it's in the repos now.

really is envy in repos? Damn where i have been living:lolflag: Problem is i am still supporting gutsy for certain users it will take time for me to get used to Hardy myself.

---

### Post by master_kernel on 2008-06-13
**ANNOUNCEMENT:** KernelCheck HopeStar is really coming along. Some of the new features include:

- All the 1.0.5 features you've grown to love :)
- Envy installation support
- New graphical design
- Expandable menus
- Connection button (to download information)
- Integrated terminal for viewing building process
- Status bar
- Progress bar
- Autodefaults for config (NO MORE USER INTERACTION :) (but still not recommended))

Since I pretty much rewrote the code from 1.0.5, there are still some bugs for me to catch up on, but I plan to add custom patching support as well as a patch system and error trapping.

---

### Post by txnec on 2008-06-15
Just wanted to mention - great program.

I'm still a linux newb so here goes: how do i access the kernel options (the screen that pops up from "make xconfig") after i've compiled the kernel?

I can't seem to get my wireless (Atheros) or my sound working.  I thought I had set the right configurations prior to compiling.  I suppose it takes a little bit more tweaking on my end..

---

### Post by master_kernel on 2008-06-16
> **txnec said:**
> Just wanted to mention - great program.

I'm still a linux newb so here goes: how do i access the kernel options (the screen that pops up from "make xconfig") after i've compiled the kernel?

I can't seem to get my wireless (Atheros) or my sound working.  I thought I had set the right configurations prior to compiling.  I suppose it takes a little bit more tweaking on my end..
Check out the Master Kernel Thread in my signature. I'm not entirely sure about your wireless, but your sound is probably due to ALSA not being enabled in your kernel.

---

### Post by txnec on 2008-06-16
well, for the wireless, I had enabled Ath5k and looked at all the requirements in the xconfig.  For ALSA, I had actually enabled it along with my chipset driver.  

The other thing is, I tried using EnvyNG to install proprietary drivers for my vidcard, ATI Radeon Xpress, and nothing was installed.  Is there anyway to reconfigure xconfig without having to go back and recompile the kernel??  It's a pain in the butt to troubleshoot when you have to wait 3...4 hours for results... lol

---

### Post by master_kernel on 2008-06-16
> **txnec said:**
> well, for the wireless, I had enabled Ath5k and looked at all the requirements in the xconfig.  For ALSA, I had actually enabled it along with my chipset driver.  

The other thing is, I tried using EnvyNG to install proprietary drivers for my vidcard, ATI Radeon Xpress, and nothing was installed.  Is there anyway to reconfigure xconfig without having to go back and recompile the kernel??  It's a pain in the butt to troubleshoot when you have to wait 3...4 hours for results... lol
An ATI user I see. Well, I have an ATI Radeon Xpress also, and because of changes in the kernel API, Envy will not work for the latest kernel. You have to download the latest binary from the ATI site and install it. That one has 2.6.25 support. But sorry, I do not know of a way to reconfigure the configuration w/o recompiling it.

MK

---

### Post by txnec on 2008-06-16
lol... that's too bad cause i'm stubborn enough to recompile this thing a thousand times simply because 2.6.24 isn't really stable for me unless i'm running RT which is ***.....  What drivers did you download from the ATI site?  I have xpress 1100..  and it's not on their site....................... and if there's really no help for me... sounds like i'm f***ed until the next release in a few weeks...............

---

### Post by Payteer on 2008-06-17
Hello, I am having real problems, I did the master kernal stuff, and been a noob, I think I messed up a few things.  Anyway, no sound or wireless now also the boot up ubuntu screen has two bars on it now, not just the one.
I want to be able to sort this out in a clear way as this is really annoying.  Anyway, I have the built in intel sound card and a built in wireless in my lenovo 3000 V100. Please can some one help me get the drivers that used to work with the old hardy.  Thanks

---

### Post by master_kernel on 2008-06-17
> **txnec said:**
> lol... that's too bad cause i'm stubborn enough to recompile this thing a thousand times simply because 2.6.24 isn't really stable for me unless i'm running RT which is ***.....  What drivers did you download from the ATI site?  I have xpress 1100..  and it's not on their site....................... and if there's really no help for me... sounds like i'm f***ed until the next release in a few weeks...............
**Catalyst 8.5 Download**
[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

**Directions for Hardy Installation**
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.5.29")

Hope this helps!
MK

---

### Post by master_kernel on 2008-06-17
> **Payteer said:**
> Hello, I am having real problems, I did the master kernal stuff, and been a noob, I think I messed up a few things.  Anyway, no sound or wireless now also the boot up ubuntu screen has two bars on it now, not just the one.
I want to be able to sort this out in a clear way as this is really annoying.  Anyway, I have the built in intel sound card and a built in wireless in my lenovo 3000 V100. Please can some one help me get the drivers that used to work with the old hardy.  Thanks
I'm not quite sure how to do this, but it sounds like you may have to compile the linux-restricted-drivers package. Head over to the Master Kernel Thread and there should be some directions there.

Sorry I couldn't be of more help,
MK

---

### Post by master_kernel on 2008-06-17
**ANNOUNCEMENT:** KernelCheck HopeStar Beta is now available. The deb file is attached to the first post.
**ANNOUNCEMENT:** Beta 3 is now out. The first release candidate will be released Monday afternoon.
**ANNOUNCEMENT:** Beta 4 is out with a minor bug fix.
**ANNOUNCEMENT:** Release candidate 1 has been released. Do not check for updates in this release.
**ANNOUNCEMENT:** Release candidate 2 has been released. Do not check for updates in this release.
**ANNOUNCEMENT:** Release candidate 3 has been released. RC2 has been removed because it was no different from RC1. Apparently I forgot to build the package with the correct files. There are fixes in this release. Do not check for updates yet.

_*Bug reports (6/19):*_
[LIST]
[*]Help button has no function [FIXED]
[*]Patch system needed [FIXED]
[*]MM patch support is broken [FIXED]
[*]Expanders are sensitive when there is no kernel information [FIXED]
[/LIST]

---

### Post by dementic on 2008-06-25
Hello!

I use your program, fantastic very easy (even if I don't understand what is it asking about sometimes during the installation). But what I noticed is that it took 6 GB to update, where is all that space gone??? How can I recover it?

Another point, I have a Core2Duo processor, so I would need 686 kernel, right? How do I know which one is installed?


Thank you!

---

### Post by master_kernel on 2008-06-26
> **dementic said:**
> Hello!

I use your program, fantastic very easy (even if I don't understand what is it asking about sometimes during the installation). But what I noticed is that it took 6 GB to update, where is all that space gone??? How can I recover it?

Another point, I have a Core2Duo processor, so I would need 686 kernel, right? How do I know which one is installed?


Thank you!
1. One way you can recover some space is by deleting /usr/src/linux-2.6.25 using:
```
sudo rm -rf /usr/src/linux-2.6.25
```

2. You can select your machine architecture in the xconfig window that comes up.

3. Use 'uname -r' to find out what kernel is running.

MK

---

### Post by dementic on 2008-06-26
Thank you I will try that :) 

Another question, if I delete the source can I have problems when compiling some others drivers or something like that?

---

### Post by Megatog615 on 2008-06-27
Whoops, nevermind.

---

### Post by mond0 on 2008-06-27
I'm a big linux newb, (just got Ubuntu like 3 days ago) and i tried to up my kernel from the default to the latest stable version (2.6.25.9) using KernelCheck Hopestar v 1.1-beta3 build 17 (i clicked on the 2nd to last link on the origional post -- i did not click the final link, the RC version, because it was much smaller and the announcement said "do not check for updates in this version") -but I never got to running off the new kernel :(

1:did i mis-interprit? can i still use the rc1 version to update the kernel?
2: why is it so much smaller smaller? :)

3: So i run kernelchecker, and it goes through, scrolling things that give "warning: .........." i dont know, i just saw them, something about changing files around, i figured that's fine because that's what the program is meant to do.. eventually it comes up with a box to configure the kernel, I add some features (.config support for the kernal config, and mac80211 drivers for my intel 4965 wireless) and then hit save and close the config file, just hoping that closing it is the right choice to proceed, which it apparently was because the install continued, saying it might take 2-4 hours.  When I come back, it asks me about booting and menu.ls (i think) and i didn't want to mess with changing that so i chose not to.  Then it continues, installing kernel updates to .9 i think?  then finally it ended up with a line going something like: "packages installed:0 packages upgraded:0 packages xxxx:0 packages unchanged:0" --i really should have taken a screenshot cause i know i'm getting it wrong, but all 4 of them said "0".  I figured maybe i needed to re-boot before any changes would take effect, but after i got back in uname -r showed the old kernel (2.6.24-16-generic) and so did kernelcheck.  I go look in usr/src, and there are indeed a bunch of new files there for 2.6.25.  Is I'm sorry if this post is going on too long just trying to provide what info I can, if there is a log pls tell me i will post it.

Is there some step i missed or like i have to manually tell the system to switch over to using the new one?  Did refusing to update the boot menu mean it just didn't load the correct kernel? (just thought of that.. lol) Thanks for any help (and i hope this info helps you if there is indeed some bug), i hope it wasnt just me being dumb about the boot menu.ls..

Chris

---

### Post by master_kernel on 2008-06-27
> **dementic said:**
> Thank you I will try that :) 

Another question, if I delete the source can I have problems when compiling some others drivers or something like that?

It depends on if the drivers need the kernel source or not. Most good drivers use dkms though, so it shouldn't matter.

> I'm a big linux newb, (just got Ubuntu like 3 days ago) and i tried to up my kernel from the default to the latest stable version (2.6.25.9) using KernelCheck Hopestar v 1.1-beta3 build 17 (i clicked on the 2nd to last link on the origional post -- i did not click the final link, the RC version, because it was much smaller and the announcement said "do not check for updates in this version") -but I never got to running off the new kernel

1:did i mis-interprit? can i still use the rc1 version to update the kernel?
2: why is it so much smaller smaller?

3: So i run kernelchecker, and it goes through, scrolling things that give "warning: .........." i dont know, i just saw them, something about changing files around, i figured that's fine because that's what the program is meant to do.. eventually it comes up with a box to configure the kernel, I add some features (.config support for the kernal config, and mac80211 drivers for my intel 4965 wireless) and then hit save and close the config file, just hoping that closing it is the right choice to proceed, which it apparently was because the install continued, saying it might take 2-4 hours. When I come back, it asks me about booting and menu.ls (i think) and i didn't want to mess with changing that so i chose not to. Then it continues, installing kernel updates to .9 i think? then finally it ended up with a line going something like: "packages installed:0 packages upgraded:0 packages xxxx:0 packages unchanged:0" --i really should have taken a screenshot cause i know i'm getting it wrong, but all 4 of them said "0". I figured maybe i needed to re-boot before any changes would take effect, but after i got back in uname -r showed the old kernel (2.6.24-16-generic) and so did kernelcheck. I go look in usr/src, and there are indeed a bunch of new files there for 2.6.25. Is I'm sorry if this post is going on too long just trying to provide what info I can, if there is a log pls tell me i will post it.

Is there some step i missed or like i have to manually tell the system to switch over to using the new one? Did refusing to update the boot menu mean it just didn't load the correct kernel? (just thought of that.. lol) Thanks for any help (and i hope this info helps you if there is indeed some bug), i hope it wasnt just me being dumb about the boot menu.ls..

Chris

Here's your fix:
```
cd /usr/src
sudo dpkg -i *.deb
```
If it asks you to update your menu.lst, do it, or else your bootup menu will not be updated to include the new kernel.

On another note, the release candidate is so much smaller because the pdf file with the documentation has been removed from the package and instead posted on the KC website.

MK

---

### Post by mond0 on 2008-06-27
Hey thanks for the reply, I used the command above and it ran through, asked me to write over a file (new kernel module, i saved a backup, as it suggested just in case) and it said it was updating boot/grub/menu.lst, but I go into menu.lst and it is still the same.  Here is the relevant part of menu.lst:
```

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=40223ebe-1286-4eb7-bb4f-5ccbefd4ecee ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=40223ebe-1286-4eb7-bb4f-5ccbefd4ecee ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```
and here is what it gave me during install:
```

christopher@USB-Ubuntu:/usr/src$ sudo dpkg -i *.deb
[sudo] password for christopher: 
(Reading database ... 138089 files and directories currently installed.)
Preparing to replace linux-headers-2.6.25.9-ultimate 2.6.25.9-ultimate-10.00.Custom (using linux-headers-2.6.25.9-ultimate_2.6.25.9-ultimate-10.00.Custom_i386.deb) ...
Unpacking replacement linux-headers-2.6.25.9-ultimate ...
Preparing to replace linux-image-2.6.25.9-ultimate 2.6.25.9-ultimate-10.00.Custom (using linux-image-2.6.25.9-ultimate_2.6.25.9-ultimate-10.00.Custom_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.25.9-ultimate ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.25.9-ultimate
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Setting up linux-headers-2.6.25.9-ultimate (2.6.25.9-ultimate-10.00.Custom) ...

Setting up linux-image-2.6.25.9-ultimate (2.6.25.9-ultimate-10.00.Custom) ...
Running depmod.
Finding valid ramdisk creators.
Using mkinitramfs-kpkg to build the ramdisk.
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.25.9-ultimate-10.00.Custom was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.25.9-ultimate-10.00.Custom was configured last, according to dpkg)
Running postinst hook script update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.25.9-ultimate
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

christopher@USB-Ubuntu:/usr/src$

```

I noticed also that i have another kernel update installed (2.6.24-19-generic) but i am not running on that either.  Still on 16, the one i installed with (after installing i ran all suggested updates, including new kernel apparently).  I noticed the install looked for a "splash image" and didn't find any when under my menu.lst it says "quiet splash" is this normal?

Is there another way to edit menu.lst?  I would try myself but I don't know what UUID to use.

Thanks again master_kernel for your help earlier this seems to be my problem not one with kernelcheck.

Chris

---

### Post by shinji257 on 2008-06-27
Any chance you might be able to post your entire menu.lst file?

---

### Post by mond0 on 2008-06-27
Here it is: 
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=40223ebe-1286-4eb7-bb4f-5ccbefd4ecee ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=40223ebe-1286-4eb7-bb4f-5ccbefd4ecee ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=40223ebe-1286-4eb7-bb4f-5ccbefd4ecee ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title		Microsoft Windows XP Embedded
root		(hd0,4)
savedefault
chainloader	+1

```

When I installed, i actually had to do some maneuvering.  I'm running off a SDHC card connected via USB.  After installing, I would get to the boot menu, but nothing would happen when i hit to boot.  I checked out the problem online and found that i needed to manually edit menu.lst to point to: groot=(hd0,0), and root (hd0,0) for each of the kernel entries.  When i installed, these numbers were (hd1.0) because the install assumed i was on a hard drive?? (i think this was the reason, i looked around, followed the advice, and it worked, so that was good enough for me) then, when i tried to log into the desktop, the background would remain and nothing would load.  I found i had to manually update gnome-keyring, because something about USBs prevented a proper load in the 8.04 release, so i did that from the terminal too, though i don't know if that would affect the current problem.  But then even after running all the updates i was giver, (like 200) it never switched over to the new kernel, I've always been on the default install one.  I just found another thread  [http://ubuntuforums.org/showthread.php?t=499596](http://ubuntuforums.org/showthread.php?t=499596) do you guys think this could be my problem somehow?

Thanks for all the help
Chris

---

### Post by mond0 on 2008-06-27
A little more info: i installed everything to the USB.  I installed grub to USB and nothing is on my harddrive, my bios is set to boot to USB if it is found.

Chris

---

### Post by mond0 on 2008-06-27
Ok - i didn't really fix the problem, but i got it working.  I used qgrubedit (made me feel more comfortable) to edit menu.lst to add an option including the new kernel version, and it booted up to the new kernel fine. I just cant use my wireless on it yet.. 

Thanks to you guys for the help I'm glad there are people here that can offer some info to those like me just starting up :) 

-btw, great program master_kernel, i surely wouldn't be able to upgrade otherwise

Chris

---

### Post by master_kernel on 2008-06-27
> **mond0 said:**
> Ok - i didn't really fix the problem, but i got it working.  I used qgrubedit (made me feel more comfortable) to edit menu.lst to add an option including the new kernel version, and it booted up to the new kernel fine. I just cant use my wireless on it yet.. 

Thanks to you guys for the help I'm glad there are people here that can offer some info to those like me just starting up :) 

-btw, great program master_kernel, i surely wouldn't be able to upgrade otherwise

Chris
Thanks. :)

---

### Post by master_kernel on 2008-06-29
**ANNOUNCEMENT:** KernelCheck 1.1.4 HopeStar released!

---

### Post by Brando569 on 2008-06-30
never mind i found the python bindings for libvte, testing now ill let you know how it goes when im done. ive been waiting for this for about 4 months :D

edit:

i just got done compiling and it worked flawlessly! get yourself a beer, smoke a cigar or do whatever you do to celebrate something because you did an amazing job, apparently kernelcheck does something different when compiling a kernel then the script that i wrote awhile ago (which im pretty sure was initially based off your master kernel thread :confused:) because my intel hd audio worked perfectly immediately after i logged into kde. i was extremely skeptical at first because i tried pretty much everything and nothing worked. i used various tweaks that i found on here and other boards, i tried compiling a vanilla kernel, i tried disabling all audio devices except for the intel hd audio module under alsa, i tried recompiling alsa (which wouldnt compile for some reason) and nothing worked. i had pretty much given up hope and was about to buy a soundcard just so i could compile new kernels lol

once again great job, im glad i had to wait 4+ months for this to come out because it was definitely worth it.

---

### Post by erginemr on 2008-07-02
@master_kernel,

Kudos for this masterpiece!

This program has really made kernel compilation, which is traditionally regarded as a high-tech task for Linux geeks, a child's play. Thank you very much for all the effort you have put into the development of kernelcheck.

---

### Post by Harpoon on 2008-07-03
First, let me say this looks like a great piece of work.  Add me as a +1 on that score.

However, I have a few (embarrassing) questions concerning the meaning/use of some gui options.

My intention was to compile the 2.6.26 kernel after disabling a truckload of things I do not/will never have use for on this laptop--e.g., LVM, NFS, Acorn support, Touchscreen,...etc).  After getting the kernel information updated properly, I set the checkbox to "Confingure the kernel" (or similar), and left configure X unchecked.  Invoking "build kernel" started the process, which continued to the point of asking how to handle the grub menu list (that is a separate question, below).  After selecting (something) there, the build continued to the end, but without any option to change the kernel configuration (no makemenu appeared).  I apparently have a compiled 2.6.25 kernel with all options including a cold fusion powered toilet compiled into the kernel (from a post compile inspection). (ugh)

This begs the question, "did I err in making this menu selection, is the description misleading, or is there some other problem I am not smart enough to see?"  Any help here would be greatly appreciated.

As to the grub menu list option, I must admit embarrassment that my best efforts to parse the displayed options to figure out what to choose was utterly depressing.  If I want the newly compiled kernel to show up in  the list, which is the correct choice?  Grub did not update for me, the program crashed, and required a system restart.  I can fix this by updating grub manually, but I am curious where my error is.

Apart from the above (and the grub menu thing is probably just me not being able to shift my thinking), I think you are on to one of the biggest advances in usability that we have seen in a long, long, time.

If expecting to trim the fat out of the kernel using this tool is more than it was intended to do, no problem.  There is a case to be made for doing it the old-fashioned way.

Again, thanks for any insights.  I will slink into lurk mode to preserve what little dignity I have left.


Lenovo 3000/N100 core2duo laptop; intel graphics, sound, and wifi.

---

### Post by Brando569 on 2008-07-06
also kernelcheck wont run on kubuntu unless you know or already have the libraries that it needs. I forget what I did to fix this before but I keep getting this error:

```
Traceback (most recent call last):
  File "/usr/bin/kernelcheck", line 9, in <module>
    import KernelCheck.main, os, gtk, sys
  File "/usr/lib/python2.5/site-packages/KernelCheck/main.py", line 20, in <module>
    import gnome.ui
ImportError: No module named gnome.ui
```

could you add something in the next version (or maybe a minor update) that checks to see if you have the correct dependencies? sometimes hunting down these dependencies is harder then compiling the kernel itself :?

---

### Post by the8thstar on 2008-07-06
Hello,

Will I be able to automount UFS partitions (OpenSolaris) if I upgrade to the latest kernel through KernelCheck?

---

### Post by ForksHolder on 2008-07-06
A question:

Does KernelCheck can auto configure itself or it will can in the next version?

Thanks.

---

### Post by Brando569 on 2008-07-06
> **the8thstar said:**
> Hello,

Will I be able to automount UFS partitions (OpenSolaris) if I upgrade to the latest kernel through KernelCheck?

you should be able to as long as the UFS modules are compiled in with the kernel.

> **ForksHolder said:**
> A question:

Does KernelCheck can auto configure itself or it will can in the next version?

Thanks.

yes it can, there is an option for this that is usually checked that says "configure kernel manually" and if you want everything to be automatic you just uncheck it. it is highly recommended that you configure the kernel yourself, give it a try :D

---

### Post by traxk on 2008-07-07
RE: KernelCheck HopeStar version 1.14
a- option: "running kernel" doesn`t show rc version
b- no sound although sound device detected (kernel 2.26.26-rc8/2.26-rc9)
c- configuration tab, ALSA  marked as module, PCI>IHDA marked as module, CMI8738 selected
d- Ubuntu 8.04.1, kernel 2.6.26-rc9-ultimate root (hd0,4) kernel /boot/vmlinuz-2.6.26-rc9-ultimate root=UUID=1e6acda7-9e2b-4af7-a286-840bfa850a79 ro quiet
   splash initrd /boot/initrd.img-2.6.26-rc9-ultimate quiet

   Ubuntu 8.04.1, kernel 2.6.26-rc8-kernelcheck root (hd0,4) kernel /boot/vmlinuz-2.6.26-rc8-kernelcheck root=UUID=1e6acda7-9e2b-4af7-a286-840bfa850a79 ro
   quiet splash initrd /boot/initrd.img-2.6.26-rc8-kernelcheck
e- boot-screen shows three progress bars instead of one 
f- I am runnig a Dell-Dimension2400/IntelCeleron CPU 2.60GHz dual boot WXP-h/SP3 + Linux-Ubuntu 8.04.1
g- anything ells I can do!?

---

### Post by master_kernel on 2008-07-07
> **Harpoon said:**
> First, let me say this looks like a great piece of work.  Add me as a +1 on that score.

However, I have a few (embarrassing) questions concerning the meaning/use of some gui options.

My intention was to compile the 2.6.26 kernel after disabling a truckload of things I do not/will never have use for on this laptop--e.g., LVM, NFS, Acorn support, Touchscreen,...etc).  After getting the kernel information updated properly, I set the checkbox to "Confingure the kernel" (or similar), and left configure X unchecked.  Invoking "build kernel" started the process, which continued to the point of asking how to handle the grub menu list (that is a separate question, below).  After selecting (something) there, the build continued to the end, but without any option to change the kernel configuration (no makemenu appeared).  I apparently have a compiled 2.6.25 kernel with all options including a cold fusion powered toilet compiled into the kernel (from a post compile inspection). (ugh)

This begs the question, "did I err in making this menu selection, is the description misleading, or is there some other problem I am not smart enough to see?"  Any help here would be greatly appreciated.

As to the grub menu list option, I must admit embarrassment that my best efforts to parse the displayed options to figure out what to choose was utterly depressing.  If I want the newly compiled kernel to show up in  the list, which is the correct choice?  Grub did not update for me, the program crashed, and required a system restart.  I can fix this by updating grub manually, but I am curious where my error is.

Apart from the above (and the grub menu thing is probably just me not being able to shift my thinking), I think you are on to one of the biggest advances in usability that we have seen in a long, long, time.

If expecting to trim the fat out of the kernel using this tool is more than it was intended to do, no problem.  There is a case to be made for doing it the old-fashioned way.

Again, thanks for any insights.  I will slink into lurk mode to preserve what little dignity I have left.


Lenovo 3000/N100 core2duo laptop; intel graphics, sound, and wifi.

These are perfectly valid questions, don't be hard on yourself.
Here are some suggestions/tips:

[LIST=1]
[*]Configure kernel option manually is automatically selected when KernelCheck starts. This causes a configuration window to appear when it is time to configure the kernel.
[*]Make sure you include your Wireless LAN modules in your kernel, ALSA sound, and the Intel HD audio module
[*]When the dialog in the terminal asks you if you want to replace your GRUB list with the maintainer's version, allow it
[/LIST]

---

### Post by master_kernel on 2008-07-07
> **traxk said:**
> RE: KernelCheck HopeStar version 1.14
a- option: "running kernel" doesn`t show rc version
b- no sound although sound device detected (kernel 2.26.26-rc8/2.26-rc9)
c- configuration tab, ALSA  marked as module, PCI>IHDA marked as module, CMI8738 selected
d- Ubuntu 8.04.1, kernel 2.6.26-rc9-ultimate root (hd0,4) kernel /boot/vmlinuz-2.6.26-rc9-ultimate root=UUID=1e6acda7-9e2b-4af7-a286-840bfa850a79 ro quiet
   splash initrd /boot/initrd.img-2.6.26-rc9-ultimate quiet

   Ubuntu 8.04.1, kernel 2.6.26-rc8-kernelcheck root (hd0,4) kernel /boot/vmlinuz-2.6.26-rc8-kernelcheck root=UUID=1e6acda7-9e2b-4af7-a286-840bfa850a79 ro
   quiet splash initrd /boot/initrd.img-2.6.26-rc8-kernelcheck
e- boot-screen shows three progress bars instead of one 
f- I am runnig a Dell-Dimension2400/IntelCeleron CPU 2.60GHz dual boot WXP-h/SP3 + Linux-Ubuntu 8.04.1
g- anything ells I can do!?
Does this happen when you compile a normal stable kernel as well?

---

### Post by traxk on 2008-07-08
@Master_KernelCheck,
1-RE: My posts #207/209 and #211 (Kernel 2.6.25) No sound...device is busy, invalid argument, audio output unavailable etc.
2-Kernel 2.6.25 stable kernel!?
3-Third attempt after two failures this time using KernelCheck HopeStar version 1.14 Building kernel 2.6.26-rc9 on Fresh install updated OS Ubuntu 8.04.1
4-Dell Pc on-board sound card 'OFF' 
5-PCI 'Enabled' (Sweex 5.1 PCI sound card) 
6-Sweex 5.1 Works well with WXP-h/3SP and Ubuntu 8.04.1/kernel 2.6.24-19
7-I have done configuration (file saved) as per your advice. (your post 208)
8-Kernel 2.6.26-26-rc9 performs well (besides audio/boot-screen issues) 
   Traxk

---

### Post by master_kernel on 2008-07-09
> **traxk said:**
> @Master_KernelCheck,
1-RE: My posts #207/209 and #211 (Kernel 2.6.25) No sound...device is busy, invalid argument, audio output unavailable etc.
2-Kernel 2.6.25 stable kernel!?
3-Third attempt after two failures this time using KernelCheck HopeStar version 1.14 Building kernel 2.6.26-rc9 on Fresh install updated OS Ubuntu 8.04.1
4-Dell Pc on-board sound card 'OFF' 
5-PCI 'Enabled' (Sweex 5.1 PCI sound card) 
6-Sweex 5.1 Works well with WXP-h/3SP and Ubuntu 8.04.1/kernel 2.6.24-19
7-I have done configuration (file saved) as per your advice. (your post 208)
8-Kernel 2.6.26-26-rc9 performs well (besides audio/boot-screen issues) 
   Traxk

[LIST]
[*]I've done some searching around, and the module you need to enable in your kernel is *C-Media 8338, 8738, 8768, 8770* (if it is not already enabled)
[*]If that does not solve the problem, try adding the module to every boot sequence
```
gksudo gedit /etc/modules
```
Add snd-cmipci to the end of the file (if not already there)
Example:
> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

snd-cmipci
[*]As for the boot screen, try removing anything that says vga=XXX in your GRUB menu.lst (/boot/grub/menu.lst)
[/LIST]

---

### Post by traxk on 2008-07-11
@Master_Kernel,
(your post #258)
1--have added "snd-cmipci" to /etc/modules...no sound progress
2--re:/boot/grub/menu.lst...have remove "=vga=791"...no difference  
3--meanwhile kernel 2.6.24-19 now suffers same sound issues
4--on both kernels ff3 now plays flash-video with sound (You Tube/News sites)
5--media players are striking...(rhythm-box, vlc, mplayer, totem)
6--cmi8338/8738 files in /usr/share/alsa/cards and /proc/asound
7--I think one important file has been removed!?
8--sound was perfect running kernel 2.6.24-16/17/18/19
9--"good sound" on WXP-h/SP3 using same Sweex 5.1 sound card
10-no calammity here I am testing your software "KernelCheck"

Ps.:ALSA/PCI-IHDA and CMI are enabled on configuration tab

---

### Post by master_kernel on 2008-07-11
> **traxk said:**
> @Master_Kernel,
(your post #258)
1--have added "snd-cmipci" to /etc/modules...no sound progress
2--re:/boot/grub/menu.lst...have remove "=vga=791"...no difference  
3--meanwhile kernel 2.6.24-19 now suffers same sound issues
4--on both kernels ff3 now plays flash-video with sound (You Tube/News sites)
5--media players are striking...(rhythm-box, vlc, mplayer, totem)
6--cmi8338/8738 files in /usr/share/alsa/cards and /proc/asound
7--I think one important file has been removed!?
8--sound was perfect running kernel 2.6.24-16/17/18/19
9--"good sound" on WXP-h/SP3 using same Sweex 5.1 sound card
10-no calammity here I am testing your software "KernelCheck"

Ps.:ALSA/PCI-IHDA and CMI are enabled on configuration tab
Oh, run *sudo update-grub* to update your menu.lst and make sure it does not re-add a VGA option.

It sounds like a very important sound package has been removed...

---

### Post by isaacj87 on 2008-07-11
@master_kernel:

I had a couple questions for you...I was planning on using some of your code to make my own program (more specifically I'm using KernelCheck as a reference/tool/guide to learn from, I'm a noob hobbyist programmer). I fully intended to get credit where it is deserved...Is is okay with you?

With that said, how is KernelCheck able to build the kernel without ever asking the user for the root password?

---

### Post by chrisblue on 2008-07-12
I am having a similar sound problem after compiling a new kernel with KernelCheck 1.1.4.

Originally running Ubuntu 8.04.1, kernel 2.6.24-19-generic however needed to increase the timer rate (so an IR remote would be reliably detected)

Did one compile with the performance patch to Ubuntu 8.04.1, kernel 2.6.25-ultimate, changed the scan rate option and checked the ALSA option in the configuration dialogue and found that there were no sound drivers installed although Ubuntu can at least see the hardware.

```
chris@dogbox:~$ lspci -v
<<snip>>

00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
    Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
    I/O ports at dc00 [size=256]
    I/O ports at e000 [size=256]
    Memory at d6003000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>


```Recompiled again with the performance patch but this time with only the scan rate changed iin the config. Ubuntu 8.04.1, kernel 2.6.25.10-ultimate. Again same problem with no sound.

Removed and reinstalled the ALSA drivers with 

[SIZE=2]```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
```[/SIZE]```
[SIZE=2]sudo apt-get install linux-sound-base alsa-base alsa-utils[/SIZE]
```Also tried to compile them from source using module-assistant which seemed to work but still no sound.

Tried a new kernel compile this time with no patches applied and checking all the ALSA options that seemed to relate to my card (ie intelx80 driver) and again everything seems to work fine except no sound - the new scan frequency works great though :)

So as you said it looks like some critical sound files are being missed out somewhere.

Cheers

---

### Post by larryfroot on 2008-07-13
Exactly the same problem here...hopestar used and sound spannered. Have also done all that the previous respondents have with the same unhappy result. Any help would be most appreciated. Thanks!

---

### Post by master_kernel on 2008-07-13
> **isaacj87 said:**
> @master_kernel:

I had a couple questions for you...I was planning on using some of your code to make my own program (more specifically I'm using KernelCheck as a reference/tool/guide to learn from, I'm a noob hobbyist programmer). I fully intended to get credit where it is deserved...Is is okay with you?

With that said, how is KernelCheck able to build the kernel without ever asking the user for the root password?
Of course you can use my code, thats what GPL is for after all! :)

KernelCheck is started up with a 'gksu' command, which is exactly like running the program as root. (ex: gksu kernelcheck)

When it is not run as root, it pops out an error message.

---

### Post by master_kernel on 2008-07-13
> **chrisblue said:**
> I am having a similar sound problem after compiling a new kernel with KernelCheck 1.1.4.

Originally running Ubuntu 8.04.1, kernel 2.6.24-19-generic however needed to increase the timer rate (so an IR remote would be reliably detected)

Did one compile with the performance patch to Ubuntu 8.04.1, kernel 2.6.25-ultimate, changed the scan rate option and checked the ALSA option in the configuration dialogue and found that there were no sound drivers installed although Ubuntu can at least see the hardware.

```
chris@dogbox:~$ lspci -v
<<snip>>

00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
    Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
    I/O ports at dc00 [size=256]
    I/O ports at e000 [size=256]
    Memory at d6003000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>


```Recompiled again with the performance patch but this time with only the scan rate changed iin the config. Ubuntu 8.04.1, kernel 2.6.25.10-ultimate. Again same problem with no sound.

Removed and reinstalled the ALSA drivers with 

[SIZE=2]```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
```[/SIZE]```
[SIZE=2]sudo apt-get install linux-sound-base alsa-base alsa-utils[/SIZE]
```Also tried to compile them from source using module-assistant which seemed to work but still no sound.

Tried a new kernel compile this time with no patches applied and checking all the ALSA options that seemed to relate to my card (ie intelx80 driver) and again everything seems to work fine except no sound - the new scan frequency works great though :)

So as you said it looks like some critical sound files are being missed out somewhere.

Cheers
Here's your solution:

At the configuration window for the kernel, under ALSA > PCI Devices you need to enable Intel/SiS/nVidia/AMD/ALi AC97 Controller (shown in the attachment).

> Exactly the same problem here...hopestar used and sound spannered. Have also done all that the previous respondents have with the same unhappy result. Any help would be most appreciated. Thanks!

Can you post the output of:
```
lspci -v | grep "Audio"
```

Master Kernel

---

### Post by chrisblue on 2008-07-14
I'll give that a try tonight when I am back in front of my PC. I would like to get rid of the crappy compiles I have done though. Is that just a matter of deselecting them using the package manager whilst booted up with the last good one, then editing the grub menu to remove those entries?

Also is there any facility in KernelCheck to build using an older kernel?

---

### Post by master_kernel on 2008-07-14
> **chrisblue said:**
> I'll give that a try tonight when I am back in front of my PC. I would like to get rid of the crappy compiles I have done though. Is that just a matter of deselecting them using the package manager whilst booted up with the last good one, then editing the grub menu to remove those entries?

Also is there any facility in KernelCheck to build using an older kernel?
1. All you have to do is remove the packages in Synaptic, then run "sudo update-grub" in a terminal.

2. Sorry, at the moment there is no easy way to build an older kernel in KernelCheck without hacking the program. If you would like to find out how to do this, let me know.

MK

---

### Post by Blinkiz on 2008-07-15
Hacking section sounds interesting. One +1 for that one! :)

---

### Post by traxk on 2008-07-15
@Master_Kernel
1--Thanks to kernel version 2.6.26 I have got sound again on my Pc; even greetings-sound works
2--No Ubuntu boot-screen comes with this final version; black-screen
3--The kernel boots start and runs but screen stays black; grub fails!?
4--I have to manually start the kernel; on boot-menu I select which kernel to start than  press 'e'> kernel> 'b'
5--Ubuntu version 8.04.1/2.6.19-
Thanks

---

### Post by master_kernel on 2008-07-15
> **traxk said:**
> @Master_Kernel
1--Thanks to kernel version 2.6.26 I have got sound again on my Pc; even greetings-sound works
2--No Ubuntu boot-screen comes with this final version; black-screen
3--The kernel boots start and runs but screen stays black; grub fails!?
4--I have to manually start the kernel; on boot-menu I select which kernel to start than  press 'e'> kernel> 'b'
**5--Ubuntu version 8.04.1/2.6.19-**
Thanks

[LIST=1]
[*]What do you mean by the bolded line above?
[*]Does the boot screen work right with another kernel? If so make sure you did not enable the boot logo option in the kernel. It is not enabled by default.
[*]Try running 'sudo update-grub' and 'grub-install hd0'
[/LIST]

MK

---

### Post by Blinkiz on 2008-07-16
I would like KernelCheck to work with distcc.
distcc only works when running as a user that is not root. KernelCheck is running make-kpkg as root. Anyone has a solution?

---

### Post by traxk on 2008-07-16
@Master_Kernel
re:your post #270,

1--re:item '5' on list post #269...[Issued first week July]>> the Ubuntu OS version 8.04.1 lts with kernel 2.6.19
2--The Ubuntu boot-screen with progress-bar was OK with kernel 2.6.19 but vanished afterwards
3--I haven`t touch the boot-logo option
4--I have run in terminal both commands "sudo update-grub and grub-install hd0" ....no improvement
5--Shut down-screen shows for a short period of time vertical red/white stripes
6--Kernel 2.6.26 feels stable and I will keep-on testing your software
Thanks

---

### Post by traxk on 2008-07-16
@Master_Kernel
re:last post #272 
1--first item:sorry for omission...Pls read "kernel 2.6.24-19"
2--Linux image updated today (July 16 2008) to version 2.6.24-19.36
3--The boot-menu is back to normal ('e' and 'b' not any more necessary)
4--No Ubuntu boot-screen at start-up 
Thanks

---

### Post by Totson on 2008-07-19
@Master_Kernel
First of all : THANKS FOR THIS NICE PIECE OF SOFTWARE !!!

Just wanted to gice some feedback. Installed the deb package on a striped down version of 8.04.1 running a custom kernel build vith previous kernelcheck on another host. Just wanted to report those 2 small glitches I noticed :

- the deb requests dependance on python2.4, while python (v2.5) is installed. "apt-get -f ..." installs python2.4 and then kernelcheck uses default python anyways ... so now I have python2.4 uselessly installed :-)

- also, python-vte (in ubuntu) is required for kernelcheck to run. Had to install it. So it may be a good idea to put as a dependency to the package.

Thanks again for your excellent tool !!!
Cheers !

---

### Post by chrisblue on 2008-07-20
> **master_kernel said:**
> Here's your solution:

At the configuration window for the kernel, under ALSA > PCI Devices you need to enable Intel/SiS/nVidia/AMD/ALi AC97 Controller (shown in the attachment).



Thanks for this. All worked well. Don't think I am up to hacking KernelCheck to use an older kernel but it would be nice to stay with the same kernel if all you wanted to do was change a few settings and recompile. Maybe a feature for down the track?

Anyway thanks a lot for the utility. It make what looked like a painful task a lot simpler and almost noob friendly :)

Cheers.

---

### Post by LarryEdwards on 2008-07-21
After running KernelCheck my 2.6.26 ultimate system hangs at
Starting up . . .
Decompressing Linux . . . Parsing ELF . . . done
Booting the kernel 
[ 0.297095] ACPI: EC: GPE storm detected, disabling EC GPE

If I start up in recovery mode I get to 
[ 0.257142] ACPI : Using IOAPIC for interrupt routing



I have a Toshiba laptop A215-S7422 dual booted with Vista. Am running 8.04.1 with 2.6.24-19 kernel and trying to upgrade to 2.6.26 so my Realtek wireless card will work.

I am a weary, but committed newbie.

---

### Post by onewithnature83 on 2008-07-27
LarryEdwards,

> I have a Toshiba laptop A215-S7422 dual booted with Vista. Am running 8.04.1 with 2.6.24-19 kernel and trying to upgrade to 2.6.26 so my Realtek wireless card will work.

I too have the same wireless chipset. I was told that it would not be untill 2.6.27 would the kernel module be added for the rtl8187b chip=set.

Please share your experience, and results with this Kernel 2.6.26 upgrade goes. 

I am also attempting this.

You can find more information on making it work here:

[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)

you will also find my e-mail there.

I apologize to for the off-topic post.

--TJ onewithnature83

Thank you to the developer and all who made this possible for all of us.

---

### Post by logos34 on 2008-07-27
I just used your program.  Successful (man it boots like a rocket now!)

One problem though:

I now have a HUGE folder in /usr/src  called "linux-2.6.26" of ~2.4 GB!!!  

Can I get rid of it?

Edit: also, restricted drivers refuses to show nvidia drivers in use...can't run nvidia-settings.  nvidia-xconfig doesn't configure.  No change even after installing the nvidia proprietary driver via EnvyNG.  (paravirtualization was set 'off' in qconf). But I got xserver to start finally by simply copying my old xorg.conf file and using that

---

### Post by master_kernel on 2008-08-02
> **logos34 said:**
> I just used your program.  Successful (man it boots like a rocket now!)

One problem though:

I now have a HUGE folder in /usr/src  called "linux-2.6.26" of ~2.4 GB!!!  

Can I get rid of it?

Edit: also, restricted drivers refuses to show nvidia drivers in use...can't run nvidia-settings.  nvidia-xconfig doesn't configure.  No change even after installing the nvidia proprietary driver via EnvyNG.  (paravirtualization was set 'off' in qconf). But I got xserver to start finally by simply copying my old xorg.conf file and using that
You can get rid of that folder.
And which version of the nVidia driver does Envy compile?

---

### Post by master_kernel on 2008-08-02
> **traxk said:**
> @Master_Kernel
re:last post #272 
1--first item:sorry for omission...Pls read "kernel 2.6.24-19"
2--Linux image updated today (July 16 2008) to version 2.6.24-19.36
3--The boot-menu is back to normal ('e' and 'b' not any more necessary)
4--No Ubuntu boot-screen at start-up 
Thanks
Make sure you don't disable anything in the kernel configuration unless you're entirely sure about what it does. Also, make sure your graphics card is selected.

---

### Post by logos34 on 2008-08-02
> **master_kernel said:**
> You can get rid of that folder.
And which version of the nVidia driver does Envy compile?

envy has three to choose from, the latest being 173.14.09 (which is what I tried).

It turns out I just needed to point it ('--kernel-source-path=') to the linux-2.6.26 folder rather than the linux-headers folder in /usr/src.  I managed to drastically reduce the size of the folder by compiling it manually with the prefix **INSTALL_MOD_STRIP=1** fakeroot make-kpkg...

folder now averages ~500-600  mb, which is more like it

---

### Post by logos34 on 2008-08-02
funny, I just installed the latest 2.26.6.1 kernel on my regular ubuntu studio partition, but for the life of me the nvidia driver will not go in--gives me the familiar complaint about the /usr/lib32/libnvidia-173.14.so.1 not being where it should, etc.  I uninstalled, then deleted the leftover libnv* files (in tls/ subfolder too).  Tried installation a second time but same thing.

I ran into this problem when I was did a test run on another partition but managed after a few tries to get it to install.  So I know the 173.14.09.pkg2.run driver works.  Why is it fighting me?

---

### Post by master_kernel on 2008-08-11
Thread cleaned up, and added a tutorial for how to install the devel version.
MK

---

### Post by master_kernel on 2008-08-19
Poll added for feature request for Lumen.

---

### Post by foxy123 on 2008-08-25
Great programme! Thanks a lot for that. I used to compile kernel manually but it saves a lot of hassle. 

The only wee of problem I have is that after compiling a new kernel I cannot launch terminal as it complains something about 'child process' and Thunderbird suddenly freezes taking up 100% of resources. I guess I selected/unselected something wrongly but I do not know what.

---

### Post by RATM_Owns on 2008-08-26
It doesn't have audio support for mine.


Anyways, great app. Keep up the good work.

---

### Post by of_darkness on 2008-08-27
I have tried to purge and reinstall the exmap packages but still it gives this error and kernbel is not bootable

64bit hardy 

error message from hopstar

```
make -C /lib/modules/2.6.26.3-ultimate/build M=/usr/src/modules/exmap modules
make[4]: Går till katalogen "/usr/src/linux-2.6.26"
  CC [M]  /usr/src/modules/exmap/exmap.o
/usr/src/modules/exmap/exmap.c: I funktion "init_module":
/usr/src/modules/exmap/exmap.c:510: fel: "proc_root" är odeklarerad (första förekomsten i denna funktion)
/usr/src/modules/exmap/exmap.c:510: fel: (Varje odeklarerad identifierare rapporteras bara en gång
/usr/src/modules/exmap/exmap.c:510: fel: för varje funktion den finns i.)
/usr/src/modules/exmap/exmap.c: I funktion "cleanup_module":
/usr/src/modules/exmap/exmap.c:535: fel: "proc_root" är odeklarerad (första förekomsten i denna funktion)
make[5]: *** [/usr/src/modules/exmap/exmap.o] Fel 1
make[4]: *** [_module_/usr/src/modules/exmap] Fel 2
make[4]: Lämnar katalogen "/usr/src/linux-2.6.26"
make[3]: *** [kernel_modules] Fel 2
make[3]: Lämnar katalogen "/usr/src/modules/exmap"
make[2]: *** [binary-modules] Fel 2
make[2]: Lämnar katalogen "/usr/src/modules/exmap"
make[1]: *** [kdist_build] Fel 2
make[1]: Lämnar katalogen "/usr/src/modules/exmap"
Module /usr/src/modules/exmap failed.
Hit return to Continue


```

translation of important swedish words:
odeklarerad=undifined
Fel=error
Lämnar katalogen=leving directory
Går till katalogen=goes to directory

---

### Post by Mikolaj.Q on 2008-08-28
Hi,

Thanks for your great program. I've been using it many times with a full success. But now i have a small problem. I use **Kubuntu** 8.04.1 and Hopestar from repo didn't work, so i tried experimental version. I downloaded the program from bzr (rev 10). Installation is ok, but i can not launch it. 

This is console output:

bogdan@icy:~/Pulpit/Nowy katalog_1$ sudo kernelcheck
Traceback (most recent call last):
  File "/usr/bin/kernelcheck", line 9, in <module>
    import KernelCheck.main, os, gtk, sys
  File "/usr/lib/python2.5/site-packages/KernelCheck/main.py", line 28, in <module>
    import pango
ImportError: No module named pango
bogdan@icy:~/Pulpit/Nowy katalog_1$    

What should I install to run the program? I've installed everything from repo with "pango" in name - didn't help. I have no idea what to do.

---

### Post by master_kernel on 2008-08-28
> **of_darkness said:**
> I have tried to purge and reinstall the exmap packages but still it gives this error and kernbel is not bootable

64bit hardy 

error message from hopstar

```
make -C /lib/modules/2.6.26.3-ultimate/build M=/usr/src/modules/exmap modules
make[4]: Går till katalogen "/usr/src/linux-2.6.26"
  CC [M]  /usr/src/modules/exmap/exmap.o
/usr/src/modules/exmap/exmap.c: I funktion "init_module":
/usr/src/modules/exmap/exmap.c:510: fel: "proc_root" är odeklarerad (första förekomsten i denna funktion)
/usr/src/modules/exmap/exmap.c:510: fel: (Varje odeklarerad identifierare rapporteras bara en gång
/usr/src/modules/exmap/exmap.c:510: fel: för varje funktion den finns i.)
/usr/src/modules/exmap/exmap.c: I funktion "cleanup_module":
/usr/src/modules/exmap/exmap.c:535: fel: "proc_root" är odeklarerad (första förekomsten i denna funktion)
make[5]: *** [/usr/src/modules/exmap/exmap.o] Fel 1
make[4]: *** [_module_/usr/src/modules/exmap] Fel 2
make[4]: Lämnar katalogen "/usr/src/linux-2.6.26"
make[3]: *** [kernel_modules] Fel 2
make[3]: Lämnar katalogen "/usr/src/modules/exmap"
make[2]: *** [binary-modules] Fel 2
make[2]: Lämnar katalogen "/usr/src/modules/exmap"
make[1]: *** [kdist_build] Fel 2
make[1]: Lämnar katalogen "/usr/src/modules/exmap"
Module /usr/src/modules/exmap failed.
Hit return to Continue


```

translation of important swedish words:
odeklarerad=undifined
Fel=error
Lämnar katalogen=leving directory
Går till katalogen=goes to directory
Try apt-get build-dep PACKAGES.

---

### Post by master_kernel on 2008-08-28
> **Mikolaj.Q said:**
> Hi,

Thanks for your great program. I've been using it many times with a full success. But now i have a small problem. I use **Kubuntu** 8.04.1 and Hopestar from repo didn't work, so i tried experimental version. I downloaded the program from bzr (rev 10). Installation is ok, but i can not launch it. 

This is console output:

bogdan@icy:~/Pulpit/Nowy katalog_1$ sudo kernelcheck
Traceback (most recent call last):
  File "/usr/bin/kernelcheck", line 9, in <module>
    import KernelCheck.main, os, gtk, sys
  File "/usr/lib/python2.5/site-packages/KernelCheck/main.py", line 28, in <module>
    import pango
ImportError: No module named pango
bogdan@icy:~/Pulpit/Nowy katalog_1$    

What should I install to run the program? I've installed everything from repo with "pango" in name - didn't help. I have no idea what to do.
Did you install libpango1.0-common?

---

### Post by of_darkness on 2008-08-28
> **master_kernel said:**
> Try apt-get build-dep PACKAGES.

   > apt-get build-dep exmap exmap-modules-source Läser paketlistor... Färdig Bygger beroendeträd Läser tillståndsinformation... Färdig 0 uppgraderade, 0 nyinstallerade, 0 att ta bort och 267 ej uppgraderade. [ root: /home/blutengel ]#                                              any other ideas?

---

### Post by Crafty Kisses on 2008-08-28
This is awesome, thanks for this!

---

### Post by Mikolaj.Q on 2008-08-28
bogdan@icy:~/Pulpit/Nowy katalog_1$ sudo kernelcheck
Traceback (most recent call last):
File "/usr/bin/kernelcheck", line 9, in <module>
import KernelCheck.main, os, gtk, sys
File "/usr/lib/python2.5/site-packages/KernelCheck/main.py", line 28, in <module>
import pango
ImportError: No module named pango
bogdan@icy:~/Pulpit/Nowy katalog_1$

######################

Did you install libpango1.0-common?

#######################

Yes I did, no success. 
Good news is, that at least I could launch kernelcheck. It was possible after I've install startupmanager, which has a lot of gnome libs dependencies. Previously i was using ubuntu (gnome) and i had no problems. Unfortunately i don't know which particular package is responsible for my happiness. It would be good to find it out and add this package to lumen dependencies. Thank You for express response, and great job, of course.

---

### Post by hanzomon4 on 2008-08-29
How can I use this to install the development branch of the linux kernel like the 2.6.27-rc* kernels?

---

### Post by hanzomon4 on 2008-08-30
Nevermind, I see that I just needed to use the dev patch. I wanted the ath9k driver....

---

### Post by master_kernel on 2008-08-31
> **of_darkness said:**
> any other ideas?
Are you using a normal Ubuntu Gnome install?

---

### Post by master_kernel on 2008-08-31
> **Mikolaj.Q said:**
> bogdan@icy:~/Pulpit/Nowy katalog_1$ sudo kernelcheck
Traceback (most recent call last):
File "/usr/bin/kernelcheck", line 9, in <module>
import KernelCheck.main, os, gtk, sys
File "/usr/lib/python2.5/site-packages/KernelCheck/main.py", line 28, in <module>
import pango
ImportError: No module named pango
bogdan@icy:~/Pulpit/Nowy katalog_1$

######################

Did you install libpango1.0-common?

#######################

Yes I did, no success. 
Good news is, that at least I could launch kernelcheck. It was possible after I've install startupmanager, which has a lot of gnome libs dependencies. Previously i was using ubuntu (gnome) and i had no problems. Unfortunately i don't know which particular package is responsible for my happiness. It would be good to find it out and add this package to lumen dependencies. Thank You for express response, and great job, of course.
Thanks, I'll try and hunt down this dependency.

---

### Post by of_darkness on 2008-09-01
> **master_kernel said:**
> Are you using a normal Ubuntu Gnome install?

 normal? well im primarly using kde3(kubuntu) but have both installed..

---

### Post by yosemite610 on 2008-09-09
I finally got past my alsa-drivers error but I'm noticing the Lumen window is not interactive.

It's stopping with the question: > Do you wish to reconfigure the X server now? [Y/n]
But I can't click in or type in the window. Screenshot below.

---

### Post by banditos on 2008-09-15
How can I install RC kernel. For example I have 2.6.26 kernel, your program says that I have the latest version but I want 2.6.27 kernel - is it possible ? Could you answer ?

---

### Post by risker on 2008-09-29
Hey,

i want to try your kernelcheck, but i have to use a proxyserver ... my Env is working correct, but it seems your program doesn't like proxies...is there are way to use it behind a proxyserver?

Best regards,
risker

---

### Post by master_kernel on 2008-11-04
Proxy support will be added in the next version.

---

### Post by Gary.M on 2008-11-08
Is kernelcheck OK with Intrepid?

---

### Post by killersnowgoon on 2008-11-09
hey, ive used kernelcheck many times on a 32bit install of hardy heron and it worked great, but i upgraded to 64bit intrepid, and i can get to configuring the kernel, but once it tries to make it, i get this error:

make[1]: Entering directory '/usr/src/linux-2.6.27'
Makefil:518: /usr/src/linux-2.6.27/arch/xen/Makefile: No such file or directory
make[1]: *** No rule to make target '/usr/src/linux-2.6.27/arch/xen/Makefile'. Stop.
make[1]: Leaving directory 'usr/src/linux-2.6.27/
make: *** [minimul_clean] Error 2

ABORT: stage5 returned exit status 2

any ideas?

---

### Post by killersnowgoon on 2008-11-12
> **killersnowgoon said:**
> hey, ive used kernelcheck many times on a 32bit install of hardy heron and it worked great, but i upgraded to 64bit intrepid, and i can get to configuring the kernel, but once it tries to make it, i get this error:

make[1]: Entering directory '/usr/src/linux-2.6.27'
Makefil:518: /usr/src/linux-2.6.27/arch/xen/Makefile: No such file or directory
make[1]: *** No rule to make target '/usr/src/linux-2.6.27/arch/xen/Makefile'. Stop.
make[1]: Leaving directory 'usr/src/linux-2.6.27/
make: *** [minimul_clean] Error 2

ABORT: stage5 returned exit status 2

any ideas?

bump

---

### Post by killersnowgoon on 2008-11-16
anyone here?

---

### Post by andyrogers2008 on 2008-11-18
Yep I have also got this same problem using Intrepid

andy

---

### Post by jklasdf on 2008-11-19
see bug # [280173]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/280173")

---

### Post by techmin on 2008-11-20
Thi problem is relate to this Debian bug
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=446879](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=446879)

Add --arch=am64 --subarch=x86_64 when calling make-kpkg
or your arch and subarch specify for your architecture

bug on ubuntu launchpad
[https://bugs.launchpad.net/ubuntu/+source/kernel-package/+bug/281699](https://bugs.launchpad.net/ubuntu/+source/kernel-package/+bug/281699)

---

### Post by blazemore on 2008-11-26
On the screen of the kernelcheck wizard when you have to click "Get Kernel Information", you've but an apostrophe in posessive "its" when there should be none :)
Easy mistake to make, but makes your app look more polished.

---

### Post by kevdog on 2008-12-01
I used your old version back in Feisty along with your old how to compile that latest kernel guide, way back when.  I kind of miss that guide.

Anyway two problems Im having using Intrepid

#1 - The current kernel version, available kernel, and patch information is never displayed.  It downloads kernel information, but never displays anything about the currently installed kernel

#2. - I went through compiling a kernel -- changed nothing but kept the defaults -- and the kernel version that was compiled was older than my running version?  What??? How did that happen?  I'm really confused about that one??

Suggestion
Rather that offering to compile the most recent vanilla kernel (although I don't think this is working), it would be great to offer to compile any kernel version.  I'd like to recompile the Feisty generic kernel since it better supported by crappy hardware.  It would be great if your program could except any historic kernel version, and also mention as a point of reference what kernel versions were included in Ubuntu's past releases (this would act like a benchmark).

Thanks for your consideration.

---

### Post by conjunctivitis on 2008-12-01
Hello

I am trying to maximize performance for simple internet usage and desktop stuff while minimizing power usage on my Acer Extensa 4420 (AMD Athlon 64 X2).  I downloaded and installed your program and started it, but the numerous options scared me off.  Where can I find a description of the stuff I can/should change and what should be left alone?  Thanks

---

### Post by conjunctivitis on 2008-12-01
hello,

i just tried compiling a kernel with kernelcheck and it closed with an error message as follows
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.27.7-ultimate.postinst line 1181.
dpkg: error processing linux-image-2.6.27.7-ultimate (--configure):
subprocess post-installation script returned error exit status 2
Errors were encountered while processing: linux-image-2.6.27.7-ultimate
E: Sub-process /usr/bin/dpkg returned an error code (1)

ABORT: dpkg returned exit status 100

---

### Post by youngman on 2008-12-01
> **conjunctivitis said:**
> Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.27.7-ultimate.postinst line 1181.


Similar here. Solution: [https://bugs.launchpad.net/ubuntu/+bug/292606](https://bugs.launchpad.net/ubuntu/+bug/292606)

sudo apt-get purge nvidia-common
(kernel install should complete here)
sudo apt-get install nvidia-common

---

MK - Many thanks for this sweet software!

---

### Post by blazemore on 2008-12-10
youngman you are a genius.
I've been searching for this fix for over a year.

---

### Post by Arcturus691 on 2008-12-21
> **techmin said:**
> Thi problem is relate to this Debian bug
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=446879](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=446879)

Add --arch=am64 --subarch=x86_64 when calling make-kpkg
or your arch and subarch specify for your architecture

bug on ubuntu launchpad
[https://bugs.launchpad.net/ubuntu/+source/kernel-package/+bug/281699](https://bugs.launchpad.net/ubuntu/+source/kernel-package/+bug/281699)

I having the above problem.  I can get around it by editing the .config file and changing config_XEN = y  to config_XEN = n.  What is the consequence of changing config_XEN to N?  Also how do you: 
Add --arch=am64 --subarch=x86_64 when calling make-kpkg
or your arch and subarch specify for your architecture in KernelCheck?

This is for kernel 2.6.27.10 upgrading from 2.6.27-9-generic
on a AMD Athlon 3800+ 2.4 processor.

---

### Post by master_kernel on 2008-12-23
> **Arcturus691 said:**
> I having the above problem.  I can get around it by editing the .config file and changing config_XEN = y  to config_XEN = n.  What is the consequence of changing config_XEN to N?  Also how do you: 
Add --arch=am64 --subarch=x86_64 when calling make-kpkg
or your arch and subarch specify for your architecture in KernelCheck?

This is for kernel 2.6.27.10 upgrading from 2.6.27-9-generic
on a AMD Athlon 3800+ 2.4 processor.
Sorry, I don't know what config_XEN does at all. I'd better brush up on my kernel knowledge.

Future versions should include manual options, but you will have to edit the KC script in the python directory. To locate it try:

$ sudo updatedb
$ locate kscript.sh

---

### Post by Arcturus691 on 2009-01-02
> **master_kernel said:**
> Sorry, I don't know what config_XEN does at all. I'd better brush up on my kernel knowledge.

Future versions should include manual options, but you will have to edit the KC script in the python directory. To locate it try:

$ sudo updatedb
$ locate kscript.sh

Thanks for replying.  I am not sure what I am doing wrong now.  I was able to find the script using the locate command:
~$ locate kscript.sh
/usr/lib/python2.4/site-packages/KernelCheck/library/kscript.sh
/usr/lib/python2.5/site-packages/KernelCheck/library/kscript.sh
/usr/share/pyshared/KernelCheck/library/kscript.sh

I gedited the /usr/share/pyshared/KernelCheck/library/kscript.sh and modified (mod line in red) as follows:

function stage5 {
cd /usr/src/linux
echo -e "\033[1;31mStage 5/6: Cleaning up for the build"
echo -e "\033[0m"
make-kpkg [COLOR="DarkRed"]--arch=am64 --subarch=x86_64[/COLOR] clean
checkretcode stage5
echo ""
exit
}

When I run kernelcheck I get the following error:

Stage 5/6: Cleaning up for the build

exec make -f /usr/share/kernel-package/ruleset/minimal.mk clean  KPKG_ARCH=am64   KPKG_SUBARCH=x86_64 
====== making target minimal_clean [new prereqs: ]======
Cleaning.
test ! -f .config || cp -pf .config config.precious
test ! -e stamp-building || rm -f stamp-building
test ! -f Makefile || \
            make    ARCH=am64 distclean
make[1]: Entering directory `/usr/src/linux-2.6.28'
Makefile:518: /usr/src/linux-2.6.28/arch/am64/Makefile: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-2.6.28/arch/am64/Makefile'.  Stop.
make[1]: Leaving directory `/usr/src/linux-2.6.28'
make: *** [minimal_clean] Error 2

ABORT: stage5 returned exit status 2

Any ideas?   Thanks in advance

[edit]
I looked in the below directory and found there is no am64 directory.
Is this the reason for the error?
:/usr/src/linux-2.6.28/arch$ ls
[COLOR="LightBlue"]alpha  blackfin  h8300    m32r       mips     powerpc  sparc    x86
arm    cris      ia64     m68k       mn10300  s390     sparc64  xtensa
avr32  frv       Kconfig  m68knommu  parisc   sh       um[/COLOR]

---

### Post by Frak on 2009-01-04
I am a very experienced packager, but on an attempt to reinstall after the first install was whacked caused apt/dpkg to go into a state of paralysis that could only be fixed by an entire reinstall of Ubuntu. Something needs to be addressed if another module package is found on the system. The current non-ability to handle the questioning system is unacceptable. Allow users to manipulate the console messages, they are currently locked behind a nice looking python glass.

Purely unacceptable

---

### Post by Frak on 2009-01-04
Ah, yes, I need to manually fix the missing image problem. Poor program indeed. Were exceptions in kernel compilation never considered at all?

---

### Post by kevdog on 2009-01-05
Frak -- what are your recommending then?

---

### Post by Frak on 2009-01-05
> **kevdog said:**
> Frak -- what are your recommending then?
Meh, I just blew up in rage. It's more apts fault for being stubborn when it can't find something, even if you tell it to disregard it.

---

### Post by kevdog on 2009-01-06
So is there a workaround?

---

### Post by Kow on 2009-01-06
I should mention that the -K/--kernel-module-only option of the NVIDIA driver installer is broken.... as it is completely ignored:

```

sudo sh NVIDIA-Linux-x86_64-177.82-pkg2.run -K -k 2.6.28-ultimate -n -s

```

results in:
ERROR: No NVIDIA driver is currently installed; the '--kernel-module-only'
       option can only be used to install the NVIDIA kernel module on top of an
       existing driver installation.

so I tried --kernel-module-only instead of -K and got the same result. Go nVidia....

EDIT: It seems the 180.17 driver (currently beta) fixes a lot of these issues. Installed fine for me but there are still some outstanding bugs per other forums.

---

### Post by master_kernel on 2009-01-12
**Frak, I have sent you this message in an email, but in case you do not receive it, I have copied it below.**


I have some questions regarding your posts on my thread:
[http://ubuntuforums.org/showpost.php?p=6495957&postcount=319](http://ubuntuforums.org/showpost.php?p=6495957&postcount=319)
and
[http://ubuntuforums.org/showpost.php?p=6495957&postcount=320](http://ubuntuforums.org/showpost.php?p=6495957&postcount=320)

I have discovered from feedback that a package called python-gnome2 is an unlisted dependency. But to which missing image problem are you referring?

Despite this, I am wondering if you have discovered what caused APT to become hell for you. I do realize that the current uninstall script included in KernelCheck is inadequate for stable use, but I cannot understand how APT screwed up if you used it (referring to APT) to uninstall/reinstall KernelCheck.

Also, could you elaborate on how the current questioning system is unacceptable? Are you referring to the radio buttons and checkboxes or the console messages shown in the python script? After all, the user should not need to answer any questions in the console window since there are none. Are you suggesting a "advanced" mode where the program stops after each step to allow to user to add "in-between" steps and also the option to modify each command KernelCheck runs?

Sincerely,
Master Kernel

---

### Post by Frak on 2009-01-12
For the entire situation, I used KernelCheck, compiled a kernel for the second time, without uninstalling it (I just figured it would replace it). Anyways, it came to a point requiring my confirmation over console. I wasn't able to do anything with it, so I closed it. Once I tried to install updates, it alerted me that the image was installed, but there was no file with it, so it was unable to uninstall. Basically, it tried to install, failed, and never cleaned up after itself.

---

### Post by boob11 on 2009-01-14
Tnx

---

### Post by master_kernel on 2009-01-14
> **Frak said:**
> For the entire situation, I used KernelCheck, compiled a kernel for the second time, without uninstalling it (I just figured it would replace it). Anyways, it came to a point requiring my confirmation over console. I wasn't able to do anything with it, so I closed it. Once I tried to install updates, it alerted me that the image was installed, but there was no file with it, so it was unable to uninstall. Basically, it tried to install, failed, and never cleaned up after itself.
Now I understand. I will add user input support to the next version.

---

### Post by kevdog on 2009-01-14
New feature to compile any new, current, old kernel version implemented yet?

---

### Post by master_kernel on 2009-01-16
> **kevdog said:**
> New feature to compile any new, current, old kernel version implemented yet?
It's in the alpha version on my machine, but I'm not sure if it's uploaded to Launchpad or not. Lately I haven't had the time to discover the new rules of Sourceforge and Launchpad for uploading files. Plus studying for exams is never fun.

You can try downloading the alpha version off of Launchpad and see if that one works.

---

### Post by Praxicoide on 2009-01-28
A success and a failure for me.

I compiled a Dell Inspiron a few days ago (with the .1 patch) and it worked great (thank you very much). 

But I did not have the same luck just now with an old VAIO computer running Xubuntu. Speed improvement is very important in this case, since we're talking about a Duron with 128MB of RAM.

I first tried yesterday with the same 2.6.28.1 stable kernel using your Master Kernel thread. It took a solid seven hours of compiling, during which I got more than a few "non-literal" errors. In the end it never even make a deb. I deleted the downloaded Kernel, patch, directory and linux directory. I created an empty Linux directory again, just in case.

I thought I would try Kernelcheck since it worked so great before. It was a lot faster to compile, but again there were several errors of the same kind. After it was done, I rebooted and right after grub booted, the screen went completely red with white bars. I turned it off and tried again to see if I could get into secure mode, but I got the same thing again. This time I waited and the bars began to move, then the x started. I could log in OK and the desktop loaded, but now all the letters are [size=3]HUGE![/size]. A line of text takes up a quarter of the screen, even though the icons are fine. I can't even get into a shell promt, because ctrl+alt+F1 takes me to the same red screen from the start.

I would think I messed up some options, if not for all those non-literal errors.

EDIT: Holy crud! I panicked for a minute after booting off 2.6.27.11 since the same problem persists! but now the sound is working and that's when I remembered that Xfce remembers all settings when switching off (grrrr...). So now it appears I have to reset that using cli.

EDIT2: Yup. it was just Xfce. I had to delete the .config/xfce4 and .config/xfce-session directories

---

### Post by Mikey_S on 2009-01-28
For some reason I get:  

```

make[1]: Entering directory 'usr/src/linux-2.6.28'
Makefile: 518: /usr/src/linux-2.6.28/arch/xen/Makefile: No such file or directory
make[1]: *** No rule to make target '/usr/src/linux-2.6.28/arch/xen/Makefile'. Stop.
make[1]: Leaving directory '/usr/src/linux-2.6.28'
make: *** [minimal_clean] Error 2

ABORT: stage5 returned exit status 2
```

This is after the configuration window comes up...
Any idea what causing this and how to fix this?

I'm currently using linux-2.6.27-9 kernel :)

Thanks

---

### Post by Praxicoide on 2009-01-28
I read about that error here in the thread, so I read about it, didn't take any chances and disabled it. I'm not going to use virtualization anyways, so I don't care if I don't have that, especially since it seems it is no longer supported:

[http://en.wikipedia.org/wiki/Xen](http://en.wikipedia.org/wiki/Xen)

[https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen)

> Note: This guide is written for Feisty. It is currently not fully compatible with Gutsy, use at your own risk! And it seems Ubuntu has dropped support for Xen dom0 altogether in current and future releases.

Note: If you just want to run a virtual instance of windows, it is recommended to try KVM or VirtualBox instead.

---

### Post by Arcturus691 on 2009-01-29
ARCH=am64 is incorrect, I believe it should be ARCH=amd64


[I]When I run kernelcheck I get the following error:

Stage 5/6: Cleaning up for the build

exec make -f /usr/share/kernel-package/ruleset/minimal.mk clean  KPKG_ARCH=am64   KPKG_SUBARCH=x86_64 
====== making target minimal_clean [new prereqs: ]======
Cleaning.
test ! -f .config || cp -pf .config config.precious
test ! -e stamp-building || rm -f stamp-building
test ! -f Makefile || \
            make    ARCH=am64 distclean
make[1]: Entering directory `/usr/src/linux-2.6.28'
Makefile:518: /usr/src/linux-2.6.28/arch/am64/Makefile: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-2.6.28/arch/am64/Makefile'.  Stop.
make[1]: Leaving directory `/usr/src/linux-2.6.28'
make: *** [minimal_clean] Error 2

ABORT: stage5 returned exit status 2

[/I]

---

### Post by Arcturus691 on 2009-02-02
Ok I got past stage 5 only to get an error on stage 6.  Seems like it is confused about the version.

Current kernel
uname -a
 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux


Error Excerpt  (see attached file for more info) 

====== making target CONFIG-common [new prereqs: testdir]======

====== making target debian/stamp-conf [new prereqs: ]======
The changelog says we are creating 2.6.28.2-ultimate.
However, I thought the version is ..-ultimate
exit 3
make: *** [debian/stamp-conf] Error 3

ABORT: stage6 returned exit status 2

Thanks in advance:)

Edit:  Found the same error in ubuntu archives:  [http://ubuntuforums.org/archive/index.php/t-968178.html]("http://ubuntuforums.org/archive/index.php/t-968178.html")

Disabling CONFIG_XEN fixes the issue, whether is makes a viable kernel is another question.  Correct me if I am wrong but I believe CONFIG_XEN is for virtualization.

---

### Post by alelinuxbsd on 2009-03-02
Thanks master_kernel for your userful program!

This is the first time that i tried to build a new kernel.

Wow!

1) I have a request, could you put a button in order to resume the download if it's stop because of poor adsl lines?
	
Because of this reason I had to quit and restart the program several times.


2) I have a doubt, I have tried to generate the kernel in a multi-core:
#
/usr/lib/python2.5/site-packages/KernelCheck/library/kscript.sh

CONCURRENCY_LEVEL=10

but during compilation I think it was used only one core or i'm wrong?

---

### Post by ^-Super_Treje-^ on 2009-03-02
i dont like, because i love the old system of the compiling (some gentoo :D)

---

### Post by alelinuxbsd on 2009-03-02
^-Super_Treje-^ is a bad boy from another forum where i have highlighted your wonderful work.

^-Super_Treje-^ is masochistic. :lolflag:

Nota:
Si discute in italiano, per benino, sul nostro forum. 	;)
Poi ti metto allo spiedo.:mrgreen:

---

### Post by alelinuxbsd on 2009-03-04
My custom kernel on Ubuntu Hardy is ok but during the boot i obtain two messages.

One message refers to the lack of AppArmor.

I think it's ok because if i go on the: 
[download project of AppArmor]("http://forge.novell.com/modules/xfmod/project/?apparmor") 	
the latest version available (in beta) is on the 2.6.26 kernel while i use the 2.6.28 kernel.

But one an update version of AppArmor is available how can use KernelCheck?

Must I download the source of apparmor or the deb on a new release of ubuntu with the same new kernel that i have installed on my system (2.6.28 )? 

But using two different versions of AppArmor on the same system, is there no risk of facing problems?

---

### Post by sh4d0w808 on 2009-03-04
Hello master_kernel, very big thanks for this work!

I'd like to recommend to add /home filesystem as temporary work directory if possible.

Regards,
sh4d0w808

---

### Post by fishb on 2009-03-13
Hi,

I've upgraded to Jaunty and my kernelcheck do not work since then. May I know how to solve it?

---

### Post by deepspring on 2009-03-16
Thank you for making this software! it has made compiling kernels much much easier.

A tip:
If you have an Intel Centrino Core Duo (not Core 2 Duo) based Laptop... under the "Processor" types and setting page in KConfig, select the "Pentium M" processor. It will make life easier for you and will give you a nice little kick.

---

### Post by Hirsch2k on 2009-03-20
Kernelcheck does not work any more.

I think it is since kernel.org restructured the code of their site. 

Maybe the correspondig lines in the kscript.sh:

```
DIR=$4
STABLE=$(head -1 $DIR)
STABLE_URL=$(head -2 $DIR | tail -1)
PATCH=$(head -3 $DIR | tail -1)
PATCH_URL=$(head -4 $DIR | tail -1)
ENVY_SUPPORT=$(head -5 $DIR | tail -1)
```

So kernelcheck gets the wrong URL for the Kernel from kernel.org.
I am not into python, but i think the problem is easy to fix, so maybe someone has an idea how to fix it?

---

### Post by deepspring on 2009-03-20
I'm using the latest development build of KernelCheck and I haven't seen any problems  with downloading kernels/patches yet.

---

### Post by Hirsch2k on 2009-03-21
That is strange. In Kernecheck Lumen as well as in Hopestar I get errors. For example, if i click "get kernel information" one long line of html code is displayed for current kernel or kernel patches. 
If I want to download the kernel I get errors like "can't resolve hostname href:"

---

### Post by master_kernel on 2009-03-21
Hirsch2k, I'm using KC Hopestar and haven't encountered any errors yet. Have you modified scripts in any way?

---

### Post by deepspring on 2009-03-21
> **Hirsch2k said:**
> That is strange. In Kernecheck Lumen as well as in Hopestar I get errors. For example, if i click "get kernel information" one long line of html code is displayed for current kernel or kernel patches. 
If I want to download the kernel I get errors like "can't resolve hostname href:"

This may or may not help. Try running KernelCheck from a terminal window and see if any debug info comes up, if it does paste it here (in a post).

Also, running the latest development build of KernelCheck from the Gnome menu doesn't work for me, the program exits automatically after clicking the Apply button. I have to run it from the terminal in order to get it to run properly.

```
sudo kernelcheck
```

Try this and see if this works for you.

---

### Post by Hirsch2k on 2009-03-21
I didn't modified scripts. Here is a screenshot of Lumen:
[IMG]http://i601.photobucket.com/albums/tt98/Hirsch2k/kernelcheck.jpg[/IMG]

and the error i get when kernelcheck tries to download the files:

[IMG]http://i601.photobucket.com/albums/tt98/Hirsch2k/kernelcheck2.jpg[/IMG]

hope this could help

edit: i get the same errors in hopestar too.

---

### Post by deepspring on 2009-03-22
Ok. Thanks for the screenshots, now I can sort of see what you mean.

It might be better if you pipe the debug data out to a file and attach it to your next post rather than post screenshots.

```
sudo kernelcheck > debug.txt
```

Sorry, I know this isn't helping you directly. But, the more debug data we gather, the quicker we can figure out whats going wrong.

---

### Post by Hirsch2k on 2009-03-22
I'm afraid the debug.txt won't be much of a help:

```
Testing your network connection...
Connection found.

Caching stable webpage from kernel.org
Page successfully cached

Caching stable prepatch webpage from kernel.org
Page successfully cached

Caching stable mm patch webpage from kernel.org
Page successfully cached

Caching stable webpage from kernel.org
Page successfully cached
```

Unfortunately I cannot copy the contents from the terminal that opens within kernelcheck, so i posted the screenshots.

---

### Post by deepspring on 2009-03-22
> **Hirsch2k said:**
> Unfortunately I cannot copy the contents from the terminal that opens within kernelcheck, so i posted the screenshots.

Thats a pain in the buttocks. :rolleyes:

Judging by those screenshots you've posted previously. It looks like its dumping the entire cached web page onto the "kscript.sh" shell script command instead of just the URL for the kernel and/or patch.

The "kscript.sh" file appears to be only a shell script that handles the command level stuff like using "wget" to fetch files, unzipping the kernel source, applying the kernel patches, running "make xconfig", etc (?). It doesn't look like there is anything wrong with that.

I'll have a look at the python source. Though I don't know how much help I'll be, I can only read and understand parts of python code, not write it. If I come up with something, I'll post it (doubt it).


**-- EDIT 23/03/09 @ 5:15am --**

I can't be certain because I can't replicate the problem here... but it looks like it could be any one of three issues. Either:

[list=1]
[*]There are some stale temporary files lurking on your system.
[*]One of the many temporary files created by KernelCheck is being incorrectly parsed or referenced by accident.
[*]A string variable is being set with unparsed raw html data.
[/list]

You can try cleaning out the "/tmp" folder, specifically any files with names that start with "tmp" (example: "tmpFoNMBa"). See if that helps.

---

### Post by deepspring on 2009-03-22
**FEATURE REQUEST**

master_kernel,

I love KernelCheck, and I seriously want to help in the improvement of this wonderful application.

Is it possible to add some debug features to the code so we can figure out where things tend to break? :D


**-- EDIT 23/03/09 @ 8:21am --** 

Nevermind, I found the "/var/log/kernelcheck.log" file, but it doesn't have the data I was looking for. I ended up making a simple "kscript.sh" file to capture the data being passed to it from python and dump it to file (doesn't do any of the compiling or anything).

After I've had some sleep, I'll see if can make a debug class and add it to the python scripts.

Let me know if you want me to upload anything I've done.


**-- EDIT 23/03/09 @ 2:20pm --**

I created a small class for capturing debug information from Variables, Lists, Tuples, Dictionaries, etc.

It's fairly easy to implement, just look at the code. Let me know if you need help.

Note: this is the first time I've coded in Python, be gentle.

---

### Post by Hirsch2k on 2009-03-23
Ok, I replaced the original kscript.sh with your version and its output is something like that: 

```
####################################################################
DEBUG TEST @ prestage
====================================================================

FUNCTION      = prestage
CONFIGURE     = True
RECONFIGURE   = False
DIR           = /tmp/tmpCs6g7r


--------------------------------------------------------------------
Contents of: /tmp/tmpCs6g7r


2.6.28
http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.28.tar.bz2
2.6.28.8
http://www.kernel.org/pub/linux/kernel/v2.6/patch-2.6.28.8.bz2">2.6.28.8</a></b></td><td>2009-03-17 01:05 UTC</td><td><a href="/pub/linux/kernel/v2.6/linux-2.6.28.8.tar.bz2">F</a></td><td><a href="/diff/diffview.cgi?file=%2Fpub%2Flinux%2Fkernel%2Fv2.6%2Fpatch-2.6.28.8.bz2">V</a></td><td><a href="/diff/diffview.cgi?file=%2Fpub%2Flinux%2Fkernel%2Fv2.6%2Fincr%2Fpatch-2.6.28.7-8.bz2">VI</a></td><td><a href="http://git.kernel.org/?p=linux%2Fkernel%2Fgit%2Fstable%2Flinux-2.6.28.y.git;a=summary">C</a></td><td><a href="/pub/linux/kernel/v2.6/ChangeLog-2.6.28.8">Changelog</a></td></tr></table><hr><p align="center"><a href="/
Normal
```

So I deleted /tmp/tmpCs6g7r, but another file with the same content is created everytime I run kernelcheck. 

I tried to run kcdebug.py with
```

sudo python kcdebug.py
```

but it didn't do any output to /var/log

maybe we should wait for master_kernel, he wrote me that he is now 3 weeks away.

---

### Post by deepspring on 2009-03-23
> **Hirsch2k said:**
> --snip--

It looks like one of the variables in the main program needs fixing. I'll look at source code and see if I can come up with something. I'm fairly new to Python so don't expect anything magic.

The KCDebug.py file needs to implemented in the source code. I put it there for master_kernel's sake, hopefully he can use it to find errors like the one you are experiencing.


**-- EDIT 24/03/09 @ 1:00pm --**

I don't have a fix for you, because I can't replicate the problem. But what I do have is a pair of modified file (see attached tar file) that outputs some debug information from the program to a file in "/var/log". Before you go and install this file, please note that it is a work progress and may contain bugs of its own.

Save the attached file to your home directories root (ie: "/home/<username>").

Open up a terminal window:
```

cd /usr/lib/python2.5/site-packages/KernelCheck
sudo mv main.py main.py-original
sudo mv library/kscript.sh library/kscript.sh-original
sudo tar zxvf ~/kcheck.tar.gz -C .

```

So what do the new files do...

The version of "kscript.sh" included in the attached tar file doesn't do anything except dump variable data to the log file "/var/log/kscript-debug.log". That means it doesn't download or change anything on the system.

The version of "main.py" included in the attached tar file is fully functional and almost identical to the original with the only change being that it logs certain variables to the log file "/var/log/kernelcheck-debug-(date).log" (replace "(date)" with todays date. ie: "kernelcheck-debug-2009-03-24.log").

Now run KernelCheck again, setting all the required settings, and let KernelCheck do its things. When it is finished, upload the two log files mentioned above so I can look at them and see whats happening.

**-- 24/03/2009 @ 4:00pm -- **

Fixed a small bug in the code. Please try this version.

---

### Post by Hirsch2k on 2009-03-28
First of all, thank you for your friendly and ongoing effort! 
Unfortunately I haven't had the time to try your new files until now.
So since it's weekend, I decided to attend to the problem again. 

So this morning I visited kernel.org to have a look at what's going on with the new 2.6.29 and also looked at their site code. Remember when I said, the html code of kernel.org was just one long line two weeks ago? Now somehow it's fixed and it looks "normal" (structured) again. So I started kernelcheck and everything works perfectly normal again. Can you believe that??
I don't know what it was, but since you couldn't reproduce the problem and kernelcheck worked fine for you, I think it wasn't a problem with kernel.org.

---

### Post by Hirsch2k on 2009-03-28
Ok, I had another problem. After kernelcheck worked again (that´s what i thought) it messed up my apt completely. So I decided to give 9.04 a try and installed it. I downloaded and installed kernelcheck, but it didn't work. I figured out, that 9.04 uses python 2.6 instead of 2.5. So I replaced the words python2.5/site-packages with python2.6/dist-packages in the python files. And it worked. But now I'm getting the same error again I had at the very beginning (kernelcheck doesn't catch the URLs for kernels correctly). I downloaded the 2.6.29 manually and copied it to /usr/src. Now kernelcheck is compiling and I hope it works. I'll let you know.

---

### Post by deepspring on 2009-03-29
I've actually managed to break my setup with a Ubuntu 9.04 beta upgrade, so I can't look at it until get everything setup again.

---

### Post by deepspring on 2009-03-29
The attached file is for Jaunty users **ONLY**. Do not use it if you are using an earlier version of Ubuntu.

To install this version:
```

tar jxvf kernelcheck-1.2.0.tar.bz2
cd kernelcheck-1.2.0
sudo python setup.py install

```The only difference between this and the official development/experimental version, is as follows:

[LIST]
[*]Based on KernelCheck 1.2.0 Lumen (the development/experimental version).
[*]Manually changed all base paths in the source code from "/usr/lib/python2.5/site-packages/KernelCheck" to "/usr/local/lib/python2.6/dist-packages/KernelCheck/".
[*]Removed some crud from the archive (old files, etc) to make debugging a little easier.
[/LIST]
  Under Jaunty, the files get installed to the following locations:

[LIST]
[*]/usr/local/lib/python2.6/dist-packages/KernelCheck/*
[*]/usr/local/lib/python2.6/dist-packages/kernelcheck-testing.egg-info
[*]/usr/local/share/kernelcheck/*
[*]/usr/local/share/applications/kernelcheck.desktop
[*]/usr/local/bin/kernelcheck
[/LIST]

**-- EDIT 31/03/2009 @ 5:00pm --**

Fixed missing file problem.

---

### Post by deepspring on 2009-03-29
> **Hirsch2k said:**
> But now I'm getting the same error again I had at the very beginning (kernelcheck doesn't catch the URLs for kernels correctly). I downloaded the 2.6.29 manually and copied it to /usr/src. Now kernelcheck is compiling and I hope it works. I'll let you know.
I'm working on a solution, reading and understanding master_kernel's code is taking some time.


**-- Edit 30/03/2009 @ 1:10am --**

Hirsch2k,

Attached is modified version of KernelCheck 1.2.0 that uses an alternative method to get the latest kernel info. It will only work on Jaunty so I don't recommend trying it on any other version of Ubuntu. 

Try this only if you are still having problems with the current version of KernelCheck.


[B]-- EDIT 31/03/2009 @ 5:00pm --

[/B]Fixed missing file bug.

---

### Post by frohike on 2009-03-30
I have a problem with the above kernelcheck lumen on ubuntu 9.04 with running kernel 2.6.28-11-generic I get this output in the terminal when trying to use the program. I hope this help you debug it.
```
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/KernelCheck/build.py", line 393, in <module>
    window = KernelCheck()
  File "/usr/local/lib/python2.6/dist-packages/KernelCheck/build.py", line 88, in __init__
    self.build("call")
  File "/usr/local/lib/python2.6/dist-packages/KernelCheck/build.py", line 207, in build
    temp_path = build_kernel.build(config, reconfigure, patchtype, data)
NameError: global name 'build_kernel' is not defined

```

---

### Post by deepspring on 2009-03-31
> **frohike said:**
> I have a problem with the above kernelcheck lumen on ubuntu 9.04 with running kernel 2.6.28-11-generic I get this output in the terminal when trying to use the program. I hope this help you debug it.
```
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/KernelCheck/build.py", line 393, in <module>
    window = KernelCheck()
  File "/usr/local/lib/python2.6/dist-packages/KernelCheck/build.py", line 88, in __init__
    self.build("call")
  File "/usr/local/lib/python2.6/dist-packages/KernelCheck/build.py", line 207, in build
    temp_path = build_kernel.build(config, reconfigure, patchtype, data)
NameError: global name 'build_kernel' is not defined

```

Yeah looks like I missed a file in packaging. Try the attached version.

---

### Post by frohike on 2009-04-01
The update works perfect thanks for the fast upgrade :D PS love the hot pink look :)

---

### Post by deepspring on 2009-04-07
Another KernelCheck experimental release is in the works at the moment and should be released as soon as Master Kernel catches up on whats been happening on and off the forum. In the mean time...

[SIZE=5]**A Quick Guide to Uninstalling Kernel Check**[/SIZE]

The following completely removes all traces of KernelCheck from your system. It is encouraged that you do this _before_ trying a new KernelCheck experimental release.

For people on **ALL VERSIONS OF UBUNTU **that installed KernelCheck using the recommended stable install method (the *deb package):

```

sudo apt-get remove --purge kernelcheck*

```For users on **_K/X/Ubuntu 8.10_** and earlier that used either of the advanced install methods...

```

sudo rm -rf /usr/bin/kernelcheck
sudo rm -rf /var/log/kernelcheck*
sudo rm -rf /usr/lib/python2.5/site-packages/KernelCheck*
sudo rm -rf /usr/share/kernelcheck
sudo rm -rf /usr/share/applications/kernelcheck.desktop

```For users on **_K/X/Ubuntu 9.04_** and higher that used either of the advanced install methods...

```

sudo rm -rf /usr/local/bin/kernelcheck
sudo rm -rf /var/log/kernelcheck*
sudo rm -rf /usr/local/lib/python2.6/dist-packages/KernelCheck*
sudo rm -rf /usr/local/share/kernelcheck
sudo rm -rf /usr/local/share/applications/kernelcheck.desktop

```Future versions of KernelCheck _may_ include an uninstaller.

---

### Post by master_kernel on 2009-04-10
The latest development version is now up for grabs in the BZR repo. Check the changelog for details.

---

### Post by mcshade on 2009-04-16
Thanx!!

---

### Post by vampirefo on 2009-04-23
Anyway to tell kernelcheck to download and compile a different kernel? rather than just the latest, for example 2.6.27 or 2.6.28 instead of 2.6.29

---

### Post by matmat07 on 2009-04-23
You need the development version for that

---

### Post by deepspring on 2009-04-23
> **vampirefo said:**
> Anyway to tell kernelcheck to download and compile a different kernel? rather than just the latest, for example 2.6.27 or 2.6.28 instead of 2.6.29
The development version allows you to select an older version of the kernel.

---

### Post by vampirefo on 2009-04-23
OK thanks.

---

### Post by loomsen on 2009-04-25
Hello.


Just noticed this small bug, installing manually makes the app install to 
/usr/local/bin/ 
the menu-launcher created through the installer points to 
/usr/bin/ 
tho, so nothing at all happens if one tries to use it...

---

### Post by deepspring on 2009-04-25
> **loomsen said:**
> Hello.


Just noticed this small bug, installing manually makes the app install to 
/usr/local/bin/ 
the menu-launcher created through the installer points to 
/usr/bin/ 
tho, so nothing at all happens if one tries to use it...

The bug you've experienced is known and only affects KernelCheck 1.1.4 when it is installed on Ubuntu 9.04.  

You need to use the latest development version for Ubuntu 9.04, please remove the version you have installed by following these instructions: [HERE]("http://ubuntuforums.org/showpost.php?p=7028917&postcount=363").

And install the latest development version using the "Advanced/Manual Installation Method (Development)" described: [HERE]("http://ubuntuforums.org/showpost.php?p=3404994&postcount=1").

---

### Post by loomsen on 2009-04-26
Actually, I did both. First using the tar archive, then checking out the bzr branch...

Just wanted to point at...
(I didnt even touch the stable release ^^)

---

### Post by Beastie Boy on 2009-04-27
I can't get KernelCheck to run :(  Running in a terminal gives this error:
```
Testing your network connection...
Connection found.

(kernelcheck:4294): libglade-WARNING **: could not find glade file '/usr/lib/python2.5/site-packages/KernelCheck/library/main.glade'
Traceback (most recent call last):
  File "/usr/bin/kernelcheck", line 21, in <module>
    KernelCheck.main.start ()
  File "/usr/lib/python2.6/dist-packages/KernelCheck/main.py", line 757, in start
    window = KernelCheck()
  File "/usr/lib/python2.6/dist-packages/KernelCheck/main.py", line 300, in __init__
    self.widgets = gtk.glade.XML("/usr/lib/python2.5/site-packages/KernelCheck/library/main.glade")
RuntimeError: could not create GladeXML object
```

I have searched this thread for 'Glade' and 'GladeXML', but I can't find any reference to thi problem.
I am running the latest stable release, 1.1.4.

Any ideas? According to Synaptic, I have anything related to Glade installed. This is a fresh installation of Ubuntu 9.04.

Cheers, Beastie.

Edit: I can confirm that the folder KernelCheck does not exist under /usr/lib/python2.5/site-packages.

---

### Post by deepspring on 2009-04-28
> **Beastie Boy said:**
> I can't get KernelCheck to run :(  Running in a terminal gives this error:
```
Testing your network connection...
Connection found.

(kernelcheck:4294): libglade-WARNING **: could not find glade file '/usr/lib/python2.5/site-packages/KernelCheck/library/main.glade'
Traceback (most recent call last):
  File "/usr/bin/kernelcheck", line 21, in <module>
    KernelCheck.main.start ()
  File "/usr/lib/python2.6/dist-packages/KernelCheck/main.py", line 757, in start
    window = KernelCheck()
  File "/usr/lib/python2.6/dist-packages/KernelCheck/main.py", line 300, in __init__
    self.widgets = gtk.glade.XML("/usr/lib/python2.5/site-packages/KernelCheck/library/main.glade")
RuntimeError: could not create GladeXML object
```I have searched this thread for 'Glade' and 'GladeXML', but I can't find any reference to thi problem.
I am running the latest stable release, 1.1.4.

Any ideas? According to Synaptic, I have anything related to Glade installed. This is a fresh installation of Ubuntu 9.04.

Cheers, Beastie.

Edit: I can confirm that the folder KernelCheck does not exist under /usr/lib/python2.5/site-packages.


See this post here...
[http://ubuntuforums.org/showpost.php?p=7147973&postcount=371](http://ubuntuforums.org/showpost.php?p=7147973&postcount=371)

---

### Post by Beastie Boy on 2009-04-28
Thanks. ;)

---

### Post by a person on 2009-04-29
I am currently getting this when running aptitude:

```

E: I wasn't able to locate a file for the linux-image-2.6.29.1-ultimate package. This might mean you need to manually fix this package. (due to missing arch)

```

I have suspect to believe kernelcheck had something to do with this.  Can anyone shed some light on this for me?

I'm on 9.04.

---

### Post by Aiman on 2009-04-29
Ever since i ran Ubuntu hardy i never thought about changing my OS to anything else.
I did run the kernelcheck before and came across a problem,i lost everything related to my setup for some reason,and specially the graphics,im running it on HP pavilion ZD8000 with an ATI x600,which needed custom configure to run compiz with the fglrx driver
when i applied the last kernel update 2.6.29 and restarted,i lost the theme options
I reinstalled all got everything back up and running,maybe even better than before
anyway,i tried giving KernelCheck a try once again,but i came across an error that i didn't get the first time,not sure whats the problem,i checked the statement in the mentioned file,but its there
below is a screen shoot from the error
[IMG]http://img99.imageshack.us/img99/6194/erroro.jpg[/IMG]

---

### Post by deepspring on 2009-04-29
> **Aiman said:**
> Ever since i ran Ubuntu hardy i never thought about changing my OS to anything else.
I did run the kernelcheck before and came across a problem,i lost everything related to my setup for some reason,and specially the graphics,im running it on HP pavilion ZD8000 with an ATI x600,which needed custom configure to run compiz with the fglrx driver
when i applied the last kernel update 2.6.29 and restarted,i lost the theme options
I reinstalled all got everything back up and running,maybe even better than before
anyway,i tried giving KernelCheck a try once again,but i came across an error that i didn't get the first time,not sure whats the problem,i checked the statement in the mentioned file,but its there
below is a screen shoot from the error
-snip-


I'm using ubuntu 9.04, and a lot has been changed since 8.04 came out, so its hard to say for sure. But, it looks like you are missing some dependancies needed to compile the kernel, most probably "kernel-package".

You can try:
```
sudo apt-get install kernel-package
```If it installs then cool, try re-running KernelCheck.

---

### Post by jofre on 2009-04-30
I have the same problem as Beastie Boy:


```
sudo kernelcheck

Testing your network connection...
Connection found.

(kernelcheck:11849): libglade-WARNING **: could not find glade file '/usr/lib/python2.5/site-packages/KernelCheck/library/main.glade'
Traceback (most recent call last):
  File "/usr/local/bin/kernelcheck", line 21, in <module>
    KernelCheck.main.start ()
  File "/usr/lib/python2.6/dist-packages/KernelCheck/main.py", line 757, in start
    window = KernelCheck()
  File "/usr/lib/python2.6/dist-packages/KernelCheck/main.py", line 300, in __init__
    self.widgets = gtk.glade.XML("/usr/lib/python2.5/site-packages/KernelCheck/library/main.glade")
RuntimeError: could not create GladeXML object
```


but the solution provided by Deepspring, does not work for me. I still get exactly the same error.

Any ideas?

---

### Post by deepspring on 2009-04-30
> **jofre said:**
> I have the same problem as Beastie Boy:


```
sudo kernelcheck

Testing your network connection...
Connection found.

(kernelcheck:11849): libglade-WARNING **: could not find glade file '/usr/lib/python2.5/site-packages/KernelCheck/library/main.glade'
Traceback (most recent call last):
  File "/usr/local/bin/kernelcheck", line 21, in <module>
    KernelCheck.main.start ()
  File "/usr/lib/python2.6/dist-packages/KernelCheck/main.py", line 757, in start
    window = KernelCheck()
  File "/usr/lib/python2.6/dist-packages/KernelCheck/main.py", line 300, in __init__
    self.widgets = gtk.glade.XML("/usr/lib/python2.5/site-packages/KernelCheck/library/main.glade")
RuntimeError: could not create GladeXML object
```
but the solution provided by Deepspring, does not work for me. I still get exactly the same error.

Any ideas?

Looks like you're trying to use the stable version on 9.04.

You can't use the stable version (1.1.4) on Ubuntu 9.04, it wont work. You need to use the latest development version (1.2.5).

1. [Remove the old version you have installed.](http://ubuntuforums.org/showpost.php?p=7028917&postcount=363)
2. [Follow the instructions to install Kernel Check using the Advanced/Manual Installation Method (Development).](http://ubuntuforums.org/showpost.php?p=3404994&postcount=1)

---

### Post by Aiman on 2009-05-02
thanks deepspring
the kernel-package did the trick :)

---

### Post by jofre on 2009-05-04
I apologise, I didn't see:

```
sudo apt-get remove --purge kernelcheck*
```


;-)

It seem to work ok.

Thanks,
Jofre

---

### Post by VastOne on 2009-05-24
Running kernelcheck for first time

have purged all am sure I am at the latest dev version.

I get to section 3 and then this happens:

Traceback (most recent call last):
  File "/usr/local/share/kernelcheck/scripts/build.py", line 168, in close
    gtk.main_quit()
RuntimeError: called outside of a mainloop


Appreciate the help

---

### Post by master_kernel on 2009-05-25
> **VastOne said:**
> Running kernelcheck for first time

have purged all am sure I am at the latest dev version.

I get to section 3 and then this happens:

Traceback (most recent call last):
  File "/usr/local/share/kernelcheck/scripts/build.py", line 168, in close
    gtk.main_quit()
RuntimeError: called outside of a mainloop


Appreciate the help

Make sure the following are installed:

python-gnome2, python-glade2, python-vte

I'm not sure if that is the problem, but I remember back when I used to get those errors. I can't remember what I did though...

---

### Post by VastOne on 2009-05-25
> **master_kernel said:**
> Make sure the following are installed:

python-gnome2, python-glade2, python-vte

I'm not sure if that is the problem, but I remember back when I used to get those errors. I can't remember what I did though...

I solved it...

Turned out to be a space issue.  My filesystem was way too small for these ops and I had to enlarge it. Once I did that, the script ran perfectly.

I do have a weird end result though.  The script correctly wrote to my menu.lst and in looking at it I see the entries. But on boot, I do not have the new kernel as a choice to boot to.

title		Ubuntu 9.04, kernel 2.6.29.4-candela
uuid		428ae622-173c-4eb7-a1c1-5958387d6b46
kernel		/boot/vmlinuz-2.6.29.4-candela root=UUID=428ae622-173c-4eb7-a1c1-5958387d6b46 ro quiet splash 
initrd		/boot/initrd.img-2.6.29.4-candela
quiet

title		Ubuntu 9.04, kernel 2.6.29.4-candela (recovery mode)
uuid		428ae622-173c-4eb7-a1c1-5958387d6b46
kernel		/boot/vmlinuz-2.6.29.4-candela root=UUID=428ae622-173c-4eb7-a1c1-5958387d6b46 ro  single
initrd		/boot/initrd.img-2.6.29.4-candela

title		Ubuntu 9.04, kernel 2.6.28-12-generic
uuid		428ae622-173c-4eb7-a1c1-5958387d6b46
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=428ae622-173c-4eb7-a1c1-5958387d6b46 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-12-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode)
uuid		428ae622-173c-4eb7-a1c1-5958387d6b46
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=428ae622-173c-4eb7-a1c1-5958387d6b46 ro  single
initrd		/boot/initrd.img-2.6.28-12-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		428ae622-173c-4eb7-a1c1-5958387d6b46
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=428ae622-173c-4eb7-a1c1-5958387d6b46 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		428ae622-173c-4eb7-a1c1-5958387d6b46
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=428ae622-173c-4eb7-a1c1-5958387d6b46 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		428ae622-173c-4eb7-a1c1-5958387d6b46
kernel		/boot/memtest86+.bin
quiet


The only options I see are the originals I had starting at 2.6.28.12

When I expanded my root (filesystem) partition. I have a single SATA drive so I created a new ext4 partition and then simply copied and pasted the root to the new partition and gparted expanded it perfectly and I was able to boot fine. I then ran your script and within 30 minutes it was done. The only concern I have is that once it finished and I closed kernelcheck, it's term session did not end with it.

ANy thoughts on why 2.6.29.4 kernel is not displaying as an option?

---

### Post by VastOne on 2009-05-26
FYI I am not the only kernelcheck user with this issue

See  [http://ubuntuforums.org/showthread.php?t=1170161](http://ubuntuforums.org/showthread.php?t=1170161)

Thanks

---

### Post by deepspring on 2009-05-26
> **VastOne said:**
> ANy thoughts on why 2.6.29.4 kernel is not displaying as an option?

I don't know why it isn't showing, but you could try removing and re-installing the 2.6.29.4 kernel and headers. If KernelCheck worked as it should, there should be ".deb" packages for the kernel and headers in "/usr/src/" that you can use to re-install.

---

### Post by VastOne on 2009-05-26
> **deepspring said:**
> I don't know why it isn't showing, but you could try removing and re-installing the 2.6.29.4 kernel and headers. If KernelCheck worked as it should, there should be ".deb" packages for the kernel and headers in "/usr/src/" that you can use to re-install.

The creation process worked as it should have but now there are at least two users with no capabilities of getting grub to work as it should.  In both instances the menu.lst clearly shows the correct 2.6.29-4 instances but they are not making it to grub.

I want to submit a bug report but am not sure what approach to use.

---

### Post by Makrin on 2009-05-26
I sometimes have that problem(kernel doesn't show up in grub) aswell. I usually resolve it by removing the older custom candela kernel.  But it looks like you only have one..hmm maybe try removing the oldest generic kernel ?

---

### Post by VastOne on 2009-05-26
> **deepspring said:**
> I don't know why it isn't showing, but you could try removing and re-installing the 2.6.29.4 kernel and headers. If KernelCheck worked as it should, there should be ".deb" packages for the kernel and headers in "/usr/src/" that you can use to re-install.

I will try this thank you....

---

### Post by VastOne on 2009-05-26
> **Makrin said:**
> I sometimes have that problem(kernel doesn't show up in grub) aswell. I usually resolve it by removing the older custom candela kernel.  But it looks like you only have one..hmm maybe try removing the oldest generic kernel ?

I will also try this thank you. 

When you saw this before, did you also see that your menu.lst was properly setup but grub did not display it?

---

### Post by deepspring on 2009-05-26
I don't think it is a bug with KernelCheck, but a bug with the deb install procedure and how it updates grub.

You can try updating grub manually after installing the kernels with:
```
sudo update-grub
```That should fix things by reloading and install the options from menu.lst.

---

### Post by VastOne on 2009-05-26
> **deepspring said:**
> I don't think it is a bug with KernelCheck, but a bug with the deb install procedure and how it updates grub.

You can try updating grub manually after installing the kernels with:
```
sudo update-grub
```That should fix things by reloading and install the options from menu.lst.

Tried that several times with no results... Thank you though! :D

May have found the culprit at this thread...

Check it out, it is rather intriguing to say the least

[http://ubuntuforums.org/showthread.php?t=1170161](http://ubuntuforums.org/showthread.php?t=1170161)

---

### Post by VastOne on 2009-05-26
My issues are solved....

I had two drives with the same uuid

Thanks to all and especially Unutbu for the help and solution

---

### Post by VastOne on 2009-05-27
Just want to give a shout out and huge thank you for kernelcheck.  

On my first try at a kernel build, I ran into some big setup issues on my side, but once they were solved, the kernelcheck script ran perfectly and I am now running 2.6.29.4 kernel.

I never had to tweak a thing, nVidia installed perfectly and it all took about 22 minutes!

Thankee Sai's!

:D

---

### Post by Greenwidth on 2009-05-27
Hi
Just finished my first kernel compile and got dpkg quit error 100 (?) at 90%+, but everything seems to work fine except, just after GRUB I get:

[ 0.890497] cpufreq: No nForce2 chipset.

And then it continues to boot normally, it is quite correct, I don't have nForce2 chipset, I have nForce 680i SLI..

Is it anything to worry about?

---

### Post by master_kernel on 2009-05-27
> **Greenwidth said:**
> Hi
Just finished my first kernel compile and got dpkg quit error 100 (?) at 90%+, but everything seems to work fine except, just after GRUB I get:

[ 0.890497] cpufreq: No nForce2 chipset.

And then it continues to boot normally, it is quite correct, I don't have nForce2 chipset, I have nForce 680i SLI..

Is it anything to worry about?
Shouldn't be. As long as after dpkg quit you made sure you ran dpkg --configure -a.

EDIT: and dpkg finished successfully.

---

### Post by Greenwidth on 2009-05-28
Sadly it was a problem..
I obviously set something bad in the configure kernel options, some reading up in order I think.
Any suggested reading? 
Thanks.

---

### Post by master_kernel on 2009-05-30
> **Greenwidth said:**
> Sadly it was a problem..
I obviously set something bad in the configure kernel options, some reading up in order I think.
Any suggested reading? 
Thanks.
Check this post: [http://ubuntuforums.org/showpost.php?p=6777898&postcount=21](http://ubuntuforums.org/showpost.php?p=6777898&postcount=21)

Also look at the thread if you have > 1 CPU (or CPU core).

---

### Post by master_kernel on 2009-06-09
**Release deadline for Lumen: June 22, 2009.**

---

### Post by steffan72 on 2009-06-12
can you post the url for the experimental version for use with jaunty please

Cheers

Stef

---

### Post by deepspring on 2009-06-12
> **steffan72 said:**
> can you post the url for the experimental version for use with jaunty please

Cheers

Stef

Do you mean the development version (Lumen) or the experimental branch?

**I suggest you follow the instructions in the first post of this thread for installing the development version (Lumen) instead.**

The experimental branch is under constant development, so it may contain some major bugs. All of our brain storming work is done in the experimental branch. It is only available via bazaar (bzr).

If you really want the experimental branch, open a terminal window up and fire these commands:
```

sudo apt-get install bzr
bzr branch lp:~team-kcheck/kernelcheck/experimental
cd experimental
sudo python setup.py install

```Don't expect any help if you encounter any bugs with this version. Chances are the bugs are be deliberate inclusions for debugging and testing purposes.

**Edit:** To remove the experimental version, open a terminal window and fire these commands:
```

sudo rm -rf /var/log/kernelcheck*
sudo rm -rf /usr/local/bin/kernelcheck
sudo rm -rf /usr/local/lib/python2.6/dist-packages/KernelCheck*
sudo rm -rf /usr/local/share/kernelcheck
sudo rm -rf /usr/share/applications/kernelcheck.desktop
sudo rm -rf /usr/share/pixmaps/kernelcheckicon.png

```

---

### Post by steffan72 on 2009-06-12
got it

i did find it in the end and have compiled the new kernel but it didn't install the nvidia graphics drivers. doesn't seem to want to install them through the hardware drivers section either

any thoughts

---

### Post by master_kernel on 2009-06-12
> **steffan72 said:**
> got it

i did find it in the end and have compiled the new kernel but it didn't install the nvidia graphics drivers. doesn't seem to want to install them through the hardware drivers section either

any thoughts
You probably encountered this error:
```
Your /etc/rc.local file is temporarily being moved to install
the nVidia driver on reboot. It will be run as normal on reboot.
Please boot into the new kernel at the GRUB menu.

Press ENTER to acknowledge these instructions. 
**/usr/local/share/kernelcheck/scripts/kscript.sh: line 313: [185.18.14: command not found**
```

I'm looking into it right now.

**Edit:** If that was the case, you need to move /etc/rc.local.backup-kernelcheck to /etc/rc.local ASAP in order to prevent your computer from getting stuck in an nVidia-installation loop when it reboots.

---

### Post by steffan72 on 2009-06-12
actually i am getting a different error to that

it comes up with an error saying failure to load nvidia module then it tells me x is already running on monitor 0 and wants me to run in low or default graphics mode on monitor 1.  This isw all happening before it loads up the gui

---

### Post by deepspring on 2009-06-12
> **steffan72 said:**
> actually i am getting a different error to that

it comes up with an error saying failure to load nvidia module then it tells me x is already running on monitor 0 and wants me to run in low or default graphics mode on monitor 1.  This isw all happening before it loads up the gui
You need to reconfigure X server so it uses one of the fail safe drivers instead.

Restart the computer, when it gets to the "Loading grub" message, press the ESC key. You should be presented with a list of kernels to boot from, select the first "(recovery mode)" option and hit ENTER.

The machine should be booting into Recovery Mode at this point, when it is finished you should be presented with a menu, scroll down and select the "xfix" option and hit ENTER. When that completes, you should be returned to the menu, press the TAB key until "CANCEL" is selected and hit ENTER.

The computer should startup as normal.

Once you are back in Gnome, use the System -> Administration -> Hardware Drivers applet to install the nVidia drivers.

---

### Post by vampirefo on 2009-06-15
kernelcheck 1.2.5 is crashing as soon as apply tab is pressed, kernelcheck will work if ran in terminal as root.

Any ideal what's causing kernelcheck to close when the apply tab is pressed?

issue has been fixed thanks.

---

### Post by master_kernel on 2009-06-17
This would have been bug 387426:[https://bugs.launchpad.net/kernelcheck/+bug/387426](https://bugs.launchpad.net/kernelcheck/+bug/387426)

---

### Post by djamu on 2009-06-17
Thx for this app.

just a few suggestions since one can't use the nvidia 180 driver without a patch. ( and the kernelcheck nvidia installer is / was broken )...
I had quite a hard time fixing some issues 

My suggestions > wouldn't it be wise to include an unistaller ( purge ) for any nvidia related packages prior to compiling a new driver.
Purging everything nvidia related prior to manually compile the 185 driver not only fixed the driver issue itself, but strangely enough also fixed a mounting issue ( fstab trying to mount a couple of shares before all NIC's where up ) 

to resume > here's what I did ( as root ) after compiling the 2.6.30 kernel
stopping the X server prior to following steps is important > CTRL+ALT+F1 > login > /etc/init.d/gdm stop

```

Ctrl+Alt+F1  
/etc/init.d/gdm stop 
apt-get purge nvidia*
reboot

/etc/init.d/gdm stop   
cd /tmp
wget http://us.download.nvidia.com/XFree86/Linux-x86_64/185.18.14/NVIDIA-Linux-x86_64-185.18.14-pkg2.run

sh NVIDIA-Linux-x86_64-185.18.14-pkg2.run
reboot

```

I did enable 32 bit compatibility mode for any 32 bit app that might need it.

64bit kernel on 
> i7 965
> Asrock Supercomputer X58
> 12GB OCZ  @ 1600
> 295GTX

---

### Post by master_kernel on 2009-06-19
> **djamu said:**
> Thx for this app.

just a few suggestions since one can't use the nvidia 180 driver without a patch. ( and the kernelcheck nvidia installer is / was broken )...
I had quite a hard time fixing some issues 

My suggestions > wouldn't it be wise to include an unistaller ( purge ) for any nvidia related packages prior to compiling a new driver.
Purging everything nvidia related prior to manually compile the 185 driver not only fixed the driver issue itself, but strangely enough also fixed a mounting issue ( fstab trying to mount a couple of shares before all NIC's where up ) 

to resume > here's what I did ( as root ) after compiling the 2.6.30 kernel
stopping the X server prior to following steps is important > CTRL+ALT+F1 > login > /etc/init.d/gdm stop

```

Ctrl+Alt+F1  
/etc/init.d/gdm stop 
apt-get purge nvidia*
reboot

/etc/init.d/gdm stop   
cd /tmp
wget http://us.download.nvidia.com/XFree86/Linux-x86_64/185.18.14/NVIDIA-Linux-x86_64-185.18.14-pkg2.run

sh NVIDIA-Linux-x86_64-185.18.14-pkg2.run
reboot

```

I did enable 32 bit compatibility mode for any 32 bit app that might need it.

64bit kernel on 
> i7 965
> Asrock Supercomputer X58
> 12GB OCZ  @ 1600
> 295GTX
This is already integrated into the latest development version, becoming stable by June 22.

Thanks for the feedback,
MK

---

### Post by makno on 2009-06-21
I'm facing a different problem here, been wrestling with kernel for like a week now and still nothing so i bumped into kernelcheck and remembered i used it before and gave it a shot. Kernel 2.6.30 seems to have compiled properly so i saved added into lilo.conf and done /sbin/lilo. If i restart the server with 2.6.30 it hangs, i can see throught vKVM that it loads fine and i get to the login phase but apart from that i can't ping the machine or ssh into it. Any idea what it could be?

---

### Post by djamu on 2009-06-21
> **makno said:**
> 
...snipsnip..
Kernel 2.6.30 seems to have compiled properly so i saved added into lilo.conf and done /sbin/lilo. If i restart the server with 2.6.30 it hangs,

to my knowledge LILO is deprecated. Development is halted, home page is down, start using GRUB
> 
 i can see throught vKVM that it loads fine and i get to the login phase but apart from that i can't ping the machine or ssh into it. Any idea what it could be?

Login? I suppose you mean a bash shell login ? 

for starters: try in a terminal  
```
sudo ifconfig
```
this should reveal your current IP ( if any )
look for anything following eth0 / eth1 etc... 
( should state > inet addr xxx.xxx.xxx.xxx )

if not then 
2 options.

1. either your network is set to use dhcp without a dhcp server on the network ( is this a desktop system ? do you know anything of networking ? more info is required )

2. kernel didn't load your drivers
check lspci do >
```
sudo lspci
```
and check if an ethernet controller recognized
```
sudo lspci -v
```
reveals more info and displays what driver is loaded for each device.
```
sudo lspci -vv
```
even more


```
sudo lsmod
```
displays all drivers in use


dump all results here

---

### Post by MaCk- on 2009-06-23
i'm stuck using kernelcheck because i can't install libqt3-mt-dev

this is the error:

```
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libqt3-mt-dev: Depends: libglu1-mesa-dev but it is not going to be installed or
                          libglu-dev
E: Broken packages

```

I have googled for hours but can't find a solution.
Anyone here??

---

### Post by deepspring on 2009-06-23
> **MaCk- said:**
> i'm stuck using kernelcheck because i can't install libqt3-mt-dev

this is the error:

```
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libqt3-mt-dev: Depends: libglu1-mesa-dev but it is not going to be installed or
                          libglu-dev
E: Broken packages

```I have googled for hours but can't find a solution.
Anyone here??
What version of Ubuntu are you running?

Do you have the Pre-released and Unsupported Updates options enabled on the Update tab in the Software Sources applet?

---

### Post by MaCk- on 2009-06-23
Jaunty 9.04, I dont have pre-released and unsupported uncommented in my sources.list

But I have found the solution, *sudo aptitude -f dist-upgrade* seemed to do the trick for me.

> mark@d830:~/$ uname -a
Linux d830 2.6.30-candela #1 SMP Tue Jun 23 10:50:17 CEST 2009 i686 GNU/Linux

thanks to kernelcheck!

---

### Post by benphane on 2009-07-10
KernelCheck installed and running using this thread.  Thanks.

I had set KernelCheck aside when an attempt using a "How-to" focusing solely on the tar file, fizzled.

Is it sacrilegious to inquire as to the reason for the AutoKernel forking?

I'm very happy with KernelCheck in my Kubuntu 9.04 environment.

---

### Post by master_kernel on 2009-07-10
> **benphane said:**
> KernelCheck installed and running using this thread.  Thanks.

I had set KernelCheck aside when an attempt using a "How-to" focusing solely on the tar file, fizzled.

Is it sacrilegious to inquire as to the reason for the AutoKernel forking?

I'm very happy with KernelCheck in my Kubuntu 9.04 environment.
Autokernel seemed dead when I found it, so I just decided to fork it into an entirely new project.

---

### Post by benphane on 2009-07-10
> **master_kernel said:**
> Autokernel seemed dead when I found it, so I just decided to fork it into an entirely new project.

So often is the case but I'm grateful for the work that was done and, very grateful that you have continued.  Without KernelCheck, it would probably have been several more years before I would be up to such.

I would not have been surprised and, would have been willing to have dealt with a steeper curve.  So far, smooth sailing and, better, more stable performance than the previous kernel.

Thank you very much.

---

### Post by master_kernel on 2009-07-10
> **benphane said:**
> So often is the case but I'm grateful for the work that was done and, very grateful that you have continued.  Without KernelCheck, it would probably have been several more years before I would be up to such.

I would not have been surprised and, would have been willing to have dealt with a steeper curve.  So far, smooth sailing and, better, more stable performance than the previous kernel.

Thank you very much.
Thanks, but I don't deserve all the credit. deepspring has been a huge help in structuring and optimizing speed. Just wait until the next version - so far it's blowing Lumen away as far as graphics are concerned, and hopefully also performance-wise since we're restructuring it and optimizing the code base. Look for pause/resume buttons in the next version so you can suspend/hibernate safely while compiling a kernel.

---

### Post by benphane on 2009-07-10
> **master_kernel said:**
> Thanks, but I don't deserve all the credit. deepspring has been a huge help in structuring and optimizing speed. Just wait until the next version - so far it's blowing Lumen away as far as graphics are concerned, and hopefully also performance-wise since we're restructuring it and optimizing the code base. Look for pause/resume buttons in the next version so you can suspend/hibernate safely while compiling a kernel.

My thanks to deepsprings.  Didn't even consider suspend/hibernate.  Being my first time, I basically watched the process fairly closely while doing other things.  Suspend/hibernate safely will be great because -- well because.=D> Now I know I might should worry, I look forward to being able to go out for coffee and, not worry.

---

### Post by VastOne on 2009-07-18
Using kernelcheck on last 3 attempts to get to 2.6.30.1 on 3 different machines I have successfully built the kernel but he nVidia drivers have killed it and I have had to completely re-install.

Any reasons as to why? And if I elect to not use the nVidia drivers with the install, will 2.6.30.1 use any default drivers once installed?

---

### Post by VastOne on 2009-07-18
> **VastOne said:**
> Using kernelcheck on last 3 attempts to get to 2.6.30.1 on 3 different machines I have successfully built the kernel but he nVidia drivers have killed it and I have had to completely re-install.

Any reasons as to why? And if I elect to not use the nVidia drivers with the install, will 2.6.30.1 use any default drivers once installed?

I answered the last question by installing 2.6.30.1 without the nVidia driver option and I got a black screen after the "you need to correct the X display" upon boot up

So, is 2.6.30.1 broken for all nVIdia?

---

### Post by master_kernel on 2009-07-18
> **VastOne said:**
> I answered the last question by installing 2.6.30.1 without the nVidia driver option and I got a black screen after the "you need to correct the X display" upon boot up

So, is 2.6.30.1 broken for all nVIdia?
I'm compiling now...

---

### Post by master_kernel on 2009-07-18
My install went flawlessly. Are you using the nVidia option in KC or repo drivers on your own?

---

### Post by VastOne on 2009-07-18
> **master_kernel said:**
> My install went flawlessly. Are you using the nVidia option in KC or repo drivers on your own?

Using what KC provides... Which nVidia driver is it that KC uses? 180.60?

I am now doing a new KC build without changing anything on the options just doing what KC wants adding nothing manually. 

Will let you know the results as it is compiling now

---

### Post by VastOne on 2009-07-18
> **VastOne said:**
> Using what KC provides... Which nVidia driver is it that KC uses? 180.60?

I am now doing a new KC build without changing anything on the options just doing what KC wants adding nothing manually. 

Will let you know the results as it is compiling now

Still the same thing...No loading of nVidia into the kernel

It also does not update the menu.lst as I had to add the new kernel to the grub menu

I installed Kernelcheck via the bzr method....Is that the 1.2.5 version?

---

### Post by master_kernel on 2009-07-18
> **VastOne said:**
> Still the same thing...No loading of nVidia into the kernel

It also does not update the menu.lst as I had to add the new kernel to the grub menu

I installed Kernelcheck via the bzr method....Is that the 1.2.5 version?
The development branch is, not experimental.  KC uses whatever the latest stable one is on nVidia.com. Try uninstalling the binary nVidia driver. You should have a copy of the .run file in /usr/src so you can use the --uninstall option. Then install the kernel, run dpkg-reconfigure -phigh xserver-xorg, reboot into 30.1 and install the binary nVidia driver.

---

### Post by VastOne on 2009-07-18
> **master_kernel said:**
> The development branch is, not experimental.  KC uses whatever the latest stable one is on nVidia.com. Try uninstalling the binary nVidia driver. You should have a copy of the .run file in /usr/src so you can use the --uninstall option. Then install the kernel, run dpkg-reconfigure -phigh xserver-xorg, reboot into 30.1 and install the binary nVidia driver.

Is there a wayI can tell kernelcheck to use 30.0

---

### Post by VastOne on 2009-07-18
> **master_kernel said:**
> The development branch is, not experimental.  KC uses whatever the latest stable one is on nVidia.com. Try uninstalling the binary nVidia driver. You should have a copy of the .run file in /usr/src so you can use the --uninstall option. Then install the kernel, run dpkg-reconfigure -phigh xserver-xorg, reboot into 30.1 and install the binary nVidia driver.

I am using the proprietary drivers (180.44) in this 2.6.28-13-generic build. If I disable (deactivate)it, is that the same as the --uninstall option?

I do not have a .run file in my /usr/scr dir

---

### Post by VastOne on 2009-07-18
> **master_kernel said:**
> The development branch is, not experimental.  KC uses whatever the latest stable one is on nVidia.com. Try uninstalling the binary nVidia driver. You should have a copy of the .run file in /usr/src so you can use the --uninstall option. Then install the kernel, run dpkg-reconfigure -phigh xserver-xorg, reboot into 30.1 and install the binary nVidia driver.

OK, this worked and I am now in 30.1 

What method of installation and version would you suggest for the binary nVidia driver?

---

### Post by master_kernel on 2009-07-18
Use the .run file in /usr/src.
Make sure the path exists.

sh /usr/src/nvidia-driver -a -q --kernel-source-path=/usr/src/linux-headers-2.6.30.1-candela

EDIT: you should have the run file if you ever checked the nVidia option in KC. If not, go download the latest one from nVidia.

---

### Post by VastOne on 2009-07-18
Got it all squared away....

Thanks for your help!

---

### Post by master_kernel on 2009-07-18
Anytime. I just don't understand why KC didn't remove all the nVidia stuff when you checked the option. Guess I got some bug work to do.

---

### Post by VastOne on 2009-07-18
> **master_kernel said:**
> Use the .run file in /usr/src.
Make sure the path exists.

sh /usr/src/nvidia-driver -a -q --kernel-source-path=/usr/src/linux-headers-2.6.30.1-candela

EDIT: you should have the run file if you ever checked the nVidia option in KC. If not, go download the latest one from nVidia.

I did use the nVidia option and the .run file was not there.

I ended up using the deb and ppa that brought me to 185.14

Also, as I noted, kernelcheck did not update menu.lst but I did see in the script that it would not do it because it was seen as a reinstall of the same kernel. This is fine as I added my own, but it might want to give the option to update the menu.lst no matter what and avoid conflict/confusion

Thanks!

---

### Post by VastOne on 2009-07-18
> **master_kernel said:**
> Anytime. I just don't understand why KC didn't remove all the nVidia stuff when you checked the option. Guess I got some bug work to do.

Let me know if I can assist in any way...

I have several test machines at your disosal

---

### Post by master_kernel on 2009-07-18
Thanks, I'll be putting together a completely revamped script next week, and I'll need some testing help since my co-developer has other obligations coming up.

---

### Post by MadCow108 on 2009-07-19
this is a really great tool thanks.

But it should not automatically download and install the newest nvidia driver 185 if you check the nvidia option. It is also not mentioned which driver it is going to load.
I just clicked the option in good hope but ended up with the wrong driver and had to change the link in /usr/src by hand to the 96 drivers.


btw the 96.43.11 drivers need a patch to run with the 2.6.30.1 kernel (haven't tested the 96.43.13 yet):
[http://www.nvnews.net/vbulletin/showthread.php?t=133990](http://www.nvnews.net/vbulletin/showthread.php?t=133990)

---

### Post by VastOne on 2009-07-19
> **MadCow108 said:**
> this is a really great tool thanks.

But it should not automatically download and install the newest nvidia driver 185 if you check the nvidia option. It is also not mentioned which driver it is going to load.
I just clicked the option in good hope but ended up with the wrong driver and had to change the link in /usr/src by hand to the 96 drivers.


btw the 96 drivers need a patch to run with the 2.6.30.1 kernel:
[http://www.nvnews.net/vbulletin/showthread.php?t=133990](http://www.nvnews.net/vbulletin/showthread.php?t=133990)

Which driver is the "wrong driver" that it picked up?

---

### Post by MadCow108 on 2009-07-20
it loaded a 185 driver
I need a 96 legacy driver for my old card.

(btw I just saw there's a new 96 driver available so my note with the patch only aplies to the old 96.43.11 driver.)

---

### Post by VastOne on 2009-07-20
> **MadCow108 said:**
> it loaded a 185 driver
I need a 96 legacy driver for my old card.

(btw I just saw there's a new 96 driver available so my note with the patch only aplies to the old 96.43.11 driver.)

I am pretty sure the script is only setup to get the latest stable drivers from the nVidia site. I think it would be near impossible for it to do a hal scan to determine what you and every other user would need for a driver, but I will let the author speak to that...

---

### Post by MadCow108 on 2009-07-20
Of course it would be to much work to check which card a user has.
But it would be nice if you could choose your driver in the wizard when you activate the nvidia option. Similar to how you choose your kernel patch. (there also are only 3 types of nvidia drivers anyway)
The automatic removal of the old driver and installation on reboot is a nice feature which should also be available for older (nvidia)cards (well it is but currently it requires some additional user action before rebooting).

At least it should say which driver version it will download and try to install in the summary page (maybe I also just overlooked it :/ ).

---

### Post by master_kernel on 2009-07-20
> **MadCow108 said:**
> Of course it would be to much work to check which card a user has.
But it would be nice if you could choose your driver in the wizard when you activate the nvidia option. Similar to how you choose your kernel patch. (there also are only 3 types of nvidia drivers anyway)
The automatic removal of the old driver and installation on reboot is a nice feature which should also be available for older (nvidia)cards (well it is but currently it requires some additional user action before rebooting).

At least it should say which driver version it will download and try to install in the summary page (maybe I also just overlooked it :/ ).
I may add support for legacy in the next version. But it does say which version it will install, only it shows in the terminal right before the run package is downloaded.

---

### Post by MadCow108 on 2009-07-20
great thanks.

I saw it in the terminal and did correct it but I didn't know until that step whats going to happen. It should be stated before the program starts running.

---

### Post by BlackNinjaVirus on 2009-07-25
Can I save a kernelcheck kernel and implant it into a Debian Testing CD with a iwl4965 wireless driver installed?

I like straight Debian, but the kernels don't supprt booting off EXT4 like Ubuntu does, so I will always have Ubuntu, but Debian is stable enough for my Graduate Degree laptop.

---

### Post by Clintonostra on 2009-07-27
Running Jaunty and KDE4.2
I have kernelcheck 1.2.5-3 deb installed.
I have checked your thread and google but can't find a solution for the following message:
Need to install python bindings for libvte

Your help appreciated.
Jack

---

### Post by master_kernel on 2009-07-31
> **BlackNinjaVirus said:**
> Can I save a kernelcheck kernel and implant it into a Debian Testing CD with a iwl4965 wireless driver installed?

I like straight Debian, but the kernels don't supprt booting off EXT4 like Ubuntu does, so I will always have Ubuntu, but Debian is stable enough for my Graduate Degree laptop.
I don't see why not.

---

### Post by master_kernel on 2009-07-31
> **Clintonostra said:**
> Running Jaunty and KDE4.2
I have kernelcheck 1.2.5-3 deb installed.
I have checked your thread and google but can't find a solution for the following message:
Need to install python bindings for libvte

Your help appreciated.
Jack
```
sudo apt-get install python-vte
```

---

### Post by Clintonostra on 2009-08-01
sudo apt-get install python-vte

Have python-vte-1:0.20.0-Oubuntu2(AMD64) installed. Received the same message when trying to run kernelckeck:Need to install python bindings for libvte
Jack

---

### Post by mathyou on 2009-08-13
10char

---

### Post by xenogia on 2009-08-13
I can't use Kernelcheck due to QT3 dependencies, using gnome.. it wont install them because of the following:

The following packages have unmet dependencies:
  libglu1-mesa-dev: Depends: libglu1-mesa (= 7.4-0ubuntu3.1) but 7.4-0ubuntu3.2 is to be installed

---

### Post by master_kernel on 2009-08-17
Dependency hell. It's a Ubuntu repo problem. Try getting the package again, and if it doesn't work, file a bug for libglu1-mesa-dev in Launchpad.

EDIT: I just saw you solved this problem: [http://ubuntuforums.org/showthread.php?t=1239739&highlight=kernelcheck](http://ubuntuforums.org/showthread.php?t=1239739&highlight=kernelcheck)

---

### Post by Synchro on 2009-08-18
I used kernelcheck a while ago to upgrade a kernel on an Ubuntu 8.10 server in order to work around a RAID problem on some particular hardware. Since then I've had an ongoing problem that aptitude clearly has no idea what kernelcheck did, so is stuck offering me upgrades to older kernels. How can I get kernelcheck's kernel to sync with apt?

I used kernelcheck 1.1.4 at the time, but I notice that I can't run the latest version on 8.10 because of a python-central dependency.

---

### Post by FlekkeN on 2009-08-25
Hi!

In the program i can't find any info how much disk space it use for compiling a kernel. I think this should be included. Nice program though, keep it going!

---

### Post by xir_ on 2009-08-26
just trying out your program, very nice.

would it be possible to give a better progress bar, perhaps by having it monitor the folder letter the compiler is running in. e.g when in a top level folder starting with a 1% and when in a folder starting with z at 99%?

I'm not sure if this is already taken care of but my config file hadn't specified cpu type, could you create and option to optimize for cpu type? (forgive me if i have misunderstood)

just a thought.

---

### Post by Cato2 on 2009-08-29
> **Synchro said:**
> I used kernelcheck a while ago to upgrade a kernel on an Ubuntu 8.10 server in order to work around a RAID problem on some particular hardware. Since then I've had an ongoing problem that aptitude clearly has no idea what kernelcheck did, so is stuck offering me upgrades to older kernels. How can I get kernelcheck's kernel to sync with apt?

I used kernelcheck 1.1.4 at the time, but I notice that I can't run the latest version on 8.10 because of a python-central dependency.

You need to do a 'hold' on the APT packages that you don't need (i.e. linux-generic, linux-headers, or whatever Aptitude is offering to upgrade).  This means that you won't ever get them upgraded by aptitude or apt-get etc.

Here's what to do:

1. aptitude hold linux-generic  (and other packages.)  This only works for aptitude though, so do step 2-3 as well.

2. aptitude install wajig

3. wajig hold linux-generic (etc)

Wajig works for apt-get, synaptic, etc as well.  It also has some nice query features, but I only use it occasionally when aptitude makes something difficult.

The one downside of this is that you don't get any security updates for your kernel - so if malware runs as a normal user on your system, it may be able to use a root exploit to become root - and in some cases there could be a remote exploit, e.g. in a wireless driver as happened a while back.  

So I recommend you sign up to ubuntu-security-announce at [https://lists.ubuntu.com/#Announcement+Lists](https://lists.ubuntu.com/#Announcement+Lists) so you get some idea of the vulnerabilities not being fixed, and re-run your kernel build if you decide these vulnerabilities need fixing - or just do a periodic rebuild.

---

### Post by Zoot7 on 2009-09-12
Major thanks to master_kernel! :)

Used this to upgrade to 2.6.30.5 on Jaunty and it worked like a charm!

---

### Post by joeelmex on 2009-09-22
i installed kernel check and when i click on get kernel information i get an error:
kernel.org server couldnt fulfill request error 404.  Then it closes.  Any ideas?  Thanks

---

### Post by deepspring on 2009-09-23
> **joeelmex said:**
> i installed kernel check and when i click on get kernel information i get an error:
kernel.org server couldnt fulfill request error 404.  Then it closes.  Any ideas?  Thanks
Unfortunately for us, kernel.org have removed the files used by kernelcheck to retrieve the latest kernel information. Master_Kernel is looking into alternatives, but it will be a while before he can focus on KernelCheck due to his studies.

---

### Post by joeelmex on 2009-09-23
bummer so we need to install kernels the old fashion way again.

---

### Post by deepspring on 2009-09-23
> **joeelmex said:**
> bummer so we need to install kernels the old fashion way again.

There is an excellent guide here:
[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

---

### Post by polacrilex on 2009-09-28
FYI: Launchpad bug report:
[https://bugs.launchpad.net/kernelcheck/+bug/432732](https://bugs.launchpad.net/kernelcheck/+bug/432732)

---

### Post by Nutterpc on 2009-10-02
I tried to use this program earlier on today, it tells me the master.kernelcheck.org is not there

---

### Post by master_kernel on 2009-10-18
Fix commmitted, just waiting on feedback now.

---

### Post by VastOne on 2009-10-18
FYI, I just dloaded and installed the latest 1.2.5 from your site and then tried to patch by (The patching system works when you click "Check for KernelCheck Updates" on the second page of the wizard.) an it did not work...

Says that there is no patch

Just Info for you

---

### Post by VastOne on 2009-10-18
MOre info in trying o apply the packages

vastone@vastone-phenom4am3:/usr/share/pyshared/KernelCheck$ cat source_changes.patch | patch -p1
can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -NaurB old/KernelCheck/KernelPageParser.py new/KernelCheck/KernelPageParser.py
|--- old/KernelCheck/KernelPageParser.py	2009-06-20 12:42:18.373073000 -0400
|+++ new/KernelCheck/KernelPageParser.py	2009-10-18 11:53:09.028558254 -0400
--------------------------
File to patch: ^C



vastone@vastone-phenom4am3:/usr/share/pyshared/KernelCheck$ sudo patch -p1 <source_changes.patch
[sudo] password for vastone: 
can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -NaurB old/KernelCheck/KernelPageParser.py new/KernelCheck/KernelPageParser.py
|--- old/KernelCheck/KernelPageParser.py	2009-06-20 12:42:18.373073000 -0400
|+++ new/KernelCheck/KernelPageParser.py	2009-10-18 11:53:09.028558254 -0400
--------------------------
File to patch: 


I may be doing something wrong but I think I am following the right directions????

---

### Post by master_kernel on 2009-10-19
> **VastOne said:**
> MOre info in trying o apply the packages

vastone@vastone-phenom4am3:/usr/share/pyshared/KernelCheck$ cat source_changes.patch | patch -p1
can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -NaurB old/KernelCheck/KernelPageParser.py new/KernelCheck/KernelPageParser.py
|--- old/KernelCheck/KernelPageParser.py	2009-06-20 12:42:18.373073000 -0400
|+++ new/KernelCheck/KernelPageParser.py	2009-10-18 11:53:09.028558254 -0400
--------------------------
File to patch: ^C



vastone@vastone-phenom4am3:/usr/share/pyshared/KernelCheck$ sudo patch -p1 <source_changes.patch
[sudo] password for vastone: 
can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -NaurB old/KernelCheck/KernelPageParser.py new/KernelCheck/KernelPageParser.py
|--- old/KernelCheck/KernelPageParser.py	2009-06-20 12:42:18.373073000 -0400
|+++ new/KernelCheck/KernelPageParser.py	2009-10-18 11:53:09.028558254 -0400
--------------------------
File to patch: 


I may be doing something wrong but I think I am following the right directions????
You got the wrong patch. You used the one to apply to the source code. You should use the two patches listed under that one if KernelCheck is already installed.

---

### Post by VastOne on 2009-10-19
That was the one I did pull down.  I will try it again and let you know

---

### Post by VastOne on 2009-10-19
> **master_kernel said:**
> You got the wrong patch. You used the one to apply to the source code. You should use the two patches listed under that one if KernelCheck is already installed.

Let me make sure I understand this.  I have dloaded the main_changes.patch.  I then need to go to /usr/share/pyshared/KernelCheck/ and /usr/share/kernelcheck/scripts/ and run 

cat main_changes.patch | patch -p1 

in each directory, correct?

After putting the files in each directory, of course

---

### Post by master_kernel on 2009-10-19
> **VastOne said:**
> Let me make sure I understand this.  I have dloaded the main_changes.patch.  I then need to go to /usr/share/pyshared/KernelCheck/ and /usr/share/kernelcheck/scripts/ and run 

cat main_changes.patch | patch -p1 

in each directory, correct?

After putting the files in each directory, of course
Yep

---

### Post by Nutterpc on 2009-10-19
And I can say firsthand, after working with Master_kernel & deepspring, that these patches do work

Running on a highly trimmed 64Bit kernel right now, as I post this

2.6.32-rc5-candela

Makes it slammingly fast now, and because it allows you the chance to update the kernel to your liking, you can include/disallow whatever options/drivers you wish

For example: Using the default kernel that comes with ubuntu, my onboard laptop wireless refused to work

Using this new kernel now, the laptop is singing

---

### Post by VastOne on 2009-10-20
From here:

vastone@vastone-phenom4am3:~$ cd /usr/share/pyshared/KernelCheck

vastone@vastone-phenom4am3:/usr/share/pyshared/KernelCheck$ ls

about.py      __init__.py  KernelPageParser.py   virtualterminal.py
constants.py  KCDebug.py   source_changes.patch


I am running this:

vastone@vastone-phenom4am3:/usr/share/pyshared/KernelCheck$ cat 
source_changes.patch | patch -p1

can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -NaurB old/KernelCheck/KernelPageParser.py new/KernelCheck/KernelPageParser.py
|--- old/KernelCheck/KernelPageParser.py	2009-06-20 12:42:18.373073000 -0400
|+++ new/KernelCheck/KernelPageParser.py	2009-10-18 11:53:09.028558254 -0400
--------------------------
File to patch:

I have grabbed the sources_changes.patch right off the launchpad site

[https://bugs.launchpad.net/kernelcheck/+bug/432732](https://bugs.launchpad.net/kernelcheck/+bug/432732)

Am I supposed to input the file name to patch as it asks or is this suppose to do that for me? 

Thanks

---

### Post by dagodemon42 on 2009-10-20
> **VastOne said:**
> From here:

vastone@vastone-phenom4am3:~$ cd /usr/share/pyshared/KernelCheck

vastone@vastone-phenom4am3:/usr/share/pyshared/KernelCheck$ ls

about.py      __init__.py  KernelPageParser.py   virtualterminal.py
constants.py  KCDebug.py   source_changes.patch


I am running this:

vastone@vastone-phenom4am3:/usr/share/pyshared/KernelCheck$ cat 
source_changes.patch | patch -p1

can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -NaurB old/KernelCheck/KernelPageParser.py new/KernelCheck/KernelPageParser.py
|--- old/KernelCheck/KernelPageParser.py	2009-06-20 12:42:18.373073000 -0400
|+++ new/KernelCheck/KernelPageParser.py	2009-10-18 11:53:09.028558254 -0400
--------------------------
File to patch:

I have grabbed the sources_changes.patch right off the launchpad site

[https://bugs.launchpad.net/kernelcheck/+bug/432732](https://bugs.launchpad.net/kernelcheck/+bug/432732)

Am I supposed to input the file name to patch as it asks or is this suppose to do that for me? 

Thanks
therearetwo different patches needed. The patch for KernelPageParser.py is listed as parser_changes.patch. It is a little further down the page from the main_changes.patch. I used the "sudo" method of installing the patches and it worked great. Many thanks to master_kernel and all involved in this project.

---

### Post by gumshore on 2009-10-24
could someone please upload a .deb with this fix committed already? That would really help me out here, since my computer does not seem to want to patch the files

---

### Post by marksken on 2009-11-03
Any fixed version we can download ?
Don't get it how to use fix.

Thanx Marksken

---

### Post by stevenpusser on 2009-11-06
Hmmm....I have a fixed Debian Lenny compatible package here:

[https://sites.google.com/site/stevosfilehideaway/Home/kernelcheck-1.2.5_mlrepo3.zip](https://sites.google.com/site/stevosfilehideaway/Home/kernelcheck-1.2.5_mlrepo3.zip)


It should also run on Ubuntu.

Source files are included if you want to examine the code and build your own package...remember, it's bad security practice to install unknown programs.  That's what gets the Windows guys in big trouble. 

I did help Master_Kernel with the deb package for Lumen, for what it's worth.  The packaging setup is pretty robust; I just threw his patches into /debian/patches and rebuilt, and was good to go.


I made it Lenny compatible to see it anybody over on the Debian forums will try it...so far I have one person game to try it, and the usual "what makes this any better than the command line tools?"

---

### Post by marksken on 2009-11-16
o stevenpusser

Thanx for the fixed version, worked perfect on my ubuntu 9.10,
need to compile the kernel for my dvd-drive with kernelcheck it's so easy

---

### Post by gumshore on 2009-11-20
thanks for the deb. I know have a problem with getting ndiswrapper to work. When I build the kernel, It compiles and runs just fine, but the only thing that does not work is ndiswrapper! Basiclly, that makes the new kernel useless. I read somewhere that you need to install ndiswrapper-sources, but that does not seem to be in the repositories. could someone please guide me through this?

---

### Post by master_kernel on 2009-11-22
> **gumshore said:**
> thanks for the deb. I know have a problem with getting ndiswrapper to work. When I build the kernel, It compiles and runs just fine, but the only thing that does not work is ndiswrapper! Basiclly, that makes the new kernel useless. I read somewhere that you need to install ndiswrapper-sources, but that does not seem to be in the repositories. could someone please guide me through this?
Try downloading the source from [http://sourceforge.net/projects/ndiswrapper/]("http://sourceforge.net/projects/ndiswrapper/") and compiling it with the new kernel running. Let me know how that goes.

---

### Post by gumshore on 2009-11-23
> **master_kernel said:**
> Try downloading the source from [http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/) and compiling it with the new kernel running. Let me know how that goes.
Thanks for the help, but it did not work. here is my terminal output:

```
ryan@ryan-laptop:~$ cd ndiswrapper*
ryan@ryan-laptop:~/ndiswrapper-1.55$ sudo make uninstall
[sudo] password for ryan: 
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
ryan@ryan-laptop:~/ndiswrapper-1.55$ make
make -C driver
make[1]: Entering directory `/home/ryan/ndiswrapper-1.55/driver'
make -C /usr/src/linux-headers-2.6.31.6-candela M=/home/ryan/ndiswrapper-1.55/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.31.6-candela'
  LD      /home/ryan/ndiswrapper-1.55/driver/built-in.o
  MKEXPORT /home/ryan/ndiswrapper-1.55/driver/crt_exports.h
  MKEXPORT /home/ryan/ndiswrapper-1.55/driver/hal_exports.h
  MKEXPORT /home/ryan/ndiswrapper-1.55/driver/ndis_exports.h
  MKEXPORT /home/ryan/ndiswrapper-1.55/driver/ntoskernel_exports.h
  MKEXPORT /home/ryan/ndiswrapper-1.55/driver/ntoskernel_io_exports.h
  MKEXPORT /home/ryan/ndiswrapper-1.55/driver/rtl_exports.h
  MKEXPORT /home/ryan/ndiswrapper-1.55/driver/usb_exports.h
  CC [M]  /home/ryan/ndiswrapper-1.55/driver/crt.o
In file included from /home/ryan/ndiswrapper-1.55/driver/crt.c:16:
/home/ryan/ndiswrapper-1.55/driver/ntoskernel.h: In function &#8216;PushEntrySList&#8217;:
/home/ryan/ndiswrapper-1.55/driver/ntoskernel.h:905: error: implicit declaration of function &#8216;cmpxchg8b&#8217;
make[3]: *** [/home/ryan/ndiswrapper-1.55/driver/crt.o] Error 1
make[2]: *** [_module_/home/ryan/ndiswrapper-1.55/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31.6-candela'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/ryan/ndiswrapper-1.55/driver'
make: *** [all] Error 2
ryan@ryan-laptop:~/ndiswrapper-1.55$ sudo make install
make -C driver install
make[1]: Entering directory `/home/ryan/ndiswrapper-1.55/driver'
make -C /usr/src/linux-headers-2.6.31.6-candela M=/home/ryan/ndiswrapper-1.55/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.31.6-candela'
  CC [M]  /home/ryan/ndiswrapper-1.55/driver/crt.o
In file included from /home/ryan/ndiswrapper-1.55/driver/crt.c:16:
/home/ryan/ndiswrapper-1.55/driver/ntoskernel.h: In function &#8216;PushEntrySList&#8217;:
/home/ryan/ndiswrapper-1.55/driver/ntoskernel.h:905: error: implicit declaration of function &#8216;cmpxchg8b&#8217;
make[3]: *** [/home/ryan/ndiswrapper-1.55/driver/crt.o] Error 1
make[2]: *** [_module_/home/ryan/ndiswrapper-1.55/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31.6-candela'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/ryan/ndiswrapper-1.55/driver'
make: *** [install] Error 2
ryan@ryan-laptop:~/ndiswrapper-1.55$ sudo depmod -a
ryan@ryan-laptop:~/ndiswrapper-1.55$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module ndiswrapper not found.
ryan@ryan-laptop:~/ndiswrapper-1.55$ 
```
I also tried compiling it using the ubuntu kernel and with the svn version of ndiswrapper, and neither of those worked. If I can get this working by Thursday the 26th, that would be greatly appreciated.

---

### Post by stevenpusser on 2009-12-04
The ndiswrapper 1.5.4 -source package builds with 2.6.31 and 2.6.32 kernels for me...I'm using a Debian Lenny based system, but it should also work for you on Ubuntu.  The Debian deb files are available here:  [http://packages.debian.org/sid/ndiswrapper-source](http://packages.debian.org/sid/ndiswrapper-source)

and you can build automatically build and install a deb with module-assistant:

**sudo m-a update&&m-a prepare&&m-a a-i -t ndiswrapper-source**

I use the -t (terminal) flag because I like to watch the messages, otherwise you will get a rather uninformative ncurses terminal "GUI".

---

### Post by lunaparadox on 2009-12-20
after running I get this at the end

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.32.2-candela.postinst line 1186.
dpkg: error processing linux-image-2.6.32.2-candela (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.32.2-candela
E: Sub-process /usr/bin/dpkg returned an error code (1)

now when I install anything through apt-get after it installs it reruns the end of kernelcheck with this ending as well. if need be I can copy all thats running there. Just thought this might be enough for an answer.
thanks. oh and I did get to boot into the new kernel by running the grub stuff myself after the error at the end. I'm using ubuntu 9.10

---

### Post by deepspring on 2009-12-20
> **lunaparadox said:**
> after running I get this at the end

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.32.2-candela.postinst line 1186.
dpkg: error processing linux-image-2.6.32.2-candela (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.32.2-candela
E: Sub-process /usr/bin/dpkg returned an error code (1)

now when I install anything through apt-get after it installs it reruns the end of kernelcheck with this ending as well. if need be I can copy all thats running there. Just thought this might be enough for an answer.
thanks. oh and I did get to boot into the new kernel by running the grub stuff myself after the error at the end. I'm using ubuntu 9.10

Try this.
[http://ubuntuforums.org/showthread.php?p=6289960&highlight=nvidia-common#post6289960](http://ubuntuforums.org/showthread.php?p=6289960&highlight=nvidia-common#post6289960)

---

### Post by lunaparadox on 2009-12-21
Thanks that got it:)

---

### Post by MIke65 on 2009-12-27
Hy!
I was complied a new (2.6.32.2) kernel to linux mint 8 with the kernelcheck app. In the upcoming menuconfig I don't do nothing since i'm not an expert in kernel compiling, so i think it uses the default kernel options what comes with mint 8. After it done i was rebooted and choose the new kernel in grub, but then it won't boot, only show black screen. What can be the problem? The only reason i need the newest kernel is the support for my ati r6xx card's 3d acceleration. The default mint kernel is still works fine. I get the following message when i load the 2.6.31-14 kernel's config: warning Symbol value 'm' invalid for FB_VESA.
So the old config not fully compatible i think. But how can i solve this? I'm a rookie when it comes to config the kernel. I was search for fb_vesa in the menuconfig and it gives me a new vga vesa option, so i choose y for it. But the result is the same. After i try to start the safe mode of the kernel i see some lines and before the black screen i saw 2 lines what started with [SATA], then the monitor goes black. Alt+sysRq+reisub the only thing what react. I was try the glxpayload=text option to start the kernel (changed from vga=normal) but it do the same thing.

---

### Post by wmd on 2010-01-12
Is there a way of using KernelCheck just on command line? I'd like to run it on my Ubuntu Server install to get to 2.26.32 together with BFS and maybe compile everything with ICC. Remotely possible?

---

### Post by master_kernel on 2010-01-24
Sorry, console/terminal support is planned for the next version.

---

### Post by stevenpusser on 2010-02-04
I don't think ATI had released a driver that would build with the 2.6.32 kernel at that time.  When you build a new kernel, you also have to rebuild Nvidia and ATI proprietary drivers.  Ordinarily, dkms will do this automatically if the drivers support it...but you may have to wait a bit for the new fglrx support.

Unless you are talking about the new xorg radeon driver, which is open-source?  Then you may have to do a little web searching to see what the correct configuration for that driver in the kernel is.  I think you have at least enable kernel mode setting for ATI cards.

That "m" symbol that was no longer compatible means build that driver as a module; like you said, that may no longer be an option.

> **MIke65 said:**
> Hy!
I was complied a new (2.6.32.2) kernel to linux mint 8 with the kernelcheck app. In the upcoming menuconfig I don't do nothing since i'm not an expert in kernel compiling, so i think it uses the default kernel options what comes with mint 8. After it done i was rebooted and choose the new kernel in grub, but then it won't boot, only show black screen. What can be the problem? The only reason i need the newest kernel is the support for my ati r6xx card's 3d acceleration. The default mint kernel is still works fine. I get the following message when i load the 2.6.31-14 kernel's config: warning Symbol value 'm' invalid for FB_VESA.
So the old config not fully compatible i think. But how can i solve this? I'm a rookie when it comes to config the kernel. I was search for fb_vesa in the menuconfig and it gives me a new vga vesa option, so i choose y for it. But the result is the same. After i try to start the safe mode of the kernel i see some lines and before the black screen i saw 2 lines what started with [SATA], then the monitor goes black. Alt+sysRq+reisub the only thing what react. I was try the glxpayload=text option to start the kernel (changed from vga=normal) but it do the same thing.

---

### Post by kenm_uk on 2010-02-07
> **master_kernel said:**
> You probably encountered this error:
```
Your /etc/rc.local file is temporarily being moved to install
the nVidia driver on reboot. It will be run as normal on reboot.
Please boot into the new kernel at the GRUB menu.

Press ENTER to acknowledge these instructions. 
**/usr/local/share/kernelcheck/scripts/kscript.sh: line 313: [185.18.14: command not found**
```

I'm looking into it right now.

**Edit:** If that was the case, you need to move /etc/rc.local.backup-kernelcheck to /etc/rc.local ASAP in order to prevent your computer from getting stuck in an nVidia-installation loop when it reboots.

I recently compiled the 2.6.32.3 kernel (with a patch) on my Ubuntu 9.10 machine and had this error as well.  When running 'top' I could see nvidia-installer continually running at 100% CPU.  The above fix above along with running /usr/src/NVIDIA* to install the nvidia driver fixed the problem for me.

Thanks!

---

### Post by lpeter on 2010-03-27
27 Mar 2010

Newbie.  Am trying to upgrade kernel in Toshiba laptop running 9.10 to fix wireless problem and generally improve performance.   Downloaded and have run KernelCheck several times.  Keeps hanging at 70% according to the indicator bar. the Terminal window has these details:
[INDENT]This is kernel package version 11.015.
echo "The UTS Release version in include/Linux/version.h"; echo "       \"\" "; echo "does not match current version:"; echo "    \"2.6.33.1-candela\" "; echo "Please correct this."; exit 2
The UTS Release version in include/Linux/version.h
                       ""
does not match current version:
"2.6.33.1-candela"
Please correct this.
make[1]: *** [debian/stamp/install/linux-image-2.6.33.1-candela] Error 2
make: *** [kernel_image] Error 2
make[1]: leaving directory '/usr/src/linux-2.6.33'

ABORT: stage6 returned exit status 2
[/INDENT]I have no clue on what all of that means and what I need to do to fix whatever is wrong.  I would be most grateful for any assistance.

(Also, a small post-script, I retyped all of the terminal remarks above because copy paste is unavailable.  Is there some alternative method to C-P when, like now, I cannot select text in the terminal?  Thnx).
Many thanks in advance.
LTP

---

### Post by ghostkill3r on 2010-04-01
hi
i downloaded the newest source from SF and patched it, but everytime i try to run it from the terminal and click on "Get Kernel Information" i get this error

```
Testing your network connection...
Connection found.
have not read
read feed
Traceback (most recent call last):
  File "/usr/local/share/kernelcheck/scripts/main.py", line 502, in get_data
    patch_url, patch, stable, stable_url, OldKernelList, OldKernelLinks, prepatch, prepatch_url = self.kernelinfo()
  File "/usr/local/share/kernelcheck/scripts/main.py", line 126, in kernelinfo
    KPParser.close()
  File "/usr/lib/python2.6/HTMLParser.py", line 112, in close
    self.goahead(1)
  File "/usr/lib/python2.6/HTMLParser.py", line 164, in goahead
    self.error("EOF in middle of construct")
  File "/usr/lib/python2.6/HTMLParser.py", line 115, in error
    raise HTMLParseError(message, self.getpos())
HTMLParser.HTMLParseError: EOF in middle of construct, at line 7, column 11

```

am i missing something?

it just stays on "Retrieving information from http://www.kernel.org/" and dosen't do anything :/

but if i click on "Check for KernelCheck Updates" it works

i hope someone can help me with this

ciao
ghostkill3r

---

### Post by balloons on 2010-04-01
ghostkill3r.. in the meantime, try 1.5

# Download the KernelCheck source from LaunchPad:
$ bzr branch lp:~team-kcheck/kernelcheck/experimental

# Enter the directory
$ cd experimental

# Install KernelCheck (as root - su)
$ python setup.py install

# Use it! (once again, as root)
$ kernelcheck

---

### Post by ghostkill3r on 2010-04-01
> **guitara said:**
> ghostkill3r.. in the meantime, try 1.5

# Download the KernelCheck source from LaunchPad:
$ bzr branch lp:~team-kcheck/kernelcheck/experimental

# Enter the directory
$ cd experimental

# Install KernelCheck (as root - su)
$ python setup.py install

# Use it! (once again, as root)
$ kernelcheck


thanks, and i love you for your tip :)
it's working now, and it's working good :)

i came across this version before, but never wanted to install something with the name experimental, as a Linux noob.
but i changed from windoz to linux just for this i think :)
so, thanks to You i will try something like this experimental thingy nextime.

thank you

ciao
ghostkill3r

---

### Post by ghostkill3r on 2010-04-02
hmm maybe i was to fast :(

i mean the program is running very nicely, it's doing its jobs (checking for the kernels), i then made my choices go to the last tab clicked on this "start build" button and thougt ist ok to go to bed, i then woke up today and saw that the program has done nothing at all.

i tried the same thing again today (beside going to bed), and again nothing after i click on on this "start build" button :(

what could be the problem? i mean there is not even a message in the terminal saing whats wrong :(

anyway its a realy good program, even if its not working for me.
but i think i will try the "Old" kernel way.

i've done sudo kernelcheck > debug.txt, and thats all i got
```

Kernel Name: 2.6.33
Link: http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.33.tar.bz2
Type: base
Base Kernel: 2.6.33
Partial Base: 33
Ending: None


Kernel Name: 2.6.33.2
Link: http://kernel.org/pub/linux/kernel/v2.6/2.6.33.2.bz2
Type: performance patch
Base Kernel: 2.6.33
Partial Base: 33
Ending: None


Kernel Name: 2.6.34-rc3
Link: http://www.kernel.org/pub/linux/kernel/v2.6/testing/2.6.34-rc3.bz2
Type: prepatch
Base Kernel: 2.6.33
Partial Base: 33
Ending: rc3


Kernel Name: 2.6.33.1-rt11
Link: http://www.kernel.org/pub/linux/kernel/projects/rt/patch-2.6.33.1-rt11.bz2
Type: rt patch
Base Kernel: 2.6.33
Partial Base: 33
Ending: rt11


Kernel Name: 2.6.34-rc3-next-20100401
Link: http://www.kernel.org/pub/linux/kernel/people/sfr/linux-next/patch-v2.6.34-rc3-next-20100401.bz2
Type: latest linux-next patchset
Base Kernel: 2.6.34-rc3
Partial Base: 34
Ending: rc3-next-20100401


Kernel Name: 2.6.33-next-20100308
Link: http://www.kernel.org/pub/linux/kernel/people/sfr/linux-next/patch-v2.6.33-next-20100308.bz2
Type: linux-next patchset for 2.6.33
Base Kernel: 2.6.33
Partial Base: 33
Ending: next-20100308


Kernel Name: 2.6.33.2-rc1
Link: http://www.kernel.org/pub/linux/kernel/v2.6/stable-review/patch-2.6.33.2-rc1.bz2
Type: stable review patchset
Base Kernel: 2.6.32.2-rc1
Partial Base: 32
Ending: rc1


Discovering older kernels and creating dictionary

Kernel Name: 2.6.31-20-generic-pae
Link: localhost
Type: running kernel
Base Kernel: 2.6.31
Partial Base: 31
Ending: 20-generic-pae

```

ciao
ghostkill3r

ps: sorry for ..., not having english as my native language.

---

### Post by master_kernel on 2010-04-04
> **ghostkill3r said:**
> hmm maybe i was to fast :(

i mean the program is running very nicely, it's doing its jobs (checking for the kernels), i then made my choices go to the last tab clicked on this "start build" button and thougt ist ok to go to bed, i then woke up today and saw that the program has done nothing at all.

i tried the same thing again today (beside going to bed), and again nothing after i click on on this "start build" button :(

what could be the problem? i mean there is not even a message in the terminal saing whats wrong :(

anyway its a realy good program, even if its not working for me.
but i think i will try the "Old" kernel way.

i've done sudo kernelcheck > debug.txt, and thats all i got
```

Kernel Name: 2.6.33
Link: http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.33.tar.bz2
Type: base
Base Kernel: 2.6.33
Partial Base: 33
Ending: None


Kernel Name: 2.6.33.2
Link: http://kernel.org/pub/linux/kernel/v2.6/2.6.33.2.bz2
Type: performance patch
Base Kernel: 2.6.33
Partial Base: 33
Ending: None


Kernel Name: 2.6.34-rc3
Link: http://www.kernel.org/pub/linux/kernel/v2.6/testing/2.6.34-rc3.bz2
Type: prepatch
Base Kernel: 2.6.33
Partial Base: 33
Ending: rc3


Kernel Name: 2.6.33.1-rt11
Link: http://www.kernel.org/pub/linux/kernel/projects/rt/patch-2.6.33.1-rt11.bz2
Type: rt patch
Base Kernel: 2.6.33
Partial Base: 33
Ending: rt11


Kernel Name: 2.6.34-rc3-next-20100401
Link: http://www.kernel.org/pub/linux/kernel/people/sfr/linux-next/patch-v2.6.34-rc3-next-20100401.bz2
Type: latest linux-next patchset
Base Kernel: 2.6.34-rc3
Partial Base: 34
Ending: rc3-next-20100401


Kernel Name: 2.6.33-next-20100308
Link: http://www.kernel.org/pub/linux/kernel/people/sfr/linux-next/patch-v2.6.33-next-20100308.bz2
Type: linux-next patchset for 2.6.33
Base Kernel: 2.6.33
Partial Base: 33
Ending: next-20100308


Kernel Name: 2.6.33.2-rc1
Link: http://www.kernel.org/pub/linux/kernel/v2.6/stable-review/patch-2.6.33.2-rc1.bz2
Type: stable review patchset
Base Kernel: 2.6.32.2-rc1
Partial Base: 32
Ending: rc1


Discovering older kernels and creating dictionary

Kernel Name: 2.6.31-20-generic-pae
Link: localhost
Type: running kernel
Base Kernel: 2.6.31
Partial Base: 31
Ending: 20-generic-pae

```

ciao
ghostkill3r

ps: sorry for ..., not having english as my native language.
Still looks like you have the experimental version installed. You have to fully remove it before installing the patched version of 1.5. (By manually removing files)

As of right now, the experimental version does nothing, but I will try to have working kernel compilation support by tomorrow - I want to test drive pause/resume buttons and/or the new CLI support. But note for future reference that the experimental build may not work at all times - the development build is the one you want to download (except when it outdates the stable version ;)).

---

### Post by stevenpusser on 2010-04-04
> **lpeter said:**
> 27 Mar 2010

Newbie.  Am trying to upgrade kernel in Toshiba laptop running 9.10 to fix wireless problem and generally improve performance.   Downloaded and have run KernelCheck several times.  Keeps hanging at 70% according to the indicator bar. the Terminal window has these details:
[INDENT]This is kernel package version 11.015.
echo "The UTS Release version in include/Linux/version.h"; echo "       \"\" "; echo "does not match current version:"; echo "    \"2.6.33.1-candela\" "; echo "Please correct this."; exit 2
The UTS Release version in include/Linux/version.h
                       ""
does not match current version:
"2.6.33.1-candela"
Please correct this.
make[1]: *** [debian/stamp/install/linux-image-2.6.33.1-candela] Error 2
make: *** [kernel_image] Error 2
make[1]: leaving directory '/usr/src/linux-2.6.33'

ABORT: stage6 returned exit status 2
[/INDENT]I have no clue on what all of that means and what I need to do to fix whatever is wrong.  I would be most grateful for any assistance.

(Also, a small post-script, I retyped all of the terminal remarks above because copy paste is unavailable.  Is there some alternative method to C-P when, like now, I cannot select text in the terminal?  Thnx).
Many thanks in advance.
LTP

Yes, that's a known bug with kernel-package for new kernels.  You will have to upgrade to the latest upstream Debian or Ubuntu version to build the 2.6.33+ kernels.

---

### Post by master_kernel on 2010-04-05
The patched version of KernelCheck is now in the Launchpad Trunk. Use the development method to install it.

---

### Post by ghostkill3r on 2010-04-07
thank you i will try, till it works :)

ciao
ghostkill3r

---

### Post by ghostkill3r on 2010-04-07
it's working and compiling thank you :)
but i still have a little problem, my native resolution is 1920x1080, but i also tryed the other possible resolution of 1280x720 but xconfig is not useable for me when i use your programm.
the font is way toooooooo small, its ok when i try to compile a new kernel without your programm :/

here is a link to the pic i made so you can see what i mean
[http://de.tinypic.com/r/1tvvdi/]("http://de.tinypic.com/r/1tvvdi/5")

i hope this can be fixed :)


ciao
ghostkill3r

---

### Post by master_kernel on 2010-04-13
> **ghostkill3r said:**
> it's working and compiling thank you :)
but i still have a little problem, my native resolution is 1920x1080, but i also tryed the other possible resolution of 1280x720 but xconfig is not useable for me when i use your programm.
the font is way toooooooo small, its ok when i try to compile a new kernel without your programm :/

here is a link to the pic i made so you can see what i mean
[http://de.tinypic.com/r/1tvvdi/]("http://de.tinypic.com/r/1tvvdi/5")

i hope this can be fixed :)


ciao
ghostkill3r
That is really odd - I have no idea why it would be doing that. All KernelCheck does is call make xconfig. No options or anything.

---

### Post by stevenpusser on 2010-04-17
I've pulled the fixes from trunk and made a new deb package on Mepis, which means it should work for recent Ubuntus and Debian too--you need python-central 0.6.8 or higher, and python2.5 or higher.

I've included the source files, too, if anyone wants to rebuild it on Ubuntu.

Link: [https://sites.google.com/site/stevosfilehideaway/Home/more-files/kernelcheck-fixed-16_april_2010.zip](https://sites.google.com/site/stevosfilehideaway/Home/more-files/kernelcheck-fixed-16_april_2010.zip)


Edit:  For the teeny fonts on the qt3 xconfig, perhaps it's a qt3 problem. There's the qt3-qtconfig GUI for configuring font size, among other things;  perhaps that will help.

---

### Post by LostSpoon on 2010-05-29
I'm having trouble getting KernelCheck to run for me on Kubuntu 10.04.

If I try the straight dev method listed on top it all goes fine until I try to run
```
sudo kernelcheck
```

At which point I get back

```
Traceback (most recent call last):
  File "/usr/local/bin/kernelcheck", line 9, in <module>
    import os, gtk, sys, getopt, shutil
ImportError: No module named gtk

```

As far as I can tell, gtk is installed already.

And when I try using the .deb from stevenpusser I get

```
Error: Cannot install 'python-glade2'
```

From Package Installer.

So I try to find python-glade2 which says it requires python-gtk2 which says it needs python2.5-gobject.

Attempts to install meet with 

```
Package python2.5-gobject is a virtual package provided by:
You should explicitly select one to install.
E: Package python2.5-gobject has no installation candidate
```

So I do some digging around and find out that this is already depreciated and I have the newest version already. So I'm not entirely sure where to go from here.


The overarching reason for all of this is my laptop doesn't realize when it's plugged in and others with the same make and model have fixed the problem by compiling their own kernel with certain parts as modules. So if anyone can either help me get KernelCheck working or get my laptop to realize it's plugged in it would be much appreciated.


:KS Thanks

---

### Post by master_kernel on 2010-05-29
> **LostSpoon said:**
> I'm having trouble getting KernelCheck to run for me on Kubuntu 10.04.

If I try the straight dev method listed on top it all goes fine until I try to run
```
sudo kernelcheck
```

At which point I get back

```
Traceback (most recent call last):
  File "/usr/local/bin/kernelcheck", line 9, in <module>
    import os, gtk, sys, getopt, shutil
ImportError: No module named gtk

```

As far as I can tell, gtk is installed already.

And when I try using the .deb from stevenpusser I get

```
Error: Cannot install 'python-glade2'
```

From Package Installer.

So I try to find python-glade2 which says it requires python-gtk2 which says it needs python2.5-gobject.

Attempts to install meet with 

```
Package python2.5-gobject is a virtual package provided by:
You should explicitly select one to install.
E: Package python2.5-gobject has no installation candidate
```

So I do some digging around and find out that this is already depreciated and I have the newest version already. So I'm not entirely sure where to go from here.


The overarching reason for all of this is my laptop doesn't realize when it's plugged in and others with the same make and model have fixed the problem by compiling their own kernel with certain parts as modules. So if anyone can either help me get KernelCheck working or get my laptop to realize it's plugged in it would be much appreciated.


:KS Thanks

Hmmm.... Try installing python-gobject. Also try apt-get build-dep python-gtk2 and then try installing python-gtk2. You definitely need that to run KC.

---

### Post by LostSpoon on 2010-05-29
According to apt python-gobject is already the newest version.

And when I try ```
apt-get build-dep python-gtk2
```

I get

```
Picking 'pygtk' as source package instead of 'python-gtk2'
The following packages have unmet dependencies:
  gnome-icon-theme: Depends: librsvg2-common but it is not going to be installed
  libglade2-dev: Depends: libglade2-0 (= 1:2.6.4-1) but 1:2.6.4-1build1 is to be installed
                 Depends: libxml2-dev but it is not going to be installed
  libgtk2.0-dev: Depends: libgtk2.0-0 (= 2.18.3-1ubuntu2.2) but 2.20.1-0ubuntu1 is to be installed
                 Depends: libglib2.0-dev (>= 2.21.3) but it is not going to be installed
                 Depends: libpango1.0-dev (>= 1.20) but it is not going to be installed
                 Depends: libatk1.0-dev (>= 1.13.0) but it is not going to be installed
                 Depends: libcairo2-dev (>= 1.6.4-6.1) but it is not going to be installedPicking 'pygtk' as source package instead of 'python-gtk2'
The following packages have unmet dependencies:
  gnome-icon-theme: Depends: librsvg2-common but it is not going to be installed
  libglade2-dev: Depends: libglade2-0 (= 1:2.6.4-1) but 1:2.6.4-1build1 is to be installed
                 Depends: libxml2-dev but it is not going to be installed
  libgtk2.0-dev: Depends: libgtk2.0-0 (= 2.18.3-1ubuntu2.2) but 2.20.1-0ubuntu1 is to be installed
                 Depends: libglib2.0-dev (>= 2.21.3) but it is not going to be installed
                 Depends: libpango1.0-dev (>= 1.20) but it is not going to be installed
                 Depends: libatk1.0-dev (>= 1.13.0) but it is not going to be installed
                 Depends: libcairo2-dev (>= 1.6.4-6.1) but it is not going to be installed
                 Depends: libx11-dev (>= 2:1.0.0-6) but it is not going to be installed
                 Depends: libxext-dev (>= 1:1.0.1-2) but it is not going to be installed
                 Depends: libxinerama-dev (>= 1:1.0.1-4.1) but it is not going to be installed
                 Depends: libxi-dev (>= 1:1.0.1-4) but it is not going to be installed
                 Depends: libxrandr-dev (>= 1:1.2.99) but it is not going to be installed
                 Depends: libxcursor-dev but it is not going to be installed
                 Depends: libxfixes-dev (>= 1:3.0.0-3) but it is not going to be installed
                 Depends: libxcomposite-dev (>= 1:0.2.0-3) but it is not going to be installed
                 Depends: libxdamage-dev (>= 1:1.0.1-3) but it is not going to be installed
  python-all-dbg: Depends: python (= 2.6.4-0ubuntu1) but 2.6.5-0ubuntu1 is to be installed
                  Depends: python-all (= 2.6.4-0ubuntu1) but it is not going to be installed
                  Depends: python-dbg (= 2.6.4-0ubuntu1) but 2.6.5-0ubuntu1 is to be installed
  python-all-dev: Depends: python (= 2.6.4-0ubuntu1) but 2.6.5-0ubuntu1 is to be installed
                  Depends: python-all (= 2.6.4-0ubuntu1) but it is not going to be installed
                  Depends: python-dev (= 2.6.4-0ubuntu1) but it is not going to be installed
                  Depends: python2.6-dev but it is not going to be installed
  python-gobject-dev: Depends: python-dev but it is not going to be installed
                      Depends: libglib2.0-dev (>= 2.8.0) but it is not going to be installed
                      Depends: libffi-dev (>= 3.0.5) but it is not going to be installed
  python-numpy-dbg: Depends: python-numpy (= 1:1.3.0-3) but it is not going to be installed
                    Depends: libblas3gf but it is not going to be installed or
                             libblas.so.3gf or
                             libatlas3gf-base but it is not going to be installed
                    Depends: libgfortran3 (>= 4.3) but it is not going to be installed
                    Depends: liblapack3gf but it is not going to be installed or
                             liblapack.so.3gf or
                             libatlas3gf-base but it is not going to be installed
E: Build-dependencies for python-gtk2 could not be satisfied.
                 Depends: libx11-dev (>= 2:1.0.0-6) but it is not going to be installed
                 Depends: libxext-dev (>= 1:1.0.1-2) but it is not going to be installed
                 Depends: libxinerama-dev (>= 1:1.0.1-4.1) but it is not going to be installed
                 Depends: libxi-dev (>= 1:1.0.1-4) but it is not going to be installed
                 Depends: libxrandr-dev (>= 1:1.2.99) but it is not going to be installed
                 Depends: libxcursor-dev but it is not going to be installed
                 Depends: libxfixes-dev (>= 1:3.0.0-3) but it is not going to be installed
                 Depends: libxcomposite-dev (>= 1:0.2.0-3) but it is not going to be installed
                 Depends: libxdamage-dev (>= 1:1.0.1-3) but it is not going to be installed
  python-all-dbg: Depends: python (= 2.6.4-0ubuntu1) but 2.6.5-0ubuntu1 is to be installed
                  Depends: python-all (= 2.6.4-0ubuntu1) but it is not going to be installed
                  Depends: python-dbg (= 2.6.4-0ubuntu1) but 2.6.5-0ubuntu1 is to be installed
  python-all-dev: Depends: python (= 2.6.4-0ubuntu1) but 2.6.5-0ubuntu1 is to be installed
                  Depends: python-all (= 2.6.4-0ubuntu1) but it is not going to be installed
                  Depends: python-dev (= 2.6.4-0ubuntu1) but it is not going to be installed
                  Depends: python2.6-dev but it is not going to be installed
  python-gobject-dev: Depends: python-dev but it is not going to be installed
                      Depends: libglib2.0-dev (>= 2.8.0) but it is not going to be installed
                      Depends: libffi-dev (>= 3.0.5) but it is not going to be installed
  python-numpy-dbg: Depends: python-numpy (= 1:1.3.0-3) but it is not going to be installed
                    Depends: libblas3gf but it is not going to be installed or
                             libblas.so.3gf or
                             libatlas3gf-base but it is not going to be installed
                    Depends: libgfortran3 (>= 4.3) but it is not going to be installed
                    Depends: liblapack3gf but it is not going to be installed or
                             liblapack.so.3gf or
                             libatlas3gf-base but it is not going to be installed
E: Build-dependencies for python-gtk2 could not be satisfied.
```


Digging a bit deeper librsvg2-common also seems to be installed, but an older version is needed apparently:

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  librsvg2-common: Depends: librsvg2-2 (= 2.26.0-1) but 2.26.3-0ubuntu1 is to be installed
```


This is seeming less a problem with KernelCheck and more with some bug in the dependency system.

---

### Post by master_kernel on 2010-05-31
Yeah that's a little ridiculous. Try python-gnome2.

---

### Post by BlitzkreigBop on 2010-05-31
Tried using it on Ubuntu 10.04-UNE (which was upgraded from 9.10)and I received this error message after running the command: 

```
sudo kernelcheck
```

```
Testing your network connection...
Test was successful, you are connected to the internet

Begin data retrival. Please be patient as this may take some time.
Traceback (most recent call last):
  File "/usr/local/bin/kernelcheck-stage2", line 555, in <module>
    ProgressBar()
  File "/usr/local/bin/kernelcheck-stage2", line 336, in __init__
    spurl, kpver, sdate, kver, release = kernel_info1()
  File "/usr/local/bin/kernelcheck-stage2", line 84, in kernel_info1
    htmlFeed = urllib2.urlopen('http://www.kernel.org/kdist/fragments/stable.html')
  File "/usr/lib/python2.6/urllib2.py", line 126, in urlopen
    return _opener.open(url, data, timeout)
  File "/usr/lib/python2.6/urllib2.py", line 397, in open
    response = meth(req, response)
  File "/usr/lib/python2.6/urllib2.py", line 510, in http_response
    'http', request, response, code, msg, hdrs)
  File "/usr/lib/python2.6/urllib2.py", line 435, in error
    return self._call_chain(*args)
  File "/usr/lib/python2.6/urllib2.py", line 369, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.6/urllib2.py", line 518, in http_error_default
    raise HTTPError(req.get_full_url(), code, msg, hdrs, fp)
urllib2.HTTPError: HTTP Error 404: Not Found

```

Any help?

---

### Post by master_kernel on 2010-06-02
> **BlitzkreigBop said:**
> Tried using it on Ubuntu 10.04-UNE (which was upgraded from 9.10)and I received this error message after running the command: 

```
sudo kernelcheck
```

```
Testing your network connection...
Test was successful, you are connected to the internet

Begin data retrival. Please be patient as this may take some time.
Traceback (most recent call last):
  File "/usr/local/bin/kernelcheck-stage2", line 555, in <module>
    ProgressBar()
  File "/usr/local/bin/kernelcheck-stage2", line 336, in __init__
    spurl, kpver, sdate, kver, release = kernel_info1()
  File "/usr/local/bin/kernelcheck-stage2", line 84, in kernel_info1
    htmlFeed = urllib2.urlopen('http://www.kernel.org/kdist/fragments/stable.html')
  File "/usr/lib/python2.6/urllib2.py", line 126, in urlopen
    return _opener.open(url, data, timeout)
  File "/usr/lib/python2.6/urllib2.py", line 397, in open
    response = meth(req, response)
  File "/usr/lib/python2.6/urllib2.py", line 510, in http_response
    'http', request, response, code, msg, hdrs)
  File "/usr/lib/python2.6/urllib2.py", line 435, in error
    return self._call_chain(*args)
  File "/usr/lib/python2.6/urllib2.py", line 369, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.6/urllib2.py", line 518, in http_error_default
    raise HTTPError(req.get_full_url(), code, msg, hdrs, fp)
urllib2.HTTPError: HTTP Error 404: Not Found

```

Any help?
You need to upgrade to the latest version. You can download the .deb or the source code here: [http://sourceforge.net/projects/kcheck/files/kernelcheck/1.2.5/](http://sourceforge.net/projects/kcheck/files/kernelcheck/1.2.5/)

---

### Post by LostSpoon on 2010-06-07
Is there someway to have it compile using the free space in /home instead of /?

It filled up / forcing me to reinstall when I couldn't empty enough space to log in, and after reinstalling I tried running it again and it filled up 4 GB of free space on my / partition before exiting because there is no more room.

So, how do I delete all the files it created, how much room do I need and how can I set the compile directory somewhere else?

Sorry for all these questions

---

### Post by master_kernel on 2010-06-10
> **LostSpoon said:**
> Is there someway to have it compile using the free space in /home instead of /?

It filled up / forcing me to reinstall when I couldn't empty enough space to log in, and after reinstalling I tried running it again and it filled up 4 GB of free space on my / partition before exiting because there is no more room.

So, how do I delete all the files it created, how much room do I need and how can I set the compile directory somewhere else?

Sorry for all these questions
Not yet. I planned this for the next version.

---

### Post by Melcar on 2010-06-10
After I discovered the kernel ppa I stopped using kernelcheck, but I have gone back to it due to the recent ppa packages not playing nice with my laptop for some reason.  Like the new interface, even if it doesn't look as nice under KDE4.  
Only issue I have encountered so far is that it doesn't work with rc kernels.  Been trying to build the latest 2.6.35 but it always exits at stage 3.
I also tried the development version.  When I try to run it the terminal comes back with a "you need python gtk bindings" message.  I do have said bindings already installed though.  OS is Kubuntu 10.04 32bit.

---

### Post by VastOne on 2010-06-11
Can you force KernelCheck to use the latest Kernel Prepatch 2.6.35-rc2?

---

### Post by TheForumTroll on 2010-06-14
Really nice program you've made here. I just found it and it's doing its magic right now. Can't wait to see if it works out in the first try with all the tweaks I made to the config. Thank you :)

---

### Post by galv on 2010-06-18
Thanks for your hard work :) I have two questions:
1) Kernel.org shows that 2.6.34 is a stable version of kernel, why don't I get to compile that one? just 2.6.33.5

2) Is there tips for a Nvidia Ion based system, with Atom 330. (I have a Giada Cube N3).

):P

---

### Post by afrodeity on 2010-07-24
I've tried installing the candela kerneltwice. First time with defaults, second time with the deprecated IDE/SATA support checked on. Both times I run into a kernel panic and recovery mode suggests problem with the root init

If it try to update-initramfs I get a modules not found error.
```

sudo update-initramfs -c -k linux-image-2.6.34.1-candela 
update-initramfs: Generating /boot/initrd.img-linux-image-2.6.34.1-candela
Cannot find /lib/modules/linux-image-2.6.34.1-candela
update-initramfs: failed for /boot/initrd.img-linux-image-2.6.34.1-candela

```

This is the contents of /boot showing a missing initrd.img for candela kernel

```
 ls
abi-2.6.31-19-generic             memtest86+.bin
abi-2.6.31-20-generic             System.map-2.6.31-19-generic
abi-2.6.32-22-generic             System.map-2.6.31-20-generic
abi-2.6.32-23-generic             System.map-2.6.32-22-generic
abi-2.6.34-020634-generic         System.map-2.6.32-23-generic
config-2.6.31-19-generic          System.map-2.6.34-020634-generic
config-2.6.31-20-generic          System.map-2.6.34.1-candela
config-2.6.32-22-generic          vmcoreinfo-2.6.31-19-generic
config-2.6.32-23-generic          vmcoreinfo-2.6.31-20-generic
config-2.6.34-020634-generic      vmcoreinfo-2.6.32-22-generic
config-2.6.34.1-candela           vmcoreinfo-2.6.32-23-generic
grub                              vmlinuz-2.6.31-19-generic
initrd.img-2.6.31-19-generic      vmlinuz-2.6.31-20-generic
initrd.img-2.6.31-20-generic      vmlinuz-2.6.32-22-generic
initrd.img-2.6.32-22-generic      vmlinuz-2.6.32-23-generic
initrd.img-2.6.32-23-generic      vmlinuz-2.6.34-020634-generic
initrd.img-2.6.34-020634-generic  vmlinuz-2.6.34.1-candela

```

---

### Post by afrodeity on 2010-07-24
Putting this out there helped me solve this I hope.

```

Cannot find /lib/modules/linux-image-2.6.34.1-candela

```
should have been a clue

I cd'd into the /lib/modules/ and found my problem "**linux-image**" is not part of the initramfs way of doing things.

Correct syntax should be:

```

 sudo update-initramfs -c -k 2.6.34.1-candela

```

---

### Post by afrodeity on 2010-07-24
well, that only solved the "update-initramfs" modules not found issue. It still wants me to append a root, but grub is supposed to pass a "root=UUID=xxx" parameter. Anybody know what is going on and how to fix?
[B]
Kernel panic not solved.[/B]

UPDATE: I'm going to guess and say I have to run update-grub as well? See you next boot.

SOLVED --- update-grub did the trick, guess the kernelcheck script is slightly out of date.

---

### Post by zanadou on 2010-08-08
> **galv said:**
> Thanks for your hard work :) I have two questions:
1) Kernel.org shows that 2.6.34 is a stable version of kernel, why don't I get to compile that one? just 2.6.33.5

I have a similar error, my copy of KernelCheck Lumen right now can't find the latest stable 2.6.35, it just tells me that the latest kernel patch is 2.6.34 with the latest prepatch being 2.6.34.2 . 

How can I "force" KernelCheck to "find" v2.6.35? Is there a problem with the kernel.org source URLs again?

---

### Post by kingsrook14 on 2010-08-10
> **zanadou said:**
> I have a similar error, my copy of KernelCheck Lumen right now can't find the latest stable 2.6.35, it just tells me that the latest kernel patch is 2.6.34 with the latest prepatch being 2.6.34.2 . 

How can I "force" KernelCheck to "find" v2.6.35? Is there a problem with the kernel.org source URLs again?

Hello,
Download 2.6.35 kernel and save to /usr/src
           Choose Custom ==> Old stable patch as 2.6.35 in KernelCheck

Compiled 2.6.35 using KernelCheck Old Stable patch method with modified config for my laptop
Working very well so far (1 hr old)
    Trying to fix === Wireless issues

EDIT: BTW my Core i7 4 GB RAM HP dv6 laptop compiled and installed kernel in 20 mins flat with -j16 flag
            No Turbo Boost working

---

### Post by HeadHunter00 on 2010-08-21
Also, kernelcheck doesn't create any initrd images. So, make sure to create one before reboot using these steps: 1. cd /boot
                                     2. sudo mkinitramfs -o initrd.img-*kernel.name kernel.name*

---

### Post by HeadHunter00 on 2010-08-21
> **kingsrook14 said:**
> 
EDIT: BTW my Core i7 4 GB RAM HP dv6 laptop compiled and installed kernel in 20 mins flat with -j16 flag
            No Turbo Boost working
arghh, I am so jealous of you.

---

### Post by macaddict01 on 2010-11-04
Appears that KC is broken now that 2.6.36 is stable. Anyone found a workaround?

---

### Post by jdeeth on 2010-11-16
Been trying to roll my own 2.6.35.8 on a new Asus laptop for a few days and I'm getting hung up on nVidia drivers. I've tried both the Yes and No options to reinstall the nVidia drivers during the kernel build and I fail each time.

The most common outcome is I get to a command line login prompt and after I log in, startx fails. The other outcome is, after the Asus splash screen, I simply have a blank screen.

lspci -v under 2.6.35.22 gives me these specs:

01:00.0 VGA compatible controller: nVidia Corporation Device 0df0 (rev a1) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Device 1522
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d2000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at d0000000 (64-bit, prefetchable) [size=32M]
	I/O ports at d000 [size=128]
	[virtual] Expansion ROM at d3000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nouveau, nvidiafb

Been using KernelCheck with no major issues on my old laptop for a year plus. What am I doing wrong here?:confused:

---

### Post by TheNikkoMan on 2011-03-04
I know the above post is very old, but I had the same problem but managed to solve it. So, for future reference;
Most likely you have compiled with the nvidiafb module enabled, which had the same impact on me when I did the same. Compile again, WITHOUT Nvidia Framebuffer (or something), and you'll be good to go.
Just pumping in my own question here; The instructions on the first page showing how to change the name of the produced kernel does no longer apply. I've checked all three of my python-directories in usrlib, but no-one of them contained the correct file. Is there an equalient that still applies?

---

### Post by afrodeity on 2011-04-22
Just did a kernelcheck compile of latest kernel 2.6.38-candela. Didn't see a clean up tick box, and now wanting to cleanup the excess space used, anybody know where the working directory for candela would be?

UPDATE: forgot about this, its the linux-2.6.38 directory in /usr/src

---

### Post by static chaser on 2011-05-12
I think I borked up my latest kernel. I used KC to download and compile 2.6.38.6 candela and I get an error that says "The package linux-image-2.6-38.6-candela needs to be reinstalled, but I can't find an archive for it."  When I try Synaptic or apt-get or KC to reinstall it gives me this same error. I am on 10.04 AMD64 & have tried several times to reboot. I have used KC once before to fix a freezing problem and the program worked very well.  Any help would be appreciated.

---

### Post by mockingbird on 2011-05-24
Does this work with Kubuntu?  When I launch it fromt he menu, it keeps asking me for the password which it claims is incorrect, but if I launch it from sudo or kdesudo it works but then crashes and exits when I press "Apply".

---

### Post by Z06Gal on 2011-06-28
I am giving kc a whirl right now and wanted to ask those of you who have done this did you make alot of changes the first time you used it?  I didn't make any changes than what came up on the config because I wasn't sure what to "tweak."  Lol


Robin


Edit to add everything went great.  This will make upgrading kernels so much better.  Thanks to the developer of this program :)

---

### Post by master_kernel on 2011-07-24
KernelCheck 1.5.0 due out late this July or early August.

MK

---

### Post by wormwang on 2011-07-31
When KernelCheck support v3.0 Linux kernel?

---

### Post by zanadou on 2011-12-27
Has KernelCheck development been abandoned?? It's starting to look that way...

---

### Post by afrodeity on 2011-12-29
Would be a shame if it was, I rely on Kernelcheck, especially when the Ubuntu kernels fail.

---

### Post by deepspring on 2011-12-31
Just a quick note from me...

I am not a member of the KernelCheck development team, and haven't been for nearly 2 years. Unfortunately Master_Kernel no longer checks his emails and hasn't bothered to update his sourceforge and launchpad sites to reflect this fact. There aren't any disagreements or anything between Master_Kernel and myself, it's just that life has pulled us in different directions.

I have not heard anything from Master_Kernel in years, so I am unaware of what he is doing with his life now.

I am now a Graphic Designer and have moved away from using Linux as my primary Operating System of choice in favour of Apple Mac OSX (which is the industry standard).

---

