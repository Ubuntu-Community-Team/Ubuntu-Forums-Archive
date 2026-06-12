---
title: "[Ubuntu Server 14.04] Can't control fan speed"
date: 2014-10-03
forum: Server Platforms
---

### Post by mansonthomas on 2014-10-03
Hi,
 
I'm trying to control the fan speed so that it makes lower noise. 

Ubuntu server 14.04, x64, hardware :

[TABLE="width: 0, align: center"]
[TR]
[TD="align: center"]1[/TD]
[TD]AMD Athlon 64 X2 4850e[/TD]
[/TR]
[TR]
[TD="align: center"]1[/TD]
[TD][COLOR=#222222]Asus[/COLOR] [COLOR=#222222]M3N78[/COLOR]-EMH HDMI[/TD]
[/TR]
[TR]
[TD="align: center"]2[/TD]
[TD]Corsair Flash Voyager - 8 Go[/TD]
[/TR]
[TR]
[TD="align: center"]1[/TD]
[TD]Enermax Modu 82+ - 425W[/TD]
[/TR]
[TR]
[TD="align: center"]2[/TD]
[TD]G.Skill Extreme2 2 Go PC5300 PQ[/TD]
[/TR]
[TR]
[TD="align: center"]1[/TD]
[TD]Noctua NH-C12P[/TD]
[/TR]
[TR]
[TD="align: center"]1[/TD]
[TD]Samsung SH-S223F - OEM, noir[/TD]
[/TR]
[TR]
[TD="align: center"]1[/TD]
[TD]Silverstone Sugo SG03 (noir)[/TD]
[/TR]
[TR]
[TD="align: center"]2[/TD]
[TD]Western Digital Caviar Green S-ATA - 750 Go - 16 Mo[/TD]
[/TR]
[/TABLE]



I've looked some tuto on internet, but it seems that pwmconfig can't find my fan, while, sensors can...

any idea of how to progress on this issue ?

Thanks,
Thomas.



root@home:~# sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:   +28.0°C
Core0 Temp:   +29.0°C
Core1 Temp:   +35.0°C
Core1 Temp:   +29.0°C

atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.01 V  (min =  +0.80 V, max =  +1.80 V)
 +3.3 Voltage:      +3.31 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:        +4.97 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:      +12.09 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:     1591 RPM  (min =  600 RPM, max = 7200 RPM)
CHASSIS FAN Speed:  492 RPM  (min = 1200 RPM, max = 7200 RPM)
CPU Temperature:    +38.0°C  (high = +60.0°C, crit = +95.0°C)
MB Temperature:     +36.0°C  (high = +45.0°C, crit = +95.0°C)




root@home:~# pwmconfig
# pwmconfig revision 6166 (2013-05-01)
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed
root@home:~#

---

### Post by mansonthomas on 2014-10-13
Nobody can help on this ? 
please.... for my ears  :wink::wink:

---

### Post by lukeiamyourfather on 2014-10-13
Not all sensors and controllers are supported, especially for newer hardware. It would be best to control the fan settings from the BIOS/UEFI. Most motherboards have an option to set the temperature threshold and minimum fan speed.

---

### Post by mansonthomas on 2014-10-14
Well, my server is like 6 years old... kinda prehistoric !

---

