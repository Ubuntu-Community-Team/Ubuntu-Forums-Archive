---
title: "Determining CPU temperature?"
date: 2015-09-15
forum: Ubuntu/Debian BASED
---

### Post by G33shooter on 2015-09-15
I'm having trouble figuring out my CPU temperature and was hoping someone on this forum could help.  Here is what I have done so far:

I've installed ```
lm-sensors
```  I ran ```
sensors-detect
``` and said yes to each question.  Here is the result:

```
# sensors-detect revision 6170 (2013-05-20 21:25:22 +0200)
# Board: Gigabyte Technology Co., Ltd. F2A88XM-D3H

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): yes
Module cpuid loaded successfully.
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
AMD Family 12h and 14h thermal sensors...                   No
AMD Family 15h thermal sensors...                           No
AMD Family 15h power sensors...                             No
AMD Family 16h power sensors...                             No
Intel digital thermal sensor...                             No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): yes
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      Yes
Found unknown chip with ID 0x8620
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No

Some systems (mainly servers) implement IPMI, a set of common interfaces
through which system health data may be retrieved, amongst other things.
We first try to get the information from SMBIOS. If we don't find it
there, we have to read from arbitrary I/O ports to probe for such
interfaces. This is normally safe. Do you want to scan for IPMI
interfaces? (YES/no): yes
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): yes
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): yes
Using driver `i2c-piix4' for device 0000:00:14.0: AMD Hudson-2 SMBus
Module i2c-dev loaded successfully.

Next adapter: Radeon i2c bit bus 0x90 (i2c-0)
Do you want to scan it? (yes/NO/selectively): yes

Next adapter: Radeon i2c bit bus 0x91 (i2c-1)
Do you want to scan it? (yes/NO/selectively): yes

Next adapter: Radeon i2c bit bus 0x92 (i2c-2)
Do you want to scan it? (yes/NO/selectively): yes

Next adapter: Radeon i2c bit bus 0x93 (i2c-3)
Do you want to scan it? (yes/NO/selectively): yes

Next adapter: Radeon i2c bit bus 0x94 (i2c-4)
Do you want to scan it? (yes/NO/selectively): yes

Next adapter: Radeon i2c bit bus 0x95 (i2c-5)
Do you want to scan it? (yes/NO/selectively): yes
Client found at address 0x4a
Probing for `National Semiconductor LM75'...                No
Probing for `National Semiconductor LM75A'...               No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `National Semiconductor LM77'...                No
Probing for `Analog Devices ADT7410/ADT7420'...             No
Probing for `Analog Devices ADT7411'...                     No
Probing for `Maxim MAX6642'...                              No
Probing for `National Semiconductor LM73'...                No
Probing for `National Semiconductor LM92'...                No
Probing for `National Semiconductor LM76'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Probing for `NXP/Philips SA56004'...                        No
Client found at address 0x4b
Probing for `National Semiconductor LM75'...                No
Probing for `National Semiconductor LM75A'...               No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `National Semiconductor LM77'...                No
Probing for `Analog Devices ADT7410/ADT7420'...             No
Probing for `Analog Devices ADT7411'...                     No
Probing for `Maxim MAX6642'...                              No
Probing for `National Semiconductor LM92'...                No
Probing for `National Semiconductor LM76'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Probing for `NXP/Philips SA56004'...                        No
Probing for `Analog Devices ADT7481'...                     No

Next adapter: Radeon i2c bit bus 0x96 (i2c-6)
Do you want to scan it? (yes/NO/selectively): yes

Next adapter: Radeon i2c bit bus 0x97 (i2c-7)
Do you want to scan it? (yes/NO/selectively): yes

Next adapter: card0-DP-1 (i2c-8)
Do you want to scan it? (YES/no/selectively): yes

Next adapter: SMBus PIIX4 adapter at 0b00 (i2c-9)
Do you want to scan it? (YES/no/selectively): yes
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Client found at address 0x53
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: SMBus PIIX4 adapter at 0b20 (i2c-10)
Do you want to scan it? (YES/no/selectively): yes

Sorry, no sensors were detected.
Either your system has no sensors, or they are not supported, or
they are connected to an I2C or SMBus adapter that is not
supported. If you find out what chips are on your board, check
http://www.lm-sensors.org/wiki/Devices for driver status.

```

I then ran ```
sensors
``` 

 Here is the result:

```
radeon-pci-0100
Adapter: PCI adapter
temp1:        +43.0°C  (crit = +120.0°C, hyst = +90.0°C)

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +14.0°C  (high = +70.0°C)
                       (crit = +80.0°C, hyst = +79.0°C)
```

I am not sure if any of these reading are correct, and do not know for sure  what my temperature of my CPU is.  I am running a AMD x4 860k CPU  overclocked to 4.1 GHz with boost disabled and stock voltage of 1.356  VCORE.  Ram is 2133 (profile_1 enabled) Corsair Vengeance Pro 2x4GB.   GPU is Sapphire R9 270. Board is Gigabyte F2A88x-d3h.  I am also using a  Coolermaster Hyper Evo 212 on the CPU with a 92mm and 140mm intake fans  on the front of the case as well as 92mm and 140mm exhaust fans on back  and top of case. OS: elementary OS Freya. 

  My system seems to be running fine after 2 hours of gaming and no glitches or anything, but I really want to be able to check my CPU temperature  just to be sure I am not running my CPU at an unsafe temperature.  

Any advice?

---

### Post by QIII on 2015-09-16
*Moved to Ubuntu/Debian **BASED***

Your CPU temperature is listed in the section "k10temp-pci-00c3"

However, AMD does not report a physical temperature, but a value in Celsius on an arbitrary scale that "specifies the processor temperature relative to the point at which the system must supply the maximum cooling for the processor's specified maximum case temperature and maximum thermal power dissipation."

In other words, its effectively meaningless unless you are a motherboard determining how fast to spin the CPU fans.

In your case, you can see that the "temperature" indicated is sub-ambient, which makes no sense.

You might find [this article]("http://theleftcoastgeek.net/index.php/general-interest/5-lm-sensors-conky-and-amd-temperatures") on my blog to be of interest.

---

### Post by G33shooter on 2015-09-16
I read your article, thanks.  It mentioned in the lm-sensors wiki that if your cortemp is unrealistically low, you're probably far away from critical limit, so your system should be running fine.  If I cannot accurately find my temperature, with what I can see, would it be a safe bet to say my system is okay or is that a dangerous assumption?  Is the temp reading in my BIOS accurate at all?[COLOR=#000000][FONT=helvetica][/FONT][/COLOR]

---

### Post by QIII on 2015-09-16
BIOS isn't any more accurate.  It's how AMD processors report.

But, yeah.  With a temp that low you are certainly doing just fine.

---

### Post by G33shooter on 2015-09-16
Thank you for the quick reply and help!  Much appreciated.

---

