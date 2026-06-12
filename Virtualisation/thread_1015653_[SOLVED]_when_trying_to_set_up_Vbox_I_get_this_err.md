---
title: "[SOLVED] when trying to set up Vbox I get this error"
date: 2008-12-19
forum: Virtualisation
---

### Post by nakama85 on 2008-12-19
```

Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.


Result Code: 
NS_ERROR_FAILURE (0x00004005)
Component: 
Host
Interface: 
IHost {f39438d7-abfd-409b-bc80-5f5291d92897}
Callee: 
IMachine {ea6fb7ea-1993-4642-b113-f29eb39e0df0}

```

What should I do. I know I downloaded the personal use addition.

any ideas

---

### Post by Michael.Godawski on 2008-12-19
hey,

try to add this line into your fstab file

```
#usbfs
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
```

---

### Post by HotShotDJ on 2008-12-19
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
none	/proc/bus/usb	usbfs	devgid=1001,devmode=664	0	0
```
[*]IMPORTANT: Replace 1001 with the Group ID number that you wrote down earlier.
[*]Save the edited file (File -> Save) and then exit gedit.
[*]Reboot your system
[*]Make sure you've enabled USB Controller in VirtualBox
[*]Enjoy USB goodness in VirtualBox
[/LIST]

---

### Post by Surabhi123 on 2009-01-01
Thank you...
this solved the problem for me too :):D

---

