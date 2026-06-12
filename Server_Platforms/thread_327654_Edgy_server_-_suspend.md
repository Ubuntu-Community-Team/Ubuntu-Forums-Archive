---
title: "Edgy server - suspend"
date: 2006-12-29
forum: Server Platforms
---

### Post by sulla on 2006-12-29
Hi!

I installed Ubuntu-Edgy-server on my old machine (Pentium III) to serve as a SAMBA file server for my home-net (very small, only 2 clients).

I do not want to have my server running 24/7 so I wanted to suspend it. However, I can't.
when I ssh in from a client and try a
sudo echo "disk" > /sys/power/state
I get an error message
-bash: /sys/power/state: Permission denied

The contents of /sys/power/state is
standby disk
so I assume I should be able to switch to standby and suspend2disk, but not suspend to ram, is that right?

ACPI seems to work, a grep ACPI /var/log/messages gives a lot of entries, like
kernel: [42949375.100000] ACPI: (supports S0 S1 S4 S5)
kernel: [42949375.160000] PCI: Using ACPI for IRQ routing
kernel: [42949374.530000] pnp: PnP ACPI: found 11 devices
kernel: [42954285.340000] apm: overridden by ACPI.

but also
kernel: [42949375.540000] ACPI: Looking for DSDT ... not found!

What would I have to do to get powersaving to work?


Also, I would like to put my machine to sleep after a certain time of inactivity on eth0. How would I have to set that up??

Thanx for help,
Sulla

---

### Post by fimblo on 2006-12-30
could you try doing a sudo bash, followed by a echo "disk" > /sys/power/state ?

normally, if the user running sudo doesn't have access to the file, sudo doesnt help you. In other words- the command supplied to sudo is run as root, but the files you specified (everything after the command) is not run using escalated permissions.


anyway- if this was the case, try writing a small wrapper which does this for you, i.e.

```
$ sudo bash
# cat <<EOF> /usr/local/sbin/suspend.sh
#!/bin/bash
if [ "$(id -u)" != '0' ] ; then 
  echo "Must be superuser. Aborting."
  exit 1
fi
echo "Suspending to disk"
echo -n "disk" > /sys/power/state
exit 0
EOF
#
# chmod 755 /usr/local/sbin/suspend.sh
# exit
$ 
$ # try running it as an unprivileged user
$ /usr/local/sbin/suspend.sh
Must be superuser. Aborting.
$ 
$ # try it as root
$ sudo /usr/local/sbin/suspend.sh
Suspending to disk
```

---

### Post by sulla on 2007-05-17
Hi Fimblo!

Thanks for your answer. I totally forgot to answer and thank you for your help! Sorry.

> **fimblo said:**
> could you try doing a sudo bash, followed by a echo "disk" > /sys/power/state ?


Indeed, that did the trick. I now can suspend my server!

I still need to figure out how to suspend the server automatically after, say, an hour of inactivity (perhaps I'll give powersaved a chance) and then try to wake it up using wake-on-lan.

Thanx for helping me,
Sulla

---

### Post by fimblo on 2007-05-19
cool.

happy to help.

About suspending automatically after so-and-so many minutes, I remember I did something like that a couple years ago on my gentoo system- I wrote a perl hack which did something... damn, cant remember, but anyway, I told xscreensaver to start that script when it detected 30 minutes of inactivity.

Since gnome-screensaver is, in essence, xscreensaver, you should be able to do the same thing here... perhaps. not sure, havent tested.

course, if you have a server with no GUI, this isnt very helpful :)

---

