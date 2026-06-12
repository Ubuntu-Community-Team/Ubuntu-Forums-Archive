---
title: "[SOLVED] Adjusting resolution in VirtualBox installation of Ubuntu"
date: 2008-06-19
forum: Virtualisation
---

### Post by dnaga57 on 2008-06-19
used the guide to Install Hardy inside Win XP in Virtual Box.
I use a Dell D420 Latitude.
The Ubuntu window in Virtual box is shrunk. It asks me to adjust display to 32 bit from the current 16 bit.
I do not know how
Advise please

---

### Post by geo909 on 2008-06-19
When you power the machine on, there is a "devices" option.
There you should find an option about mounting an iso that has some addons.
Mount it and follow the instructions, you should then have the choice to make it fullscreen and other things.

Excuse me for the lack of details. I don't have virtual box anymore so this is what I can tell from memory.

If you can't find such a menu, it's my fault, please ignore my post then.

---

### Post by Sigudian on 2008-06-19
i have windows XP in virtualbox in ubuntu, 
i pressed device -> install guest addon (mounts driver disc)
use the contents of the disc and probably reboot the virtual machine (atleast for windows)
there you go you may now do what you wished for :)

---

### Post by dnaga57 on 2008-06-19
I understand that the resolution configuration can be modified thru the file path /etc/x11/xconfig.
I do not know how to form a command line for this
Can you help
When I power my VB it immediately boots Ubuntu, cant get the Devices option. Any advice?

---

### Post by overdrank on 2008-06-19
> **dnaga57 said:**
> I understand that the resolution configuration can be modified thru the file path /etc/x11/xconfig.
I do not know how to form a command line for this
Can you help
When I power my VB it immediately boots Ubuntu, cant get the Devices option. Any advice?

Hi and please do not make multiple threads on the same issue
[http://ubuntuforums.org/showthread.php?t=834562](http://ubuntuforums.org/showthread.php?t=834562)
[http://ubuntuforums.org/showthread.php?p=5221396#post5221396](http://ubuntuforums.org/showthread.php?p=5221396#post5221396)
You can edit your xorg with the command 
```
gksu gedit /etc/X11/xorg.conf
```
Sorry I have not use Ubuntu in a Virtual machine inside windows and you may seek the Virtual manual.

---

### Post by geo909 on 2008-06-20
> **dnaga57 said:**
> I understand that the resolution configuration can be modified thru the file path /etc/x11/xconfig.
I do not know how to form a command line for this
Can you help
When I power my VB it immediately boots Ubuntu, cant get the Devices option. Any advice?

I'm pretty sure it's not about X11 in you situation..
I guess ubuntu sees your VB window as a tiny screen.

When you power up the virtual machine, don't you see something like that
in the red circle in the screenshot below? (Ignore the error message)

[[IMG]http://www.imageshack.gr/files/52bze5tbw8rp626xciij_thumb.png[/IMG]](http://www.imageshack.gr/view.php?file=52bze5tbw8rp626xciij.png)

---

### Post by Virtualpower on 2008-06-20
I am having a similar problem and I have a Dell Latitude 820 laptop. What I have done so far is having Guest Additions installed in Ubuntu and added "vboxvideo" as the driver in xorg.conf. After all this, I still get the 32bit color depth required issue and Ubuntu switches to shell prompt. Note that I am running Ubuntu from raw disk and not from live CD. In fact, when I try to run it via live CD, it works fine so I am very puzzled.

Can one use "vboxvideo" as a primary video driver for Ubuntu or does that only work in Virtual mode?

---

### Post by dnaga57 on 2008-06-20
> **overdrank said:**
> Hi and please do not make multiple threads on the same issue
[http://ubuntuforums.org/showthread.php?t=834562](http://ubuntuforums.org/showthread.php?t=834562)
[http://ubuntuforums.org/showthread.php?p=5221396#post5221396](http://ubuntuforums.org/showthread.php?p=5221396#post5221396)
You can edit your xorg with the command 
```
gksu gedit /etc/X11/xorg.conf
```
Sorry I have not use Ubuntu in a Virtual machine inside windows and you may seek the Virtual manual.

I am sorry - apologies for double posting. I thought my post within another thread is being missed by helpful guys, hence made a separate one.
Will try your advice
Thanks again

---

### Post by dnaga57 on 2008-06-20
> **geo909 said:**
> I'm pretty sure it's not about X11 in you situation..
I guess ubuntu sees your VB window as a tiny screen.

When you power up the virtual machine, don't you see something like that
in the red circle in the screenshot below? (Ignore the error message)

[[IMG]http://www.imageshack.gr/files/52bze5tbw8rp626xciij_thumb.png[/IMG]](http://www.imageshack.gr/view.php?file=52bze5tbw8rp626xciij.png)

I do get a message that 
Your resolution is set to 16 bit, will be better in 32 bit, Please change to 32 bit on the guest OS   
or something like that. Only I am groping with changing it to 32 bit without knowing How
:confused::confused::confused:
:(:(:(

---

### Post by philinux on 2008-06-20
Have you installed "Guest Additions".

[http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/](http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/)

---

### Post by dnaga57 on 2008-06-20
> **philinux said:**
> Have you installed "Guest Additions".

[http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/](http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/)

I am using Sum Microsystems Virtual Box ver 1.6.2 for Windows. The tutorial is for Ubntu.
I do not get the device option in the version I have
Pls help

---

### Post by philinux on 2008-06-20
You install the additions when in the guest not in the host. Which in your first post says it is ubuntu.

---

### Post by dnaga57 on 2008-06-20
> **philinux said:**
> You install the additions when in the guest not in the host. Which in your first post says it is ubuntu.

Thanks a lot.
I downloaded the .iso file of VBox Additions, ran it thru Terminal, rebooted
Presto !!!!
Got a proper full sized Ubuntu window.
Thanks a lot again:):):)
:guitar:

---

### Post by dnaga57 on 2008-06-21
> **philinux said:**
> You install the additions when in the guest not in the host. Which in your first post says it is ubuntu.

Thank you. I am coming back witrh a request.
I have installed LinuxMint 5.0 in Virtual Box. I have the same resolution problem.
I have downloaded the .iso file of VBox additions. It is in the desktop of LinuxMint.
I cant run it as 'it says that autorun feature is not enabled.
I did something in Ubuntu thru Terminal which wirked. I have forgotten What I did.
Can you help me to run /media/cdrom0/VBoxGuestAdditions.exe so that I get the resolution normalised.
Thanks in advance

---

### Post by Wesley on 2008-06-22
installed mint 5 on virtualbox, also installed guest additions and it worked with mouse, but still stuck on resolution of 800x600, i checked control panel to change the resolution but there no higher than 800x600. 

i know its not the resolution itself, its the vbox video driver in xconf file. 

[PHP]# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
    Driver      "vboxmouse"
	Option		"CorePointer"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection[/PHP]

so what do i have to change to enable vbox video driver?

thanks

---

### Post by Wesley on 2008-06-22
dnaga57

i wondered if you dont mind copy/paste of your xorg file? 

run in terminal : sudo gedit /etc/X11/org.conf 

copy/paste everything

cheers :)

---

