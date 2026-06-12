---
title: "Installation of virtual box on ubuntu 16.04"
date: 2017-04-05
forum: Virtualisation
---

### Post by IJM on 2017-04-05
Setting up virtualbox for Unbuntu 16.04
   Site for installation instructions:	
 [https://www.virtualbox.org/wiki/Linux_Downloads]("https://www.virtualbox.org/wiki/Linux_Downloads")
 [h=3]Installation instructions for Debian-based Linux distributions[/h] 	Followed in order:
 ```
sudo nano /etc/apt/sources.list:  
```
 	Inserted the line
 ```
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) xenial contrib
```
	Ctrl+O to save Ctrl+X to quit
	Following lines in order
```
wget -q [https://www.virtualbox.org/download/oracle_vbox_2016.asc](https://www.virtualbox.org/download/oracle_vbox_2016.asc) -O- | sudo apt-key add -
wget -q [https://www.virtualbox.org/download/oracle_vbox.asc](https://www.virtualbox.org/download/oracle_vbox.asc) -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install virtualbox-5.1
sudo apt-get install dkms
```
	The virtual package is &#8216;hadoop&#8217; which was downloaded.  When trying to run from VB, the following errors occurred
```
 Kernel driver not installed (rc=-1908)
 The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing   '/sbin/vboxconfig'   as root.
where: suplibOsInit what: 3 VERR_VM_DRIVER_NOT_INSTALLED (-1908) - The support driver is not installed. On linux, open returned ENOENT.
 sudo /sbin/vboxconfig
	
	vboxdrv.sh: Stopping VirtualBox services.
	vboxdrv.sh: Building VirtualBox kernel modules.
	vboxdrv.sh: Starting VirtualBox services.
	vboxdrv.sh: Building VirtualBox kernel modules.
	vboxdrv.sh: failed: modprobe vboxdrv failed. Please use 'dmesg' to find out why.

	There were problems setting up VirtualBox.  To re-start the set-up process, run
 	 /sbin/vboxconfig
	as root. 
```
 
 I&#8217;ve seen this problem in several older posts but not with any satisfactory solution &#8211; any ideas as to what is going on, it seems to be something to do with the Kernel,  although I&#8217;m not sure exactly what the error message actual means?

---

### Post by TheFu on 2017-04-05
Out of date guest additions?

Does lsmod show the vboxdrv?

---

### Post by Bucky Ball on 2017-04-05
I'm just wondering why you're installing it with a PPA for Debian-based installs when Virtualbox is in the official repositories. Just use Synaptics or Software or whatever package manager you use (or a terminal) and install from there. Perhaps that will make a difference. 

You don't need a PPA to install Virtualbox and it is always better, and safer, to look in the repositories first for the app before going further afield (you install any repo at your own risk and third-party repositories have nothing to do with Canonical; if a PPA goes down, becomes out of date or unsupported, that is down to whoever owns the repo).

---

### Post by IJM on 2017-04-05
Thanks for this.  I have tried this but it got the same result.  I'll have another go.  I think i've installed and then removed at least five times using a variety of approaches, including different terminal commands as well as the software centre solution, all with no success.

---

### Post by ajgreeny on 2017-04-05
Like IJM I use the repositories provided by Oracle-Virtualbox and fully detailed in the "Debian-based Linux distributions" at [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads).

Doing so gives me VBox version 5.1.18 rather than 5.0.32 which is the default version in Xenial repos.  I have had no problems using that installation/update system for some time now on my Xubuntu 16.04 and it means I have the most recent VBox version always.

Have you checked that your BIOS is enabled for virtualisation? I can't remember exactly what it is called but is something like VT-x so have a look in your BIOS/UEFI settings to ensure it is enabled.

---

### Post by lammert-nijhof on 2017-04-05
I use the same version 5.1.18 of Virtualbox on Ubuntu 16.04, however I always install dkms and other dependencies BEFORE installing virtualbox. I do not worry about ppa, because virtualbox itself will warn me, when there is a new version. I just load the deb and the USB extension, dpkg the download and double click on the extension. If a dependency is missing dpkg will tell you and you apt that missing package and dpkg again. No problem not with 14.04 nor with 16.04. I decide after scanning the release notes, whether I need that upgrade or not. Many times I just skip a few versions, because there is nothing in it for me and updating all guests is really work. All those Linus distros and Windows versions from Windows for Work-groups 3.11, NT-4.0 up to the last Windows I used and bought Vista.  If you don't upgrade all guests, soon all guests will be on different versions. If I decide to upgrade, I download the deb and dpkg it again, quite simple just like a Windows application.

---

### Post by SeijiSensei on 2017-04-05
Did you run dmesg as suggested in the error?

I've only ever used the Oracle repositories for VirtualBox following the method referenced by ajgreeny above.  Always worked like a charm.

I presume you've already installed the other required packages like the gcc compiler, or they were installed as dependencies for vbox.  Run 
```

sudo apt-get update
sudo apt-get install build-essential

```
and try again.

---

