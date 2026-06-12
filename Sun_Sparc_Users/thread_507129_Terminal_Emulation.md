---
title: "Terminal Emulation"
date: 2007-07-22
forum: Sun Sparc Users
---

### Post by stuartbh on 2007-07-22
Ubuntu users/admins:

I booted Ubuntu 7.04 to assert installation on an E450 via the serial console.

I had a serial/usb cable plugged into the PowerBook (Mac) with an appropriate cable to the E450 serial port, which displayed all the text with no problem...until...the installations screens came along!

As soon as the install screens started to draw all of a sudden I got "high bit characters"

Here is the terminal script I used to do emulation:

tell application "Terminal"
	do script with command "screen /dev/tty.usbserial"
	set number of rows of window 1 to 100
	set number of columns of window 1 to 80
	set background color of window 1 to "black"
	set normal text color of window 1 to "green"
	set custom title of window 1 to "SerialOut"
end tell


Thanks,

Stuart, N3GWG

---

