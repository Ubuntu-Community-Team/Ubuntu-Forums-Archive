---
title: "[SOLVED] installing my USB Bluetooth device in Virtualbox windows xp"
date: 2008-10-31
forum: Virtualisation
---

### Post by medya on 2008-10-31
my host is ubuntu hardy
my guest is windows xp 
I use virtualbox

I wanna install the bluetooth USB device on my windows xp .
the usb bluetooth works fine in ubuntu (host) .

please guide me .

---

### Post by medya on 2008-11-01
bump .

---

### Post by uidb4056 on 2008-11-01
Wich version of virtualbox are you running?

---

### Post by medya on 2008-11-01
version 2

---

### Post by uidb4056 on 2008-11-01
I would mean if you install the version from the repository (ending with OSE, the versions from the repository are open source and has not support for USB), i suggest you uninstall the current version and follow this link [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) , this will install the last version of Virtualbox free but not open source with support for USB.

Just in case you are running Intrepid Ibex 8.10 you can select from the link the Hardy repositories that works OK in my case

Be sure to add the refered repositoy to your sources and also the key as indicates the link.

---

### Post by HotShotDJ on 2008-11-01
> **uidb4056 said:**
> Just in case you are running Intrepid Ibex 8.10 you can select from the link the Hardy repositories that works OK in my case.The Intrepid repository works, even though it is not listed (as of this evening).
```
deb http://download.virtualbox.org/virtualbox/debian intrepid non-free

```And, of course, make sure to add the public key according to the instructions given in uidb4056's link.

---

### Post by medya on 2008-11-02
I already told you  I installed verion 2, 
the one in the repository is version 1.5

i have version 2 and it supports usb but I dont know how to use it .

---

### Post by HotShotDJ on 2008-11-02
> **medya said:**
> i have version 2 and it supports usb but I dont know how to use it .[LIST=1]
[*]Go to System -> Administration -> Users & Groups
[*]Unlock  "Users Settings" using the "Unlock" button near the lower right of the box (next to the close button)
[*]Click on "Manage Groups"
[*]Click on "+ Add Group"
[*]In the "Group Name" text box, type "usbuser"
[*]IMPORTANT:  Write down the Group ID number on a piece of paper... you'll need this later!
[*]Click on your user name in the "Group Members" table -- a check mark will appear in front of the user name.  Do this for each user you wish to allow USB access in VirtualBox
[*]Click OK, and then Close, then Close again.
[*]Now, open Applications -> Accessories -> Terminal
[*]Type "gksudo gedit /etc/fstab" (without the quotes)
[*]Add following lines to the end of the file:```
# For USB access with Virtualbox
none	/proc/bus/usb	usbfs	devgid=1001,devmode=664	0	0
```
[*]IMPORTANT: Replace 1001 with the Group ID number that you wrote down earlier.
[*]Save the edited file (File -> Save) and then exit gedit.
[*]Reboot your system
[*]Make sure you've enabled USB Controller in VirtualBox
[*]Enjoy USB goodness in VirtualBox
[/LIST]

---

### Post by 73ckn797 on 2008-11-10
> **HotShotDJ said:**
> 
[LIST=1]
[*]Go to System -> Administration -> Users & Groups
[*]Unlock  "Users Settings" using the "Unlock" button near the lower right of the box (next to the close button)
[*]Click on "Manage Groups"
[*]Click on "+ Add Group"
[*]In the "Group Name" text box, type "usbuser"
[*]IMPORTANT:  Write down the Group ID number on a piece of paper... you'll need this later!
[*]Click on your user name in the "Group Members" table -- a check mark will appear in front of the user name.  Do this for each user you wish to allow USB access in VirtualBox
[*]Click OK, and then Close, then Close again.
[*]Now, open Applications -> Accessories -> Terminal
[*]Type "gksudo gedit /etc/fstab" (without the quotes)
[*]Add following lines to the end of the file:```
# For USB access with Virtualbox
none    /proc/bus/usb    usbfs    devgid=1001,devmode=664    0    0
```
[*]IMPORTANT: Replace 1001 with the Group ID number that you wrote down earlier.
[*]Save the edited file (File -> Save) and then exit gedit.
[*]Reboot your system
[*]Make sure you've enabled USB Controller in VirtualBox
[*]Enjoy USB goodness in VirtualBox
[/LIST]


I tried this setup with VB in 8.10. The Group ID that was assigned was 1001. Upon following all the steps I still cannot read USB flash drives. The printer is recognized as a USB device but nothing else.

Any other info you would need?

edit: I was not running the PUEL version but the one through Synaptic. It did have options for USB but they did nothing to make it work.

---

### Post by solimanm on 2010-08-25
> **HotShotDJ said:**
> [LIST=1]
[*]Go to System -> Administration -> Users & Groups
[*]Unlock  "Users Settings" using the "Unlock" button near the lower right of the box (next to the close button)
[*]Click on "Manage Groups"
[*]Click on "+ Add Group"
[*]In the "Group Name" text box, type "usbuser"
[*]IMPORTANT:  Write down the Group ID number on a piece of paper... you'll need this later!
[*]Click on your user name in the "Group Members" table -- a check mark will appear in front of the user name.  Do this for each user you wish to allow USB access in VirtualBox
[*]Click OK, and then Close, then Close again.
[*]Now, open Applications -> Accessories -> Terminal
[*]Type "gksudo gedit /etc/fstab" (without the quotes)
[*]Add following lines to the end of the file:```
# For USB access with Virtualbox
none	/proc/bus/usb	usbfs	devgid=1001,devmode=664	0	0
```
[*]IMPORTANT: Replace 1001 with the Group ID number that you wrote down earlier.
[*]Save the edited file (File -> Save) and then exit gedit.
[*]Reboot your system
[*]Make sure you've enabled USB Controller in VirtualBox
[*]Enjoy USB goodness in VirtualBox
[/LIST]
I've followed your steps accurately, but during the reboot, the ubuntu welcome screen showed me the error:

"mount point /proc/bus/usb does not exist"

and a choice between skipping that mount operation and manually mounting it.

Looking under /proc/bus I found only those folders:

input
pccard
pci

I'm trying to enable bluetooth on virtual box v3.2.8 so that I can use it on my windows XP VM.

If I enable bluetooth on the ubuntu host, it is shown as dimmed (unavailable) on the VM menu under USB devices, and if I disable it, it is not shown at all.

---

### Post by solimanm on 2010-09-04
I found this site:

[http://www.clearevo.com/blog/howto/2010/05/25/virtualbox_usb_fix_for_ubuntu_1004.html](http://www.clearevo.com/blog/howto/2010/05/25/virtualbox_usb_fix_for_ubuntu_1004.html)

It worked :)

Apparently, it wasn't just the bluetooth device, I was unable to connect any USB devices.

It only worked when I did the following steps (extracted from the link above):

1. Go to  System>Administration>Users and Groups - then "Manage Groups"
2. double-click "vboxusers" then check your account in there
3. Click Add > enter group name: "usb", group id: "85", check your account  in there too
4. Restart your computer

I have no idea what's up with the particular number "85" but it works...

---

