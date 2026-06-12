---
title: "collectd-exec not working"
date: 2010-05-11
forum: Server Platforms
---

### Post by deadite66 on 2010-05-11
using 10.04 and i can't get this to work any ideas?

relevent bits from collectd.conf 
```
LoadPlugin exec
<Plugin exec>
#	Exec "lee" "/etc/collectd/getgput"
	Exec "lee:lee" "/etc/collectd/getgput"
#	NotificationExec user "/path/to/exec"
</Plugin>

```

execute bit set
```
lee@sakura:/var/lib/collectd/rrd/sakura$ ls -l /etc/collectd/getgput 
-rwxr-xr-x 1 root root 182 2010-05-11 11:28 /etc/collectd/getgput
```

script
```
#!/bin/sh
while true; do
export DISPLAY=:0.0
GPUT="nvclock -T | grep GPU | cut -b 21,22" 
echo "PUTVAL sakura/gpu/gpu-temp interval=10 $(eval date +%s):$(eval $GPUT)"
sleep 10
done
```

what the script outputs
```
lee@sakura:/var/lib/collectd/rrd/sakura$ /etc/collectd/getgput 
PUTVAL sakura/gpu/gpu-temp interval=10 1273574200:62
PUTVAL sakura/gpu/gpu-temp interval=10 1273574210:62
PUTVAL sakura/gpu/gpu-temp interval=10 1273574221:62
PUTVAL sakura/gpu/gpu-temp interval=10 1273574231:62
```

no gpu folder
```
lee@sakura:/var/lib/collectd/rrd/sakura$ ls
cpu-0     disk-sda1  disk-sda6  disk-sr0   load                      thermal-cooling_device1
cpufreq   disk-sda2  disk-sdb   hddtemp    sensors-acpitz-virtual-0  thermal-thermal_zone0
disk-sda  disk-sda5  disk-sdb1  interface  thermal-cooling_device0   uptime
```



i have log set to debug but still don't much help
```
[2010-05-11 11:18:28] Exiting normally.
[2010-05-11 11:18:28] collectd: Stopping 5 read threads.
[2010-05-11 11:18:28] exec plugin: Sent SIGTERM to 22683
[2010-05-11 11:18:28] rrdtool plugin: Shutting down the queue thread. This may take a while.
[2010-05-11 11:18:30] cpufreq plugin: Found 1 CPU
[2010-05-11 11:18:30] Initialization complete, entering read-loop.

```

---

### Post by 0nelove on 2010-06-25
ever get this worked out?

---

### Post by deadite66 on 2010-06-25
yes the filename of a rrd created must start with one of the defined type in /usr/share/collectd/types.db

```
#!/bin/sh
while true; do
export DISPLAY=:0.0
GPUT="nvclock -T | grep GPU | cut -b 21,22" 
#echo "PUTVAL sakura/gpu/temperature interval=10 date +%s):$(eval $GPUT)"
echo "PUTVAL sakura/gpu/temperature interval=10 N:$(eval $GPUT)"
sleep 10
done

```

so i replaced gpu-temp with temperature, you can add extra text after temperature to help separate different rrd's ie. temperature-cpu_one

---

