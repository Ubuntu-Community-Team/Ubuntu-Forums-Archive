---
title: "Landscape-Sysinfo - edit to display º f in MOTD"
date: 2010-06-23
forum: Server Platforms
---

### Post by dkelley033 on 2010-06-23
so theres a few fixes for y'all's complaints:
im running ubuntu server 10.04 x64
landscape python scripts are in 
/usr/share/pyshared/landscape/sysinfo/
 
things i have edited are bolded
 
Ad Banner:
change landscapelink.py to read as follows (just delete the link and return header lines)
 
```
 
from twisted.internet.defer import succeed
class LandscapeLink(object):
def register(self, sysinfo):
self._sysinfo = sysinfo
def run(self):
return succeed(None)

```
 
 
Disk usage path:
edit the following line (bolded path) in disk.py to reflect the location you want to display disk usage information for. theres also another line farther down that reference /home that you can change as well...
 
```
 
class Disk(object):
def __init__(self, mounts_file="/proc/mounts", statvfs=os.statvfs):
self._mounts_file = mounts_file
self._statvfs = statvfs
def register(self, sysinfo):
self._sysinfo = sysinfo
def run(self):
main_info = get_filesystem_for_path("/**media/Storage**", self._mounts_file,
self._statvfs, STABLE_FILESYSTEMS)

```
 
 
temperature: display both ºC and ºF 
edit temperature.py
 
```
 
from twisted.internet.defer import succeed
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
**n = int(zone.temperature_value)* (9.0/5.0) + 32**
max_value = zone.temperature_value
if temperature is not None:
self._sysinfo.add_header("Temperature", temperature** + " " + str(n) + " F"**)
return succeed(None)

```
 
hope someone finds this useful...

---

### Post by Sultore on 2012-06-07
So, at least one person found this useful!

2 years later and it's still helpful. Thanks!

---

### Post by xdracco on 2012-09-04
And another person found this useful..... 2 years later.. thanks!

---

### Post by PyrexKidd on 2012-09-24
Me too!  though, if you are on a minimal install, you will need to install the update-motd and landscape-common packages.

---

