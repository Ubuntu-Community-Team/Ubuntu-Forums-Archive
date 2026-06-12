---
title: "Wine and Ubuntu 14.04LTS"
date: 2016-03-17
forum: Ubuntu, Linux and OS Chat
---

### Post by Dixie_Lou on 2016-03-17
I am NOT new to Ubuntu, Linux, Puppy or Mint, Fedora etc etc etc, but I am new to this forum, and I thank you all for all the help you have been.

I have made this observation using Ubuntu  over the years. Wine, and now Wine HQ seems to be getting better with age.

I have been able to run about all Windows Software in Wine HQ, but USB stuff that hooks to weird things takes more than I know.
Things like GPS toys, quad copters with Gui's and camera's with Windows specific hardware.

Any of you all get some of these things to work?

---

### Post by 6975 on 2016-03-17
In opposite I've been survive on Ubuntu/Debian based without any single drops of wine.

---

### Post by Lasakro on 2016-03-17
> **Dixie_Lou said:**
> ... but USB stuff that hooks to weird things takes more than I know.


I'm assuming that your Windows programs are looking for Com ports. If so the following should help if your programs are not self populating with com #'s. If they are this probably won't work. Over the past several days I've been trying to get 3 win Radio Scanner progrms working with wine. I've tested the following with both RS-232 direct and a TRENDnet TU_S9 USB to Serial Conterter (PL2303 chip) and doesn't need any of the included drivers installed. I'm 2/3rd's there. I was about to post my results here since they are very hard to find and came across your post.

                        [LEFT] 1) Add current user to the dialout group:
[/LEFT]

 sudo adduser <Your_User_Name_Here> dialout

[LEFT]2) Create symbolic link to the serial port:

 For RS-232 Run: ln -s /dev/ttyS0 ~/.wine/dosdevices/com1
 For USB to RS-232 Run: ln -s /dev/ttyUSB0 ~/.wine/dosdevices/com1

[LEFT] 3) Add serial port to the registry:

 Run: gedit ~/.wine/system.reg
 Add to file under the line &#8220;#arch=win32&#8221;:
[/LEFT]
[Hardware\\Devicemap\\Serialcomm] 1131331688
"COM1"="COM1"

Save, close and may need to reboot.

I'm also into AUAV's now using APM Planner with Ubuntu.Good luck and happy flying.






[/LEFT]

---

### Post by Dixie_Lou on 2016-03-18
Lasakro, thank you for the post, I will copy it and play with it. THANK YOU
My specific device I was referring to is the Blade 350QX3 GUI, it seems to open in Wine and looks good, just making the contact via USB looking cord to the quad copter seemed hopeless.
Truth I also need to add. If I can make all 4 of my devices work in Wine, I will reformat my drive without Windows of any version.
Garmin GPS (2) Base Camp and Express, only work in Microsoft Windows via Internet Explorer, specifically,. Garmin Express would not install in Windows until I plugged the GPS unit in to the USB port.
Pentax Camera (DONE) it works without Wine, Ubuntu has it's own software.

---

