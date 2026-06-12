---
title: "How To: Adjust or Save Brightness in Ubuntu (intel_backlight, acpi_video, setpci)"
date: 2013-07-14
forum: Tutorials
---

### Post by daniwaber on 2013-07-14
Brightness issues are some of the most common I ever found in Ubuntu. Either laptop brightness function keys don't work or brightness is reset to max at every boot. In case you are experiencing issues too,following are a few solutions I made for myself:

_***For the devices using [COLOR=#ff0000]acpi_video0[/COLOR] interface:***_
As tested on Dell Vostro 3360 (that uses acpi_video0 interface), the brightness can be changed by Function Keys, but is reset to full at every boot of Ubuntu. Follow these instructions:
Add the following bold line at the indicated place to /etc/rc.local (this can be done by running "sudo nano /etc/rc.local")
```
**chmod 666 /sys/class/backlight/acpi_video0/brightness**[FONT=arial]
exit 0[/FONT]
```
Download the binaries from here:
[rapidshare.com/files/3700090565/brightnessByDaniwaber2.zip]("http://rapidshare.com/files/3700090565/brightnessByDaniwaber2.zip")
After that, extract and copy all the files in the folder named "service" to a new folder named  “.brightn” placed in your home folder and add a refrence in startup to  it with the command as the full path to the executable file. You may need to fix  permissions for the file (Right click, click on Permissions and allow  the file to be run as executable)
The startup command must run as follows:
```
**./.brightn/service**
```
[U][I][B]
For the devices using [COLOR=#ff0000]intel_backlight[/COLOR] interface:[/B][/I][/U]
For devices that need intel_backlight, follow the same steps above, just replace "acpi_video0" in the rc.local step with "intel_backlight". Also, use these binaries instead:
[http://rapidshare.com/files/621358379/intelServDaniwaber.zip](http://rapidshare.com/files/621358379/intelServDaniwaber.zip)
Then follow the same steps, copying all files from "intelServ" instead.

_***For the devices using [COLOR=#ff0000]setpci[/COLOR] interface:***_
This is probably for devices where Function keys do not work and hence, there is no way to change the brightness (tested on Xubuntu 13.04 on Asus Eee PC 1015 CX). Extract the following binaries to the ".brightn" folder and add a startup refrence to the file named "start":
[http://rapidshare.com/files/4244361567/setpciBrightDaniwaber.zip](http://rapidshare.com/files/4244361567/setpciBrightDaniwaber.zip)
You also need a visudo exception to be added. This means that if you want to run a sudo command without password, run **"sudo visudo"** in terminal and add the bold line at the position indicated.
```
%sudo ALL=(ALL:ALL) ALL [B]
%YOURGROUP ALL=(ALL:ALL) NOPASSWD:/usr/bin/setpci[/B]
```
Replace YOURGROUP by your group name.
Now you can adjust (and save) the brightness by running **"./.bright/adjust**" in terminal or by running the "adjust" file.
My orignal thread is here: [http://ubuntuforums.org/showthread.php?t=2018560](http://ubuntuforums.org/showthread.php?t=2018560)

_***Please report any broken links.***_
Note: The attached source files are *Real Studio Projects* since I develop in real studio (now Xojo).

---

