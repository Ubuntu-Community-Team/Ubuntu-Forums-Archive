---
title: "Installed guest 14.04; installed guest additions; still can't get full screen"
date: 2015-05-25
forum: Virtualisation
---

### Post by AussieGuy on 2015-05-25
So I've spent most of the day installing and reinstalling ubuntu 14.04 as a guest OS in VirtualBox 4.3.28, running as a host on Windows 7 Enterprise 64 bit.  And I've installed the virtualbox-guest-dkms as instructed, and rebooted.  But I still can't get a full screen - I'm stuck on 640x480.  I remember when I did this last about a year ago I had to jump through all sorts of hoops to get it working... and I can't remeber what they were.  Advice would be warmly received!

Thanks,
-A

---

### Post by QIII on 2015-05-25
When you say "installed", do you mean you added the inserted the guest additions image?  Did you also run the guest additions installation script on the guest?

Do you have the Virtualbox Extension Pack installed on the host?

---

### Post by AussieGuy on 2015-05-25
All of these.  I have the VirtualBox guest ISO downloaded for the host; I also downloaded it (using apt-get) in the guest, and ran it to configure and install the modules.  Just to make sure I ran 'sudo dpkg reconfigure VBoxLinuxAdditions.run'.

I can't mount the ISO from Virtualbox, however, and the option "Auto-resize Guest display" is grayed-out: disabled.  So *something's* wrong, but I don't know quite where...

---

### Post by ajgreeny on 2015-05-25
You really need the VBox-guest-additions direct from Oracle for the best working of VBox, as the version from the repos seems to be several behind your VBox install so get it from the link below and install it again.
[http://download.virtualbox.org/virtualbox/4.3.28/Oracle_VM_VirtualBox_Extension_Pack-4.3.28-100309.vbox-extpack](http://download.virtualbox.org/virtualbox/4.3.28/Oracle_VM_VirtualBox_Extension_Pack-4.3.28-100309.vbox-extpack)

You may still need to add the virtual CD to the guest from the **Devices->Insert Guest Additions CD** menu, if it is not showing in nautilus.
Now in the guest ubuntu open a terminal and use **sudo -i** to get a root terminal.

Open up the VBox-guest-additions virtual CD disk, which should appear in the left hand pane of nautilus and drag and drop the VBox-linux.run file (I can't remember exactly what it's called) to the terminal and just hit Enter to run the script.

This is how I did it in my Ubuntu 14.04 guest on a Xubuntu 14.04 host.  I can't help with Windows as host as I do not run Windows any more.

---

