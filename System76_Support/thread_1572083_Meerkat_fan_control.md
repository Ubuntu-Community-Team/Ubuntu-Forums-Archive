---
title: "Meerkat fan control"
date: 2010-09-10
forum: System76 Support
---

### Post by tonyyarusso on 2010-09-10
I'm running Ubuntu Server 10.04 on a first-generation Meerkat.  It seems like the CPU fan always runs at top speed, and I'd like to change that.  With the 2.6.32 kernel I am able to get CPU temperatures from lm-sensors with the 'coretemp' module, and sensors-detect thought it found a suitable one for fan speed:
```
Driver `smsc47m1':
  * ISA bus, address 0x680
    Chip `SMSC LPC47M15x/192/997 Super IO Fan Sensors' (confidence: 9)
```
However, the smsc47m1 module fails to load.  dmesg notes:
```
[    4.248984] smsc47m1: Found SMSC LPC47M15x/LPC47M192/LPC47M997
[    4.249175] ACPI: resource smsc47m1 [0x680-0x6ff] conflicts with ACPI region RTIO [0x680-0x6ff]
[    4.249183] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
```
This then leads to pwmconfig saying "There are no pwm-capable sensor modules installed".

What do I need to do to be able to control the fan speed on this system?

---

### Post by tonyyarusso on 2010-09-10
Found this in an old thread - turned out to be correct:

> Background: The board supports to fans: The CHIPSET-Fan and the CHASSIS-Fan. According to the specification of the board only the CHASSIS-Fan may run at variable speed. But the fan is connected to the header which only runs at full speed. So all we have to do is to plug the fan in to the other header - the rest is straight forward. 

---

