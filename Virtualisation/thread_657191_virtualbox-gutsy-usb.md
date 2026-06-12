---
title: "virtualbox-gutsy-usb?"
date: 2008-01-03
forum: Virtualisation
---

### Post by DestroyMicroshaft on 2008-01-03
Heres the problem, Im using xp in a virtual machine, I want xp to see my usb hard drive, Ive read the guides and what not floating around in here, but they all say to go to the usb settings in the virtual machines settings. Hers the issue, I dont have usb options, they arent there. WTF

---

### Post by fiddledd on 2008-01-03
If you have no USB settings you must be using the OSE of VirtualBox. As far as I know you need the closed source edition for USB support. Just download it from the Virtualbox website.

---

### Post by DestroyMicroshaft on 2008-01-03
thank you, i didnt notice! :guitar:

---

### Post by freddyp on 2008-01-04
I had to make several changes to my Gutsy 71.0 configuration to get USB working in VirtualBox 1.5.2 under Windows XP.  Here's what I did:

Downloaded the current version directly from the VirtualBox site, installed, and then made the following two changes to get USB devices working in VirtualBox.

Note -- I'm running VirtualBox 1.5.2; the web site has a new 1.5.4 version. Not sure these changes are required in 1.5.4. I suspect they are still needed.

************************************************** **

FIRST CHANGE - edits to /etc/init.d/mountdevsubfs.sh

Support for /proc/bus/usb/* was removed in Ubuntu 7.10. Software developers will (over time) port USB calls to check /dev/bus/usb first but until then the following work-around re-enables /proc/bus/usb/devices in Ubuntu 7.10. It appears that VirtualBox 1.5.2 still calls /proc/bus/usb/devices.

In a terminal windows execute the following:

sudo /etc/init.d/mountdevsubfs.sh

The edits involve simply removing the # (comment symbol) from the mkdir through mount lines (Code after line 40)

#
# Magic to make /proc/bus/usb work
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

Execute the script manually to enable the change before a system reboot by running the following in a terminal window:

sudo /etc/init.d/mountdevsubfs.sh start

************************************************** ***

SECOND CHANGE - edits to /etc/udev/rules.d/40-permissions.rules

This provides/enables USB selection icon in VirtualBox. In a terminal window execute the following:

sudo gedit /etc/udev/rules.d/40-permissions.rules

Here are the edits in the file.

#Edited to enable USB devices on VirtualBox
#Original line commented out under #USB devices (usbfs replacement)
#added the new line

# USB devices (usbfs replacement)
#SUBSYSTEM=="usb_device", MODE="0664" # ORIGINAL
SUBSYSTEM=="usb_device", MODE="0666" # NEW LINE ENABLES USB ICON

# Now in VirtualBox select your machine, select USB controller,
# select Enable USB controller and add filter with blanks

# On the bottom of the VirtualBox window there is a icon to add USB devices
# right click and select device - to be safe you should unmount USB device
# in Ubuntu first

# ----------END OF COMMENTS -----------------------

Hope this helps!

---

### Post by DestroyMicroshaft on 2008-01-07
thanx all works great

---

### Post by blackenedbloodx on 2008-01-07
umm... yea how do i get this key? i have seen this "download here" on other things but i have no idea how to work it... all it is is txt. i have tried copying it in the terminal and all... please bear with me i'm still new to linux

EDIT: ok i got it to install but im still curious about how to do those... and now my USB dont work... how do i get it? i read the guy that made changes, but im kinda skeptical fom running chmod 666(cant remember the whole command). if u know what that is then u know i have good reason to be skeptical

---

### Post by ArtInvent on 2008-01-29
I'm running Gutsy, Virtualbox 1.5.4 (NOT the OSE edition), WinXP running as a guest. It's been working pretty sweetly for months but try as I might, still no USB access. I have modified fstab, added all users to the usbusers group, etc. etc. I've tried all this and suggestions from other blogs as to how to get USB going, no joy. 

The thing is, I can add the devices in the Virtualbox USB section before starting the VM. While XP is running as a guest. I can check and uncheck the devices, which are correctly identified, in the Machine - Devices - USB Devices menu.  In the XP system tray, I can even see a little green-arrowed 'Safely Remove Hardware' icon. But the USB devices (Creative Zen Nano Plus, Lexar SD Media card reader, etc.) never show up, I can't see them in the drive listing under My Computer in an Explorer window, WMP won't recognize the MP3 player, nothing. If I click on the Safely Remove Hardware icon, the window pops up -  but there are no devices listed. If I unplug the device, the icon disappears, and if I plug it back in, it reappears, but still not accessible. Weird. I'm probably missing something really stupid but I can't figure it out.

Any help please please.

---

### Post by desktopfan on 2008-01-30
Same problem here.

---

### Post by desktopfan on 2008-01-30
Ok after some more fiddling I managed to get it working.
 First I disabled EHCI Controller under USB settings then I removed all fields (excluding Vendor and Product ID) for my usb device.

Everything seems to be working now.

---

### Post by ArtInvent on 2008-01-30
@desktopfan -

Nice. There are a number of slightly different workarounds floating around I've tried involving a number of different config. files etc. Wonder if you could describe what settings, group id assignment,  or changes you made, if any, to these:

[B]/etc/fstab
/etc/udev/rules.d/40-permissions.rules
/etc/init.d/mountdevsubfs.sh
[/B]

---

### Post by desktopfan on 2008-01-31
**/etc/fstab**
#usbfs
none /proc/bus/usb usbfs devgid=1002,devmode=666 0 0

**/etc/udev/rules.d/40-permissions.rules**
# USB devices (usbfs replacement)
SUBSYSTEM=="usb_device",                MODE="0666"

**/etc/init.d/mountdevsubfs**
mkdir -p /dev/bus/usb/.usbfs
        domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
        ln -s .usbfs/devices /dev/bus/usb/devices
        mount --rbind /dev/bus/usb /proc/bus/usb

Followed all the guides to set them up correctly

---

### Post by ArtInvent on 2008-01-31
Thanks. I have been through every imaginable setting of those files, but after your previous post about disabling EHCI etc. I was able to, sort of, finally get some USB devices to mount. Though whether that was the problem it's hard to say. I also ended up running this command to alter the permissions of /proc/bus/usb as it didn't seem to have the correct group r/w permissions after boot no matter what I set the config files to (group still set to root) -
[FONT="Courier New"]
$ sudo chown -R root:e /proc/bus/usb[/FONT]   (e is my user acc't. and it's group)

The reasoning being that this is (afaik) the key mount directory that needs to be writable and the target of all the config files. This setting won't survive the next reboot I imagine. I also don't know whether this really helped, as I'm pretty sick of rebooting Ubuntu over and over to see the effect of settings.

Success: in stubborn determination  I basically just checked and unchecked the device a few times in succession in the VM, and after getting an error message, the device would suddenly just mount as a drive. I was able to copy files to a USB key, and WMPlayer recognized the MP3 player and was able to sync music files to it.

However, stopping and restarting the VM, reconnecting these devices is hit and miss. Check, uncheck the device 5 or 10 times, it might finally show up. 

Just for the heck of it, I re-enabled EHCI to get USB 2.0 support, also with mixed results. The VM installed a USB 2 driver etc but it also grabbed a printer that is on USB that it hadn't before and that I really don't want it to. And I couldn't get it to grab the USB key or mp3 player. 

I also found that it wasn't necessary to set up* any filters at all* in the VirtualBox settings, doesn't seem to make any difference. Plug a new USB device in and the VM picks it up and lists it and might even grab it without having to check it off.  (Or it might not!) I don't really see what the filters are supposed to do for you.

Anyway, I guess I'll keep messing with it. One last quick question for desktopfan - you have a group ID setting of 1002 - what group is that on your box?

---

### Post by theZoid on 2008-02-01
> **desktopfan said:**
> Ok after some more fiddling I managed to get it working.
 First I disabled EHCI Controller under USB settings then I removed all fields (excluding Vendor and Product ID) for my usb device.

Everything seems to be working now.

I have the ECHI checkbox 'checked'....however, I can't get my built in webcam to work because it says I don't have enough bandwidth...still working on that one, but everything else works fine.

---

### Post by jimbob on 2008-02-02
freddyp:  many thanks for your post - works great:

---

### Post by ArtInvent on 2008-02-13
Just wanted to add a note that I think I've finally got my USB mp3 player working pretty well in an XP host. It's an iRiver Clix2. It needs to hook up via MTP pretocol so I can use it in Napster to sync downloaded tracks via Windows Media Player. 

What really screwed me up was that Ubuntu by default had been set to recognize an MTP music player and to start Rhythmbox. I had to disable this by going to the menu: System | Preferences | Removable Drives and Media | Portable Music Players and uncheck the 'Play music . . .' option.

I actually re-booted just to be sure. Then I plugged in the music player, set up a USB filter for it in the VM settings, and started XP. The player was recognized on boot and a little red icon was sitting in the system tray. I started Win Media Player and was able to sync, detach, and re-attach the player, sync again, etc. Pretty slick.

---

### Post by zed41 on 2008-02-29
Got my Zune working with Virtualbox and gutsy, nice....

---

### Post by siki1981 on 2008-03-03
Thanks freddyp! Works like a charm :) Ubuntu support is great. At this point  I am finally ready to say..  Goodbye Windows.. 4 ever

---

### Post by iGrinch on 2008-04-25
> **desktopfan said:**
> **/etc/fstab**
#usbfs
none /proc/bus/usb usbfs devgid=1002,devmode=666 0 0

**/etc/udev/rules.d/40-permissions.rules**
# USB devices (usbfs replacement)
SUBSYSTEM=="usb_device",                MODE="0666"

**/etc/init.d/mountdevsubfs**
mkdir -p /dev/bus/usb/.usbfs
        domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
        ln -s .usbfs/devices /dev/bus/usb/devices
        mount --rbind /dev/bus/usb /proc/bus/usb

Followed all the guides to set them up correctly

Desktopfan - That was the missing link I needed. USB is fully working now.

Thanks!
Paul

---

### Post by aldodefilippi on 2008-05-02
VirtualBox is not showing my CD/DVD drive in the drop down box

I'm using version 1.6.0-30421 for gutsy I also tried version 156-28266 for gutsy same result. Now I even can't mount the cd drive from inside ubuntu. I need help. Thanks

---

### Post by theZoid on 2008-05-02
> **aldodefilippi said:**
> VirtualBox is not showing my CD/DVD drive in the drop down box

I'm using version 1.6.0-30421 for gutsy I also tried version 156-28266 for gutsy same result. Now I even can't mount the cd drive from inside ubuntu. I need help. Thanks

This is the way it works perfect for me in Hardy:

[http://forum.notebookreview.com/showthread.php?t=242936](http://forum.notebookreview.com/showthread.php?t=242936)

If I use mode 0666 things wont' work.

---

