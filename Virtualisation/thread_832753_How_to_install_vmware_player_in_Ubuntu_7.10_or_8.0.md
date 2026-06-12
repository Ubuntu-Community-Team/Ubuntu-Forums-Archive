---
title: "How to install vmware player in Ubuntu 7.10 or 8.04 tutorial."
date: 2008-06-18
forum: Virtualisation
---

### Post by linuxmaveric on 2008-06-18
Some of my friends have asked me many times how I install Vmware player for Ubuntu 7.10 or 8.04. So here's my basic tutorial. I hope this makes sense everyone. This tutorial will explain how to install VMware Player on Ubuntu Gutsy or Hardy Heron.

Download the most current tar.gz package                            (VMware-player-2.0.4-93057.i386.tar.gz) from the VMware website. 
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

untar the .tar.gz file using the following command:
[B]
tar -xzvf VMware-player-2.0.4-93057.i386.tar.gz[/B]

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

[B]
The installation process is now finished[/B] and you can start VMware Player from your Applications Menu under "system tools". (Gnome)

If for some reason you don't like VMware-player and you want to try something else use the following command in the command line to remove Vmware player:

**sudo /usr/bin/vmware-uninstall.pl**

Have fun!
P.S. if your are looking for vmware virtual images to play around with I suggest the following website:
[http://www.vmware.com/appliances/directory/cat/45](http://www.vmware.com/appliances/directory/cat/45)

If you are interested in making your very own virtual OS images try this website:
[http://www.easyvmx.com/](http://www.easyvmx.com/)  (use the Easy-VMX ver 2.0)

Once again have fun! :guitar:

---

### Post by dellboy on 2008-08-17
Thank you linuxmaveric

**and for anyone reading this **

you need to put the VMware-player-2.0.4-93057.i386.tar.gz or what ever version you have in your home folder i found it easyer to just extract the file my self by right clicking and the use the terminal to instill 

thank you again linuxmaveric i could have not of done this with out you :)

---

### Post by flouran on 2008-08-20
Hi Guys,
I wanted to install VMWare Player on Ubuntu 8.04 so that I could run the NST (Network Security Toolkit) v 1.8.0 on VMWare. I downloaded the .tar.gz file from [http://www.vmware.com/products/player/]("http://www.vmware.com/products/player/")
,and when I untarred it and tried to run, vmware-install.pl, and followed the instructions, when I was asked where the C headers for the current Linux kernel version I was running (2.6.24-19-generic), it said it couldn't find the directory, /usr/src/linux/include.

Does anyone know where the C headers for the current kernel version I am running are located in Ubuntu?
Also, does anyone know any good guides where I could install VMWare Player on Ubuntu 8.04 LTS? I've searched Google for guides, and they don't work (I even tried: [http://ubuntuforums.org/showthread.php?t=832753]("http://ubuntuforums.org/showthread.php?t=832753"), but to no avail)! And, if someone knows how to do this from experience I am happy to hear from them as well. Please help!!

---

### Post by PabloCardoso on 2008-08-28
@flouran:
This is a common error when you run the install script without having the kernel headers installed. Did you remember to install the headers?

```

sudo apt-get install linux-headers-2.6.24-19 linux-headers-2.6.24-19-generic

```

HTH

---

### Post by wgarider on 2008-09-01
Thanks linuxmaveric - install went great!

---

