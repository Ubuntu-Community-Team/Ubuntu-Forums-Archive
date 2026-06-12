---
title: "Preparing a Proliant 1600 for Ubuntu installation"
date: 2008-11-16
forum: Server Platforms
---

### Post by Aethylred on 2008-11-16
[SIZE="5"]Ubuntu on a Compaq Proliant 1600[/SIZE]

[SIZE="4"]Introduction[/SIZE]
The Compaq Proliant 1600 was a top-of-the-line server circa 1999, and though it&#8217;s quite obsolete by today standards, it still suite some infrastructure roles due to its reliability and robust nature. Occasionally fully kitted out units can be found at bargain prices. At max specs a Compac Proliant 1600 will have 2 x 600Mhz Intel Pentium 3 processors, 1GB ECC RAM, and 5 x 18.6GB wide SCSI drives. This document will cover configuring this specification (because I have one).

[SIZE="4"]Preparation[/SIZE]
Power up your Proliant and check that you have everything you need (e.g. PS2 keyboards!), check that it runs and everything seems ok. In particular check that the SCSI cables are not crimped or pinched by the case. Then perform a complete system erase and reconfigure it for running Linux.

[SIZE="3"]Obtain Compaq SmartStart and Firmware CDs[/SIZE]
[LIST=1]
[*]Download Compaq SmartStart for the Proliant 1600 from the HP support site. SmartStart 5.50 was the last version to support the Proliant 1600.
[*]Download the Firmware Maintenance 7.30 CD for the Proliant 1600 support site
[*]Burn the ISOs to CD
[/LIST]

[SIZE="3"]Perform a full System Erase[/SIZE]
**NOTE:** This will erase all data from the server!
**NOTE:** The server can take some time to boot up again after a System Erase, give it at least 10 minutes before trying to solve the issue. It is also normal for the Server to reboot itself a few times during configuration.
**NOTE:** After a full system erase it is normal to see some error messages on boot up, for example:
[LIST]
[*]172-System Configuration Nonvolatile Memory Invalid
[*]172-1 Configuration Nonvolatile Memory Invalid
[*]162-System Options Not Set
[*]1785-Slot 4 Drive Array Not Configured
[/LIST]

[LIST=1]
[*]Insert the SmarStart CD into the Proliant and reboot
[*]When the SmartStart utilities load, select System Erase, this may take some time, up to 8 minutes per drive. Wait for it to complete.
[*]Eject the CD and power down the Proliant for at least 30 seconds before continuing
[/LIST]

[SIZE="3"]Reconfigure the Server for Linux[/SIZE]
[*]Insert the SmartStart CD into the Proliant and boot it up. You may need to press F1 to continue after boot-up errors caused by a system erase
[LIST=1]
[*]Once the SmartStart utilities have loaded select an appropriate language
[*]Set the date and time when prompted
[*]Click on Continue in the System Configuration Summary
[*]Click on the I Agree check box and then Continue to accept the licensing agreement
[*]Select Manual Configuration and then click on the Begin to start manual system configuration
[*]In the Operating System Selector select Linux (you may need to select a specific kernel version) and then click on Next
[*]The configuration utility will begin to set up the Proliant for running Linux, accept the default settings for any further prompts until the server reboots and loads the Array Configuration Utility loads
[/LIST]

[SIZE="3"]Configure the Array Controller[/SIZE]
[LIST=1]
[*]Boot the Proliant up with the SmartStart CD and select the Array Configuration Utility (if it has not already booted up to this utility)
[*]Your operating system should already be selected
[*]Configure your RAID settings (RAID 5, with 1 online spare is recommended for most applications) and click on Next
[*]Click on Save Configuration Now to confirm these settings
[*]Click on Controller &#61664; Exit to exit the utility
[*]The server will now go through a few reboot cycles configuring the RAID controller, which may take some time.
[*]The server should now be ready to install Ubuntu
[/LIST]

[SIZE="3"]Kernel boot options[/SIZE]
In order to get the latest versions of Ubuntu to boot the following options will have to either be added at boot up, or permanently added to /boot/grub/menu.lst

```
noapic nolapic acpi=off
```

[SIZE="3"]Follow ups[/SIZE]
[LIST]
[*]Check to see if using F10 to enter Advanced Server configuration can be used to resolve ACPI/APIC issues
[*]Updating the server&#8217;s firmware with the Firmware Maintenance CD
[/LIST]

[SIZE="3"]References[/SIZE]
[http://h20000.www2.hp.com/bizsupport/TechSupport/Home.jsp?lang=en&cc=us&prodSeriesId=254906&prodTypeId=15351](http://h20000.www2.hp.com/bizsupport/TechSupport/Home.jsp?lang=en&cc=us&prodSeriesId=254906&prodTypeId=15351)
[http://www.cpqlinux.com/](http://www.cpqlinux.com/)
[http://www.cpqlinux.com/linux.html](http://www.cpqlinux.com/linux.html)
[http://www.cpqlinux.com/steps.html](http://www.cpqlinux.com/steps.html)

---

### Post by wstout on 2009-01-31
Thanks for the tutorial. I suppose I maybe getting in a little late on this, but to the best of my knowledge I have followed your tutorial and everything works great other than the mouse :) Have any ideas I have done some searching before I stumbled on your thread and seems its a common problem curious if/how you over came it?

---

### Post by Aethylred on 2009-02-01
> **wstout said:**
> Thanks for the tutorial. I suppose I maybe getting in a little late on this, but to the best of my knowledge I have followed your tutorial and everything works great other than the mouse :) Have any ideas I have done some searching before I stumbled on your thread and seems its a common problem curious if/how you over came it?

The Proliant requires genuine PS2 keyboard and mouse. Mine would not work with a USB-PS2 converter dongle thingamabob.

I bought one of these for NZ$20:

[http://www.gigabyte.com.tw/Products/Keyboard/Products_Spec.aspx?ProductID=2527](http://www.gigabyte.com.tw/Products/Keyboard/Products_Spec.aspx?ProductID=2527)

Which sorted out my problems.

---

### Post by wstout on 2009-02-01
Aethylred, thanks for the reply, I am actually using PS/2 mouse and keyboard. The mouse works fine with the Proliant set up stuff and also with Windows, but will not work with Ubuntu, or any other distro I have tried so far, what version of Ubuntu did you get working on it? I have swapped some mice around with the same results.

---

### Post by Aethylred on 2009-02-01
I'm currently running Ubuntu 8.04.1 Server LTS without the X GUI, i.e. console only interface.

---

### Post by wstout on 2009-02-01
Probably what i need to do anyway. I don't really need the GUI for my purposes either, just hate to have a problem I can't solve but i think I may chunk this one up to that and get on with it. Thanks for the help.

---

### Post by scruz on 2009-09-04
I'm a little late to the party, I know, but I found that you have to use nousb at boot up also in order for the boot to work with the latest BIOS (11/2000). It took me a little time, but I finally got it working after reading about it in the Fedora forums. :D

---

### Post by wstout on 2009-09-04
scruz, thanks for the word, I did try that but just never could get it to working, but the server has been running without issue for over 6 months now, without a mouse :)

---

