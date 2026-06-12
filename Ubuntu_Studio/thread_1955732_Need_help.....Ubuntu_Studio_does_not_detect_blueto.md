---
title: "Need help.....Ubuntu Studio does not detect bluetooth keyboard"
date: 2012-04-10
forum: Ubuntu Studio
---

### Post by nibbin on 2012-04-10
Installed a fresh copy of the Ubuntu Studio 11.10 on my system.

However to my dismay I realized that UBUNTU would not recognize the keyboard and mouse on starting.
It worked and was detected during installation. Works perfect in Windows 7.

I am used to Logitech MX5500 wireless keyboard mouse combo.
So I did away with my wired keyboard. I have no access to wired keyboard and I dont want to purchase one again.

I have a wired mouse
Is there anyway I can enable access to the bluetooth keyboard WITHOUT TYPING (coz unless the keyboard is detected I cant enter keystrokes)
Cant seem to find virtual keyboard in Ubuntu Studio.

Not able to use ubuntu at all since install :(:(

---

### Post by nibbin on 2012-04-10
SOLVED:
Found a work around this.....

Used wire mouse to login to the Ubuntu Studio as guest. (Guest acount would not allow me to start the Synaptic program)
Created new user account with Desktop user credential. Disabled password login for this. (Used character map program to key in text and admin password)
Logged off and logged into the newly created account.
Fired Synaptic and searched for OnScreen Keyboard app :lolflag:
Installed on Screen keyboard app and used it to search for blueman
Install blueman and other bluetooth utilities. 
Fire up the installed bluetooth console from settings menu.
Press the discovery button on the bluetooth dongle, click search on the manager.
The mouse and keyboard will be detected. Clicked on device => input service to enable. Added both to the trusted devices and viola.
Its working perfect now!

There might be other easier and faster way to get it working but this was one I found.
Excellent compilation of media apps on Ubuntu Studio..... love it!
Going to use it for mainstream work! Thx fellas

---

