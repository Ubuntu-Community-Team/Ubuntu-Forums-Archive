---
title: "Xserver_1.13 in Xorg-edgers PPA"
date: 2012-08-01
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Harry33 on 2012-08-01
A git version of xserver_1.13 (2:1.12.99.903+git20120730.afa53fe7-0ubuntu0ricotz)  can be downloaded from Xorg-edgers PPA for QQ.
Also the necessrary other drivers (input and video) can be obtained from there.
And of course the correct nvidia-current_304.30 is also there.
These are built against the new xserver ABI: xorg-input-abi-18 and xorg-video-abi-13.

There is, however, something worng about the 3D I think.
I cannot login to gnome-shell. It crashes and system returns to the login screen.
However, gnome-panel (classic) works just fine, referring an issue with 3 D.

---

### Post by Harry33 on 2012-08-01
Still cannot start gnome-shell session, only gnome classic works.
I get the xsession error saying xserver resource temporarily unavailable.

---

### Post by Yahoé on 2012-08-01
Only Unity 2d works with Xserver_1.13, Unity 3d loops back to LightDM.
Removing nvidia-current 304.30 for now until this is fixed.

---

### Post by Harry33 on 2012-08-01
Well it would be interesting to see if the open source drivers (like xserver-xorg-video-ati) works with 3D desktops and xserver 1.13.

Here is the open source ati for xserver 1.13:
[https://launchpad.net/ubuntu/quantal/+source/xserver-xorg-video-ati/1:6.99.99~git20120713.6ef1ad6a-0ubuntu1]("https://launchpad.net/ubuntu/quantal/+source/xserver-xorg-video-ati/1:6.99.99%7Egit20120713.6ef1ad6a-0ubuntu1")

Nvidia claims that the proprietary driver 304.30 supports xserver 1.13 abi already.
[INDENT]> 
- Added support for xserver ABI 13 (xorg-server 1.13). 

- Fixed a bug that caused RRSetOutputPrimary requests to incorrectly  generate BadValue errors when setting the primary output to None.  This  caused [[COLOR=#234865][COLOR=#234865 !important][FONT=inherit !important][COLOR=#234865 ! important][FONT=inherit ! important]gnome[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.phoronix.com/scan.php?page=news_item&px=MTE1MDM#")-settings-daemon  to crash after changing the screen configuration in response to a  display hotplug or the display change hot-key being pressed. 

- Fixed a problem where RENDER Glyphs operations would exhibit  severe performance issues in certain cases, such as when used with  gradients by Cairo and Chromium. 

- Fixed a bug that caused X to hang when resuming certain  DisplayPort display devices (such as Apple brand mini-DisplayPort to  dual-link DVI adapters) from power-saving mode. 

- Added support for the following GPU: Tesla K10 

- Fixed a bug that caused an X screen to be extended to Quadro SDI  Output devices by default.  An X screen will still use an SDI Output  device if it is the only display device available.  To use a SDI Output  device on an X screen with other display devices available, include the  SDI Output device with either the "UseDisplayDevice" or "MetaMode" X [[COLOR=#234865][COLOR=#234865 !important][FONT=inherit !important][COLOR=#234865 !important][FONT=inherit !important]configuration [/FONT][/COLOR][COLOR=#234865 !important][FONT=inherit !important]options[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.phoronix.com/scan.php?page=news_item&px=MTE1MDM#"). 

- Updated X11 modeline validation such that modes not defined in a  display device's EDID are discarded if the EDID 1.3 "GTF Supported" flag  is unset or if the EDID 1.4 "Continuous Frequency" flag is unset.  The  new "AllowNonEdidModes" token for the ModeValidation X configuration  option can be used to disable this new check. 

- Fixed a bug, introduced in the 295.xx release series, with EDID  detection on some laptop internal panels.  This bug caused the laptop  internal panel to show six small copies of the desktop. 

- Added support for FXAA, Fast Approximate Anti-Aliasing.



[/INDENT]

---

### Post by Harry33 on 2012-08-01
QQ just got the fglrx_8.960

Here:
[https://launchpad.net/ubuntu/quantal/+source/fglrx-installer-updates/2:8.960-0ubuntu6](https://launchpad.net/ubuntu/quantal/+source/fglrx-installer-updates/2:8.960-0ubuntu6)

Note, that this driver is for xserver 1.12, not the proposed xserver 1.13.
Ati proprietary drivers do not support xserver 1.13 yet.

---

### Post by jfernyhough on 2012-08-01
8.960 is 12.4, which IIRC doesn't work with xserver 1.12.
edgers has 8.980 (which is 12.6) but I don't know if it's been patched to work with xserver 1.12... I guess I should try it. :D

---

### Post by Harry33 on 2012-08-02
> **jfernyhough said:**
> 8.960 is 12.4, which IIRC doesn't work with xserver 1.12.
edgers has 8.980 (which is 12.6) but I don't know if it's been patched to work with xserver 1.12... I guess I should try it. :D

OK, I haven't tested that.
However, the package is built against the xserver 1.12, though.

---

### Post by Harry33 on 2012-08-05
Just tested that not even the latest nvidia-current (in xorg-edgers PPA) v.304.32 beta works with 3D desktops if xserver 1.13 branch (like 1.12.99-*) is used.

---

### Post by ronacc on 2012-08-05
I had the same problem with the Nvidia driver from xorg-edgers , see this thread [http://ubuntuforums.org/showthread.php?t=2037526](http://ubuntuforums.org/showthread.php?t=2037526) reverting to nouveau fixed it .

---

