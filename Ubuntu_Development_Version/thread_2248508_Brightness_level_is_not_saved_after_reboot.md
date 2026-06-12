---
title: "Brightness level is not saved after reboot"
date: 2014-10-15
forum: Ubuntu Development Version
---

### Post by tamir2 on 2014-10-15
How to fix?
OS - Ubuntu 14.10


```
tr@tr-lp:~$ lspci -k | grep -E "VGA|3D"
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Trinity [Radeon HD 7520G]
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Thames [Radeon HD 7500M/7600M Series] (rev ff)
tr@tr-lp:~$ lspci -k | grep VGA -A2
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Trinity [Radeon HD 7520G]
    Subsystem: Samsung Electronics Co Ltd Device c0da
    Kernel driver in use: radeon
--
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Thames [Radeon HD 7500M/7600M Series] (rev ff)
    Kernel driver in use: radeon
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 09)
tr@tr-lp:~$ 

```

---

### Post by tamir2 on 2014-12-04
Waiting for new open source drivers)).

---

### Post by tamir2 on 2014-12-22
It turns out that the bug-report  has long existed. Link - [https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/1270579](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/1270579)

Please everyone affected from the same problem confirms this on page report, click on the Does this bug affect you? - More - Yes, it affects me.

Currently, the system default upstart **init** goes (including the latest LTS ), this method of solving the problem will be very relevant.

---

### Post by pqwoerituytrueiwoq on 2014-12-22
[http://pastebin.com/HzzHrS2g](http://pastebin.com/HzzHrS2g) - backlightx (i have a intel laptop, should still work for amd)
i rigged some scripts to do this 
```
~$ cat /usr/local/bin/greeter-setup-script
#!/bin/bash
numlockx on
if [ -f /var/log/backlightx ];then
    val=$(cat /var/log/backlightx)
    if [ ${#val} -gt 0 ];then
        xbacklight -set $((10*$val))
    fi
fi
```
```
~$ cat /usr/local/bin/session-cleanup-script 
#!/bin/bash
backlightx --get current > /var/log/backlightx
```
```
~$ cat /etc/lightdm/lightdm.conf
[SeatDefaults]
greeter-session=lightdm-gtk-greeter
user-session=xubuntu
greeter-setup-script=/usr/local/bin/greeter-setup-script
session-cleanup-script=/usr/local/bin/session-cleanup-script
#session-setup-script=
#display-setup-script =
```

---

