---
title: "VirtualBox on Hardy Heron not working"
date: 2007-12-31
forum: Virtualisation
---

### Post by MageMasher on 2007-12-31
Ok I'm trying to get virtualbox to work in hardy. The kernel module in the repos is out of date with the actual kernel and doesn't work showing:
 * Starting VirtualBox kernel module vboxdrv                                                                                                                                FATAL: Module vboxdrv not found.

 * Modprobe vboxdrv failed. Please use 'dmesg' to find out why.

dmesg doesn't show anything regarding the module :confused:
Trying to compile from source following the instructions from [https://help.ubuntu.com/community/VirtualBox]("https://help.ubuntu.com/community/VirtualBox") doesn't work either. I just get to about 34 percent till I get:
Kernel Configuration is invalid.
include/linux/autoconf.h or include/config/auto.con
Run 'make oldconfig && make prepare' on kernel src.

So I try doing what it says "cd /usr/src/linux/ && sudo make oldconfig && sudo make prepare" which just returns loads of errors. I ignore them and try compiling the virtualbox modules again anyway, but this time I get a message about the kernel headers not existing anymore. I ran "sudo aptitude reinstall linux-headers-2.6.22-14-generic" which brings them back, but it stills fails at 34% with the same message.

---

### Post by |2eason on 2007-12-31
You need the full OSE source code here: [http://www.virtualbox.org/download/1.5.4/VirtualBox-1.5.4_OSE.tar.bz2](http://www.virtualbox.org/download/1.5.4/VirtualBox-1.5.4_OSE.tar.bz2)

Then follow the instructions here: [http://www.virtualbox.org/wiki/Linux%20build%20instructions](http://www.virtualbox.org/wiki/Linux%20build%20instructions)

Edit: Just to show that it will build;

---

### Post by |2eason on 2008-01-01
Ok, so, Virtualbox will only run from sudo after a fresh build, so there's a afew more steps needed.
First, open a shell and;
```
sudo chmod 777 /dev/vboxdrv
```
then, since the 'Users and Groups' GUI in Hardy seems to be borked (ie it doesn't go sudo when you hit 'unlock') use bash to;
```

sudo addgroup vboxusers
sudo adduser [yourusernamehere] vboxusers

```
Then, to make a menu launcher, make a shell script in ~/scripts, like;
```

#!/bin/bash
clear
LD_LIBRARY_PATH=/home/[yourusernamehere]/VirtualBox-1.5.4_OSE/out/linux.x86/release/bin/
export LD_LIBRARY_PATH
/home/[yourusernamehere]/VirtualBox-1.5.4_OSE/out/linux.x86/release/bin/VirtualBox
```
Then just put the script in a custom app launcher.

---

### Post by UbuWu on 2008-01-02
The version that is in the hardy repositories is incompatible with the 2.6.24 kernel that is used for Hardy. Virtualbox 1.5.4 needs to be synced from debian to fix this.

[https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/156210](https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/156210)

---

### Post by BrianLucas on 2008-03-25
When running hardy, I was able to install and run VirtualBox from the company's repository instead of using the Ubuntu packages.  Add this repository to /etc/apt/sources.list:

[FONT="Courier New"]deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) gutsy non-free [/FONT]

then [FONT="Courier New"] apt-get install virtualbox-ose[/FONT]

---

### Post by caver1 on 2008-03-26
Don't use the OSE version of virtual box if you want usb support.
go to Virtualbox's  web site and download their free (non ose) version of Virtualbox and load it. Then go to Users and Groups. Then in manage groups enable what ever user you want to be able to use it.
works fine here for me using Heron 64 bit 3.04 2.4.26.12-generic kernel.
caver1  :)

---

### Post by bajun on 2008-03-26
> Don't use the OSE version of virtual box if you want usb support.
go to Virtualbox's web site and download their free (non ose) version of Virtualbox and load it. Then go to Users and Groups. Then in manage groups enable what ever user you want to be able to use it.
works fine here for me using Heron

Confirmed. Everything is OK.

---

### Post by J@n on 2008-03-30
> **caver1 said:**
> Don't use the OSE version of virtual box if you want usb support.
go to Virtualbox's  web site and download their free (non ose) version of Virtualbox and load it. Then go to Users and Groups. Then in manage groups enable what ever user you want to be able to use it.
works fine here for me using Heron 64 bit 3.04 2.4.26.12-generic kernel.
caver1  :)

Is it possible for you to supply a link to the download location? I don't seem to be able to find the non-OSE version of Virtual Box. I would like to follow the installation guidelines but it's kinda difficult if one can't find the download:(

Greetz,

J@n

---

### Post by bajun on 2008-03-30
> **J@n said:**
> Is it possible for you to supply a link to the download location?

Add this to your /etc/apt/sources.list:

```
deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) gutsy non-free
```

There is only one packet - non OSE version of VirtualBox

I have installed gutsy version on hardy, everything is ok

---

### Post by J@n on 2008-03-30
OK, so I will try the non-free version. I would be happy to have my virtual machines back, no matter if I have USB support.

Thanks.

Greetz,

J@n

---

### Post by J@n on 2008-03-30
I was too fast in my reply.

This is what I planted in my /etc/apt/sources.list:
```

deb http://www.virtualbox.org/debian gutsy non-free

```

This is the result:
```

root@ubuntu:~# apt-get install virtualbox-ose
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  virtualbox-ose-source
Recommended packages:
  virtualbox-ose-modules
The following packages will be REMOVED:
  virtualbox
The following NEW packages will be installed:
  virtualbox-ose
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 6361kB of archives.
After this operation, 18.0MB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://nl.archive.ubuntu.com hardy/universe virtualbox-ose 1.5.6-dfsg-2ubuntu2 [6361kB]
Fetched 6361kB in 19s (323kB/s)
Preconfiguring packages ...
(Reading database ... 167220 files and directories currently installed.)
Removing virtualbox ...
 * Stopping VirtualBox kernel module vboxdrv                             [ OK ]
Shutting down VirtualBox host networking...done.
Selecting previously deselected package virtualbox-ose.
(Reading database ... 166556 files and directories currently installed.)
Unpacking virtualbox-ose (from .../virtualbox-ose_1.5.6-dfsg-2ubuntu2_i386.deb) ...
Setting up virtualbox-ose (1.5.6-dfsg-2ubuntu2) ...

Configuration file `/etc/vbox/interfaces'
 ==> File on system created by you or by a script.
 ==> File also in package provided by package maintainer.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : background this process to examine the situation
 The default action is to keep your current version.
*** interfaces (Y/I/N/O/D/Z) [default=N] ? d [COLOR="Blue"](I wanted to see the differences)[/COLOR]

Configuration file `/etc/vbox/interfaces'
 ==> File on system created by you or by a script.
 ==> File also in package provided by package maintainer.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : background this process to examine the situation
 The default action is to keep your current version.
*** interfaces (Y/I/N/O/D/Z) [default=N] ? n
Installing new version of config file /etc/init.d/vboxdrv ...
Starting VirtualBox host networking ...done.
Warning - failed to add interface vbox0 to the bridge br0
 * Starting VirtualBox kernel module vboxdrv
[COLOR="Red"] * No suitable module for running kernel found.[/COLOR]

```

:???:I am kinda at a loss here :( Any help would be much appreciated[-o<

---

### Post by bajun on 2008-03-30
> **J@n said:**
> This is what happens when I try to update my sources

Uninstall all virtualbox packages, then install virtualbox (not ose) again.

> **J@n said:**
> no matter if I have USB support.

Have you USB Patch applied?

If not, you need to make this, was necessary on Gutsy to make USB work. I've checked, this is also necessary on Hardy.

1. add group "usbusers", add your user to this group

2. edit the script `/etc/init.d/mountdevsubfs.sh and delete # symbol before the four lines around line 40 (Magic to make /proc/bus/usb work).

 Then execute

```
/etc/init.d/mountdevsubfs.sh start
```

3. add this to your /etc/fstab
```
# virtualbox usb patch
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
```

4. Check "USB devices" section of your
/etc/udev/rules.d/40-permissions.rules
file. This section should look as here
```
# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
SUBSYSTEM=="usb_device",		MODE="0664"
```


Restart, enjoy

---

### Post by J@n on 2008-03-30
OK, followed your steps and after reboot and tweaking a little bit I got it working (as it seems for now):)

Thanks for your help. Where would I be without the help of this invaluable forum.

Thanx a billion:biggrin:

---

### Post by caver1 on 2008-03-30
> **J@n said:**
> Is it possible for you to supply a link to the download location? I don't seem to be able to find the non-OSE version of Virtual Box. I would like to follow the installation guidelines but it's kinda difficult if one can't find the download:(

Greetz,

J@n

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.5.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.5.6-G-F@CDS-CDS_SMI)
I think you can figure it out from there.   :popcorn:
caver1

---

### Post by bajun on 2008-04-03
There is this vboxdrv problem again after kernel update from 2.6.24-12 to 2.6.24-14

---

### Post by bajun on 2008-04-03
> **bajun said:**
> There is this vboxdrv problem again after kernel update from 2.6.24-12 to 2.6.24-14

oops, I was stupid, linux-headers was not installed. After install is everything works.

---

### Post by JMann on 2008-04-04
> **bajun said:**
> Add this to your /etc/apt/sources.list:

```
deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) gutsy non-free
```



Where do you add this code?  Terminal?

I tried that but got: 
[code]bash: deb: command not found[code]

---

### Post by J@n on 2008-04-05
Hi JMann,

Try this in Ubuntu:

Go to System > Administration > Software Sources. In the dialogue that appears you can add the line
[COLOR="Red"]deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) gutsy non-free[/COLOR]
That should do the trick

HTH

Greetz,

J@n

---

### Post by jacrider on 2008-04-05
Ok, I just did a system update to kernel 2.6.24-15.

Normally when we get a kernel upgrade, I go install a new virtualbox-modules for the kernel.

This time, I can't seem to find a new modules version for this kernel.

Any suggestions?

EDIT:  Kernel 2.6.24-15 NOT 17.

---

### Post by karyonix on 2008-04-05
Just wait, new module will be available in a few days. 
For today, select your old kernel in GRUB menu and use old virtualbox module.

---

### Post by jacrider on 2008-04-05
Thanks.  I have already done that, just wondering if the new update has been released.

---

### Post by thecure on 2008-04-05
> **bajun said:**
> Add this to your /etc/apt/sources.list:

```
deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) gutsy non-free
```

There is only one packet - non OSE version of VirtualBox

I have installed gutsy version on hardy, everything is ok

Thanks guys. I originally had virtualbox working when I had upgraded from Gutsy to Hardy but after awhile did a clean install of Hardy and never could get the ose version to work. Changing to VirtualBox version fixed the issue.

---

### Post by Kiri on 2008-04-06
> **jacrider said:**
> Ok, I just did a system update to kernel 2.6.24-15.

Normally when we get a kernel upgrade, I go install a new virtualbox-modules for the kernel.

This time, I can't seem to find a new modules version for this kernel.

Any suggestions?

EDIT:  Kernel 2.6.24-15 NOT 17.

How can I update the modules if I am using the non ose version?
In the repository there is only the ose-modules.
I have already added the non ose sources to synaptic though

---

### Post by BetterSense on 2008-04-06
I'm still on kernal -12, because last time I updated it sploded my machine.

 Anyway, I can't seem to install virtualbox. I installed virtualbox-ose from the hardy reps, but then when I tried to install the modules, the only modules I could find were for kernals -15. So after reading this thread, II aptitude removed virtualbox-ose, I added the gutsu-nonfree line to my sources.list but when I go to install, it says it can't lock the download directory, and selects virtualbox-ose instead of virtualbox.  My internet is working fine, I'm confused. I just used apt to install wine.

```


chaz@brutus:/etc/apt$ gksudo kwrite  sources.list
Reusing existing ksycoca
chaz@brutus:/etc/apt$ sudo apt-get install virtualbox
Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting virtualbox-ose instead of virtualbox
The following extra packages will be installed:
  libxalan110 libxerces27 virtualbox-ose
Suggested packages:
  xalan bridge-utils virtualbox-ose-source
Recommended packages:
  virtualbox-ose-modules
The following NEW packages will be installed:
  libxalan110 libxerces27 virtualbox-ose
0 upgraded, 3 newly installed, 0 to remove and 365 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
chaz@brutus:/etc/apt$                             
```

---

### Post by bajun on 2008-04-06
> **jacrider said:**
> Ok, I just did a system update to kernel 2.6.24-15.
...This time, I can't seem to find a new modules version for this kernel.
Any suggestions?

> **Kiri said:**
> How can I update the modules if I am using the non ose version?
...I have already added the non ose sources to synaptic though

I had your problems with new kernels 2.6.24 and NON-OSE virtualbox version. My solution was roughly but very easy.

First, I've installed "linux-headers" package. This was "linux-headers-rt" package with dependencies: "linux-headers-2.6.24-15-rt" and "linux-headers-2.6.24-15", in accordance with my realtime kernel.
If you have generic kernel, you probably need "linux-headers-generic" package with dependencies: "linux-headers-2.6.24-15-generic" and "linux-headers-2.6.24-15"

Second, I have reinstalled virtualbox again. Everything works...

Edit: Dont need to reinstall virtualbox, simply - ```
/etc/init.d/vboxdrv setup
```

---

### Post by jacrider on 2008-04-07
For those who have upgraded the kernel to -15, the OSE module for the kernel is now in the repos.  Good news.

---

### Post by pilsna on 2008-04-12
I had the same problem after upgrading gutsy to hardy. I'm using kernel 2.6.24-15-generic and the non-free virtualbox.
I managed to get vbox up and running after doing this:

1. applying two patches to the vbox driver source from this post:
[http://vbox.innotek.de/pipermail/vbox-users/2007-October/002372.html]("http://vbox.innotek.de/pipermail/vbox-users/2007-October/002372.html")

2. recompiling the vbox kernel module by running 
```
/etc/init.d/vboxdrv setup
```

After that, I'm up and running again.

---

### Post by drsox1899 on 2008-04-13
> **bajun said:**
> Uninstall all virtualbox packages, then install virtualbox (not ose) again.



Have you USB Patch applied?

If not, you need to make this, was necessary on Gutsy to make USB work. I've checked, this is also necessary on Hardy.

1. add group "usbusers", add your user to this group

2. edit the script `/etc/init.d/mountdevsubfs.sh and delete # symbol before the four lines around line 40 (Magic to make /proc/bus/usb work).

 Then execute

```
/etc/init.d/mountdevsubfs.sh start
```

3. add this to your /etc/fstab
```
# virtualbox usb patch
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
```

4. Check "USB devices" section of your
/etc/udev/rules.d/40-permissions.rules
file. This section should look as here
```
# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
SUBSYSTEM=="usb_device",		MODE="0664"
```


Restart, enjoy

Mucho thanks for this.  I had most of the steps from other posts, but not the first and the last.

Now my USB stick works in WinXp - but not yet my iPod.

---

### Post by famous3warriors on 2008-04-13
I apologize for this but how do I get into the script so I can edit line 40 so i can get the usb working.

---

### Post by famous3warriors on 2008-04-13
never mind got it sorry about that.

---

### Post by himikeb on 2008-05-05
For me, the biggest trick was making sure the version of the linux-headers matched the kernel.  After my upgrade to Hardy, my headers were 2.6.24-16, but the kernel was actually 2.6.24-17.
Once I found and installed the correct headers, the command "sudo /etc/init.d/vboxdrv setup"   worked as it was supposed to work.
I now have VirtualBox 1.6 running on Hardy - way cool.

To Sun: Nice Splash in the BIOS :P

---

### Post by hardskinone on 2008-05-30
After installing the correct linux-header for current running kernel:

```
$ sudo apt-get install linux-headers-`uname -r`
```

I was unable to run "sudo /etc/init.d/vboxdrv setup" successifully. To solve:

```

$ /usr/src/vboxdrv-1.6.0 [This folder is installed by vbox1.6 deb package]
$ sudo make && sudo make install

```

You have to compile and install the module after every kernel package update.

Hope helps.

---

### Post by theZoid on 2008-05-31
Yes, VB will even give you the CLI command to do that when you try and launch the program without doing so.

---

### Post by ACGilbert on 2008-06-05
Thank you hardskinone & thezoid,
An intermediate noob such as myself needed one more step.
REBOOT
DUH!
Then I had the -17 kernel working. Was on the -16.
Thanks again.
AC

---

### Post by jputman on 2008-06-13
To get Virtualbox working on Hardy today I started with:
_sudo apt-get install virtualbox_
but it complained about not having the kernel module. Then I installed: 
_sudo apt-get install virtualbox-ose-modules-generic_
After this VirtualBox complained I wasn't a member of the vboxusers group so I added myself:
_sudo adduser user vboxusers_
and rebooted. 

Now it works.  I hope this helps anyone who's looking here for suggestions.

[Edit Jun 18th 2008]
And it's broken again.... Darn, Probably by the latest updates. 

WARNING: The character device /dev/vboxdrv does not exist.
Please install the virtualbox-ose-modules package for your kernel, which is likely virtualbox-ose-modules-generic.You will not be able to start VMs until this problem is fixed.

I tried fixing the module with the directions here: [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox) 
but I think the module compilation is failing.

[Edit Jun 21th 2008]
It's working again.  It looks like the kernel module was updated and a recent update fixed it.  I guess the moral of the story is be careful around the updates, but it works :-)

---

### Post by ktakasmanov on 2008-07-15
if you use SCIM, this might be a problem
I have installed the scim-bridge-client-qt package and it worked

Hope this will work for you

---

### Post by Proodigy on 2008-07-16
I just tried it and it worked!!! :KS

---

### Post by Richard_2007 on 2008-07-29
I get the following error when I try to start virtual box on hardy.


Could not load the settings file '/home/xxxxxxxx/.VirtualBox/VirtualBox.xml' (VERR_OPEN_FAILED).
FATAL ERROR: Attribute 'version' has a value, '1.3-linux', that does not match its #FIXED value, '1.2-linux'
Location: '/home/xxxxxxxx/.VirtualBox/VirtualBox.xml', line 5, column 83.


Result Code: 
0x80004005
Component: 
VirtualBox
Interface: 
IVirtualBox {76b25f3c-15d4-4785-a9d3-adc6a462beec}

Anyone seen this and have a fix for it? Thanks Richard:guitar:

---

