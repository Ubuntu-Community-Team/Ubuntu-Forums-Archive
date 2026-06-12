---
title: "lm-sensors issue."
date: 2012-07-06
forum: Server Platforms
---

### Post by d4m1r on 2012-07-06
Hey guys, so I need something to monitor the temperature of my Ubuntu server and while doing research on this, **lm-sensors** came up. Basically I installed it like the guide said and proceeded to set up the sensors/detect them, but the process failed...Despite detecting my machine and a sensor or two (although it did say "No" to most things). See below for the log, does anyone know why the below occurred? Anyway to work around it? :confused:

```
damir@server3:~$ sudo sensors-detect
# sensors-detect revision 5946 (2011-03-23 11:54:44 +0100)
# System: Dell Computer Corporation OptiPlex GX150

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): YES
Module cpuid loaded successfully.
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
AMD Family 12h and 14h thermal sensors...                   No
Intel digital thermal sensor...                             No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): YES
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   Yes
Found `Nat. Semi. PC87364 Super IO Fan Sensors'
    (but not activated)
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No

Some systems (mainly servers) implement IPMI, a set of common interfaces
through which system health data may be retrieved, amongst other things.
We first try to get the information from SMBIOS. If we don't find it
there, we have to read from arbitrary I/O ports to probe for such
interfaces. This is normally safe. Do you want to scan for IPMI
interfaces? (YES/no): YES
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): YES
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): YES
Using driver `i2c-i801' for device 0000:00:1f.3: Intel 82801BA ICH2
Module i2c-i801 loaded successfully.
Module i2c-dev loaded successfully.

Next adapter: SMBus I801 adapter at dcd0 (i2c-0)
Do you want to scan it? (YES/no/selectively): YES
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No
Client found at address 0x51
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)

Sorry, no sensors were detected.
Either your system has no sensors, or they are not supported, or
they are connected to an I2C or SMBus adapter that is not
supported. If you find out what chips are on your board, check
http://www.lm-sensors.org/wiki/Devices for driver status.

```

---

### Post by d4m1r on 2012-07-06
50+ views but nobody can help me out setting up lm-sensors? :cry:

---

### Post by topet2k12001 on 2012-10-14
> **d4m1r said:**
> 50+ views but nobody can help me out setting up lm-sensors? :cry:

Hello Friend,

Based on the website link: [http://lm-sensors.org/wiki/Devices](http://lm-sensors.org/wiki/Devices), there is support available for your board (PC87364, from National Semiconductor). Also you may want to install the latest stable version. Per the same website link:

> If your version of sensors-detect failed to detect a chip, you should try the [ latest version of sensors-detect]("http://dl.lm-sensors.org/lm-sensors/files/sensors-detect").  sensors-detect is a stand-alone script, so you can simply download it  and run it on any system, without installing anything (other than perl).  You may also try our [Installation Wizard]("http://lm-sensors.org/wiki/iwizard/1").

Are you planning to monitor just the fans/board temperatures? For core temperature monitoring you may want to install "coretemp" as well. Once both coretemp and the latest version of lm-sensors are installed, try to run sensors-detect once again.

---

### Post by d4m1r on 2012-10-14
> **topet2k12001 said:**
> Hello Friend,

Based on the website link: [http://lm-sensors.org/wiki/Devices](http://lm-sensors.org/wiki/Devices), there is support available for your board (PC87364, from National Semiconductor). Also you may want to install the latest stable version. Per the same website link:


Thanks! That be new as my log shows, it detects the sensor but then says it is not available....By the way, the server is running 12.04 LTS (32 bit) and it says my sensor is supported in kernel 2.6.10+, does anyone know what kernel server 12.04 LTS would have? :confused:

---

### Post by ian dobson on 2012-10-14
Hi,

Also it looks as if the BIOS doesn't initalise the PC87364 correctly, so I don't think that lm-sensors will work.

and have a look here:- [http://www.coulterfamily.org.uk/pages/PCs/Linux/FAQ-LINUX-lm_sensors.php](http://www.coulterfamily.org.uk/pages/PCs/Linux/FAQ-LINUX-lm_sensors.php)

Regards
Ian Dobson

---

### Post by d4m1r on 2012-10-14
> **ian dobson said:**
>  it looks as if the BIOS doesn't initalise the PC87364 correctly, so I don't think that lm-sensors will work.


Thanks for the info. Would you know how that happens or why it would be the case? It seems to detect the BIOS/PC and sensor just find, and the sensor is listed as supported even on the lm-sensor website as previously linked to....

That article does also mention the **Dell Optiplex GX150** which is the same PC I have so I am confused why this model is so problematic ](*,)

---

### Post by thnewguy on 2012-10-14
It looks like almost everything on your board either couldn't be detected or the sensor didn't seem to be returning any information. I would suspect this is a BIOS issue or the board isn't supported by lm-sensors. Is it an older machine? You might have better luck seeing if lm-sensors has a mailing list and posting the output there for the developers to look at.

---

### Post by ian dobson on 2012-10-15
Hi,

Any chance that you can attach a full dmesg from the box. Maybe then I can see where things are going wrong.

Regards
Ian Dobson

---

### Post by d4m1r on 2012-10-15
> **ian dobson said:**
> Hi,

Any chance that you can attach a full dmesg from the box. Maybe then I can see where things are going wrong.

Regards
Ian Dobson

Hey Ian, thanks for the reply. Would you mind explaining how this is done? Did you need the full output? Let me know and I'll get it done, thanks :D

---

### Post by pqwoerituytrueiwoq on 2012-10-15
> **d4m1r said:**
> Thanks! That be new as my log shows, it detects the sensor but then says it is not available....By the way, the server is running 12.04 LTS (32 bit) and it says my sensor is supported in kernel 2.6.10+, does anyone know what kernel server 12.04 LTS would have? :confused:
12.04 has kernel 3.2.x
this command reports my cpu temp
```
acpi -t
```

---

### Post by ian dobson on 2012-10-16
Hi,

A full output would be nice:-

sudo dmesg > /tmp/dmesg.txt

Then upload /tmp/dmesg.txt as an attachment to this forum.

Regards
Ian Dobson

---

