---
title: "Attach USB device to Innotech virutal box virtual machine"
date: 2008-01-17
forum: Virtualisation
---

### Post by Rhaddad on 2008-01-17
Is there anyway to mount an unrecognisable USB device to my virutal machine (innotech)

thanks in advacned

---

### Post by VON_CAPO on 2008-01-17
First, there is 2 versions of virtualbox, the community supported and the binary non free, so, you should install the second one ---> virtualbox_1.5.4-27034_ubuntu_gutsy_i386.deb

After that, do the following:

     Go to "System/Administration/Users and Groups/Manage Groups/" and select the "vboxusers", click "Properties" and check "what_ever_is_your_user_name". 

Make Virtualbox able to recognise USB devices.
            ---> sudo gedit /etc/init.d/mountdevsubfs.sh

            Find the following lines:

                #mkdir -p /dev/bus/usb/.usbfs
                #domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
                #ln -s .usbfs/devices /dev/bus/usb/devices
                #mount --rbind /dev/bus/usb /proc/bus/usb

            Unmark them so that look like this:

                mkdir -p /dev/bus/usb/.usbfs
                domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
                ln -s .usbfs/devices /dev/bus/usb/devices
                mount --rbind /dev/bus/usb /proc/bus/usb

            Save it and reboot.

---

### Post by epitaph123 on 2008-01-21
Virtualbox XP still won't reconize my usb stick, I rebooted & everything...

Ubuntu 7.10 Gutsy Gibbon

---

### Post by Rhaddad on 2008-01-22
doesn't work??? i don't know why

---

### Post by mozetti on 2008-01-22
When you said, "unrecognizable", did you mean Ubuntu doesn't recognize the USB device? If so, I don't think any virtualization software would help you. My understanding is that the Host OS (Ubuntu) must be able to use the device if you want any client virtual machines to use it.

---

### Post by dark_phantom on 2008-01-22
If ubuntu doesn't recognize a usb drive, I doubt you can use it on a VM.  Fix that issue first then try to get the VM to see it.  BTW, did you install the VB tools?

---

### Post by Rhaddad on 2008-01-25
yea i did. Looks like i can't use my device :(

---

### Post by phyz on 2008-01-25
> **VON_CAPO said:**
> First, there is 2 versions of virtualbox, the community supported and the binary non free, so, you should install the second one ---> virtualbox_1.5.4-27034_ubuntu_gutsy_i386.deb

After that, do the following:

     Go to "System/Administration/Users and Groups/Manage Groups/" and select the "vboxusers", click "Properties" and check "what_ever_is_your_user_name". 

Make Virtualbox able to recognise USB devices.
            ---> sudo gedit /etc/init.d/mountdevsubfs.sh

            Find the following lines:

                #mkdir -p /dev/bus/usb/.usbfs
                #domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
                #ln -s .usbfs/devices /dev/bus/usb/devices
                #mount --rbind /dev/bus/usb /proc/bus/usb

            Unmark them so that look like this:

                mkdir -p /dev/bus/usb/.usbfs
                domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
                ln -s .usbfs/devices /dev/bus/usb/devices
                mount --rbind /dev/bus/usb /proc/bus/usb

            Save it and reboot.

:guitar:
 thanks....it works fine with my double-G

---

### Post by bobpress on 2008-01-26
I had trouble connecting USB to VirtualBox also.  There are full instructions available at [http://www.arsgeek.com/?p=2776](http://www.arsgeek.com/?p=2776)

---

### Post by catfacts on 2008-03-04
I have a lego NXT block, it doesnt register at all on linux but the block says its pluged in. I did the above mentioned code and set up Port 0 as COM1 to /dev/usb1 (which is where i plug in the block) but it says 
> 
Serial device 0 cannot attach to char driver
.
VBox status code: -38 (VERR_ACCESS_DENIED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 

---

