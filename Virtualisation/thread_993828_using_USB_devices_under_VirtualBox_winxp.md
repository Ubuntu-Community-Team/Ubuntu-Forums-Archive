---
title: "using USB devices under VirtualBox winxp"
date: 2008-11-26
forum: Virtualisation
---

### Post by Caraibes on 2008-11-26
I am happily running Hardy x64.

I am aiming at having a virtual XP so I can use my scanner & webcam (while Skyping)...

In order to do so, I first installed VirtualBox OSE from the repos.Then I found out this version didn't support usb, so I downloaded and installed the one from the Sun website. It works fine, but there's a problem (bug ?) when it comes to usb devices:

I installed Windows XP. The first time I used USB devices (scanner & webcam), both worked fine. Then, after reboot, they were "greyed out"... Not seen by Windows, but seen by VirtualBox, however "greyed out", so I couldn't enable/disable them...

There might be a trick I haven't seen... If any of the readers have a suggestion, please feel free.

I am also considering trying another way to have a "virtual windows"...

-Maybe VMware ?

-How's your experience with VMware on Hardy x64 ?

Thanks in advance for your insights !

---

### Post by C. Wizard on 2008-11-26
I had the same experience. It was fine the first time, but not the second. What I had done between the two sessions was to enable the
USB 2.0 (EHCI) Controller.  Once I removed the check mark in the box to the left of that line, the scanner came back to life. 
Also, do not create a filter for your USB mouse, if you have one.

---

### Post by Caraibes on 2008-11-26
Thanks for sharing your experience...

I don't have a usb mouse (mine is ps2).

I tried your tip, didn't work...

---

### Post by unknown03 on 2008-11-26
I had problems with the USB not working. How I got mine to work was to add myself to the vboxusers groups and follow this page: [http://www.davidgrant.ca/virtualbox_usb_windows_xp_guest_ubuntu_hardy](http://www.davidgrant.ca/virtualbox_usb_windows_xp_guest_ubuntu_hardy), restart, and it should be up.. remember, not everybodies <gid> is the same

Also, make sure you have filters for your devices so the Guest can see it (but if you have a USB mouse then avoid a filter for it, like c. wizzard said)

---

### Post by punkybouy on 2008-11-26
I didn't think the OSE version of VirtualBox had USB support.  You might want to check that.

---

### Post by punkybouy on 2008-11-26
opps

---

### Post by Caraibes on 2008-11-27
> **unknown03 said:**
> I had problems with the USB not working. How I got mine to work was to add myself to the vboxusers groups and follow this page: [http://www.davidgrant.ca/virtualbox_usb_windows_xp_guest_ubuntu_hardy](http://www.davidgrant.ca/virtualbox_usb_windows_xp_guest_ubuntu_hardy), restart, and it should be up.. remember, not everybodies <gid> is the same

Also, make sure you have filters for your devices so the Guest can see it (but if you have a USB mouse then avoid a filter for it, like c. wizzard said)
Thanks for the link, I read the whole article, and double-checked my settings, which were already coherent with what the author said... No luck... Still not working...

-What would be the difference between VirtualBox and VMware ?

---

### Post by C. Wizard on 2008-11-29
> **Caraibes said:**
> -What would be the difference between VirtualBox and VMware ?
Two different companies, of course, but the interface is similar. I could never get file sharing to work in VMWare Server between a virtual machine and the host. Plus when I installed Hardy/8.04 VMWare stopped working and I could couldn't find a fix.
VirtualBox has a much smaller foot print. The download file is around 29 megs vs 100+ for VWMare Server.  I've found VirtualBox easier to use, much faster to install, and file sharing works between the host and the virtual machines in VirtualBox. 
Based on my limited experience, VirtualBox is, for my purposes, the better of the two products.

---

### Post by Caraibes on 2008-11-30
Thanks for your insights ! It makes me feel like sticking with VirtualBox... If only I could use my USB devices !!!

---

### Post by Blackwolf_Oz on 2008-12-01
Here's how I got usb devices working in an XP Virtual Machine in Hardy (8.04).

You may heed to recompile for Intrepd. UPDATE To get it to recompile the kernal, if you have an error, run sudo /etc/init.d/vboxdrv setup

Add yourself to the group VirtualBox created during install called "vboxusers" The VB install creates this group, find it, don't add another one.

Create a group named "usbusers" and put yourself in it.

sudo groupadd usbusers
sudo gpasswd -a usbusers

Or do the above in Control Center under 'users and groups'.


Now then,
EDIT: Modify the rules in file “/etc/udev/rules.d/40-permissions.rules” for Gutsy, and “/etc/udev/rules.d/40-basic-permissions.rules” for Hardy:]
Change the lines :

From:

# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
SUBSYSTEM=="usb_device", MODE="0664"

To :

# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", GROUP="usbusers", MODE="0664"
SUBSYSTEM=="usb_device", MODE="0664"

Now on to......

The Grande Finale,

add this line:

none /proc/bus/usb usbfs devgid=120,devmode=664 0 0

to your /etc/fstab file (at the bottom). Just make sure that 120 is your vboxusers group (use your own number).


Reboot the computer.

Open VirtualBox and click on "Settings".

Click on the "USB" item in the left pane to edit the USB prefs.

Click on the "Add device" button to add a filter and select your printer from the list and click on the "Ok" button.

Start your VM and Windows should detect your printer.

---

