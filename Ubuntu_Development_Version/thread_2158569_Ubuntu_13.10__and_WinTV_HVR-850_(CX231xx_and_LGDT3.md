---
title: "Ubuntu 13.10  and WinTV HVR-850 (CX231xx and LGDT3350)"
date: 2013-06-29
forum: Ubuntu Development Version
---

### Post by mtbdrew on 2013-06-29
Hello,

I have the a USB WinTV HVR-850 by Hauppauge. This version has the LGDT3305 and the cx231xx, lsusb shows it as 2040:b140 Hauppauge.

With Ubuntu 12.04 the xc5000 and v4l-dvb firmwares had to be installed to get it to detect and work correctly. Now with Ubuntu 13.10 things are a little different. I've installed v4l-utils and v4l2ucp as well as the xc5000 firmware package.

dmesg | grep -i lg shows this:
usb 1-2: DVB: registering adapter 2 frontend 0 (LG Electronics LGDT3305 VSB/QAM Frontend

dmesg | grep -i firmware shows the device is using this firmware:
cx25840 6-0044: loaded v4l-cx23885-avcore-01.fw firmware (16382 bytes)

Randomly it will give and error message that the xc5000 firmware failed to download. However this does not appear to affect the operation of the tuner in anyway.

The main issue I'm having is with the cx231xx device after opening a closing MythTV frontend. Before launching frontend dmesg messages for this device are fairly clean as seen in the following attachment:
[ATTACH]244262[/ATTACH]

After launching the frontend and playing a file the same dmeg | grep -i cx231xx commands shows a different output, afterwards the is serious of messages added to the end.
[ATTACH]244261[/ATTACH]

How do I go about reporting this bug and who would it be reported too?

---

### Post by grahammechanical on 2013-06-29
Bug reporting? Here is how to do it.

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Do you get a system crash report? If not you will need to indentfy the package that is causing this problem. The forum has a section set aside for Mythbuntu

[http://ubuntuforums.org/forumdisplay.php?f=301](http://ubuntuforums.org/forumdisplay.php?f=301)

As for the serious message at the end of dmseg_post.txt it would have been more helful if you had explained what was so serious about it. Those readouts mean nothing to me. The problem may be happening on 13.10 but it still may be a Mythbuntu issue. Does it affect the ability to use the device as you are able to use it?

Regards.

---

### Post by mtbdrew on 2013-07-01
Sorry meant to say, series of messages occur. Often they will repeat for several pages of dmesg.

No crash and not sure what package would be used for this hardware other than the firmware modules. So how do I isolate the package for this particular hardware in order to run the bug report?

BTW this is regular Ubuntu that I added MythTV to not the Mythbuntu install.

---

