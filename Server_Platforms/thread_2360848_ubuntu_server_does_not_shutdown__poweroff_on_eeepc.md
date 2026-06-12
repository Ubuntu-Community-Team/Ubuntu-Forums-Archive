---
title: "ubuntu server does not shutdown / poweroff on eeepc 1000h"
date: 2017-05-09
forum: Server Platforms
---

### Post by pruda on 2017-05-09
Hi, I have old laptop with broken screen and I want to use it as ssh command line. The goal is to wake on selected time, record from dvb-t and shut down again. So I picked ubuntu server. It runs and boots fast and fine, but it refuses to shut down. It actually shuts down for a second or two (leds, fan, hdd go off), but wakes instantly again, the same bahvior is with sudo poweroff, sudo shutdown or using power button. I have followed some hints and tried to add some acpi parameters to grub, flashed last bios, but it still behaves the same. Anyone experienced this behaviour on this laptop?

I can just leave it running, because it does not consume a lot of power, but I need to record only one or two things per week, so it would only burn energy. I want to find out, because this bugs me ;-) Thank you. Ruda

edit: Ubuntu 17.04 (GNU/Linux 4.10.0-20-generic i686)

---

### Post by mastablasta on 2017-05-09
check the logs to see what it is doing (found in /var/log)

---

### Post by slickymaster on 2017-05-09
*Thread moved to **Server Platforms**.*

---

### Post by pruda on 2017-05-09
> **mastablasta said:**
> check the logs to see what it is doing (found in /var/log)

Hi, thank you for reply. What exactly are we looking for?

```
cat /var/log/syslog
May  9 12:55:48 ubuntus systemd[1]: Stopped Stop ureadahead data collection 45s after completed startup.
May  9 12:55:48 ubuntus systemd[1]: Stopped target Graphical Interface.
May  9 12:55:48 ubuntus systemd[1]: Stopping Accounts Service...
May  9 12:55:48 ubuntus systemd[1]: Stopping ACPI event daemon...
May  9 12:55:48 ubuntus systemd[1]: Stopped target Timers.
May  9 12:55:48 ubuntus systemd[1]: Stopped Daily apt activities.
May  9 12:55:48 ubuntus systemd[1]: Stopped Clean PHP session files every 30 mins.
May  9 12:55:48 ubuntus systemd[1]: Stopped Timer to automatically refresh installed snaps.
May  9 12:55:48 ubuntus systemd[1]: Stopped target System Time Synchronized.
May  9 12:55:48 ubuntus systemd[1]: Stopping User Manager for UID 1000...
May  9 12:55:49 ubuntus rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="1022" x-info="http://www.rsyslog.com"] exiting on signal 15.
May  9 12:56:47 ubuntus rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="918" x-info="http://www.rsyslog.com"] start
May  9 12:56:47 ubuntus rsyslogd: rsyslogd's groupid changed to 108
May  9 12:56:47 ubuntus rsyslogd: rsyslogd's userid changed to 104
May  9 12:56:47 ubuntus systemd[1]: Started Uncomplicated firewall.
May  9 12:56:47 ubuntus systemd[1]: Started Create list of required static device nodes for the current kernel.
May  9 12:56:47 ubuntus systemd[1]: Starting Create Static Device Nodes in /dev...
May  9 12:56:47 ubuntus systemd[1]: Started Create Static Device Nodes in /dev.
May  9 12:56:47 ubuntus systemd-modules-load[362]: Inserted module 'iscsi_tcp'
May  9 12:56:47 ubuntus systemd[1]: Starting udev Kernel Device Manager...
May  9 12:56:47 ubuntus systemd[1]: Mounted Huge Pages File System.
May  9 12:56:47 ubuntus systemd[1]: Mounted Debug File System.
May  9 12:56:47 ubuntus systemd[1]: Mounted POSIX Message Queue File System.
May  9 12:56:47 ubuntus systemd[1]: Started LVM2 metadata daemon.
May  9 12:56:47 ubuntus rsyslogd-2039: Could not open output pipe '/dev/xconsole':: No such file or directory [v8.16.0 try http://www.rsyslog.com/e/2039 ]
May  9 12:56:47 ubuntus systemd[1]: Started Nameserver information manager.
May  9 12:56:47 ubuntus keyboard-setup.sh[364]:  * Setting up keyboard layout...
May  9 12:56:47 ubuntus keyboard-setup.sh[364]:    ...done.
May  9 12:56:47 ubuntus rsyslogd-2007: action 'action 10' suspended, next retry is Tue May  9 12:57:17 2017 [v8.16.0 try http://www.rsyslog.com/e/2007 ]
May  9 12:56:47 ubuntus systemd[1]: Started Set the console keyboard layout.
May  9 12:56:47 ubuntus systemd[1]: Started udev Kernel Device Manager.
May  9 12:56:47 ubuntus systemd[1]: Starting Remount Root and Kernel File Systems...
May  9 12:56:47 ubuntus lvm[352]:   2 logical volume(s) in volume group "ubuntus-vg" monitored
May  9 12:56:47 ubuntus systemd[1]: Started Monitoring of LVM2 mirrors, snapshots etc. using dmeventd or progress polling.
May  9 12:56:47 ubuntus systemd-modules-load[362]: Inserted module 'ib_iser'
May  9 12:56:47 ubuntus systemd[1]: Started Load Kernel Modules.
May  9 12:56:47 ubuntus systemd[1]: Mounting FUSE Control File System...
May  9 12:56:47 ubuntus systemd[1]: Mounting Configuration File System...
May  9 12:56:47 ubuntus systemd[1]: Starting Apply Kernel Variables...
May  9 12:56:47 ubuntus systemd[1]: Mounted FUSE Control File System.
May  9 12:56:47 ubuntus systemd[1]: Mounted Configuration File System.
May  9 12:56:47 ubuntus systemd[1]: Started Remount Root and Kernel File Systems.
May  9 12:56:47 ubuntus systemd[1]: Reached target Local File Systems (Pre).
May  9 12:56:47 ubuntus systemd[1]: Reached target Local File Systems.
May  9 12:56:47 ubuntus systemd[1]: Starting Set console font and keymap...
May  9 12:56:47 ubuntus systemd[1]: Starting Tell Plymouth To Write Out Runtime Data...
May  9 12:56:47 ubuntus systemd[1]: Starting ebtables ruleset management...
May  9 12:56:47 ubuntus systemd[1]: Starting AppArmor initialization...
May  9 12:56:47 ubuntus systemd[1]: Starting Load/Save Random Seed...
May  9 12:56:47 ubuntus systemd[1]: Starting Flush Journal to Persistent Storage...
May  9 12:56:47 ubuntus systemd[1]: Starting udev Coldplug all Devices...
May  9 12:56:47 ubuntus systemd[1]: Started Apply Kernel Variables.
May  9 12:56:47 ubuntus systemd[1]: Started Tell Plymouth To Write Out Runtime Data.
May  9 12:56:47 ubuntus systemd[1]: Started Set console font and keymap.
May  9 12:56:47 ubuntus systemd[1]: Started Load/Save Random Seed.
May  9 12:56:47 ubuntus systemd[1]: Started Flush Journal to Persistent Storage.
May  9 12:56:47 ubuntus systemd[1]: Started ebtables ruleset management.
May  9 12:56:47 ubuntus systemd[1]: Reached target Network (Pre).
May  9 12:56:47 ubuntus systemd[1]: Starting Create Volatile Files and Directories...
May  9 12:56:47 ubuntus systemd-tmpfiles[484]: [/usr/lib/tmpfiles.d/var.conf:14] Duplicate line for path "/var/log", ignoring.
May  9 12:56:47 ubuntus systemd[1]: Started udev Coldplug all Devices.
May  9 12:56:47 ubuntus systemd[1]: Started Dispatch Password Requests to Console Directory Watch.
May  9 12:56:47 ubuntus systemd[1]: Reached target Encrypted Volumes.
May  9 12:56:47 ubuntus apparmor[443]:  * Starting AppArmor profiles
May  9 12:56:47 ubuntus systemd[1]: Started Create Volatile Files and Directories.
May  9 12:56:47 ubuntus kernel: [    0.000000] Linux version 4.10.0-20-generic (buildd@lcy01-03) (gcc version 6.3.0 20170406 (Ubuntu 6.3.0-12ubuntu2) ) #22-Ubuntu SMP Thu Apr 20 09:22:16 UTC 2017 (Ubuntu 4.10.0-20.22-generic 4.10.8)
May  9 12:56:47 ubuntus kernel: [    0.000000] KERNEL supported cpus:
May  9 12:56:47 ubuntus systemd[1]: Starting Network Time Synchronization...
May  9 12:56:47 ubuntus kernel: [    0.000000]   Intel GenuineIntel
May  9 12:56:47 ubuntus kernel: [    0.000000]   AMD AuthenticAMD
May  9 12:56:47 ubuntus kernel: [    0.000000]   NSC Geode by NSC
.
.
```

full dump: [https://pastebin.com/EZ3iCyxb](https://pastebin.com/EZ3iCyxb)

---

### Post by pruda on 2017-05-09
> **slickymaster said:**
> *Thread moved to **Server Platforms**.*

I don't think this thread deserves to be in the server thread, just because I use the server edition to get rid of the GUI... I'd not mind, except here I won't get support at all, because people using server edition usually don't power their servers off :-(

---

### Post by Aphexlog on 2017-05-09
If all you are trying to do is shut down, then try running ```
sudo init 0
```

---

### Post by Aphexlog on 2017-05-09
Because you are running a later version of Ubuntu, perhaps try using ```
[COLOR=#1A1A1A][FONT=Menlo]systemctl poweroff[/FONT][/COLOR]
``` instead

---

### Post by QIII on 2017-05-09
> **pruda said:**
> I don't think this thread deserves to be in the server thread, just because I use the server edition to get rid of the GUI... I'd not mind, except here I won't get support at all, because people using server edition usually don't power their servers off :-(

Hello!

You are using the Server edition, so your question does belong here.

People do shut their servers down for physical maintenance or upgrade from time to time, so I wouldn't worru that nobody will have an answer.

Cheers!

---

### Post by pruda on 2017-05-09
Thank you, Aphexlog, but systemctl poweroff behaves the same as sudo init 0 and sudo shutdown, means systems is powered off for 1 second and then it wakes and starts again. And thanks QIII for clarifying, I hope you are right.

---

### Post by mastablasta on 2017-05-10
look for time stamps on shut down and start up. 

if you already set it up to wake perhaps the configuration is wrong!? and rather than waking up at specified time it wakes up immediatelly.

---

### Post by pruda on 2017-05-10
> **mastablasta said:**
> look for time stamps on shut down and start up. 

if you already set it up to wake perhaps the configuration is wrong!? and rather than waking up at specified time it wakes up immediatelly.

I looked, I don't see anything strange during shutdown. I have wake disabled now, so it should not be problem too. ```
cat /proc/driver/rtc
rtc_time        : 11:01:51
rtc_date        : 2017-05-10
alrm_time       : 12:16:35
alrm_date       : 2017-05-10
alarm_IRQ       : no
alrm_pending    : no
update IRQ enabled      : no
periodic IRQ enabled    : no
periodic IRQ frequency  : 1024
max user IRQ frequency  : 64
24hr            : yes
periodic_IRQ    : no
update_IRQ      : no
HPET_emulated   : yes
BCD             : yes
DST_enable      : no
periodic_freq   : 1024
batt_status     : okay

```

Why is the system waking? There should be reason which triggers the power on one second after shut down, but there's nothing in the logs which I have uploaded.

---

### Post by ian-weisser on 2017-05-10
When the system restarts immediately after a poweroff, is it the complete boot cycle? Including the POST and manufacturer logo?
Or is it a faster startup that skips the manufacturer logo?

---

### Post by pruda on 2017-05-11
Laptop goes completely off for 1-2 seconds after shutdown command, but then turns on again and starts to cold boot showing manufacturer logo (or bios post messages, depending on bios setting).

---

### Post by ian-weisser on 2017-05-11
Ah, in that case check your BIOS settings.

A 'restart' command from software will clear memory and reload the OS from HDD...but won't hand back to BIOS nor POST.

---

### Post by pruda on 2017-05-11
I can set time or disable wbcam in bios, but that's about all, bios in this notebook is very simple. Tried to load bios defaults, but it refuses to shut down and stay shut down. Do you think it can be hardware issue? I don't know if it worked in windows, because I got it with dead windows, but I guess it was ok.

---

### Post by pruda on 2017-05-12
I have placed another disk with windows xp to netbook, booted it, tried to shut down from start menu and to my big surprise it behaves the same :confused:
I guess it is hardware issue, but I'm playing with computers more than 20 years and never seen anything like this. What can that be? Bios does not have any options which would enable/disable wake on lan etc.

---

### Post by ian-weisser on 2017-05-12
I've seen it before, mostly with servers - restart automatically upon shutdown or power restore.

---

### Post by pruda on 2017-05-25
But this is normal netbook. That's weird. I will have to use another netbook if I want to turn it off. :(

---

### Post by mastablasta on 2017-05-25
or a raspberry pi or similar board. might have simalar power for mush less energy usage.

---

