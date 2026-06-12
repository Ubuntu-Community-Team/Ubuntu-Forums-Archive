---
title: "Lenovo Z510 Laptop &amp; Ubuntu"
date: 2014-06-29
forum: Ubuntu, Linux and OS Chat
---

### Post by bell1996 on 2014-06-29
Just wanted to post my experience with a new laptop I just purchased.

I heard a lot of good things about Lenovo so decided to take a chance and bought a Lenovo Z510. I installed Ubuntu 12.04 (I decided to go with 12.04 vs 14.04 because all my other devices are 12.04). I have NO regrets.

Lenovo Z510 Specs:

15.6" Display
Intel i7 Quad Core
8 GB RAM ---> Upgrade to 16GB
1 TB Hard Drive
Intel Graphics 4600
Broadcom Wireless 802.11b/g/n
CD-ROM
HDMI
VGA
Ethernet port
2-in-1 media reader
3 USB ports (2 @ 3.0 and 1 @ 2.0)
Web Cam
Back Lit Keyboard

With Ubuntu 12.04 every almost worked right out the box!!
All the function keys worked fine (except the F5, but I have no idea what it does)
Sound working fine. Wireless worked once I activated the addition hardware.
HDMI and VGA works just fine. Ethernet working.

Disappointments:
Only one. The wireless Broadcom card does not support dual band. So I can only scan for 2.4GHz SSIDs. I'll have to upgrade that one day some.
But for now, I'm using a DLINK DWA-171 USB to get the 5.0GHz SSIDs. 

Things not working:
I could find only one thing that does not work. The Bluetooth. I rarely use it. But it would be good to get it working.
It's low on my priority list. I'll post an update once I get it working.

Oh, also, when Ubuntu boots up the screen is black. Just increase the screen brightness. There's a fix posted for this.
I'll get that done and post my results.

Ok...got the brightness working on boot up.
It was a simple solution I found. Here's the link: [http://suhothayan.blogspot.com/2012/05/setting-brightness-at-ubuntu-startup.html](http://suhothayan.blogspot.com/2012/05/setting-brightness-at-ubuntu-startup.html)
Basically, i just created a bash script and put it in the startup applications. Simple and Easy!!

---

### Post by jeremy31 on 2014-06-30
I have a Lenovo G710 and I think the FN+F5 is the wifi kill button.  Your laptop might be like mine and have a whitelist- I attempted to use a different wifi/BT card and it wouldn't boot due to unauthorized hardware, mine shipped with an Atheros AR9485 wifi/BT

Black screen on 12.04 might be fixed with ```
acpi_backlight=vendor
``` in grub.  I think at one point I added a line to /etc/rc.local to set the brightness ```
echo 4500 > /sys/class/backlight/intel_backlight/brightness
```[COLOR=#000000][/COLOR]

---

### Post by slickymaster on 2014-06-30
Moved to the **Ubuntu, Linux and OS Chat** sub-forum since it's not a support question.

---

### Post by bell1996 on 2014-06-30
Jeremy31, I just looked what the F5 function key does on the Z510. The F5 "Refreshes the desktop or the currently active window". So, I guess, it's doing what the F5 key has always done. The F7 key on the Z510 enables/disables Airplane mode (unlike your G710).

---

### Post by bell1996 on 2014-06-30
So Jeremy31, are you saying you actually REPLACED you wifi/BT module in you laptop and it wouldn't recognize it?
Wow. Good to know. Because I was planning of ordering a "working" wifi/BT module and replacing myself.

---

### Post by jeremy31 on 2014-06-30
> **bell1996 said:**
> So Jeremy31, are you saying you actually REPLACED you wifi/BT module in you laptop and it wouldn't recognize it?
Wow. Good to know. Because I was planning of ordering a "working" wifi/BT module and replacing myself.

The laptop recognized that the wifi/BT wasn't the correct one and refused to boot, yours might be different. If you have another laptop with a different chip to try, I would try that before buying a new one

 I was wrong in the other post about the FN+F5, it still is just the refresh/reload button and Fn+F7 is the soft rfkill.

---

### Post by bell1996 on 2014-07-10
Ok, I was successful in upgrading from 8GB or RAM to 16GB!!!;)

But, let me tell you. It was no picnic. To get to the RAM on the Z510, you practically have to dismantal the entire laptop.
Not just remove the screws from the bottom panel, but also have to remove the keyboard. 

Helpful hints:
Have the right tools. To remove the bottom panel and keyboard you have to wedge it out. Use something plastic. Do not use anything metal. That'll just ruin the laptop.
If you can help it, do NOT remove the keyboad all the way. Just enought to get to the screws. If you remove the ribbons to the keyboard, they are a GIANT PAIN to put back on. Yes, this took me literally 45 minutes to do (just the ribbons!!).

But in the end I was successful.

---

### Post by Dragan_Saraginov on 2014-11-28
Hey Bell not sure that this will help you from this point in time :) but there is a simple solution to put BT to work. 

For some reason Ubuntu OS (reason known to Canonical) does not have support for the [FONT=Arial, Tahoma, Helvetica, FreeSans, sans-serif]BCM43142, the firmware is missing. There are two solutions for the problem :)) one is to find already pre-built hcd file ([/FONT][FONT=Courier New]fw-105b_e065.hcd[/FONT][FONT=Arial, Tahoma, Helvetica, FreeSans, sans-serif]) and the other is to find a Windows firmware (hex file) and convert it for Linux to understand it.

[/FONT][FONT=Arial][FONT=Courier New]hex2hcd BCM43142A0_001.001.011.0161.0172.hex fw-105b_e065.hcd[/FONT][/FONT]

When done with file, just put it into /lib/firmware then reboot... Voila BT is working after reboot.

I hope this helps someone who is having problems to get BT working on IdeaPad laptops. Tested on Z510 and G510 :)

---

### Post by bell1996 on 2014-11-30
Dragan_Saraginov that's for the suggestion on getting the BT working. I went ahead and executed the command below (copy and paste from your post):

hex2hcd BCM43142A0_001.001.011.0161.0172.hex fw-105b_e065.hcd

and I got:

hex2hcd: command not found

I would LOVE to get the BT working. Any other suggestions??

---

### Post by /ADM on 2014-12-01
> **bell1996 said:**
> Dragan_Saraginov that's for the suggestion on getting the BT working. I went ahead and executed the command below (copy and paste from your post):

hex2hcd BCM43142A0_001.001.011.0161.0172.hex fw-105b_e065.hcd

and I got:

hex2hcd: command not found

I would LOVE to get the BT working. Any other suggestions??

Get hex2hcd from it's github repo, build it then you can execute the command.  It's not packaged with Ubuntu by default.

---

