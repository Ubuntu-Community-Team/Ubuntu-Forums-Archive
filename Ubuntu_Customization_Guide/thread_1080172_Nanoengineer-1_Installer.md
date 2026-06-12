---
title: "Nanoengineer-1 Installer"
date: 2009-02-25
forum: Ubuntu Customization Guide
---

### Post by technologiclee on 2009-02-25
I would like to start a thread under 3rd party software about an open source package Nanoengineer-1. [http://www.nanoengineer-1.com/content/](http://www.nanoengineer-1.com/content/) An account can be requested at [email]support@nanorex.com[/email] There is a wiki that details the installation procedure, but we are requested to not post it publicly for now. It has installers for windows and mac - but not linux - the source is available. It requires several dependent packages - some not available in the Package Manager because it uses the older versions. I would like help installing NE1 or ideally an installer to be made. Also it would be nice if more people were working on the project to accelerate development. If this is not the proper venue to do so - can you point me in the right direction?

---

### Post by smd1280 on 2009-03-11
Hi, 

If you got this installed it would be great if you could let me know how you did this.  For example, all the packages that is required. I tried but I don't really know what I'm doing. 


> **technologiclee said:**
> I would like to start a thread under 3rd party software about an open source package Nanoengineer-1. [http://www.nanoengineer-1.com/content/](http://www.nanoengineer-1.com/content/) An account can be requested at [email]support@nanorex.com[/email] There is a wiki that details the installation procedure, but we are requested to not post it publicly for now. It has installers for windows and mac - but not linux - the source is available. It requires several dependent packages - some not available in the Package Manager because it uses the older versions. I would like help installing NE1 or ideally an installer to be made. Also it would be nice if more people were working on the project to accelerate development. If this is not the proper venue to do so - can you point me in the right direction?

---

### Post by technologiclee on 2009-03-12
my notes for ubuntu 8.10 - 9.04 and Mandriva 2008 are here 

[http://sites.google.com/site/nanoengineers/installing-nanoengineer1-v111-for-ubuntu-linux-804-hardy-heron](http://sites.google.com/site/nanoengineers/installing-nanoengineer1-v111-for-ubuntu-linux-804-hardy-heron)

Nanorex uses Mandriva [- installed Mandriva 2008 on my desktop computer using]("http://www.mandriva.com/en/download") [UNetbootin]("http://sourceforge.net/project/showfiles.php?group_id=198821")


installing PyQt requires qt 4 makefile to be put on the PATH to install

can the Mandriva 2008 Path Control Center be used?

// home/lee/.kde/Autostart/


please let me know if you find out how to do this step

---

### Post by technologiclee on 2009-03-12
// q: i try to run sudo apt-get. neither user or root pw works - lee is not in the sudoers file
// a: Log in as root and do everything as root.
// a:
[lee@localhost ~]$ su root
Password:
[root@localhost lee]#

// [http://www.linuxforums.org/forum/mandriva-linux-help/106017-mandriva-2008-root-login-help.html](http://www.linuxforums.org/forum/mandriva-linux-help/106017-mandriva-2008-root-login-help.html)
// [http://www.linuxforums.org/forum/mandriva-linux-help/22582-how-do-i-login-root.html](http://www.linuxforums.org/forum/mandriva-linux-help/22582-how-do-i-login-root.html)

//[root@localhost lee]# sudo apt-get install python2.5-dev
//sudo: apt-get: command not found

// q: why does apt-get fail?


// a: You need to configure your account as sudoer before you can use sudo
// [http://www.go2linux.org/sudoers-how-to](http://www.go2linux.org/sudoers-how-to)

// q: **[COLOR="Red"]how do i close / save after the visudo command?[/COLOR]**
// a: ZZ or W  to just save
// q: nothing happened with ZZ or W. CTRL+Z gives following output

[root@localhost lee]# visudo

[1]+  Stopped                 visudo
[root@localhost lee]# 

// q: will uncommenting wheel be sufficient to continue installation?

# User privilege specification
root ALL=(ALL) SETENV: ALL

# Uncomment to allow people in group wheel to run all commands
# and set environment variables.
%wheel ALL=(ALL) SETENV: ALL

# Same thing without a password
# %wheel ALL=(ALL) NOPASSWD: SETENV: ALL

# Samples
# %users ALL=/sbin/mount /cdrom,/sbin/umount /cdrom
# %users localhost=/sbin/shutdown -h now

---

### Post by technologiclee on 2009-03-13
[http://www.icewalkers.com/Linux/Software/535940/InstallBuilder.html](http://www.icewalkers.com/Linux/Software/535940/InstallBuilder.html)

Can this be used to build an installer for NE-1?

This package is available as a .rpm . To use it in Ubuntu, first use Synaptic Package manager to install Alien to create a .deb

(Suggestion to Ubuntu developers: intergate Alien into Package Manager to run automatically)

After downloading Installbuilder to the default tmp folder:

Using Terminal, use the cd .. command to navigate to the top of the directory, then cd tmp. (when entering package name, tab can be used for auto completion)

Alien must be run as root therefore use sudo:

lee@EV007:/$ cd ..
lee@EV007:/$ ls
bin    dev   initrd.img      lost+found  opt   sbin     sys  var
boot   etc   initrd.img.old  media       proc  selinux  tmp  vmlinuz
cdrom  home  lib             mnt         root  srv      usr  vmlinuz.old
lee@EV007:/$ cd tmp
lee@EV007:/tmp$ ls
installbuilder-enterprise-6.0.2-0.i386.rpm

lee@EV007:/tmp$ alien installbuilder-enterprise-6.0.2-0.i386.rpm 
Must run as root to convert to deb format (or you may use fakeroot).
lee@EV007:/tmp$ sudo alien installbuilder-enterprise-6.0.2-0.i386.rpm 
[sudo] password for lee: 
Warning: Skipping conversion of scripts in package installbuilder: postinst postrm prerm
Warning: Use the --scripts parameter to include the scripts.
installbuilder_6.0.2-1_i386.deb generated
lee@EV007:/tmp$ ls
installbuilder_6.0.2-1_i386.deb
installbuilder-enterprise-6.0.2-0.i386.rpm



Now how do I install this? make?

---

### Post by technologiclee on 2009-04-07
The post I would have left at Icewalkers - if there was not a 70 character limit (that is not room for a substantial review):


I would like to use this package in Ubuntu (9.04) to make an installer for Nanoengineer-1.

I have used Alien to create a .deb file. I would like assistance on installing this as a .deb and creating the installer.

Perhaps an installer could be made for InstallBuilder itself .    ; )

---

### Post by technologiclee on 2009-04-21
I have inststalled Nanoengineer v1.1.1 on Ubuntu 8.10 (Studio)

My notes are here: [http://docs.google.com/Doc?id=dc26889x_102hqxfw2cg]("http://docs.google.com/Doc?id=dc26889x_102hqxfw2cg")

---

