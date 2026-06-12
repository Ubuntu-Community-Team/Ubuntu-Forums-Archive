---
title: "cursor invisible after timeout and screen-saving"
date: 2016-04-20
forum: Ubuntu Development Version
---

### Post by sudodus on 2016-04-20
During isotesting I found a new bug in [my 'main testing machine'](http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/), when I left a brand new ***Lubuntu Xenial final i386 installed system*** for a while. After the screen-saver kicked in, and I activated it again, there was no cursor on the screen, (when unlocked).

But I can select things by moving to the bottom left corner (the colour of the menu button changes), 'it is there' but invisible.

The cursor appears again after logout.

It is not a temporary glitch because I can repeat it (in that computer).

1. Please check if your computer is affected too.

2. I have no idea how to report this bug. What package should be blamed?

[hr][/hr]
***Edit:*** This bug is reported as [Bug #1572640 'cursor invisible after timeout and screen-saving'](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1572640)

It might be the same bug, but I'm not sure. It is strange, that it only affects systems made from Lubuntu Xenial Alternate, not from Lubuntu Xenial desktop. Maybe it will be considered a duplicate, maybe not.

---

### Post by sudodus on 2016-04-20
This bug does not affect the live session (I tested in the same computer and in another one).

I will check if it affects the amd64 version ...

---

### Post by sudodus on 2016-04-20
When installed from the ***Lubuntu alternate*** ISO files, the default systems are affected by this bug:

After time-out the screensaver kicks in and the user is locked out. At the unlock screen the cursor is visible, but after unlock the cursor is invisible. This bug does not affect the corresponding desktop ISO files, neither the live session nor the default installed systems. See the table below.

***ISO files:*** The Lubuntu Xenial final version dated 20160419

[b]xenial-alternate-i386.iso
xenial-desktop-i386.iso
xenial-alternate-amd64.iso
xenial-desktop-amd64.iso[/b]

***Links to the computer specs:*** [Toshiba](http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/), [Lenovo](https://shop.lenovo.com/ISS_Static/ww/wci/products/us/laptop/thinkpad/x-series/x131e-intel/X131e-Datasheet-Intel.pdf)

[table="class: grid"]
[tr]
	[td]ISO file type \ computer[/td]
	[td]Toshiba[/td]
	[td]Lenovo[/td]
[/tr]
[tr]
	[td]alternate i386[/td]
	[td][COLOR="#cc0000"]cursor hidden[/COLOR][/td]
	[td][COLOR="#cc0000"]cursor hidden[/COLOR][/td]
[/tr]
[tr][hr][/hr]

***Edit:*** This bug is reported as [Bug #1572640 'cursor invisible after timeout and screen-saving'](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1572640)

It might be the same bug, but I'm not sure. It is strange, that it only affects systems made from Lubuntu Xenial Alternate, not from Lubuntu Xenial desktop. Maybe it will be considered a duplicate, maybe not.
	[td]desktop i386[/td]
	[td]OK[/td]
	[td]OK[/td]
[/tr]
[tr]
	[td]alternate amd64[/td][hr][/hr]

***Edit:*** This bug is reported as [Bug #1572640 'cursor invisible after timeout and screen-saving'](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1572640)

It might be the same bug, but I'm not sure. It is strange, that it only affects systems made from Lubuntu Xenial Alternate, not from Lubuntu Xenial desktop. Maybe it will be considered a duplicate, maybe not.
	[td][COLOR="#cc0000"]cursor hidden[/COLOR][/td]
	[td][COLOR="#808080"](not tested)[/COLOR][/td]
[/tr]
[tr]
	[td]desktop amd64[/td]
	[td]OK[/td]
	[td]OK[/td]
[/tr]
[tr]
	[td]live[/td]
 	[td]OK[/td]
	[td]OK[/td]
[/tr]
[/table]

The cursor appears again after logout and stays after login.

This bug is similar to or the same as [Bug #1568604: Mouse cursor lost when unlocking](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1568604)

[hr][/hr]
***Edit:*** I have reported this bug as [Bug #1572640: cursor invisible after timeout and screen-saving](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1572640)

It might be the same bug, but I'm not sure. It is strange, that it only affects systems made from Lubuntu Xenial Alternate, not from Lubuntu Xenial desktop. Maybe it will be considered a duplicate, maybe not.

---

### Post by sammiev on 2016-04-23
> **sudodus said:**
> When installed from the ***Lubuntu alternate*** ISO files, the default systems are affected by this bug:

After time-out the screensaver kicks in and the user is locked out. At the unlock screen the cursor is visible, but after unlock the cursor is invisible. This bug does not affect the corresponding desktop ISO files, neither the live session nor the default installed systems. See the table below.

***ISO files:*** The Lubuntu Xenial final version dated 20160419

[b]xenial-alternate-i386.iso
xenial-desktop-i386.iso
xenial-alternate-amd64.iso
xenial-desktop-amd64.iso[/b]

***Links to the computer specs:*** [Toshiba](http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/), [Lenovo](https://shop.lenovo.com/ISS_Static/ww/wci/products/us/laptop/thinkpad/x-series/x131e-intel/X131e-Datasheet-Intel.pdf)

[table="class: grid"]
[tr]
	[td]ISO file type \ computer[/td]
	[td]Toshiba[/td]
	[td]Lenovo[/td]
[/tr]
[tr]
	[td]alternate i386[/td]
	[td][COLOR="#cc0000"]cursor hidden[/COLOR][/td]
	[td][COLOR="#cc0000"]cursor hidden[/COLOR][/td]
[/tr]
[tr][hr][/hr]

***Edit:*** This bug is reported as [Bug #1572640 'cursor invisible after timeout and screen-saving'](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1572640)

It might be the same bug, but I'm not sure. It is strange, that it only affects systems made from Lubuntu Xenial Alternate, not from Lubuntu Xenial desktop. Maybe it will be considered a duplicate, maybe not.
	[td]desktop i386[/td]
	[td]OK[/td]
	[td]OK[/td]
[/tr]
[tr]
	[td]alternate amd64[/td][hr][/hr]

***Edit:*** This bug is reported as [Bug #1572640 'cursor invisible after timeout and screen-saving'](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1572640)

It might be the same bug, but I'm not sure. It is strange, that it only affects systems made from Lubuntu Xenial Alternate, not from Lubuntu Xenial desktop. Maybe it will be considered a duplicate, maybe not.
	[td][COLOR="#cc0000"]cursor hidden[/COLOR][/td]
	[td][COLOR="#808080"](not tested)[/COLOR][/td]
[/tr]
[tr]
	[td]desktop amd64[/td]
	[td]OK[/td]
	[td]OK[/td]
[/tr]
[tr]
	[td]live[/td]
 	[td]OK[/td]
	[td]OK[/td]
[/tr]
[/table]

The cursor appears again after logout and stays after login.

This bug is similar to or the same as [Bug #1568604: Mouse cursor lost when unlocking](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1568604)

[hr][/hr]
***Edit:*** I have reported this bug as [Bug #1572640: cursor invisible after timeout and screen-saving](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1572640)

It might be the same bug, but I'm not sure. It is strange, that it only affects systems made from Lubuntu Xenial Alternate, not from Lubuntu Xenial desktop. Maybe it will be considered a duplicate, maybe not.

Hi,

I added myself to this bug as well. 

Thanks

---

