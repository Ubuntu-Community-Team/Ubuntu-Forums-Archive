---
title: "HALD not running -Can someone help?"
date: 2007-06-30
forum: Sun Sparc Users
---

### Post by sandpiper on 2007-06-30
Hi   Am running Feisty Desktop on Ultra 2 workstation. Have troubling getting HAL to initialise at startup.  Typing  "sudo hald --daemon=no  --use-syslog --verbose=yes"produces this report on the terminal screen:

$ sudo hald --daemon=no --verbose=yes --use-syslog
Runner started - allowed paths are '/usr/lib/hal:/usr/lib/hal/scripts:/usr/bin'
Run started hal-storage-cleanup-all-mountpoints (10000) (0) 
!  full path is '/usr/lib/hal/hal-storage-cleanup-all-mountpoints', program_dir is '/usr/lib/hal'
6182: XYA attempting to get lock on /media/.hal-mtab-lock
6182: XYA got lock on /media/.hal-mtab-lock
in hal-storage-cleanup-all-mountpoints
org.freedesktop.Hal.Device.Volume.UnknownFailure
Cannot open /media/.hal-mtab
/usr/lib/hal/hal-storage-cleanup-all-mountpoints exited
Run started hald-addon-cpufreq (0) (0) 
!  full path is '/usr/lib/hal/hald-addon-cpufreq', program_dir is '/usr/lib/hal'
11:57:47.655 [W] addon-cpufreq.c:1181: CPUFreq not supported. Exiting...
process 6175: arguments to dbus_pending_call_set_notify() were incorrect, assertion "pending != NULL" failed in file dbus-pending-call.c line 598.
This is normally a bug in some application using the D-Bus library.
*** [DIE] hald_runner.c:runner_died():168 : Runner died 

I am a newbie to Linux. I searched all forums and tried numerous suggestions but I still get this message above. I have no idea what the above means or where I should focus my efforts now to try and diagnose the problem. I have also checked there is "no" file: /media/.hal-mtab. There  "is" a file: /media/.hal-mtab-lock

Can someone help me our here..  even a quck indication of where should consult in the Linux docuements to get me started would help..... Chris

---

### Post by netztier on 2007-07-01
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/85592](https://bugs.launchpad.net/ubuntu/+bug/85592) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **sandpiper said:**
> Hi   Am running Feisty Desktop on Ultra 2 workstation. Have troubling getting HAL to initialise at startup.  


Same problem here - and not only here - Launchpad has a few entries about this, too:

[https://bugs.launchpad.net/ubuntu/+bug/85592](https://bugs.launchpad.net/ubuntu/+bug/85592)

> **sandpiper said:**
> 
Typing  "sudo hald --daemon=no  --use-syslog --verbose=yes"produces this report on the terminal screen:


Now that's something I should try, too. I generally just tried to restart dbus via it's init-script in /etc/init.d/
I'll keep you posted..

best regards

Marc

---

### Post by sandpiper on 2007-07-01
> **netztier said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/85592](https://bugs.launchpad.net/ubuntu/+bug/85592) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
	


Hey thanks for coming back Marc. Really appreciated. Yes I have looked at many bug reports like this over many weeks since I got Feisty Desktop running on my Ultra 2 workstation. While they gave me encouragement that I wasn't alone here they didn't give me a clue as to the "next diagnosis step" to take. The HAL and DBus software architecture is a little overwhelming for a Linux newbie like myself.. I need a little guidance......

I meant to mention in my previous post that in the boot up process (I have the messages displayed for diagnosis purposes) during the services invocation stuff I get displayed on the terminal screen the message:
Starting Hardware abstraction layer Hald 
run-parts: /etc/dbus-1/event.d/20hal exited with return code 1". 
  I have experimented with changing the priority start up  for HALD by making it earlier (moved to 8) but no change.

I have interpreted the syslog message in my original post to mean that I have an application that is causing HALD to crash. But I am not sure whether this error is related to running the  script " hald-addon-cpufreq" that is referred to in the error log or not. One of my questions is how can I prevent this part of the Hald script from running given it is XML to prove this is the culprit.... like does the Ultra 2 have this CPUfreq change capability......'   questions questions.... regards  Chris

---

### Post by sandpiper on 2007-07-05
> **sandpiper said:**
> 
I have interpreted the syslog message in my original post to mean that I have an application that is causing HALD to crash. But I am not sure whether this error is related to running the  script " hald-addon-cpufreq" that is referred to in the error log or not.

Update for Marc (and others if they are interested ;-))

I think I have made some progress. I got this gem of wisdom from my  "googling" recently - using the capabilities of strace. Note I have no idea what the following means given I am a newbie!. By typing the following at the terminal prompt:
$echo '#!bin/sh\n  /usr/bin/strace  /usr/lib/hal/hald-runner\n'  >/tmp/hald-runner
$chmod a+x  /tmp/hald-runner
$PATH=/tmp:$PATH hald  --daemon=no --verbose=no

then typing:
sudo hald --daemon=no  --verbose=yes   (which seems to contradict the above?)

I got an extensive listing of debug messages across the terminal screen. Apparently the problem is that hald-runner has died which is bad......  
Of course I have no idea what the messages mean anyway.. I have included the last few messages for info here..

7:49:14.523 [I] hotplug.c:179: /sys/class/graphics/fb1 is a class device (subsystem)
07:49:14.523 [I] classdev.c:1345: class_add: subsys=graphics sysfs_path=/sys/class/graphics/fb1 dev=/dev/fb1 physdev=0x00000000
07:49:14.524 [I] hotplug.c:179: /sys/class/graphics/fbcon is a class device (subsystem)
07:49:14.524 [I] classdev.c:1345: class_add: subsys=graphics sysfs_path=/sys/class/graphics/fbcon dev= physdev=0x00000000
07:49:14.525 [I] hotplug.c:179: /sys/class/input/input0 is a class device (subsystem)
07:49:14.525 [I] osspec.c:737: hal_util_find_known_parent: '/sys/class/input/input0'->'/sys/devices/root/f005b27c/f005d06c/serio0'
07:49:14.526 [I] classdev.c:1345: class_add: subsys=input sysfs_path=/sys/class/input/input0 dev= physdev=0x0005fa00
process 5879: arguments to dbus_pending_call_set_notify() were incorrect, assertion "pending != NULL" failed in file dbus-pending-call.c line 598.
This is normally a bug in some application using the D-Bus library.

Now my interpretation of the last few lines is that Hald-runner dies because of an issue with the serial port .. Can someone confirm that for me please and make any other comments. If so how can I stop this. Can I remove the serial port class temporarily  to prove this is the culprit? Help please  Regards Chris

---

### Post by sandpiper on 2007-07-10
Update: I have since tried: sudo hal-device-manager at the terminal prompt and received this error message:
chrisw@SunSparc:~$ sudo hal-device-manager
<gtk.Menu object (GtkMenu) at 0x3d5a08>
Traceback (most recent call last):
  File "/usr/bin/hal-device-manager", line 20, in <module>
    DeviceManager()
  File "/usr/share/hal/device-manager/DeviceManager.py", line 70, in __init__
    "/org/freedesktop/Hal/Manager")
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 410, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 230, in __init__
    _dbus_bindings.UInt32(0))
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 169, in __call__
    reply_message = self._connection.send_message_with_reply_and_block(message, timeout)
dbus.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.Hal was not provided by any .service files

Again this means nothing to me. Is there someone out there who has a knowledge of HAL that could make comment and  direct me in the right direction so I can delve further or am I simply wasting my time here.......:-( Chris

---

