---
title: "Asus F301A / X301A overheating"
date: 2013-04-25
forum: Ubuntu Development Version
---

### Post by Vicolaships on 2013-04-25
Hello,

I made a fresh install of Ubuntu 13.04 on my laptop to test. I have a big problem with my CPU. It is overheating (70°C in iddle) and I don't understand what stresses my CPU.

My laptop is a [X301A]("http://www.linlap.com/asus_f301a").

Here is a top :
```
  PID USER      PR  NI  VIRT  RES  SHR S  %CPU %MEM    TIME+  COMMAND                                                            
 3938 root      20   0  287m  57m  40m S   3,7  1,5   0:20.83 Xorg                                                               
    4 root      20   0     0    0    0 S   2,3  0,0   0:09.33 kworker/0:0                                                        
   28 root      20   0     0    0    0 S   2,3  0,0   0:09.14 kworker/0:1                                                        
 5891 root      20   0  217m 4516 3528 S   2,3  0,1   0:06.59 upowerd                                                            
  556 messageb  20   0 25484 2376  924 S   2,0  0,1   0:06.18 dbus-daemon                                                        
22789 victor    20   0  607m  29m  20m S   2,0  0,8   0:07.16 gnome-system-mo                                                    
 5728 victor    20   0  821m  19m  13m S   1,7  0,5   0:07.19 gnome-settings-                                                    
 6133 victor    20   0 1511m  79m  30m S   1,7  2,1   0:12.79 compiz                                                             
26973 victor    20   0 1472m 394m  44m S   1,7 10,3   1:06.99 firefox                                                            
21445 victor    20   0  564m 110m  29m S   1,3  2,9   0:04.61 plugin-containe                                                    
    1 root      20   0 27064 2872 1436 S   1,0  0,1   0:05.70 init                                                               
  481 root      20   0 21864 1276  436 S   1,0  0,0   0:02.52 udevd                                                              
   10 root      20   0     0    0    0 S   0,7  0,0   0:00.79 rcu_sched                                                          
   13 root      20   0     0    0    0 S   0,7  0,0   0:01.28 ksoftirqd/1                                                        
  477 root      20   0 21732 1284  472 S   0,7  0,0   0:02.85 udevd                                                              
  629 syslog    20   0  241m 3072 1116 S   0,7  0,1   0:00.92 rsyslogd                                                           
 2229 root      20   0  4508  880  576 S   0,7  0,0   0:01.04 acpid                                                              
 8271 victor    20   0  542m 7312 5644 S   0,7  0,2   0:01.94 indicator-sessi                                                    
    3 root      20   0     0    0    0 R   0,3  0,0   0:01.17 ksoftirqd/0                                                        
   48 root      20   0     0    0    0 S   0,3  0,0   0:00.52 kworker/1:1                                                        
  261 root      20   0     0    0    0 S   0,3  0,0   0:00.05 jbd2/sda5-8                                                        
  344 root      20   0 15268  644  420 S   0,3  0,0   0:00.39 upstart-file-br                                                    
  390 root      20   0 22000 1728  788 S   0,3  0,0   0:01.49 udevd                                                              
 5305 victor    20   0  421m  11m 8972 S   0,3  0,3   0:01.26 gnome-session                                                      
15793 victor    20   0  326m 8820 7092 S   0,3  0,2   0:00.85 mission-control                                                    
19364 victor    20   0  667m  20m  13m S   0,3  0,5   0:00.36 gnome-terminal                                                     
    2 root      20   0     0    0    0 S   0,0  0,0   0:00.00 kthreadd                                                           
    5 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 kworker/0:0H                                                       
    7 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 kworker/u:0H                                                       
    8 root      rt   0     0    0    0 S   0,0  0,0   0:00.08 migration/0                                                        
    9 root      20   0     0    0    0 S   0,0  0,0   0:00.00 rcu_bh                                                             
   11 root      rt   0     0    0    0 S   0,0  0,0   0:00.00 watchdog/0  
```

```
 uname -a
Linux X301A1 3.8.0-19-generic #29-Ubuntu SMP Wed Apr 17 18:16:28 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

But the system monitor shows 80% (or more) CPU usage everytme.
Where does it come from, what can I do ?

EDIT: Tried Kernel 3.8.8 : ([tutorial]("http://askubuntu.com/questions/119080/how-to-update-kernel-to-the-latest-mainline-version-without-any-distro-upgrade"))

```
uname -a
Linux X301A1 3.8.8-030808-generic #201304170248 SMP Wed Apr 17 06:49:45 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```
Same problem but the CPU looks a lttle bit cooler in idle (~ 65°C)

---

### Post by pqwoerituytrueiwoq on 2013-04-25
It probably unity using the GPU to its limit
i am running xubuntu on that same CPU and my temps are 40-45C
could have swore that CPU had Intel HD 3000 graphics
my cpu barley gets over 60C on full load, i clearly have better ventilation on my cpu, or you have dust bunnies

---

### Post by Vicolaships on 2013-04-25
I forgot to tell you but with Ubuntu 12.04 my CPU doesn't overheat at all when iddle. 40°C in iddle mode using 12.04.
I don't think the problem is hardware, I think it's "software" ! Thanks for the answer ;)

EDIT : I tried these kernels with no result :
3.4.0, 3.7.10, 3.8.8, 3.9.0

---

### Post by ventrical on 2013-04-25
There were some problems with some websites in FireFox while visiting OMGUbuntu which pumped the CPU pressure. I have an Acer Extensa 4420 Dual Core AMD64bit and I had to manually remove a cake of dust that was built up in the cooling fins. You can't see the build up from the outside.

However, since it works ok with Precise then it looks like a kernel panic of some sort if not ff.

---

### Post by Vicolaships on 2013-04-25
I have no software installed other than **lm-sensors** to check CPU temperature.
I like 13.04 but I don't want to kill my hardware so I'll revert to 12.04 if I don't have a solution :(

```
Every 2,0s: sensors                                                                                                    Thu Apr 25 23:09:51 2013

acpitz-virtual-0
Adapter: Virtual device
temp1:        +71.0°C  (crit = +88.0°C)

asus-isa-0000
Adapter: ISA adapter
temp1:        +71.0°C

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +71.0°C  (high = +80.0°C, crit = +85.0°C)
Core 0:         +71.0°C  (high = +80.0°C, crit = +85.0°C)
Core 1:         +67.0°C  (high = +80.0°C, crit = +85.0°C)

```

Using 
```
sudo killall update-apt-xapian-index
```
I save 20% CPU and I get 70% CPU usage when nothing is running (system monitor info, top gives less than 25% CPU usage)

---

### Post by ventrical on 2013-04-25
Where is your fan speed report!!??

```

ventrical@ventrical-AcerAMD64bitDual:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +40.0°C  (crit = +75.0°C)

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:   +30.0°C  
Core0 Temp:   +37.0°C  
Core1 Temp:   +32.0°C  
Core1 Temp:   +37.0°C  

atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.14 V  (min =  +0.85 V, max =  +1.60 V)
 +3.3 Voltage:      +3.30 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:      +4.95 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:     +12.10 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:     3461 RPM  (min =    0 RPM, max = 1800 RPM)
CHASSIS FAN Speed:    0 RPM  (min =    0 RPM, max = 1800 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM, max = 1800 RPM)
CPU Temperature:    +30.0°C  (high = +90.0°C, crit = +125.0°C)
MB Temperature:     +29.0°C  (high = +45.0°C, crit = +90.0°C)

ventrical@ventrical-AcerAMD64bitDual:~$ 

```

---

### Post by pqwoerituytrueiwoq on 2013-04-25
give this a try
[http://ubuntuforums.org/showthread.php?t=2115355&p=12508783&viewfull=1#post12508783](http://ubuntuforums.org/showthread.php?t=2115355&p=12508783&viewfull=1#post12508783)

---

### Post by Vicolaships on 2013-04-26
Hey there, here are the news :

I re-installed Ubuntu 13.04 : I had a big problem, a black screen with only a mouse, I plugged in ethernet, then Ctrl + Alt + F2 :
```
sudo apt-get update && sudo apt-get upgrade -y && sudo reboot
```

It fixed the graphic issue.

CPU overheating is gone, CPU is at 50°C at iddle and goes up to 60°C sometimes.
I really don't know why but I'm happy that it works fine :D Sorry for those how seek a solution...

---

