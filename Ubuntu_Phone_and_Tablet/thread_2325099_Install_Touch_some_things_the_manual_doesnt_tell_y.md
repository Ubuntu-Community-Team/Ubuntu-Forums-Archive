---
title: "Install Touch: some things the manual doesnt tell you"
date: 2016-05-19
forum: Ubuntu Phone and Tablet
---

### Post by mringer on 2016-05-19
"the manual" is   

[https://developer.ubuntu.com/en/phone/devices/installing-ubuntu-for-devices/](https://developer.ubuntu.com/en/phone/devices/installing-ubuntu-for-devices/)

1. Getting adb to work. 

1a. Get a USB cable. Not as trivial as you might think because devices have 
micro USBs in different sizes. I bought a cable that fitted but it was faulty.

1b. Identify vendor & product ID. To do this, disconect and do

lsusb

then connect and    lsusb    again. You should see an extra line of output
(if your cable is good) that looks like this:

Bus bbb Device ddd ID vvvv:pppp something

where  vvvv  is the vendor ID and   pppp  the product ID. Note these for later.
(booby-trap: as of UB 14, the standard font does not clearly distinguish 1 
(digit one) from  l (letter ell). This Forum uses a better font)

1c. Create an  ini  file.  In your home directory:

mkdir .android
cd .android
echo  vvvv  > adb_usb.ini

(Some persons do and some do not advise putting   0x  before  vvvv  .  On my PC,
both work).

1d.  Create a  udev  rule. I do **not** know what the rule should say.
I can only say what worked for me. I looked in 

/lib/udev/rules.d/70-android-tools-adb.rules

and found this [extract]

ACTION=="add|change", SUBSYSTEM=="usb", \
  ATTRS{idVendor}=="2a47", \
  ATTRS{idProduct}=="0c01|0c02|2008", \
  TAG+="uaccess"

and changed it to:

ACTION=="add|change", SUBSYSTEM=="usb", \
  ATTRS{idVendor}=="vvvv", \
  ATTRS{idProduct}=="pppp", \
  MODE="0666", GROUP="plugdev"

 The backslash is a line continue. In order for  GROUP  to
work, you need to add the intended users to that group. 
When I  *deleted* the  TAG  line, adb suddenly started to 
work.

I believe that there are more things that are needed to 
get  adb  to work reliably. All I know is that it worked, 
then stopped, then restarted and I have no idea why.
During the non-working period, the product ID changed.

Also I would be very grateful if anybody could find me a
proper manual for adb.

 3. Backup and restore. The manual tells you to backup. This is obviously
good advice. But how do you restore if installing Touch fails? 
The restore manual is:

[https://developer.ubuntu.com/en/phone/devices/reinstalling-android/](https://developer.ubuntu.com/en/phone/devices/reinstalling-android/)

It starts:

[QUOTE]
At any time you can download the Android files needed to restore your system.
This table [below] displays links to common Android images:
[\QUOTE]

But what are you supposed to do if your tablet is not in the list?
In theory, the files needed to run Android must have been on the tablet 
before you started. So if the backup command was correct, they must 
all be in the backup file. But how do you get at them?

---

