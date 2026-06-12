---
title: "Suspend when pushing Power Button"
date: 2009-11-16
forum: Server Platforms
---

### Post by GriFF3n on 2009-11-16
Running Ubuntu Server 9.10 and trying to get the computer to go into suspend when I push the power button on the front of the computer. Installed pm-utils and "pm-suspend" does work. I have no gui on this system so the setting will have to be changed via command line. Anyone have any idea how to do this? Thanks,

GriFF

---

### Post by GriFF3n on 2009-11-16
Was able to fix this. 

1. Install acpid, pm-suspend
2. edit "/etc/acpi/events/powerbtn" to say;

```
# /etc/acpi/events/powerbtn
# This is called when the user presses the power button and calls
# /etc/acpi/powerbtn.sh for further processing.

# Optionally you can specify the placeholder %e. It will pass
# through the whole kernel event message to the program you've
# specified.

# We need to react on "button power.*" and "button/power.*" because
# of kernel changes.

event=button[ /]power
#action=/etc/acpi/powerbtn.sh 
**action=/usr/sbin/pm-suspend**
``` 

3. Reboot

Now everything works as it should...:p

GriFF

---

### Post by cariboo on 2009-11-17
How do you get the server to start up again when you need it, without having to press the power button again?

---

### Post by fkjensen on 2009-12-02
> **GriFF3n said:**
> 
Was able to fix this. 
 
1. Install acpid, pm-suspend
2. edit "/etc/acpi/events/powerbtn" to say;
 
```
# /etc/acpi/events/powerbtn
event=button[ /]power
#action=/etc/acpi/powerbtn.sh 
**action=/usr/sbin/pm-suspend**
``` 

 
Works like a charm, thank you. :D 
 
Now to expand it a bit:
I would like the ability to suspend and power down (properly) by pushing buttons (power button (short/long push) and/or reset). Can this be done? I.e.:
- Short push on power button (or short push on reset button) => suspend
- Long push on power button (or short push on power button) => power off
 
~Frank

---

### Post by Wamiduku on 2010-04-01
> **fkjensen said:**
> I would like the ability to suspend and power down (properly) by pushing buttons (power button (short/long push) and/or reset). Can this be done?
Did you find the answer? I'd like to know too.

---

### Post by wirespot on 2013-02-17
> **fkjensen said:**
> I would like the ability to suspend and power down (properly) by pushing buttons (power button (short/long push) and/or reset). Can this be done? I.e.:
- Short push on power button (or short push on reset button) => suspend
- Long push on power button (or short push on power button) => power off

Long push on power button is usually handled by the BIOS. There should be a setting in BIOS (perhaps under the "power" or "ACPI" settings), which says how long you have to push it to power-off. There's usually a setting of 2-4 seconds.

So yeah, it's possible to get what you want.

---

