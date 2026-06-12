---
title: "Install of VMWare"
date: 2006-09-18
forum: Virtualisation
---

### Post by dema on 2006-09-18
I'm trying to install VMWare with this guide:
[http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)

But I'm getting this (see the end):

> Creating a new installer database using the tar3 format.

Installing the content of the package.

In which directory do you want to install the binary files?
[/usr/bin] /home/dennis/wmware

The path "/home/dennis/wmware" does not exist currently. This program is going
to create it, including needed parent directories. Is this what you want?
[yes] yes

What is the directory that contains the init directories (rc0.d/ to rc6.d/)?
[/etc] /etc

What is the directory that contains the init scripts?
[/etc/init.d]

In which directory do you want to install the daemon files?
[/home/dennis/sbin]

The path "/home/dennis/sbin" does not exist currently. This program is going to
create it, including needed parent directories. Is this what you want?
[yes]

In which directory do you want to install the library files?
[/home/dennis/lib/vmware]

The path "/home/dennis/lib/vmware" does not exist currently. This program is
going to create it, including needed parent directories. Is this what you want?
[yes]


In which directory do you want to install the manual files?
[/home/dennis/man]
The path "/home/dennis/man" does not exist currently. This program is going to
create it, including needed parent directories. Is this what you want?
[yes]

In which directory do you want to install the documentation files?
[/home/dennis/doc/vmware]

The path "/home/dennis/doc/vmware" does not exist currently. This program is
going to create it, including needed parent directories. Is this what you want?
[yes]

Unable to get the access rights of source file "./vmware-vix/bin".

Execution aborted.

dennis@dennis-laptop:/tmp/vmware-server-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Uninstalling the tar installation of VMware Server.

Stopping internet superserver: xinetd.
Starting internet superserver: xinetd.
Stopping VMware services:
   Virtual machine monitor                                             done

The removal of VMware Server 1.0.1 build-29996 for Linux completed
successfully. Thank you for having tried this software.

Installing the content of the package.

In which directory do you want to install the binary files?
[/home/dennis/wmware]

The path "/home/dennis/wmware" does not exist currently. This program is going
to create it, including needed parent directories. Is this what you want?
[yes]

What is the directory that contains the init directories (rc0.d/ to rc6.d/)?
[/etc]

What is the directory that contains the init scripts?
[/etc/init.d]

In which directory do you want to install the daemon files?
[/home/dennis/sbin]

The path "/home/dennis/sbin" does not exist currently. This program is going to
create it, including needed parent directories. Is this what you want?
[yes]

In which directory do you want to install the library files?
[/home/dennis/lib/vmware]

The path "/home/dennis/lib/vmware" does not exist currently. This program is
going to create it, including needed parent directories. Is this what you want?
[yes]

In which directory do you want to install the manual files?
[/home/dennis/man]

The path "/home/dennis/man" does not exist currently. This program is going to
create it, including needed parent directories. Is this what you want?
[yes]

In which directory do you want to install the documentation files?
[/home/dennis/doc/vmware]

The path "/home/dennis/doc/vmware" does not exist currently. This program is
going to create it, including needed parent directories. Is this what you want?
[yes]

Unable to get the access rights of source file "./vmware-vix/bin".

Execution aborted.

dennis@dennis-laptop:/tmp/vmware-server-distrib$

---

### Post by tagra123 on 2006-09-18
On the above: Did you type sudo before the install script?

Try this quide for vmplayer.

[http://ubuntuforums.org/showthread.php?t=84275](http://ubuntuforums.org/showthread.php?t=84275)

After vmplayer is install download and install vmworkstation (to create your virtual machines) VM Workstaion has a 30 day free trial. VMPLAYER is FREE.

---

### Post by mr. t. on 2006-09-26
my solution for VMware-server-1.0.1-29996

in directory ./vmware-vix create symbolic link to ../bin

---

### Post by KillerSiafu on 2007-08-05
mr. t.'s solution appears to have worked for me as well. Just create a symbolic soft link to ../bin in that ./vmware-vix directory and it no longer hits the error:

Unable to get the access rights of source file "./vmware-vix/bin".

---

### Post by chiques on 2008-04-04
What is a "symbolic link" and how do you create one for this installation?

---

### Post by p_quarles on 2008-04-05
Moved to Virtualization.

---

### Post by ikki_72 on 2008-04-28
> **chiques said:**
> What is a "symbolic link" and how do you create one for this installation?

in Windows term=shortcut
to make sym link, say in /usr/bin/ and pointing to /home/some-program/launcher and name the link myapp
```
ln -s /usr/bin/myapp /home/some-program/launcher
```

---

