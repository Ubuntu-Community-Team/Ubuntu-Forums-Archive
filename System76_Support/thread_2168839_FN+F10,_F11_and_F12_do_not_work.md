---
title: "FN+F10, F11 and F12 do not work"
date: 2013-08-19
forum: System76 Support
---

### Post by Thiudans on 2013-08-19
Greetings,

I am running openSUSE 12.3 (I know, I know....) with kernel version 3.10.6-22. In the past all the function keys worked, and I am not 100% sure when they stopped working. I am on a System76 Gazelle Professional--gazp8.

When I run XEV from the terminal, the keys for turning on the camera, wireless and Bluetooth seem to be inactive, i.e. there is no indication the X servers is receiving anything from the keyboard. The other FN keys work fine, and I see output from XEV. There is an exception, though; the screen brightness keys work, but the "increase" brightness key (FN+F9) does not send any codes if the brightness is maximized, and the decrease brightness key (FN+F8) does not send any codes when the brightness is minimized. So the driver is aware of the state of the device it attempts to control and does not send unnecessary key codes.

I am guessing this is a keyboard driver issue, but I am not sure how to proceed. It is possible I need a new kernel driver, but I am not sure. 

BTW, no key codes with "showkey" even with X stopped.

---

### Post by isantop on 2013-08-20
The keys are tied to the hardware, so it's normal for there not to be any output from showkey or XEV. They never make it to the OS. 

Is the hardware (e.g. the Camera for F10) toggling on or off?

---

### Post by Thiudans on 2013-08-20
The hardware does not toggle. The camera toggles, but not the wifi or Bluetooth. I can toggle wlan0 via Network Manager and nmcli, and none of the methods of enabling Bluetooth seem to work. I also verified the kernel modules are enabled for wifi and Bluetooth.

Bluetooth seems to be inaccessible. I even enabled Bluetooth in the BIOS, but the BIOS says to remember the last state, which is off. ;-) And it seems to me that you are saying that the keys are more like hardware switches than software switches?

---

### Post by isantop on 2013-08-21
They are hardware switches. If you're still not seeing the hardware enable, then there are problems with the kernel you have installed.

---

### Post by Thiudans on 2013-08-21
OK, I thought you said the OS does not see the key strokes. I thought the kernel ***is*** the OS. So the kernel ***does*** see the key strokes, it just doesn't respect them. :-/

Anyway, in the System76 driver changelog I see:

"System76 Driver

System76, Inc.
Copyright System76, Inc.
Released under the GNU General Public License version 2 (See LICENSE)

Version 3.2.7

1.) Fix wireless and bluetooth hotkey bug on the lemu4
    panp9, gazp7, gazp8 in Ubuntu 13.04"

Unfortunately, I could not locate where these particular fixes are in the package.

> **isantop said:**
> They are hardware switches. If you're still not seeing the hardware enable, then there are problems with the kernel you have installed.

---

