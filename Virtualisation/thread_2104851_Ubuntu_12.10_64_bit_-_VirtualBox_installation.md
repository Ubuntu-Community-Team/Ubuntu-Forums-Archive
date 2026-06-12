---
title: "Ubuntu 12.10 64 bit - VirtualBox installation"
date: 2013-01-14
forum: Virtualisation
---

### Post by ilivetowin on 2013-01-14
Hey all, 


I just installed Ubuntu 12.10 and was trying to install a Windows 8 Virtualbox. I downloaded the 64bit Virtualbox file from virtualbox.org, it then took me to Ubuntu software center where I installed another file virtualbox-4.2.

The program initially wouldn't show up, so I logged out and then it did show up. I clicked to create a new Virtualbox, inserted the Win 8 dvd, and when I clicked start I was greeted with two error boxes:

ERROR 1
The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

ERROR 2
Failed to open a session for the virtual machine Win 8 RC.
The virtual machine 'Win 8 RC' has terminated unexpectedly during startup with exit code 1.
Details

Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Machine
Interface: 
IMachine {22781af3-1c86-5126-9edf-67a020e0e989}

Im relatively new to Ubuntu, any suggestions of what went wrong? 

Thanks for taking your time to read this! 

Sean

---

### Post by SeijiSensei on 2013-01-14
I strongly recommend following the procedure described for "Debian-based" distributions on the VirtualBox [Linux download page]("https://www.virtualbox.org/wiki/Linux_Downloads").  You'll probably also need to install the kernel headers for your release so the installer can compile the needed kernel module.  Give this a try:

First, add this line to the bottom of the file /etc/apt/sources.list.  You'll need to do this as root with sudo:

```
deb http://download.virtualbox.org/virtualbox/debian quantal contrib
```

Next run the following:

```

sudo apt-get update
sudo apt-get install build-essential linux-headers-$(uname -r)
wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
sudo apt-get purge virtualbox-*
sudo apt-get install virtualbox-4.2

```

The second line installs the gcc compiler and associated files and gets the kernel header files that correspond with your current kernel version.  (Run the command "uname -r" to see how that works.)  The next line installs the Oracle public key as described in the link above.  The last two lines remove any existing VB installation and replaces it with a new copy of version 4.2.

I've never had a problem with VB when installed from the Oracle repository.  You get the nice added feature that the OS will manage any updates for VirtualBox the same way it manages updates for all the other software on your system.

---

### Post by ilivetowin on 2013-01-15
I tried your solution but I still get the same exact error popping up. Any other suggestions or is there another program I can download in place of virtualbox? The program I need to run will not run in Wine.

---

### Post by ilivetowin on 2013-01-15
Scrap that last comment, I tried it again and it did work, I likely made some silly error the first time. I get past that initial problem I was having, but now have run into a new one. I get past the info screen about how the right CTRL key is my home button and I select the DVD drive as the installation media, but then I get this error

Failed to open a session for the virtual machine Win 8 RC.
AMD-V is disabled in the BIOS. (VERR_SVM_DISABLED).

Also, there is some sort of issue with my USB ports working apparently as well, but that is solved by downloading an extension pack from the website apparently. 

Any ideas?

---

### Post by SeijiSensei on 2013-01-16
> **ilivetowin said:**
> Failed to open a session for the virtual machine Win 8 RC.
AMD-V is disabled in the BIOS. (VERR_SVM_DISABLED).

Did you look into the BIOS to see if you can change this?

> Also, there is some sort of issue with my USB ports working apparently as well, but that is solved by downloading an extension pack from the website apparently.

USB support is a proprietary add-on that requires installing the "[guest extensions](http://www.virtualbox.org/manual/ch04.html)".

---

### Post by ilivetowin on 2013-01-16
Nothing I can see in the BIOS that says anything of the sort. When I arrive at the BIOS I see these options

Standard CMOS Features
Advanced BIOS Features
Advanced Chipset Features
Integrated Peripherals
Power Management
PnP/PCI Config
PC Health Status
Frequency/Voltage Control
Load Fail-Safe Defaults
Load Optimized Defaults
Set Supervisor Password
Set User Password
Save and Exit


I checked each one of the options and nothing inside there said anything that looked like the error message. I think chose to Load Optimized Defaults in the BIOS thinking that would help, no luck.

---

### Post by ilivetowin on 2013-01-16
Got it all working! 

It was under Frequency/Voltage control > Secure VirtualMachine Mode was disabled. Clicking enabled worked. Installing extras fixed other problems. Everything with the machine is working great, I added the vboxusers to the usb list and all that. 

Only one issue left is that the program I wanted to use it for, Logitech Motion Detection that comes with Logitech cameras seems to have some issues. It recognizes the USB camera is plugged in but the screen shows as just a black screen. The camera is facing something and should be displaying an image, I will restart the PC and maybe that will fix it. 

Thanks for all the help, I really do appreciate it, your method of installing worked great after enabling that mode in BIOS. 

Sean

---

