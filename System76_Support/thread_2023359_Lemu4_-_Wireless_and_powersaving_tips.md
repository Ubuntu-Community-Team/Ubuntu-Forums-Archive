---
title: "Lemu4 - Wireless and powersaving tips"
date: 2012-07-12
forum: System76 Support
---

### Post by gaussian on 2012-07-12
First, let me state that your mileage may vary and that you might not encounter any of the problems that I describe below. Nor might you be interested in my laptop-mode hacks. I have had my Lemur for few weeks now and it is the coolest computer I have ever owned. 

My Lemur has an Intel Corporation Centrino Advanced-N 6235 wireless card. After lot of debugging I noticed two ongoing problems with the wireless card:
1) If the wireless card was put into Powersave mode the connection quality dropped dramatically. By playing with "powertop" leaving ping to my router open I get 1-3ms ping times with power saving disabled and 50-200ms ping times to my router (or iwconfig reported connection speeds of 100+MBs vs 1MBs) when power saving is on.
2) Irrespective of power-saving status suspending the computer deteriorates the wireless connection similarly.

I don't know if some of this was brought on by enabling laptop-tools and if you are not experiencing any connection problems do not follow my instructions below. But if you have connection problems, these might help. 

**Wireless**

1) In /etc/laptop-mode.conf/wireless-power.conf add the following configurations

```
# Control generic wireless interface power saving mode?
CONTROL_WIRELESS_POWER_SAVING="auto"

WIRELESS_AC_POWER_SAVING=0
#WIRELESS_BATT_POWER_SAVING=1
WIRELESS_BATT_POWER_SAVING=0

```

This is somewhat confusing, since while this is an Intel Pro wireless card, it is not (as far as I understand) a card controlled by either wireless-ipw-power.conf or wireless-iwl-power.conf. This takes care in my machine of all the non-suspend related problems.

2) Suspend problems:
In a file with a name of your choosing (mine is "nowireless") in the directory /etc/pm/config.d put the following lines:
```

HOOK_BLACKLIST="wireless"
SUSPEND_MODULES="iwlwifi"

```

The first line prevents /usr/lib/pm-utils/power.d/wireless from being run. Looking at the code it has hard coded messing up with wireless power management. The second line performs removal and reloading of the wifi driver with a suspend/wake-up sequence.

**Laptop-Mode Configurations**

I wanted to do two things with laptop-mode. 
1) Put my cpu to "powersave" governor when on battery. It is not clear that this actually saves any power, but at least it lowers the cpu temperature and heat emissions. 
2) Lower automatically the screen brightness when on battery.

After installing laptop-mode I also noticed that a clicking noise from the headphones (but not the speakers) that is caused by putting the audio driver to powersave mode. Hence:
3) Fix the clicking sound.

1) Cpu-governor: Put the following configurations to /etc/laptop-mode/conf.f/cpufreq.conf

```

BATT_CPU_MAXFREQ=fastest
BATT_CPU_MINFREQ=slowest
BATT_CPU_GOVERNOR=powersave

```

2) LCD Brightness:
Put the following code /etc/laptop-mode/lcd-brightness.conf
```

CONTROL_BRIGHTNESS=1

BATT_BRIGHTNESS_COMMAND="echo 2"
LM_AC_BRIGHTNESS_COMMAND="echo 4"
NOLM_AC_BRIGHTNESS_COMMAND="echo 4"
BRIGHTNESS_OUTPUT="/sys/class/backlight/acpi_video0/brightness"


```

Legal values for the brightness range from 1 (or 0, not sure) to 7.

3) Fixing the clicking sound:
Put the following code to /etc/laptop-mode/config.d/intel-hda-powersave.conf

```

# Control INTEL HDA audio chipset power?
# Set to 0 to disable
#CONTROL_INTEL_HDA_POWER="auto"
CONTROL_INTEL_HDA_POWER=1

# Handle power savings for Intel HDA under specific circumstances
#BATT_INTEL_HDA_POWERSAVE=1
BATT_INTEL_HDA_POWERSAVE=0
LM_AC_INTEL_HDA_POWERSAVE=0
NOLM_AC_INTEL_HDA_POWERSAVE=0

# Number of seconds to wait before you want the device to time out
INTEL_HDA_DEVICE_TIMEOUT=2

# Disable controller on Device timeout
# This saves more power
# However you might want to disable this if you get annoyed by the 
# "click" sound when the device wakes up again
#
# Set this to 1 to enable power savings for the controller also
INTEL_HDA_DEVICE_CONTROLLER=0


```

YMMV.

---

