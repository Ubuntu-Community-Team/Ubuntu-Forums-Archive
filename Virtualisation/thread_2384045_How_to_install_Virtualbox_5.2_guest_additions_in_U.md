---
title: "How to install Virtualbox 5.2 guest additions in Ubuntu 16.04"
date: 2018-02-01
forum: Virtualisation
---

### Post by smith73 on 2018-02-01
What I did on Ubuntu-Mate 16.04.3:

   Added the following line to my /etc/apt/sources.list : deb [https://download.virtualbox.org/virtualbox/debian](https://download.virtualbox.org/virtualbox/debian) <xenial> contrib

then:
wget -q [https://www.virtualbox.org/download/oracle_vbox_2016.asc](https://www.virtualbox.org/download/oracle_vbox_2016.asc) -O- | sudo apt-key add - 
sudo apt-get update 
sudo apt-get install virtualbox-5.2

Installed:
                        
virtualbox-guest-source - x86 virtualization solution - guest addition module source
 virtualbox-guest-utils - x86 virtualization solution - non-X11 guest utilities
 virtualbox-guest-source-hwe - x86 virtualization solution - guest addition module source
 virtualbox-guest-utils-hwe - x86 virtualization solution - non-X11 guest utilities

as mentioned there [https://gist.github.com/magnetikonline/1e7e2dbd1b288fecf090f1ef12f0c80b](https://gist.github.com/magnetikonline/1e7e2dbd1b288fecf090f1ef12f0c80b)


 Guest additions didn't provided full-screen for guest systems.


So I installed VBoxGuestAdditions_5.2.6.iso from there [http://download.virtualbox.org/virtualbox/5.2.6/](http://download.virtualbox.org/virtualbox/5.2.6/)[URL="http://download.virtualbox.org/virtualbox/5.2.6/VBoxGuestAdditions_5.2.6.iso"]
[/URL]and it didn't work. (I rebooted several times)

By starting a guest system and selecting Devices -> Insert Guest Additions CD, no further prompts are shown so guest additions 
are not installed this way either.

While having installed Virtualbox 5.2 and installing Guest additions 5.0 (virtualbox-guest-additions-iso  as named in repositories)
these Guest additions 5.0 remove Virtualbox 5.2.


In WIndows any updates to Virtualbox would be shown and prompted to download instantly, and installed in several clicks.
_Is Ubuntu degrading with  Virtualbox 5.2 guest additions ?_

[URL="http://download.virtualbox.org/virtualbox/5.2.6/VBoxGuestAdditions_5.2.6.iso"]

[/URL]

---

### Post by ajgreeny on 2018-09-13
I suggest you add the repos from Oracle for VBox, which it looks as though you have already done, and will give you version 5.2.18 at the moment.
You then should download the **VirtualBox Extension Pack** from [https://download.virtualbox.org/virtualbox/5.2.18/Oracle_VM_VirtualBox_Extension_Pack-5.2.18.vbox-extpack](https://download.virtualbox.org/virtualbox/5.2.18/Oracle_VM_VirtualBox_Extension_Pack-5.2.18.vbox-extpack).

Double clicking on that downloaded extpack file you downloaded will offer to install it in the VBox manager, so accept that.

Now start your Virtual machine and try again the Devices ->Insert Guest Additions CD.  You will need an empty CD drive in the storage section of the VBox manager window in which to add the virtual CD.
Once inserted you should see the new Guest Additions CD in the VM's file manager so click on that to mount it if it's not already mounted and drag the file VirtualBoxLinux-5.2.18.run into a terminal using the sudo prefix, and hit enter to install the guest additions.
Depending on the distro of you VM, if it is Linux, you may need to use ```
sudo bash VirtualBoxLinux-5.2.18.run
``` but it is not needed in the *ubuntu family of OSs.

Incidentally you must have the same version of guest additions as the VBox itself so VBox-5.2.6 will not work with a different guest additions version; get the 5.2.18 version of both in the way I advised above.

Good luck!  I hope this helps but come back again if you still have trouble.

---

### Post by howefield on 2018-09-13
Thread moved to the "*Virtualisation*" forum.

---

