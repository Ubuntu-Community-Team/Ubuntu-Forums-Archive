---
title: "Fan control / Power-Noise optimization on the Proliant DL120 G6 under Ubuntu Server?"
date: 2011-07-12
forum: Server Platforms
---

### Post by renauddenis on 2011-07-12
Hi, I'm trying to get the HP Proliant DL120 G6 server a lot quieter after startup under Ubuntu Server 11.04 (x64).

For now, it seems like there is no fan control at all: when I start the server, the fans start running at max speed, then it slightly lowers to 3.5K-5K RPM. Once there, it never goes down or up. There's just no fan or power control at all.

In no specific order, I will describe as much as I can my situation.

----

The system is IPMI 2.0 compliant, so when using the ipmitool package I can get the values of the sensors like this:

```
$sudo ipmitool sdr

Fan1 Front Rotor | 4611.70 RPM       | ok
Fan1 Rear Rotor  | 3689.36 RPM       | ok
Fan2 Front Rotor | 4611.70 RPM       | ok
Fan2 Rear Rotor  | 3806.48 RPM       | ok
Fan3 Front Rotor | 4996.00 RPM       | ok
Fan3 Rear Rotor  | 3747.00 RPM       | ok
Fan4 Front Rotor | 5450.19 RPM       | ok
Fan4 Rear Rotor  | 4440.89 RPM       | ok
System Amb Temp  | 23 degrees C      | ok
CPU Temp         | 30 degrees C      | ok
PCI Ambient Temp | 24.50 degrees C   | ok
Rear DIMM Amb Te | 29 degrees C      | ok
DIMM3A Temp      | 28.50 degrees C   | ok

```

----

I tried to follow the procedures for using the fancontrol package together with lm-sensors, as shown at [http://tuxtweaks.com/2008/08/how-to-control-fan-speeds-in-ubuntu/](http://tuxtweaks.com/2008/08/how-to-control-fan-speeds-in-ubuntu/). One of the very first steps is to launch "sensors-detect", which gives:

```
Now follows a summary of the probes I have just done.
Just press ENTER to continue:

Driver `coretemp':
  * Chip `Intel digital thermal sensor' (confidence: 9)

Driver `ipmisensors':
  * ISA bus, address 0xca2
    Chip `IPMI BMC KCS' (confidence: 8)

Warning: the required module ipmisensors is not currently installed
on your system. If it is built into the kernel then it's OK.
Otherwise, check http://www.lm-sensors.org/wiki/Devices for
driver availability.

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Adapter drivers
ipmi-si
# Chip drivers
coretemp
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

```

The module ipmisensors does not seem to exist at all, even in recent versions of the kernel. There is an open bug in launchpad at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/329012](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/329012), but it looks expired for a long time.

Further, without this kernel module, there seems to be no way for pwmconfig to probe the sensors and create the fancontrol configuration, so I'm stuck there.

----

I installed the HP utilities from the Debian stable HP repository: hp-health, in particular. Here is what's in the log of hp-health:

```
ERROR: /proc/acpi/dsdt does not exist
Cannot use ACPI tables to identify system
Trying to identify the Product Name...  Done
Using Proliant Standard
      IPMI based 1XX System Health Monitor
Using standard Linux IPMI device driver
Starting Proliant Standard
      IPMI based 1XX System Health Monitor (hpasmpld):

```      

I'm not sure that the missing /proc/acpi/dsdt means anything, since hp-health succeed to identify the system afterward. On recent versions of Ubuntu, DSDT tables seem to be stored at /sys/firmware/acpi/tables/DSDT&#65279;, but not in /proc/acpi/dsdt anymore

Here is what I have under /proc/acpi:

```
$ls /proc/acpi
ac_adapter  battery  button  event  wakeup

```

So not much I fear.

----

I also opened a case at HP, but I have no reaction so far. I don't think I must expect one since Ubuntu Server is not on their supported systems list.

[http://h30499.www3.hp.com/t5/ProLiant-Servers-ML-DL-SL/Fan-control-Power-Noise-optimization-on-the-Proliant-DL120-G6/td-p/4815357](http://h30499.www3.hp.com/t5/ProLiant-Servers-ML-DL-SL/Fan-control-Power-Noise-optimization-on-the-Proliant-DL120-G6/td-p/4815357)

----

If anyone can help me on this, I'd appreciate it a lot.

---

### Post by psusi on 2011-07-12
It looks like you don't have any supported fan controllers.  Take a look at what you have in /sys/class/hwmon to make sure.  Without that, the fan speed is entirely controlled by the hardware.  You might find some options to affect it in the bios, but that's it.

---

### Post by renauddenis on 2011-07-12
@psusi Thanks for the answer, here is the content of /sys/class/hwmon

```
$ ls -R /sys/class/hwmon/*
/sys/class/hwmon/hwmon0:
device  power  subsystem  uevent

/sys/class/hwmon/hwmon0/power:
autosuspend_delay_ms  runtime_status          wakeup_active        wakeup_hit_count     wakeup_total_time_ms
control               runtime_suspended_time  wakeup_active_count  wakeup_last_time_ms
runtime_active_time   wakeup                  wakeup_count         wakeup_max_time_ms

/sys/class/hwmon/hwmon1:
device  power  subsystem  uevent

/sys/class/hwmon/hwmon1/power:
autosuspend_delay_ms  runtime_status          wakeup_active        wakeup_hit_count     wakeup_total_time_ms
control               runtime_suspended_time  wakeup_active_count  wakeup_last_time_ms
runtime_active_time   wakeup                  wakeup_count         wakeup_max_time_ms
```

If I understand well, you think that IPMI is not supported somehow, since I can monitor the values of all the sensors (including all the fans) using ipmitool and such... ? There must be a way...

---

### Post by psusi on 2011-07-12
I don't know much about IPMI, but it doesn't sound like it is capable of controlling, only reporting.

---

### Post by renauddenis on 2011-07-16
Perhaps I am naive, but do you think there is any chance that someone at Canonical would contact someone at HP to find out if there is a way to actually make the power/fan control work seamlessly using Ubuntu Server and HP Proliant Series?

---

### Post by tgalati4 on 2011-07-16
Rack servers are designed for racks--in server rooms.  I have a couple of noisey Dell Poweredge servers in my garage.

I can't hear them in the house.

No fan control on the Dell rack servers either.  Only BIOS control.

---

### Post by renauddenis on 2011-07-16
So you tell me that rack servers' hardware does not need to be monitored and controlled basically, and that cooling systems are meant to run at full power all the time, regardless of the ecological footprint or noise disturbances :)

I personally think it's worth looking at why Ubuntu 11.04, when running on a rack server, can't do what it can do when running on my Dell laptop, don't you?

Update: s/when running on a rack server/when running on - most likely - any kind of HP Proliant and (according to you) Dell Poweredge servers/

---

### Post by psusi on 2011-07-16
Either you have hardware that supports controlling the fans, or you don't.  You appear not to, which is no surprise since rack mount servers are designed to be mounted in a cabinet in a room full of loud computers.  The design goal is to keep the system cool so it keeps running, not to be quiet.

---

### Post by renauddenis on 2011-07-17
I don't think it's a matter of having a hardware that supports controlling the fans here. It looks like it's more like a missing driver or something (see above: sensors-detect and impisensors)

[http://bmcsensors-26.sourceforge.net](http://bmcsensors-26.sourceforge.net)

I'm pretty sure it would work under Windows Server, maybe I should switch the main hard drive and give it a try.

---

