---
title: "&quot;VirtualBox kernel driver not installed&quot;"
date: 2008-04-27
forum: Virtualisation
---

### Post by wanorris on 2008-04-27
There seem to be a number of threads related to VirtualBox problems in Hardy, but I've looked at several, and haven't seen this exact problem.

Since I upgraded to Hardy (386), I can't get VirtualBox to work.

The VirtualBox console will launch, but when I try to launch a virtual machine (my one VM is Windows XP 32-bit), it pops up a dialog with the following message:

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel and execute '/etc/init.d/vboxdrv start' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}



When I search Synaptic for VirtualBox, I find the following packages:

virtualbox-ose (version 1.5.0-dfsg2-1ubuntu3)
virtualbox-ose-modules-2.6.22 6


The updater also keeps popping up and reminding me to install virtualbox-ose (version 1.5.6-dfsg-6ubuntu1). When I click on "Install Updates," it fails with the following message:

E: /var/cache/apt/archives/virtualbox-ose_1.5.6-dfsg-6ubuntu1_i386.deb: subprocess pre-installation script returned error exit status 1


I tried following the instructions in the error box and ran

sudo /etc/init.d/vboxdrv start

The result was:

 * Starting VirtualBox kernel module vboxdrv
FATAL: Module vboxdrv not found.

 * Modprobe vboxdrv failed. Please use 'dmesg' to find out why.


I also ran across a message suggesting that I run vboxdrv with the command "setup", so I ran 

sudo /etc/init.d/vboxdrv start

The result was:

 * Usage: /etc/init.d/vboxdrv {start|stop|restart|status}


Any suggestions on how to solve this problem? Thanks in advance!





Edit: oops, I made a cut and paste error. The last bit should read:


sudo /etc/init.d/vboxdrv setup

The result was:

 * Usage: /etc/init.d/vboxdrv {start|stop|restart|status}

---

### Post by Jolly Roger on 2008-04-28
i had this problem but then i ran ```
sudo /etc/init.d/vboxdrv setup
```
after trying that in the terminal i ran virtualbox again. now it's telling me:

PIIX3 cannot attach drive to the Secondary Master.
VBox status code: -102 (VERR_FILE_NOT_FOUND).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

so i haven't fixed my problem yet. hopefully i'm making some progress.

EDIT: so i seem to have fixed my own problem. i changed my cd-rom setting from /dev/hda to the name of my cd-rom drive and it is now running.

EDIT 2: i thought it was running anyway. turns out that the virtual machine starts up but windows can't boot. it's complaining that there is a problem with either my virtual hard drive or the hard drive controller. i sure do hope that my virtual machine image isn't corrupted somehow.

---

### Post by landcross on 2008-04-28
I have the same problem if you do resolve pleae post your solution.

Thanks


PIIX3 cannot attach drive to the Secondary Master.
VBox status code: -102 (VERR_FILE_NOT_FOUND).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by Ubuntwan on 2008-04-28
The post by Rytron in this thread solved this problem for me: [http://ubuntuforums.org/showthread.php?t=767451&highlight=PIIX3]("http://ubuntuforums.org/showthread.php?t=767451&highlight=PIIX3")
I had a cd mounted last time virtualbox was running and it was missing this cd now, and gave this error. In the settings menu I unchecked the mount cd/dvd drive checkbox and everything was fine again.

---

### Post by landcross on 2008-04-29
Thanks, but this sounds difficult. I do not have the CD problem, just the drive connection problem

'PIIX3 cannot attach drive to the Secondary Master'.

I looked at the link ,but how do you achieve this clone solution in simple to understand terms?

Is there no other solution

---

### Post by landcross on 2008-05-02
Ref: PIIX3 cannot attach drive to the Secondary Master.

I did a reinstall of virtual box but it did not resolve this problem. To save reinstall for anyone else::)

This later problem was solved without a reinstall in 'settings' within virtualbox.

1) Release the virtual drive 
2) Just create another virtual machine and attach the original virtual drive.

---

### Post by drsox1899 on 2008-05-02
Did anyone think to look whether they are a member of the virtual box group ?   

Try System>Administration>Users and Groups>Manage Groups>vboxusers>properties.  Then check your login to ensure you are in the group.

Then Log-out and backin.

The kernel problem should have gone away.

Second item to note :

Don't use the version in the Synaptic repositories.  Go to the source repository at VirtualBox : [https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

Breaking News !!!!

This is a new version of Virtual Box : 1.6

Ubuntu 8.04 is now supported.

This is NEW today (last 6 hours)

---

### Post by hodenkat on 2008-05-03
Nope, guess again.

Installed virtualbox_1.6.0-30421_Ubuntu_hardy_i386.deb and have the same problem.

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason.
Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.

VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).

Ran the "Re-setup" and got:

 * Stopping VirtualBox kernel module vboxdrv                             [ OK ] 
 * Recompiling VirtualBox kernel module vboxdrv                                 
 * Look at /var/log/vbox-install.log to find out what went wrong.


Looked at vbox-install.log:

Makefile:75: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.


How come if so many people are saying this is easy, it's turning into a major pain in the @$$?!:(

Here's how I fixed the problem.

In synaptic package manager, do a search for "virtualbox".
Look for virtualbox with it's checkbox checked. It will have the version to the right.

Click on it and choose "Mark for complete removal".
Click apply...done!

---

### Post by teddypompom on 2008-05-06
Hello, I was having the same problem as above but once i have install the correct kernel version for virtualbox, everything seems to work.

---

### Post by davidwillington on 2008-05-12
I fixed the kernel module problem by getting the latest version from Sun at 
[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)
and upgrading. I can't remember if I originally installed Virtualbox with Synaptic or with a downloaded .deb file. I think it was the latter. The upgrade seems to have kept my virtual machines intact which is a relief.

---

### Post by Free Hugs on 2008-05-12
> I fixed the kernel module problem by getting the latest version from Sun at
[https://cds.sun.com/is-bin/INTERSHOP...-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP...-F@CDS-CDS_SMI)

Thank you! This worked for me also.

---

### Post by notepad on 2008-05-24
check that you havent pointed your vdi to your secondary slave as your cd rom.
i had the same error as you and my problem seems to have been that i enabled my cd rom and chose the slave one instead of the master one.
when i changed it around, my error was gone and it runs fine. 
as for using the cd rom drive itself, it gives an error when there is no disc in the drive possibly because i enabled passthrough. otherwise everything is as it should be.

---

