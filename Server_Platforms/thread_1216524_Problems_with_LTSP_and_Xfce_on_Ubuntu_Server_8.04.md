---
title: "Problems with LTSP and Xfce on Ubuntu Server 8.04"
date: 2009-07-18
forum: Server Platforms
---

### Post by Avinash.Rao on 2009-07-18
Dear All,

I have installed Ubuntu Server 8.04 and Xfce Desktop for LTSP on Sun Fire X4150 server hardware.

I am doing the below to test LTSP. To begin with, On the server, I made the changes required on the desktop with regards to shortcuts, adding and deleting things from the panel. I copied the .config directory .bashrc and .profile file to /etc/skel directory. Created a user account to check if the desktop profile was copied. When i logged in locally on the server, everything seems to be ok but this what happened when i logged in from the network using LTSP.

1) When the LTSP user logs in from the network, the shortcuts created on the desktop doesn't come up. I had created a shortcut on the desktop to applications like Openoffice and Xfce Terminal, but they dont appear. But, the shortcuts created on the panel appears. I tested this for multiple users but the problem persists.

2) If the LTSP users opens Xfce Terminal, Xfce crashes it just logs off and the display comes back to login screen. I found a Fix for this at [http://tillamookrage.blogspot.com/20...crash-fix.html](http://tillamookrage.blogspot.com/20...crash-fix.html) but the DefaultDepth entry in my Xorg.conf doesn't exist at all.
But strangely, this doesn't happen on the server, it happens only for a LTSP user?

3) The Display driver entry in /etc/X11/xorg.conf is as below, how do i configure xorg to use the proper Display driver.
I searched a lot but i didn't find the modules or drivers for Sun Fire X4150 server for Ubuntu?

Section "Device"
Identifier "Configured Video Device"
EndSection

4) External USB Drives are not detected on LTSP client. But they work on the Server without any problems.

Strangely, i didn't face any such problem with Gnome, I like Xfce, but it is crucial that LTSP should work without any problems. Is anybody using LTSP with Xfce

Please help
Avinash

---

### Post by openstep on 2010-06-30
Hi,

I am using xfce 4.6.1 with ubuntu 10.04 in an LTSP env. 
Problem  is that when I plug in an usb stick on the server the client also sees  it popping up, but when I plug one in on the client it doesn not come  up.

Do you have any solution?

Thanks, Csaba

---

