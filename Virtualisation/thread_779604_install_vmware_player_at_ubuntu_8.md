---
title: "install vmware player at ubuntu 8"
date: 2008-05-02
forum: Virtualisation
---

### Post by joaomello on 2008-05-02
Hi guys?!
I'm having problem to install the VMware player at the Ubuntu 8 :(
The error:
```
mello@mello-laptop:~$ sudo /usr/bin/vmware-config.pl
Making sure services for VMware Player are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the theme icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Player is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-16-generic/build/include] 

Extracting the sources of the vmmon module.

tar: /usr/lib/vmware/modules/source/vmmon.tar: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
Unable to untar the "/usr/lib/vmware/modules/source/vmmon.tar" file in the 
"/tmp/vmware-config5" directory.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.


```

Is possible to install VMware at Ubuntu 8? How? xD

Thanks,
Mello.

---

### Post by NewbieNik on 2008-05-06
Welcome to the wonderful world of cutting edge distros. unfortunately VMWare is not able to run on the Ubuntu kernels for Hardy.
There are "fixes" around, but I have tried three of these with no joy on my 64bit system. VirtualBox is a good alternative and is in the repositories, but I have a problem with "bridging" the netowrk adaptors.
I guess we'll just have to be patient and suffer this drawback of using the latest software.

---

### Post by MadHawk1 on 2008-09-06
How to install vmware player in Ubuntu 7.10 or 8.04 tutorial:
[http://www.linuxquestions.org/questions/linux-desktop-74/how-to-install-vmware-player-in-ubuntu-7.10-or-8.04-tutorial.-649955/](http://www.linuxquestions.org/questions/linux-desktop-74/how-to-install-vmware-player-in-ubuntu-7.10-or-8.04-tutorial.-649955/)




> 
Some of my friends have asked me many times how I install Vmware player for Ubuntu 7.10 or 8.04. So here's my basic tutorial. I hope this makes sense everyone. This tutorial will explain how to install VMware Player on Ubuntu Gutsy or Hardy Heron.

Download the most current tar.gz package (VMware-player-2.0.4-93057.i386.tar.gz) from the VMware website.
[http://www.vmware.com/download/player/download.html](http://www.vmware.com/download/player/download.html)

Before you do anything, there are some things you have to look up and download in your Ubuntu system.
First you have to see what linux kernel you are using on your Ubuntu Linux PC.
Bring up your bash shell from the "applications menu bar". Click on "terminal" which is under "accessories". Type in the following command at the bash command line:

**uname -r**

This command will return the following linux kernel results:

**2.6.22-14-generic** (Gutsy Gibbon)
or
**2.6.24-19-generic** (Hardy Heron)


I have 2.6.24-19-generic, so I have to install the linux headers files for my kernel version:
(if your using Ubuntu 7.10 Gutsy install headers for 2.6.22-14-generic kernel)

Enter the following command:

**sudo apt-get install linux-headers-2.6.24-19-generic**

You also need to make sure you have "build-essential" package installed in your system before you install vmware-player.

Enter the following command:

**sudo apt-get install build-essential**

Now download VMware Player tar.gz package from the VMware website. At this time the most recent package is: VMware-player-2.0.4-93057.i386.tar.gz.

Once the download is complete move the Vmware tar package to your home folder in "Gnome" or move it to your home directory in the command line. Now untar the .tar.gz file using the following command:

**tar -xzvf VMware-player-2.0.4-93057.i386.tar.gz**

The tar.gz package is now extracted.

Now you need to change into the vmware directory with the following command:

**cd vmware-player-distrib**

Now it's time for the fun stuff: Installing with the following command:

**sudo ./vmware-install.pl**

During the installation you must answer some basic questions. For a standard installation enter the following:

In which directory do you want to install the binary files?
[/usr/bin]
What is the directory that contains the init directories (rc0.d/ to rc6.d/)?
[/etc]
What is the directory that contains the init scripts?
[/etc/init.d]
In which directory do you want to install the daemon files?
[/usr/sbin]
In which directory do you want to install the library files?
[/usr/lib/vmware]
The path &#8220;/usr/lib/vmware&#8221; does not exist currently. This program is going to
create it, including needed parent directories. Is this what you want?
[yes]
In which directory do you want to install the documentation files?
[/usr/share/doc/vmware]
The path &#8220;/usr/share/doc/vmware&#8221; does not exist currently. This program is
going to create it, including needed parent directories. Is this what you want?
[yes]
Before running VMware Player for the first time, you need to configure it by
invoking the following command: &#8220;/usr/bin/vmware-config.pl&#8221;. Do you want this
program to invoke the command for you now?
[yes]
In which directory do you want to install the theme icons?
[/usr/share/icons]
What directory contains your desktop menu entry files? These files have a
.desktop file extension.
[/usr/share/applications]
In which directory do you want to install the application&#8217;s icon?
[/usr/share/pixmaps]
None of the pre-built vmmon modules for VMware Player is suitable for your
running kernel. Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)?
[yes]
What is the location of the directory of C header files that match your running
kernel?
[/lib/modules/2.6.22-14-generic/build/include]
None of the pre-built vmblock modules for VMware Player is suitable for your
running kernel. Do you want this program to try to build the vmblock module
for your system (you need to have a C compiler installed on your system)?
[yes]
Do you want networking for your virtual machines? (yes/no/help)
[yes]
Do you want to be able to use NAT networking in your virtual machines? (yes/no)
[yes]
Do you want this program to probe for an unused private subnet? (yes/no/help)
[yes]
Do you wish to configure another NAT network? (yes/no)
[no]
Do you want to be able to use host-only networking in your virtual machines?
[yes]
Do you want this program to probe for an unused private subnet? (yes/no/help)
[yes]
Do you wish to configure another host-only network? (yes/no)
[no]

None of the pre-built vmnet modules for VMware Player is suitable for your
running kernel. Do you want this program to try to build the vmnet module for
your system (you need to have a C compiler installed on your system)?
[yes]


**The installation process is now finished** and you can start VMware Player from your Applications Menu under "system tools". (Gnome)

If for some reason you don't like VMware-player and you want to try something else use the following command in the command line to remove Vmware player:

**sudo /usr/bin/vmware-uninstall.pl**

Have fun!
P.S. if your are looking for vmware virtual images to play around with I suggest the following website:
[http://www.vmware.com/appliances/directory/cat/45](http://www.vmware.com/appliances/directory/cat/45)

If you are interested in making your very own virtual OS images try this website:
[http://www.easyvmx.com/](http://www.easyvmx.com/) (use the Easy-VMX ver 2.0)

Once again have fun!


---

