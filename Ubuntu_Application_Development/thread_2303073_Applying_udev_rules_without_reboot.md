---
title: "Applying udev rules without reboot"
date: 2015-11-16
forum: Ubuntu Application Development
---

### Post by nit2 on 2015-11-16
Hi !

Here is what I am trying to accomplish for some time now:

1) At start up, I want to only have the usb dongle managing my keyboard and mouse to be active/enable/open (the usb ids are known and fixed) - all other usb port should not be responding if any other usb devices are plugged in.
2) During the life of my program / application, by clicking on a button, I want to enable (/open) all usb port of the computer so the current user may plug in a usb key or other keyboard or any usb device.
3) Then when the user has completed its task, a click on another button of my app will make it go back to the initial state : only my keyboard and mouse active, and all usb port should not react to anything.

So far I have a solution for point (1) : by using udev rules to only authorize my usb keyboard/mouse dongle :
I have created a udev rule, greatly inspired from udev documentation and web research, in the directory: **/etc/udev/rules.d** named **10-my.rules** containing:
```
[FONT=courier new]# Rule to authorize the keyboard/mouse dongle
KERNELS=="[1-9]*-[0-9]*", SUBSYSTEMS=="usb", DRIVERS=="usb", ATTRS{idVendor}!="046d", ENV{REMOVE_ME}="1"
KERNELS=="[1-9]*-[0-9]*", SUBSYSTEMS=="usb", DRIVERS=="usb", ATTRS{idVendor}=="046d", ATTRS{idProduct}!="c529", ENV{REMOVE_ME}="1"
ENV{REMOVE_ME}=="1", RUN+="/bin/sh -c 'echo -n %k >/sys%p/driver/unbind'"[/FONT]
```

This rule works greatly: when I plug in a usb device, it is not even part of the usb device list when I am doing a '**lsusb**' command.


I need help for points (2) and (3): to activate all usb ports, and then to put back my initial rule.
For my step 2, I have attempted to remove/hide my file 10-my.rules : but no effect. Over the web I could not find any 'working' clues/commands on how to re-run the udev rules. I have read many (too many maybe) times this [links]("http://www.reactivated.net/writing_udev_rules.html") ([http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)) which is the reference on udev. If I reboot (since the rules is not here any longer) all usb ports are, of course, open ! but I really would like to prevent my user to have to reboot.
Not being an English native speaker I maybe misunderstood the udev doc. Or my approach of using udev to do what I want to do is not the 'right' one ?

If somebody has a clue on how dynamically re-run the rules / restarts usb controls (no system reboot), I am all ears.


oh, and I am on ubuntu 14.04:
reply to $> lsb_release -a:
```
[FONT=courier new]No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:        14.04
Codename:       trusty[/FONT]
```

---

### Post by nit2 on 2015-11-17
I found a solution:
First of all, I am still using udev rules, but I changed it the following way:
```
[FONT=courier new]
ln1  # Rule to disable all devices (Should not be active in the same time as the rule here below)
[FONT=courier new][FONT=courier new]ln[/FONT]2  [/FONT]ACTION=="add", SUBSYSTEM=="usb", RUN+="/bin/sh -c 'for host in /sys/bus/usb/devices/usb*; do echo 0 > $host/authorized_default; done'"
[FONT=courier new][FONT=courier new]ln[/FONT]3 [/FONT]
[FONT=courier new][FONT=courier new]ln[/FONT]4  [/FONT]# Rule to enable all devices (Should not be active in the same time as the rule here above)
[FONT=courier new][FONT=courier new]ln[/FONT]5  [/FONT]#ACTION=="add", SUBSYSTEM=="usb", RUN+="/bin/sh -c 'for host in /sys/bus/usb/devices/usb*; do echo 1 > $host/authorized_default; done'"
[FONT=courier new][FONT=courier new]ln[/FONT]6 [/FONT]
[FONT=courier new][FONT=courier new]ln[/FONT]7  [/FONT]# Rule to authorize the keyboard/mouse dongle
[FONT=courier new][FONT=courier new]ln[/FONT]8  [/FONT]ACTION=="add", ATTR{idVendor}=="046d", ATTR{idProduct}=="c529", RUN+="/bin/sh -c 'echo 1 > /sys$DEVPATH/authorized'"
[FONT=courier new][FONT=courier new]ln[/FONT]9  [/FONT]ACTION=="add", ATTR{idVendor}=="046d", ATTR{idProduct}=="c529", RUN+="/bin/sh -c 'echo 1 > /sys$DEVPATH/authorized_default'"[/FONT]
```

So, to follow my application execution process: (1) on start-up of my machine, only the keyboard/mouse is active. If any other usb devices are connected, they are not 'active' (but they **are** detected if the **lsusb** command is executed --> this is the reason why I changed the content of my rule).
(2) when I click on a button to enable the usb ports, through the execution of a script, I change my rule the following way: I comment line 2 and I uncomment line 5. At this point, we need to load and make the rules active. Once the file is updated, I apply through my script the two following command:
```
[FONT=courier new]sudo udevadm control --reload
sudo udevadm trigger --action=add[/FONT]
```
When I plug in a usb device, it is available :)!
(3) To go back, I re-update my rule file in its initial state, reload and trigger.
There is one pitfall in my solution, but I can live with it because it is not critical for me: Once the rule to disable all usb has been reapplied after step 3, if the usb device has not been removed (i.e. plugged out), it is still active - until it is plugged out and then plugged in : because the effect is on "trigger action add".

To be complete, this [link]("http://www.irongeek.com/i.php?page=security/plug-and-prey-malicious-usb-devices#3.2_Locking_down_Linux_using_UDEV") helped me along the way.

---

