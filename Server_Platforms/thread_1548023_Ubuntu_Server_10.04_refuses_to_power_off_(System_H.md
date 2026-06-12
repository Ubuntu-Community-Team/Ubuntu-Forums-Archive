---
title: "Ubuntu Server 10.04 refuses to power off (System Halted)"
date: 2010-08-07
forum: Server Platforms
---

### Post by icevalley20 on 2010-08-07
Hi all,

I have an install of Ubuntu Server 10.04 on my server and am having power off issues.  When I issue the command **'sudo shutdown -P now'** the system powers the drives down and then sits with a message saying **'System Halted'**

I then have to physically press the power button to turn the machine off.  This is very frustrating as the server is headless and not located near to me.

My motherboard has had some problems in the past with fan speed control sensor so I have disabled these in the BIOS, could this be related to ACPI?

Anyone have any ideas?

---

### Post by CharlesA on 2010-08-07
It's related to ACPI. How old is the machine and is ACPI enabled in the BIOS?

---

### Post by kevinthecomputerguy on 2010-08-08
Try this command
sudo halt -p

---

### Post by icevalley20 on 2010-08-08
The machine is an older HP compaq with a** MS-677 V4.1 **motherboard inside.  The specs of the board can be found at [this link from HP's support site.]("http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=c00068983")

It is running the most up-to-date bios image avaliable from the site and the manual states that it does support **APCI**.  The fact that the fan control has gone faulty makes me think that maybe the **APCI** is also broken?  Not sure if the two are related?

The bios makes no specific mention of **APIC**, only **APCI**.  I have attached a screenshot below....

[[img]http://s4.postimage.org/umdK0.jpg[/img]](http://www.postimage.org/image.php?v=aVumdK0)

Running the command **'sudo halt -p'** gives me the same results

---

### Post by kevinthecomputerguy on 2010-08-08
Try going back to that bios screen and disable "S3". Reboot and try it all again .
-kev

---

### Post by icevalley20 on 2010-08-08
I've disabled the S3 in the BIOS, still the same result though :(

---

### Post by kevinthecomputerguy on 2010-08-08
Darn. That fixed one of mine.
Have u tried disabling that APCI?

Looks like a typo for ACPI .

Also do you have any peripherals plugged in? Like USB hard drives or firewire or printers? Anything bus powered ?
U could try removing those. Then trying again .
Also. Maybe reset your bios to the defaults. Maybe there is wack setting somewhere .
-kev

---

### Post by icevalley20 on 2010-08-08
The APIC is actually something different so I don't think that is going to have any effect, I tried disabling it anyway just to see but still nothing :(

The only thing I have plugged in is a network cable, power and a VGA lead.

I have also tried resetting to factory defaults but this still has no effect.

---

### Post by icevalley20 on 2010-08-09
I have tried the suggestion from [http://www.understated.co.uk/2004/automatic-shutdown-in-ubuntu/](http://www.understated.co.uk/2004/automatic-shutdown-in-ubuntu/) and placed the command 

**apm power_off=1**
 

in** /etc/modules**


Rebooted but still same problem :(

---

### Post by CharlesA on 2010-08-10
Does it power off automatically if you use a different OS? Like a Debian livecd, or even a CentOS live cd?

TBH, I don't see anything in the BIOS that would let it power off automatically. Looked up what [APIC]("http://en.wikipedia.org/wiki/Advanced_Programmable_Interrupt_Controller") is and it's definitely not related to power management.

---

