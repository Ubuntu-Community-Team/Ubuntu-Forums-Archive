---
title: "vmware-tools only install incomplete"
date: 2008-03-21
forum: Virtualisation
---

### Post by xcommy on 2008-03-21
Hi there,

I installed VMware Server 1.0.5 and want to use an Ubuntu guest there. Of course I would like to install the vmware-tools. Apart from the error regarding the vmhgfs module, the orther modules simply do not compile. I mean, there are no errors or such, they simply are not installed, they seem to be ignored.

Any ideas about this?

Regards,

Matthias

---

### Post by dcstar on 2008-03-21
> **xcommy said:**
> Hi there,

I installed VMware Server 1.0.5 and want to use an Ubuntu guest there. Of course I would like to install the vmware-tools. Apart from the error regarding the vmhgfs module, the orther modules simply do not compile. I mean, there are no errors or such, they simply are not installed, they seem to be ignored.

Any ideas about this?

Regards,

Matthias

Try posting the actual output so people can have something to work with.

---

### Post by xcommy on 2008-03-21
Sorry. vmware-install.pl gives the following output:

```
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Uninstalling the tar installation of VMware Tools.

Stopping VMware Tools services in the virtual machine:
   Guest operating system daemon:-ne                                   done


File /etc/X11/xorg.conf is backed up to /etc/X11/xorg.conf.old.2.

The removal of VMware Tools 1.0.5 build-80187 for Linux completed successfully.
Thank you for having tried this software.

Installing the content of the package.

In which directory do you want to install the binary files? 
[/usr/bin] 

What is the directory that contains the init directories (rc0.d/ to rc6.d/)? 
[/etc] 

What is the directory that contains the init scripts? 
[/etc/init.d] 

In which directory do you want to install the daemon files? 
[/usr/sbin] 

In which directory do you want to install the library files? 
[/usr/lib/vmware-tools] 

The path "/usr/lib/vmware-tools" does not exist currently. This program is 
going to create it, including needed parent directories. Is this what you want?
[yes] 

In which directory do you want to install the documentation files? 
[/usr/share/doc/vmware-tools] 

The path "/usr/share/doc/vmware-tools" does not exist currently. This program 
is going to create it, including needed parent directories. Is this what you 
want? [yes] 

The installation of VMware Tools 1.0.5 build-80187 for Linux completed 
successfully. You can decide to remove this software from your system at any 
time by invoking the following command: "/usr/bin/vmware-uninstall-tools.pl".

Before running VMware Tools for the first time, you need to configure it by 
invoking the following command: "/usr/bin/vmware-config-tools.pl". Do you want 
this program to invoke the command for you now? [yes] 

It looks like you are trying to run this program in a remote session. This 
program will temporarily shut down your network connection, so you should only 
run it from a local console session. Are you SURE you want to continue? 
[no] yes


Stopping VMware Tools services in the virtual machine:
   Guest operating system daemon:-ne                                   done

Trying to find a suitable vmhgfs module for your running kernel.

None of the pre-built vmhgfs modules for VMware Tools is suitable for your 
running kernel.  Do you want this program to try to build the vmhgfs module for
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.22-14-generic/build/include] 

Extracting the sources of the vmhgfs module.

Building the vmhgfs module.

Using 2.6.x kernel build system.
make: Gehe in Verzeichnis '/tmp/vmware-config9/vmhgfs-only'
make -C /lib/modules/2.6.22-14-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /tmp/vmware-config9/vmhgfs-only/cpName.o
  CC [M]  /tmp/vmware-config9/vmhgfs-only/cpNameLinux.o
  CC [M]  /tmp/vmware-config9/vmhgfs-only/dev.o
  CC [M]  /tmp/vmware-config9/vmhgfs-only/driver.o
/tmp/vmware-config9/vmhgfs-only/driver.c: In Funktion »HgfsChangeFileAttributes«:
/tmp/vmware-config9/vmhgfs-only/driver.c:763: Fehler: »struct inode« hat kein Element namens »i_blksize«
/tmp/vmware-config9/vmhgfs-only/driver.c: In Funktion »HgfsInitializeInode«:
/tmp/vmware-config9/vmhgfs-only/driver.c:835: Fehler: »struct inode« hat kein Element namens »u«
/tmp/vmware-config9/vmhgfs-only/driver.c: In Funktion »HgfsIget«:
/tmp/vmware-config9/vmhgfs-only/driver.c:884: Fehler: »struct inode« hat kein Element namens »u«
/tmp/vmware-config9/vmhgfs-only/driver.c: In Funktion »HgfsCreate«:
/tmp/vmware-config9/vmhgfs-only/driver.c:1535: Fehler: »struct inode« hat kein Element namens »u«
/tmp/vmware-config9/vmhgfs-only/driver.c: In Funktion »HgfsLookup«:
/tmp/vmware-config9/vmhgfs-only/driver.c:1635: Fehler: »struct inode« hat kein Element namens »u«
/tmp/vmware-config9/vmhgfs-only/driver.c: In Funktion »HgfsMkdir«:
/tmp/vmware-config9/vmhgfs-only/driver.c:1727: Fehler: »struct inode« hat kein Element namens »u«
/tmp/vmware-config9/vmhgfs-only/driver.c: In Funktion »HgfsDelete«:
/tmp/vmware-config9/vmhgfs-only/driver.c:1854: Fehler: »struct inode« hat kein Element namens »u«
/tmp/vmware-config9/vmhgfs-only/driver.c: In Funktion »HgfsRename«:
/tmp/vmware-config9/vmhgfs-only/driver.c:2046: Fehler: »struct inode« hat kein Element namens »u«
/tmp/vmware-config9/vmhgfs-only/driver.c:2048: Fehler: »struct inode« hat kein Element namens »u«
/tmp/vmware-config9/vmhgfs-only/driver.c: In Funktion »HgfsRevalidate«:
/tmp/vmware-config9/vmhgfs-only/driver.c:2288: Fehler: »struct inode« hat kein Element namens »u«
/tmp/vmware-config9/vmhgfs-only/driver.c: In Funktion »HgfsSetattr«:
/tmp/vmware-config9/vmhgfs-only/driver.c:2425: Fehler: »struct inode« hat kein Element namens »u«
/tmp/vmware-config9/vmhgfs-only/driver.c: In Funktion »HgfsOpen«:
/tmp/vmware-config9/vmhgfs-only/driver.c:2801: Fehler: »struct inode« hat kein Element namens »u«
/tmp/vmware-config9/vmhgfs-only/driver.c: In Funktion »HgfsDirOpen«:
/tmp/vmware-config9/vmhgfs-only/driver.c:3414: Fehler: »struct inode« hat kein Element namens »u«
/tmp/vmware-config9/vmhgfs-only/driver.c: In Funktion »HgfsClearInode«:
/tmp/vmware-config9/vmhgfs-only/driver.c:4105: Fehler: »struct inode« hat kein Element namens »u«
make[2]: *** [/tmp/vmware-config9/vmhgfs-only/driver.o] Fehler 1
make[1]: *** [_module_/tmp/vmware-config9/vmhgfs-only] Fehler 2
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.22-14-generic'
make: *** [vmhgfs.ko] Fehler 2
make: Verlasse Verzeichnis '/tmp/vmware-config9/vmhgfs-only'
Unable to build the vmhgfs module.

The filesystem driver (vmhgfs module) is used only for the shared folder 
feature. The rest of the software provided by VMware Tools is designed to work 
independently of this feature.
If you wish to have the shared folders feature, you can install the driver by 
running vmware-config-tools.pl again after making sure that gcc, binutils, make
and the kernel sources for your running kernel are installed on your machine. 
These packages are available on your distribution's installation CD.
[ Press Enter key to continue ] 



Detected X.org version 1.3.



No drivers for X.org version: 1.3.



Do you want to change your guest X resolution? (yes/no) [no] 

Starting VMware Tools services in the virtual machine:
   Switching to guest configuration:-ne                                done

   DMA setup:-ne                                                       done

   Guest operating system daemon:-ne                                   done


The configuration of VMware Tools 1.0.5 build-80187 for Linux for this running 
kernel completed successfully.

You must restart your X session before any mouse or graphics changes take 
effect.

You can now run VMware Tools by invoking the following command: 
"/usr/bin/vmware-toolbox" during an X session.

Enjoy,

--the VMware team

```

I tried an vmware-uninstall-tools.pl, but the result is the same. It completely ignores the other modules.

Matthias

---

### Post by scottws on 2008-04-08
I'm having the same trouble.  Via Google, I've found references to altering a file in the VMware-tools that come with VMware workstation. But this doesn't work for the tools that come with VMware Server as the file that you edit does not exist.

---

### Post by larcher on 2008-04-21
[http://communities.vmware.com/thread/59360](http://communities.vmware.com/thread/59360)

It solves the problem for me

---

### Post by scottws on 2008-04-21
> **larcher said:**
> [http://communities.vmware.com/thread/59360](http://communities.vmware.com/thread/59360)

It solves the problem for me

I'll check it out but wow that thread is more than two years old, with the most recent response being more than one year old, and is for Fedora Core 5.

---

### Post by thisismalhotra on 2008-04-21
> **scottws said:**
> I'll check it out but wow that thread is more than two years old, with the most recent response being more than one year old, and is for Fedora Core 5.

Please install followinf packages before you compile vmware-tools

build-essential
linux-source 2.XX (which ever version you use)

Then try to compile again

---

