---
title: "Problems changing group of device with udev"
date: 2010-02-07
forum: Server Platforms
---

### Post by mboehm on 2010-02-07
I want to change the group of /dev/ttyS0 from "dialout" to "nut". Chgrp works only temporarily until next reboot so I want to use udev rules to set it permanent.
 
In /lib/udev/rules.d/50-udev-default.rules this entry sets the group to "dialout" during startup:
 
```
KERNEL=="tty[A-Z]*[0-9]|pppox[0-9]*|ircomm[0-9]*|noz[0-9]*|rfcomm[0-9]*", GROUP="dialout"
```
 
So I created a new rules file /etc/udev/rules.d/52-nut-serial.rules:
 
```
KERNEL=="ttyS0", GROUP="nut"
```
 
And now
 
```
 
# service udev reload
# ls -al /dev/ttyS*
crw-rw---- 1 root dialout 4, 64 2010-02-07 00:39 /dev/ttyS0
crw-rw---- 1 root dialout 4, 65 2010-02-06 15:16 /dev/ttyS1
crw-rw---- 1 root dialout 4, 66 2010-01-23 23:25 /dev/ttyS2
crw-rw---- 1 root dialout 4, 67 2010-01-23 23:25 /dev/ttyS3

```
 
Oops nothing changed, no success :(
 
I have no idea what's wrong. Could you please help me?

---

### Post by kiranmurari on 2010-02-09
Hi,

Does the new group "nut" exist? If it does not exist, you have to first create the "nut" group.
```
$ addgroup nut
```Edit the rule in /lib/udev/rules.d/50-udev-default.rules from
```
KERNEL=="tty[A-Z]*[0-9]|pppox[0-9]*|ircomm[0-9]*|noz[0-9]*|rfcomm[0-9]*", GROUP="dialout" 
```to
```
KERNEL=="tty[A-Z]*[1-9]|pppox[0-9]*|ircomm[0-9]*|noz[0-9]*|rfcomm[0-9]*", GROUP="dialout" 
```Add a new rule below this
```
KERNEL=="ttyS0", GROUP="nut" 
```Reboot the system and the group of /dev/ttyS0 now changes to "nut".

Hope this helps.

---

### Post by kiranmurari on 2010-02-09
The solution suggested in previous reply will not sustain re-installations or future upgrade of udev.

In order to resolve this, copy the /lib/udev/rules.d/50-udev-default.rules to /etc/udev/rules.d/52-udev-default.rules and change the following rule from
> KERNEL=="tty[A-Z]*[0-9]|pppox[0-9]*|ircomm[0-9]*|noz[0-9]*|rfcomm[0-9]*", GROUP="dialout" to
> KERNEL=="tty[A-Z]*[1-9]|pppox[0-9]*|ircomm[0-9]*|noz[0-9]*|rfcomm[0-9]*", GROUP="dialout"Below this add the following rule
> KERNEL=="ttyS0", GROUP="nut"From /etc/udev/rules.d/README:
> Packages do not generally install rules here, this directory is for
local rules.  If you want to override behaviour of package-supplied
rules, which can be found in /lib/udev/rules.d, you can do one of
two things:

 1) Write your own rules in this directory that assign the name,
    symlinks, permissions, etc. that you want.  Pick a number higher
    than the rules you want to override, and yours will be used.

 2) Copy the file from /lib/udev/rules.d and edit it here; you
    should generally only do this if you want to prevent a program
    from being run.
For more information on writing udev rules, please look at: "Rule Writing" section of [http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html)

---

