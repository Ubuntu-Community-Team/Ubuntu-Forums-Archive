---
title: "system shutting off, can't determine reason - need help diagnosing"
date: 2015-11-12
forum: Server Platforms
---

### Post by Scrumps on 2015-11-12
Hey everyone, I would really appreciate some help as this issue has been bugging me over the past week and I can't figure out a reason or cause.

My server machine has just shut off twice over the past week. As far as I can tell, temperatures on the machine seem to be normal but here is an output of as much info as I can get (this is right after it shut off btw):

```
server:~# hddtemp /dev/sd[a-h][1]
/dev/sda1: LSI:  drive supported, but it doesn't have a temperature sensor.
/dev/sdb1: ST380815AS: 36°C
/dev/sdc1: ST3250410AS: 32°C
/dev/sdd1: WDC WD10EZEX-00RKKA0: 36°C
/dev/sde1: ST31500341AS: 41°C
/dev/sdf1: ST3750330AS: 37°C
/dev/sdg1: ST31500541AS: 35°C
/dev/sdh1: ST2000DM001-1CH164: 29°C



```

```

server:~# sudo sensors
it8728-isa-0228
Adapter: ISA adapter
in0:          +1.28 V  (min =  +0.00 V, max =  +3.06 V)
in1:          +1.49 V  (min =  +0.00 V, max =  +3.06 V)
in2:          +1.99 V  (min =  +0.00 V, max =  +3.06 V)
in3:          +1.97 V  (min =  +0.00 V, max =  +3.06 V)
in4:          +1.85 V  (min =  +0.00 V, max =  +3.06 V)
in5:          +0.48 V  (min =  +0.00 V, max =  +3.06 V)
in6:          +2.21 V  (min =  +0.00 V, max =  +3.06 V)
3VSB:         +3.34 V  (min =  +0.00 V, max =  +6.12 V)
Vbat:         +3.34 V  
fan1:        4753 RPM  (min =    0 RPM)
fan2:           0 RPM  (min =    0 RPM)
fan3:           0 RPM  (min =    0 RPM)
fan4:        2257 RPM  (min =    0 RPM)
fan5:           0 RPM  (min =    0 RPM)
temp1:        +35.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:        +51.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
temp3:        +45.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = Intel PECI
intrusion0:  ALARM

fam15h_power-pci-00c4
Adapter: PCI adapter
power1:       87.80 W  (crit = 125.19 W)

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +45.0°C  (high = +70.0°C)
                       (crit = +80.0°C, hyst = +77.0°C)

nouveau-pci-0100
Adapter: PCI adapter
temp1:        +47.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

```

Syslog:
```
(DHCP output ommitted)
Nov 11 22:39:01 server CRON[32095]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Nov 11 22:49:04 server smartd[1567]: Device: /dev/sdb [SAT], SMART Usage Attribute: 190 Airflow_Temperature_Cel changed from 63 to 64
Nov 11 22:49:04 server smartd[1567]: Device: /dev/sdb [SAT], SMART Usage Attribute: 194 Temperature_Celsius changed from 37 to 36
Nov 11 22:49:05 server smartd[1567]: Device: /dev/sdd [SAT], SMART Usage Attribute: 194 Temperature_Celsius changed from 102 to 103
Nov 11 22:49:05 server smartd[1567]: Device: /dev/sdg [SAT], SMART Usage Attribute: 190 Airflow_Temperature_Cel changed from 64 to 65
Nov 11 22:49:05 server smartd[1567]: Device: /dev/sdg [SAT], SMART Usage Attribute: 194 Temperature_Celsius changed from 36 to 35
Nov 11 22:49:06 server smartd[1567]: Device: /dev/sdh [SAT], SMART Usage Attribute: 190 Airflow_Temperature_Cel changed from 68 to 69
Nov 11 22:49:06 server smartd[1567]: Device: /dev/sdh [SAT], SMART Usage Attribute: 194 Temperature_Celsius changed from 32 to 31
Nov 11 22:49:06 server smartd[1567]: Device: /dev/bus/0 [megaraid_disk_08] [SAT], SMART Usage Attribute: 194 Temperature_Celsius changed from 116 to 117
(DHCP output ommitted)
Nov 11 23:09:01 server CRON[1446]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
(DHCP output ommitted)
Nov 11 23:17:01 server CRON[2117]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
(DHCP output ommitted)
Nov 11 23:19:04 server smartd[1567]: Device: /dev/sdb [SAT], SMART Usage Attribute: 190 Airflow_Temperature_Cel changed from 64 to 62
Nov 11 23:19:04 server smartd[1567]: Device: /dev/sdb [SAT], SMART Usage Attribute: 194 Temperature_Celsius changed from 36 to 38
Nov 11 23:19:04 server smartd[1567]: Device: /dev/sdb [SAT], SMART Usage Attribute: 195 Hardware_ECC_Recovered changed from 80 to 79
Nov 11 23:19:04 server smartd[1567]: Device: /dev/sdc [SAT], SMART Usage Attribute: 190 Airflow_Temperature_Cel changed from 67 to 65
Nov 11 23:19:04 server smartd[1567]: Device: /dev/sdc [SAT], SMART Usage Attribute: 194 Temperature_Celsius changed from 33 to 35
Nov 11 23:19:04 server smartd[1567]: Device: /dev/sde [SAT], SMART Usage Attribute: 190 Airflow_Temperature_Cel changed from 58 to 57
Nov 11 23:19:04 server smartd[1567]: Device: /dev/sde [SAT], SMART Usage Attribute: 194 Temperature_Celsius changed from 42 to 43
Nov 11 23:19:04 server smartd[1567]: Device: /dev/sdf [SAT], SMART Usage Attribute: 190 Airflow_Temperature_Cel changed from 62 to 61
Nov 11 23:19:04 server smartd[1567]: Device: /dev/sdf [SAT], SMART Usage Attribute: 194 Temperature_Celsius changed from 38 to 39
Nov 11 23:19:04 server smartd[1567]: Device: /dev/sdf [SAT], SMART Usage Attribute: 195 Hardware_ECC_Recovered changed from 43 to 42
Nov 11 23:19:05 server smartd[1567]: Device: /dev/sdg [SAT], SMART Usage Attribute: 190 Airflow_Temperature_Cel changed from 65 to 63
Nov 11 23:19:05 server smartd[1567]: Device: /dev/sdg [SAT], SMART Usage Attribute: 194 Temperature_Celsius changed from 35 to 37
Nov 11 23:19:05 server smartd[1567]: Device: /dev/sdh [SAT], SMART Usage Attribute: 190 Airflow_Temperature_Cel changed from 69 to 67
Nov 11 23:19:05 server smartd[1567]: Device: /dev/sdh [SAT], SMART Usage Attribute: 194 Temperature_Celsius changed from 31 to 33
Nov 11 23:19:05 server smartd[1567]: Device: /dev/bus/0 [megaraid_disk_08] [SAT], SMART Usage Attribute: 194 Temperature_Celsius changed from 117 to 115
Nov 11 23:19:05 server smartd[1567]: Device: /dev/bus/0 [megaraid_disk_09] [SAT], SMART Usage Attribute: 194 Temperature_Celsius changed from 118 to 117
Nov 11 23:19:05 server smartd[1567]: Device: /dev/bus/0 [megaraid_disk_10] [SAT], SMART Usage Attribute: 194 Temperature_Celsius changed from 118 to 117
Nov 11 23:19:05 server smartd[1567]: Device: /dev/bus/0 [megaraid_disk_11] [SAT], SMART Usage Attribute: 194 Temperature_Celsius changed from 117 to 116
Nov 11 18:17:01 server CRON[16129]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 11 23:43:54 server rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="699" x-info="http://www.rsyslog.com"] start
Nov 11 23:43:54 server rsyslogd: rsyslogd's groupid changed to 104
Nov 11 23:43:54 server rsyslogd: rsyslogd's userid changed to 101
Nov 11 23:43:54 server kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov 11 23:43:54 server kernel: [    0.000000] Initializing cgroup subsys cpu
Nov 11 23:43:54 server kernel: [    0.000000] Initializing cgroup subsys cpuacct
Nov 11 23:43:54 server kernel: [    0.000000] Linux version 3.19.0-33-generic (buildd@lgw01-49) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #38~14.04.1-Ubuntu SMP Fri Nov 6 18:17:28 UTC 2015 (Ubuntu 3.19.0-33.38~14.04.1-generic 3.19.8-ckt7)
Nov 11 23:43:54 server kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-33-generic root=UUID=00f6f5a0-78bd-46bc-9147-8cc8ffb5361b ro quiet splash vt.handoff=7
Nov 11 23:43:54 server kernel: [    0.000000] KERNEL supported cpus:
Nov 11 23:43:54 server kernel: [    0.000000]   Intel GenuineIntel
Nov 11 23:43:54 server kernel: [    0.000000]   AMD AuthenticAMD
Nov 11 23:43:54 server kernel: [    0.000000]   Centaur CentaurHauls
Nov 11 23:43:54 server kernel: [    0.000000] tseg: 00cf800000

```

Prior to its recent issue, I had setup my tty1 to turn off powersave mode, and not blank the screen, while tailing the syslog file. When I noticed it was no longer connectable, I came to find that the monitor was in a type of powersave mode, and the system was still "running" even though it was non-responsive. 

I would really appreciate any help in narrowing done my problem. I tried running memtest, fsck, and spinrite on Saturday (this was after the machine shut down the first time) and everything came back with no errors. It has now shutdown again on Wednesday night. 

Could anyone spitball some ideas for me to help figure out what is going on? Should I cross-post this in the Hardware forum, or would it be better of moved to there? I haven't had issues for months before today, I am wondering if is being caused by a kernel update - I just switched it to a different kernel to see if that would make a difference. I switched to from -33-generic.:
```

Linux server 3.19.0-32-generic #37~14.04.1-Ubuntu SMP Thu Oct 22 09:41:40 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by darkod on 2015-11-12
I don't know much about this topic, but if the syslog output is correct and those disk temps are really Celsius, they are extremely high, no? It mentions temps over 100+ degrees. Even the ones that are not so high, are in the 60+ area which is again rather high for a hdd, no?

On the other hand, your hddtemp output does not show temps so high...

---

### Post by Scrumps on 2015-11-12
> **darkod said:**
> I don't know much about this topic, but if the syslog output is correct and those disk temps are really Celsius, they are extremely high, no? It mentions temps over 100+ degrees. Even the ones that are not so high, are in the 60+ area which is again rather high for a hdd, no?

On the other hand, your hddtemp output does not show temps so high...

You would be correct on that, however, they are not hot or burning to the touch, so I would say it is a safe bet to assume that the hddtemps output is a much more accurate collection of data.

---

### Post by tgalati4 on 2015-11-12
Have you cleaned out this machine and reseated all connections in the last year?  It's possible that your PSU is giving out.  How old is the machine?  Check the 12VDC connection as that is used to spin the disks.  If you are showing 11.0 VDC while running then current will rise to compensate and cause your disks to run hot (which they are) and contribute to hard disk errors (which you have).

---

### Post by Scrumps on 2015-11-12
> **tgalati4 said:**
> Have you cleaned out this machine and reseated all connections in the last year?  It's possible that your PSU is giving out.  How old is the machine?  Check the 12VDC connection as that is used to spin the disks.  If you are showing 11.0 VDC while running then current will rise to compensate and cause your disks to run hot (which they are) and contribute to hard disk errors (which you have).

I have cleaned out the machine in the past year, but haven't reseated connections. Currently the case lid is off, to allow free air flow, and I stuck a 120 mm fan on top of my RAID card to try and help that cool temps down. 

I just purchased a PSU tester, which will come tomorrow, so I can post the results of that afterwards.

The power supply is a Corsair 650 Watt (several years old). I can't really afford a new PSU at the moment, which would be a huge bummer if that was the situation. :(

In the mean time here is a photo of the voltages coming into the motherboard:
 [ATTACH=CONFIG]265527[/ATTACH]

---

### Post by tgalati4 on 2015-11-12
Both 5VDC and 12VDC are low.  A common problem for an old PSU.  If you are good with a solder iron, it might just need recapping, but otherwise I see a new PSU in your future.

---

### Post by Scrumps on 2015-11-13
So I found out it was not only the PSU, but it seems that the motherboard somehow melted the PSU ATX 12 V plugs into the socket. You can sorta see stuff stuck in the socket in the last picture.

So I now have a very humorous webpage:
[IMG]http://i.imgur.com/vB9EmvWl.png[/IMG]

[IMG]http://i.imgur.com/nwWsAXXl.jpg[/IMG]

[IMG]http://i.imgur.com/Eqj0wj3l.jpg[/IMG]

[IMG]http://i.imgur.com/QlPZF6Ql.jpg[/IMG]

---

### Post by tgalati4 on 2015-11-13
Well, it could be a PSU problem.  When voltage drops, current increases because the power draw remains the same.  Power equals Voltage * Current.  It's possible that  you are exceeding what the motherboard was designed for.  Several spinning disks will do that.  High current will cause heat and melt connections.  

Reseating connections is part of cleaning a server.  Otherwise you would not have found that issue.  "A toe shine is no shine.  A heal shine is a real shine."

---

### Post by Scrumps on 2015-11-13
> **tgalati4 said:**
> Well, it could be a PSU problem.  When voltage drops, current increases because the power draw remains the same.  Power equals Voltage * Current.  It's possible that  you are exceeding what the motherboard was designed for.  Several spinning disks will do that.  High current will cause heat and melt connections.  

Reseating connections is part of cleaning a server.  Otherwise you would not have found that issue.  "A toe shine is no shine.  A heal shine is a real shine."

Alright, so I installed a new motherboard and am waiting for the new PSU  to arrive on Tuesday. Until then, I have plugged the PSU that I have in  my desktop in this machine.

However, I do have a problem in that the Intel Network Card is not coming online. 

If I run lspci, I see the card listed, but if I do "sudo ifup eth0" it just says it can't bring the device online. There isn't any errors in syslog, and I don't see anything immediately in dmesg after running the ifup command. It isn't complaining about a lock file at all, so I am not sure where to start searching after that.

---

### Post by tgalati4 on 2015-11-13
What is the network card?  Is it a separate card or is it on the motherboard?

```
lspci | grep Ethernet
```  Check the cable and the port on the router, try changing.  A new motherboard may need a newer kernel, depending on the chipset.

---

### Post by Scrumps on 2015-11-13
> **tgalati4 said:**
> What is the network card?  Is it a separate card or is it on the motherboard?

```
lspci | grep Ethernet
```  Check the cable and the port on the router, try changing.  A new motherboard may need a newer kernel, depending on the chipset.


Well the problem is as of now the following:
1) It seemed to be a bit easier then I expected, I hope anyways. The network card is not labeled as eth0 anymore, it is labeled as something else. I would like it back to eth0. I went into /etc/udev/rules/70-*, however, there is already an entry with the MAC address/Hardware address for the device listed and specified to be eth0. So I am not sure what is causing it be labeled as p10p1 at the moment. 

2) The system boots with random issues. Every now and then, the system will get to GRUB menu screen, and will try to boot to Ubuntu and will boot to a black screen. The monitor stays on  for a short time, and then shuts off into a "power save mode", the system is still running (in terms of fans, etc), but LED Lights on certain objects were not being displayed anymore. There are no messages in dmesg/syslog, and I can't seem to really figure out any kernel flag/boot thing that would output any issues to figure out what is going on.
I have gone through several ideas for the cause in my head. Whether it is a BIOS setting on the motherboard that may not be entirely compatible with Linux, hard drive issues, or maybe overheating from the CPU (stock heatsink/fan for an FX-8350 causes problems). Everything I come to just doesn't make sense to me as to why it would intermittently bring up issues while booting.
Then I thought maybe it was the nVidia GPU I have, but, it was working fine in the old system, so to me, that means it has to be something that is directly related to the motherboard. But those are biggest issues right now.

The motherboard that is now installed is an ASUS M5A99FX PRO R2.0 with the latest BIOS available (2501). So I can't update the BIOS. I tested the RAM prior to the motherboard/psu failure, and it passed memtest fine.

So at this point, that is my biggest issue. :/

---

### Post by tgalati4 on 2015-11-14
You are using an older power supply.  Wait until your new PSU comes in and then test.  The randomness seems to be power-related.

---

### Post by Scrumps on 2015-11-14
So far (i am using a temporary PSU that is just as old, but doesn't have the same issues as the last PSU) I am now getting boots that don't randomly stall out. I also found out the issue with my NIC Card was related to this bug: [https://bugs.launchpad.net/ubuntu/+source/biosdevname/+bug/1284043](https://bugs.launchpad.net/ubuntu/+source/biosdevname/+bug/1284043) and after applying the kernel fixes, I fixed that problem. I also ordered a new CPU Cooler, so hopefully that fixes the CPU heat issue. Finally then the PSU will come and I can get everything re-installed properly into the case.

Thank you for your help. I hope all these changes won't cause the system to reboot again. :)

---

### Post by Scrumps on 2015-11-17
> **tgalati4 said:**
> You are using an older power supply.  Wait until your new PSU comes in and then test.  The randomness seems to be power-related.

So the new Power Supply and the CPU Cooler came, and I am running into a new issue. 

See the below pictures. The first & fourth photo is when I would have everything plugged in to the machine. The second & third photo was when only the Home and Root directory/drives were available. When only the Root & Home drives were available, the machine would boot up without any issue. When all drives were plugged in, it would stall out and never fully boot (until just now).

 [ATTACH=CONFIG]265644[/ATTACH][ATTACH=CONFIG]265645[/ATTACH][ATTACH=CONFIG]265646[/ATTACH][ATTACH=CONFIG]265647[/ATTACH]

Here is syslog and dmesg (though I don't think they will be incredibly helpful in this situation) when it boots:
syslog: [http://pastebin.com/msCcRzbR](http://pastebin.com/msCcRzbR)
dmesg: [http://pastebin.com/dGM8g2sb](http://pastebin.com/dGM8g2sb)

Like I said, after a few reboots it boots fine, but I am not sure what is causing it to hang. It seems udev is freaking out every time I hard power off the system, and I am not sure why. But as far as I am aware, there are no udev log files for the pre-boot stuff. :/

As far as temperature stuff goes, I installed a new intake fan that is supposed to push quite a bit of air, and I will be getting a few new exhaust fans in the next coming weeks. However here is a list of the current temps:

> 
@server:~$ sudo hddtemp /dev/sd[a-Z][1]
/dev/sda1: LSI: S.M.A.R.T. not available
/dev/sdb1: ST380815AS: 34°C
/dev/sdc1: ST3250410AS: 31°C
/dev/sdd1: WDC WD10EZEX-00RKKA0: 35°C
/dev/sde1: ST3750330AS: 36°C
/dev/sdf1: ST31500341AS: 39°C
/dev/sdh1: ST2000DM001-1CH164: 28°C
/dev/sdi1: ST31500541AS: 33°C


> 
server:~$ sudo sensors
it8721-isa-0290
Adapter: ISA adapter
in0:          +2.77 V  (min =  +0.19 V, max =  +0.10 V)  ALARM
in1:          +2.81 V  (min =  +2.51 V, max =  +1.58 V)  ALARM
in2:          +1.26 V  (min =  +1.38 V, max =  +0.95 V)  ALARM
+3.3V:        +3.22 V  (min =  +3.14 V, max =  +0.41 V)  ALARM
in4:          +0.22 V  (min =  +0.06 V, max =  +1.02 V)
in5:          +2.50 V  (min =  +0.30 V, max =  +0.59 V)  ALARM
in6:          +1.52 V  (min =  +0.13 V, max =  +0.73 V)  ALARM
3VSB:         +0.38 V  (min =  +0.48 V, max =  +3.94 V)  ALARM
Vbat:         +3.34 V  
fan1:        1081 RPM  (min =   12 RPM)
fan2:           0 RPM  (min =   11 RPM)  ALARM
fan3:        1800 RPM  (min =   11 RPM)
temp1:        +45.0°C  (low  = +70.0°C, high = -72.0°C)  ALARM  sensor = thermistor
temp2:        +30.0°C  (low  = -19.0°C, high = +63.0°C)  sensor = thermistor
temp3:       -128.0°C  (low  = +59.0°C, high = +45.0°C)  sensor = disabled
intrusion0:  OK

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +39.5°C  (high = +70.0°C)
                       (crit = +90.0°C, hyst = +87.0°C)

fam15h_power-pci-00c4
Adapter: PCI adapter
power1:        6.75 W  (crit = 125.19 W)



The new PSU is: CORSAIR RMx RM650X 650W ATX12V / EPS12V 80 PLUS GOLD Certified Full Modular Power Supply

---

### Post by tgalati4 on 2015-11-17
Find the SATA contoller chip and put your finger on it.  If it is too hot to keep your finger on it, then perhaps it is failing.  That is really bad news.  

Otherwise check your BIOS SATA settings.  Sometimes compatibility mode will only offer 2 ports versus 4 or 6.

---

### Post by Vegan on 2015-11-18
generally a machine that shuts down while in operation is suffering from a PSU that has degraded

power supplies do not last forever

---

