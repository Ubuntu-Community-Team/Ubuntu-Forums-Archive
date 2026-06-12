---
title: "virtual box (ose) usb support"
date: 2010-10-19
forum: Virtualisation
---

### Post by jarrah-95 on 2010-10-19
i need to get an iso i made in a virtual machene to my real computer, but the problem is that i cannot get virtual box to recognise the usb.
if there is no support for usb then is there another way to get the iso to the real computer???
thanks

---

### Post by LaimonasM on 2010-10-19
Closed-source features
The following list shows the enterprise features that are only present in the closed-source edition. Note that this list may change over time as some of these features will eventually be made available with the open-source version as well.

Remote Display Protocol (RDP) Server
This component implements a complete RDP server on top of the virtual hardware and allows users to connect to a virtual machine remotely using any RDP compatible client.

USB support
VirtualBox implements a virtual USB controller and supports passing through USB 1.1 and USB 2.0 devices to virtual machines.

USB over RDP
This is a combination of the RDP server and USB support allowing users to make USB devices available to virtual machines running remotely.

Open-source features
The following list shows the features that are only present in the open-source edition. The licensing conditions of the necessary libraries prevent inclusion in the full-featured product.

Virtual Network Computing (VNC) Server
This component implements a complete VNC server on top of the virtual hardware and allows users to connect to a virtual machine remotely using any VNC client.

[http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

---

### Post by ysNoi on 2010-10-21
Hi jarrah-95...

Try to share your usb to your virtual machine and copy your files on it.

Check this:
```
http://ubuntuforums.org/showthread.php?t=1594780
```

and look for reply #6 to create your shared usb.

Make it sure the media is inserted on your host machine.

HTH...

---

### Post by na5h on 2010-10-21
Virtualbox OSE does not have USB-support, but the PUEL-version [http://www.virtualbox.org/wiki/VirtualBox_PUEL]("http://www.virtualbox.org/wiki/VirtualBox_PUEL") does! It's free of charge for personal use!

---

### Post by jarrah-95 on 2010-10-22
hey i tryed what has been said in post 6 and it dident work, (it kept giving me an error, not found) then i tryed the puel version and theres no difference, still no usb support, even though they say it has it???

---

### Post by Warthaug on 2010-10-22
> **jarrah-95 said:**
> hey i tryed what has been said in post 6 and it dident work, (it kept giving me an error, not found) then i tryed the puel version and theres no difference, still no usb support, even though they say it has it???
The more common failure of USB in the PUEL version is that your user name is not part of the virtualbox group.

Open System->Administration->Users, and select your user name.  Click "Manage Groups", and scroll down to vboxusers.  Click "properties", the make sure your user ID is checked off.  Re-start VBOX and USB should work.

Bryan

---

### Post by jarrah-95 on 2010-10-22
ive just added my self to the vboxusers group and it made no difference, the virtual os still doesnt recognose usbs and no usbs appear at the bottum left of the screen (with the cd/hdd/floppy/shared folders) any more ideas???

---

### Post by na5h on 2010-10-23
Try going to the synaptic package manager and mark both versions of virtualbox for **complete** removal...then reinstall the puel-version. Also remeber: If you want to use an usb-device in virtualbox, you must click the "usb-devices"-tab when the virtual machine is on, and select the device you wish to use (tip: some usb-devices don't seem to install correctly unless you enable them before the guest os has started up completely...my Walkman mp3-player was like that when I tried to get it working in Windows 7).

---

### Post by Wobblybob on 2010-10-23
I last used Virtualbox in Jaunty, so this may not work in later versions, here are the notes i made at the time so that i could load my iPod in Win XP. I now use Floola in Ubuntu so no longer use Virtualbox.

There are two versions of Virtual Box:
- OSE (Open Source Edition) which is in the repos
- Closed Source Edition, or Standard, or just plain “Virtual Box”

OSE does not have USB support. There are a few other features from the closed source version that are missing in OSE, So, if you want to have USB support in VirtualBox, you need to install the closed source edition and make a change to /etc/fstab. Here are the steps:

Remove OSE version with

$ sudo apt-get autoremove virtualbox-ose

open the repo sources list with;

$ sudo gedit /etc/apt/sources.list

add the line;

deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) jaunty non-free
from the VirtualBox site at; 

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

to the end, save and close. Now in a [Terminal], type;

$ wget -q [http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc](http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc) -O- | sudo apt-key add -

to add the key and;

$ sudo apt-get update

to update the system.

Install the latest virtualbox package (as of this writing it is virtualbox-3.0.4) by selecting it in Synaptic, or running this command from a terminal:

$ sudo apt-get install virtualbox-3.2.10

Add yourself to the vboxusers group:

$ sudo gpasswd -a YOURUSERNAME vboxusers

Find the devgid for ‘vboxusers’:

$ grep vboxusers /etc/group

It will return something like:

vboxusers:X:125:username

Add this line to the bottom of /etc/fstab, replace the devgid number with your devgid:

none /proc/bus/usb usbfs devgid=125,devmode=664 0 0

changing devgid=125 to the number you got from the above command.

After you reboot you should now have USB support in VirtualBox, just add the usb device in VirtualBox first by adding a "filter" and using "any" in the [remote] option.

Last tested on Ubuntu 9.04 Jaunty Jackalope. Good Luck

---

### Post by jarrah-95 on 2010-10-24
thanks everyone, i just completly reinstalled virtual box with the puel one and it workes perfictly, better than the host ubuntu. (i now can see the usb in the virtual os and not the host, but thats no problem it probably just hasent mounted) 
thanks

---

### Post by Alfons81 on 2011-04-22
Hi,

Virtualbox-OSE version 4 support usb. Here the steps you may follow:

1.- launch Vbox-ose 4 and make a filter for each usb you want to run inside the virtual system. Edit the filter for each usb chaging option 'no' to 'any' on the 'remote' option.

2.- go to system > administration > users and groups and add yourself on the 'vboxusers' group.

3.- logout session or reboot your system and enjoy your vbox-ose with usb capability 

Cheers!!!

---

### Post by CharlesA on 2011-04-22
> **Alfons81 said:**
> Hi,

Virtualbox-OSE version 4 support usb. Here the steps you may follow:

1.- launch Vbox-ose 4 and make a filter for each usb you want to run inside the virtual system. Edit the filter for each usb chaging option 'no' to 'any' on the 'remote' option.

2.- go to system > administration > users and groups and add yourself on the 'vboxusers' group.

3.- logout session or reboot your system and enjoy your vbox-ose with usb capability 

Cheers!!!
You need to install the extension pack to get USB support.

---

### Post by wompshmack on 2012-08-20
> **CharlesA said:**
> You need to install the extension pack to get USB support.

Just to clarify, you are both right, you need to do both of those things to get USB support, at least as of 4.0.4, which is what I'm currently running. According to Oracle VB versions after 4.0 are all open source, and the extension pack is not. Therefore versions after 4.0 shouldn't say OSE, as they should all be opensource. The version I have does say 4.0.4 OSE, but as always, your results may vary.

---

### Post by CharlesA on 2012-08-20
> **wompshmack said:**
> Just to clarify, you are both right, you need to do both of those things to get USB support, at least as of 4.0.4, which is what I'm currently running. According to Oracle VB versions after 4.0 are all open source, and the extension pack is not. Therefore versions after 4.0 shouldn't say OSE, as they should all be opensource. The version I have does say 4.0.4 OSE, but as always, your results may vary.
The version in the Ubuntu repos is the "OSE" and is not compatible with the extension pack, which is why you need the one from the virtualboix site.

---

