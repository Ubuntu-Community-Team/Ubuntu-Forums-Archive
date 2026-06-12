---
title: "(VirtualBox) Kernel driver not installed (rc=-1908) - how do I fix this?"
date: 2014-10-18
forum: Virtualisation
---

### Post by ascendingphoenix on 2014-10-18
Solved, thanks awesome community - I just reinstalled VirtualBox using the terminal. =)

---

### Post by ascendingphoenix on 2014-10-18
I just fixed this.

All I needed to do was reinstall it using terminal - I started by starting VirtualBox in the terminal (just writing 'virtualbox') and it said that I need to reinstall it using a particular command - I wrote that command in and it reinstalled everything and now it's fine.

---

### Post by mörgæs on 2014-10-18
Please use Thread Tools for marking a thread solved.

---

### Post by pbhill on 2014-10-22
I too had the same message and reinstalled. Now I get a slightly different error; here is from install log:

"Uninstalling modules from DKMS
Attempting to install using DKMS
Failed to install using DKMS, attempting to install without
Makefile:183: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop."

I am not sure how to do all this. Can someone give me some direction?
Thank You.

---

### Post by jeffsilverm on 2014-11-10
I tried to solve the problem using the command line.

[FONT=Courier New]jeffs@jeffs-desktop:~$ **sudo virtualbox**
WARNING: The character device /dev/vboxdrv does not exist.
	 Please install the virtualbox-ose-dkms package and the appropriate
	 headers, most likely linux-headers-generic.

	 You will not be able to start VMs until this problem is fixed.

[/FONT]
Then,

[FONT=Courier New]jeffs@jeffs-desktop:~$ **sudo apt-get install virtualbox-ose-dkms**
[sudo] password for jeffs: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  virtualbox-ose-dkms
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 22.2 kB of archives.
After this operation, 121 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/universe virtualbox-ose-dkms all 4.1.12-dfsg-2ubuntu0.6 [22.2 kB]
Fetched 22.2 kB in 0s (58.4 kB/s)              
Selecting previously unselected package virtualbox-ose-dkms.
(Reading database ... 1139782 files and directories currently installed.)
Unpacking virtualbox-ose-dkms (from .../virtualbox-ose-dkms_4.1.12-dfsg-2ubuntu0.6_all.deb) ...
Setting up virtualbox-ose-dkms (4.1.12-dfsg-2ubuntu0.6) ...
jeffs@jeffs-desktop:~$ [/FONT]

I found another answer at [http://www.binarytides.com/fix-vbox-kernel-driver-error/]("http://www.binarytides.com/fix-vbox-kernel-driver-error/")  so I tried the following:

[FONT=Courier New]sudo apt-get install linux-headers-generic
sudo apt-get install build-essential module-assistant 
sudo m-a prepare
sudo /etc/init.d/vboxdrv setup
virtualbox
[/FONT]

and I still get the same error.

---

### Post by jeffsilverm on 2014-11-11
I hit the "post" button a little too soon, sorry.

I did a little more Googling, and I found the following advice

[FONT=Courier New]sudo apt-get remove virtualbox-dkms
sudo apt-get install virtualbox-dkms[/FONT]

The installation process rebuilds the virtualbox kernel modules for the kernel that you are running.  Kernel modules are tied to the specific kernel.  My understanding is that DKMS means that you don't need to recompile the modules each time you upgrade the kernel.  If that's true, then these two commands solve the problem.  If that's not true, then you have to remove and insert virtualbox-dkms each time you upgrade the kernel.

---

