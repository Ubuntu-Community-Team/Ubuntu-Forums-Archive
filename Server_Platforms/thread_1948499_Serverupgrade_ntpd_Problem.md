---
title: "Serverupgrade ntpd Problem"
date: 2012-03-28
forum: Server Platforms
---

### Post by hallo200 on 2012-03-28
Hallo Forum,

I have done a upgrade from 8.04 LTS to 10.04 LTS. Now i have in my logs the following entries:

Mar 28 09:09:46 server ntpd[1447]: kernel time sync status change 6001
Mar 28 12:17:32 server ntpd[1447]: kernel time sync status change 2001
Mar 28 13:42:58 server ntpd[1447]: kernel time sync status change 6001
Mar 28 14:00:04 server ntpd[1447]: kernel time sync status change 2001
Mar 28 14:34:13 server ntpd[1447]: kernel time sync status change 6001
Mar 28 15:59:37 server ntpd[1447]: kernel time sync status change 2001

The second Problem is that i have an Opteron CPU which becomes very hot. On Ubuntu 8.04 i had 55-60 Degree Celsius.

Now I have with "sensors" round 40 degrees.

My Mainboard is not officially supported.
It is only supported for Fedora 6, SLES 10.1, and one more.

Thanks for you opinion,
regards,
hallo200

---

### Post by hallo200 on 2012-03-29
Doest nobody know about this entires?

regards
hallo 200

---

### Post by Insomn1a on 2012-03-29
> **hallo200 said:**
> Doest nobody know about this entires?

regards
hallo 200


> Binary package hint: ntp

The logcheck filter shipped with ntp in karmic misses the following messages:

Mar 8 10:06:29 chunks ntpd[1000]: kernel time sync status change 6001
Mar 8 10:23:32 chunks ntpd[1000]: kernel time sync status change 2001

According to the NTP folks, these messages are expected behaviour (in a future version, they've eliminated the message):

*Source [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/568720](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/568720)


what kind of configuration do you have along with the opteron?  is it 55-60 idle, full load? is the cpu constantly in use?

can you paste your processes list and sensor temps?

---

### Post by hallo200 on 2012-03-29
Hallo,

Thanks for reply.

There is no CPU load expect at night for backup. I got some error messages in the syslog saying the k8temp gives wrong values.

Now idle temparatur is around 40 degrees Celsius. Bevore the upgrade i had 50-60 degrees.

Thanks,
regards,
hallo 200

---

### Post by Insomn1a on 2012-03-30
> **hallo200 said:**
> Hallo,

Thanks for reply.

There is no CPU load expect at night for backup. I got some error messages in the syslog saying the k8temp gives wrong values.

Now idle temparatur is around 40 degrees Celsius. Bevore the upgrade i had 50-60 degrees.

Thanks,
regards,
hallo 200

So long as the temps really aren't correct I would probably ignore those errors, if they are I would try installing a different tool to read those sensors.

This page has installation instructions for im-sensors

[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

---

### Post by hallo200 on 2012-03-30
Thanks for reply,

i already use lm-sensors for the temperature output.

I read your link and i started sensors-detect on a desktop test machine. 
Could it cause a server crash or something like that?

The questions make me a littel bit insecure - espacially:

> 
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)

The script tells me to accept the default answers, but when I aswere with NO there will not be change right?

thanks and regards
hallo200

---

### Post by Insomn1a on 2012-04-02
> **hallo200 said:**
> Thanks for reply,

i already use lm-sensors for the temperature output.

I read your link and i started sensors-detect on a desktop test machine. 
Could it cause a server crash or something like that?

The questions make me a littel bit insecure - espacially:


The script tells me to accept the default answers, but when I aswere with NO there will not be change right?

thanks and regards
hallo200

Im 99% sure that sensors-detect wont make a server crash, especially a linux machine. and yes you should just accept the default answers.

---

### Post by hallo200 on 2012-04-04
Hallo,

the CPU (Core 0, Core 1) are still to low.
whats this:

M/B Temp:     -1.0°C  (high =  -1.0°C, hyst =  -1.0°C)  ALARM  sensor = diode
CPU Temp:     +0.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = diode
temp3:        +0.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = diode

completly strage values!


> k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +39.0°C                                    
Core1 Temp:  +38.0°C                                    

k8temp-pci-00cb
Adapter: PCI adapter
Core0 Temp:  +42.0°C                                    
Core1 Temp:  +44.0°C                                    

adt7463-i2c-0-2e
Adapter: SMBus nForce2 adapter at 4c00
V1.5:        +2.53 V  (min =  +0.00 V, max =  +3.32 V)   
VCore:       +0.01 V  (min =  +0.00 V, max =  +2.99 V)   
V3.3:        +3.33 V  (min =  +0.00 V, max =  +4.38 V)   
V5:          +0.00 V  (min =  +0.00 V, max =  +6.64 V)   
V12:         +0.00 V  (min =  +0.00 V, max = +15.94 V)   
CPU_Fan:       0 RPM  (min =    0 RPM)
fan2:          0 RPM  (min =    0 RPM)
fan3:          0 RPM  (min =    0 RPM)
fan4:          0 RPM  (min =    0 RPM)
CPU Temp:    +45.0°C  (low  = +55.0°C, high = +65.0°C)  ALARM  
Board Temp:  +45.5°C  (low  = +45.0°C, high = +55.0°C)  ALARM  
Remote Temp: +46.0°C  (low  = +55.0°C, high = +65.0°C)  ALARM  
cpu0_vid:   +0.000 V

w83627thf-isa-0a00
Adapter: ISA adapter
VCore:       +1.94 V  (min =  +1.94 V, max =  +1.94 V)   ALARM
+12V:       +15.50 V  (min = +15.50 V, max = +15.50 V)   ALARM
+3.3V:       +4.08 V  (min =  +4.08 V, max =  +4.08 V)   ALARM
+5V:         +6.80 V  (min =  +6.80 V, max =  +6.80 V)   ALARM
-12V:        +6.06 V  (min =  +6.06 V, max =  +6.06 V)   ALARM
V5SB:        +6.85 V  (min =  +6.85 V, max =  +6.85 V)   ALARM
VBat:        +4.08 V  (min =  +4.08 V, max =  +4.08 V)   ALARM
fan1:          0 RPM  (min =    0 RPM, div = 128)  ALARM
CPU Fan:       0 RPM  (min =    0 RPM, div = 128)  ALARM
fan3:          0 RPM  (min =    0 RPM, div = 128)  ALARM
M/B Temp:     -1.0°C  (high =  -1.0°C, hyst =  -1.0°C)  ALARM  sensor = diode
CPU Temp:     +0.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = diode
temp3:        +0.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = diode
beep_enable:enabled

w83792d-i2c-0-2f
Adapter: SMBus nForce2 adapter at 4c00
VCoreA:      +1.12 V  (min =  +1.65 V, max =  +2.04 V)   ALARM
VCoreB:      +1.11 V  (min =  +1.65 V, max =  +2.04 V)   ALARM
VIN0:        +3.32 V  (min =  +0.00 V, max =  +4.08 V)   
VIN1:        +3.24 V  (min =  +0.00 V, max =  +4.08 V)   
VIN2:        +1.84 V  (min =  +0.00 V, max =  +4.08 V)   
VIN3:        +1.83 V  (min =  +0.00 V, max =  +4.08 V)   
5VCC:        +5.06 V  (min =  +0.00 V, max =  +6.12 V)   
5VSB:        +5.02 V  (min =  +0.00 V, max =  +6.12 V)   
VBAT:        +3.04 V  (min =  +0.00 V, max =  +4.08 V)   
Fan1:       1562 RPM  (min =    0 RPM, div = 8)
Fan2:       1298 RPM  (min =    0 RPM, div = 8)
Fan3:       1278 RPM  (min =    0 RPM, div = 8)
Fan4:       1520 RPM  (min =    0 RPM, div = 8)
Fan5:          0 RPM  (min =    0 RPM, div = 16)
Fan7:       1328 RPM  (min =    0 RPM, div = 8)
Temp1:       +42.0°C  (high = +127.0°C, hyst =  +0.0°C)  
Temp2:       +43.0°C  (high = +80.0°C, hyst = +75.0°C)  
Temp3:       +41.0°C  (high = +80.0°C, hyst = +75.0°C)  



I tried to remove w83627thf from /etc/modules and did:
service module-init-tools start
but if i execute 
sensors it is still there


regards
hallo200

---

### Post by hallo200 on 2012-04-04
ok, I removed the module 
w83627hf
with "modprobe -r w83627hf"

but the k8temps are still wrong!

Thanks, regards
hallo 200

---

