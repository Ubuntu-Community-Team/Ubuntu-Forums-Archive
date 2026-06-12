---
title: "landscape showing wrong temperature on HP Proliants"
date: 2010-12-09
forum: Server Platforms
---

### Post by vladoportos on 2010-12-09
Hello All,

Here is quick fix I did for HP Proliant servers where landscape shows wrong temperature eg:

root ~ # **[COLOR=Blue]landscape-sysinfo[/COLOR]**
  System load:  0.12               Temperature:         [COLOR=Red]**8 C  <----- WTF **[/COLOR]
  Usage of /:   0.2% of 808.13GB   Processes:           214
  Memory usage: 8%                 Users logged in:     1
  Swap usage:   0%                 IP address for eth0: xxxxxxxxxxxxx


issue is that ACPI doesn't work like it should... 

root ~ # [COLOR=Blue]**find /proc/acpi/thermal_zone -type f |xargs cat**[/COLOR]
<polling disabled>
0 - Active; 1 - Passive
critical (S5):           31 C
passive:                 10 C: tc1=4 tc2=4 tsp=60 devices=CPU0
temperature:             8 C
state:                   ok

This include HP DL 360 G6 / G4 and other Proliants.. new and old... as well Ubuntu server edition 10.10 and 10.04

So there are two solutions... either get ACPI working ( no idea how )

Or install HP support pack software so you can get "hpasmcli"

For Ubuntu 10.10 on Proliant DL360 G6 its easy as there are already deb packages from HP on their site.. they say that they are for 10.04 but works at 10.10 as well.. 

[COLOR=Red]**SOLUTION:**[/COLOR]

Make sure that you get good temperatures from this command:

root ~ #**[COLOR=Blue] hpasmcli -s "show temp"[/COLOR]**

Sensor   Location              Temp       Threshold
------   --------              ----       ---------
#1        AMBIENT              18C/64F    42C/107F
#2        CPU#1                0C/32F     82C/179F
#3        CPU#2                 -         82C/179F
#4        MEMORY_BD            22C/71F    87C/188F
#5        MEMORY_BD            22C/71F    78C/172F
#6        MEMORY_BD            22C/71F    87C/188F
#7        MEMORY_BD            21C/69F    78C/172F
#8        MEMORY_BD             -         87C/188F
#9        MEMORY_BD            22C/71F    78C/172F
#10       MEMORY_BD             -         87C/188F
#11       MEMORY_BD            22C/71F    78C/172F
#12       POWER_SUPPLY_BAY     23C/73F    59C/138F
#13       POWER_SUPPLY_BAY     28C/82F    73C/163F
#14       MEMORY_BD            21C/69F    72C/161F
#15       PROCESSOR_ZONE       21C/69F    73C/163F
#16       PROCESSOR_ZONE       22C/71F    64C/147F
#17       MEMORY_BD            21C/69F    63C/145F
#18       PROCESSOR_ZONE       23C/73F    69C/156F
#19       SYSTEM_BD            22C/71F    69C/156F
#20       SYSTEM_BD            23C/73F    71C/159F
#21       SYSTEM_BD            26C/78F    65C/149F
#22       SYSTEM_BD            26C/78F    71C/159F
#23       SYSTEM_BD            23C/73F    69C/156F
#24       SYSTEM_BD            26C/78F    69C/156F
#25       SYSTEM_BD            23C/73F    63C/145F
#26       SYSTEM_BD            24C/75F    66C/150F
#27       SCSI_BACKPLANE_ZONE  50C/122F   60C/140F
#28       SYSTEM_BD            36C/96F    110C/230F

I still get some wired CPU 0C temp on this server but on older G4 it works fine:

root@Destro:~# **[COLOR=Blue]hpasmcli -s "show temp"[/COLOR]**

Sensor   Location              Temp       Threshold
------   --------              ----       ---------
#0        SYSTEM_BD             -          -
#1        SYSTEM_BD            36C/96F    54C/129F
#2        CPU#1                32C/89F    60C/140F
#3        CPU#2                28C/82F    60C/140F


So for our purpose I'm going to use the AMBIENT temperature from my G6 server... 


You need to find the files that landscape is using to get temperature:

root ~ # [COLOR=Blue]**find / -type f -name temperature.py**[/COLOR]
/usr/share/pyshared/landscape/monitor/temperature.py
/usr/share/pyshared/landscape/sysinfo/temperature.py

you need this one:
[B]
/usr/share/pyshared/landscape/sysinfo/temperature.py[/B]

cd to that folder, make backup of it.

[B][COLOR=Blue]#cd /usr/share/pyshared/landscape/sysinfo/
#cp temperature.py temperature.py_bkp[/COLOR][/B]

And now replace the script inside of temperature.py with this:
```
from twisted.internet.defer import succeed
import os
from landscape.lib.sysstats import get_thermal_zones


class Temperature(object):

    def __init__(self, thermal_zone_path=None):
        self._thermal_zone_path = thermal_zone_path

    def register(self, sysinfo):
        self._sysinfo = sysinfo

    def run(self):
        temperature = None
        max_value = None
        for zone in get_thermal_zones(self._thermal_zone_path):
            if (zone.temperature_value is not None and
                (max_value is None or zone.temperature_value > max_value)):
                temperature = zone.temperature
                max_value = zone.temperature_value
        if temperature is not None:
           stdout_handle = os.popen('hpasmcli -s "show temp" | grep "AMBIENT" ')
           text = stdout_handle.read()
           text = text.split()
           self._sysinfo.add_header("Temperature", text[2])
        return succeed(None)
```as you can see I'm grepping and parsing the temperature from output of  hpasmcli

and the results ? :

root /usr/share/pyshared/landscape/sysinfo # landscape-sysinfo
  System load:  0.0                Temperature:         19C/66F
  Usage of /:   0.2% of 808.13GB   Processes:           211
  Memory usage: 8%                 Users logged in:     1
  Swap usage:   0%                 IP address for eth0: xxxxxxx

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)

Working info :) 

I know it is dirty fix but hey ! better than nothing :)

In any case safe the new **temperature.py,** in case it gets replaced in update or something....  ( if somebody know python better you can cut out the rest of the useless script part that doesn't work and post your results...) 

Comments are welcome
VladoPortos

---

### Post by OnTarget600 on 2011-03-06
That was great work. 

Thanks mate.

---

### Post by XPinG on 2011-11-13
I spent a lot of time searching for that when I finaly found the right way to do it I made that easy to follow copy-past install procedure, hope that it will be usefull for someone
```
cd /tmp
wget [http://downloads.linux.hp.com/SDR/downloads/bootstrap.sh](http://downloads.linux.hp.com/SDR/downloads/bootstrap.sh)
chmod +x bootstrap.sh
sudo ./bootstrap.sh -n ProLiantSupportPack
sudo apt-get update
sudo apt-get install hp-health
```

you have now access to hpasmcli command :)

---

