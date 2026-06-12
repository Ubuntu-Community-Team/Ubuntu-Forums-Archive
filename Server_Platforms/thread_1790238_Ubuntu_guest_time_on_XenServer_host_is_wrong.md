---
title: "Ubuntu guest time on XenServer host is wrong"
date: 2011-06-24
forum: Server Platforms
---

### Post by infecticide on 2011-06-24
I posted this on the Citrix Support Forums hoping for some insight as to how to fix this issue.






I've had this issue since I installed Ubuntu 10.04 from a template I found.

The template I found was able to integrate the Xenserver Tools and I was able to build myself an Ubuntu Server that was in PV mode.

The problem was obvious immediately after installation but until now its been a mild annoyance I would like to solve.

My XenServer is configured with the correct timezone + NTP, in the console it shows the correct time.

I also have an Openfiler virtual appliance that shows the correct time so I know this is isolated to the Ubuntu VM.

I have seen many posts that refer to the /proc/sys/xen/.... path and to set the independent_wallclock variable.
However on my VM I do not have such a path, this leads me to wonder if the XenServer Tools are missing something related to time sync.

On my Ubuntu VM I have the following time info setup:

Timezone: America / Regina (no DST)

When I run the date command:

Current default time zone: 'America/Regina'
Local time is now:      Fri Jun 24 21:58:01 CST 2011.
Universal Time is now:  Sat Jun 25 03:58:01 UTC 2011.

The time now is actually 15:58 CST

It seems as though the VM is unaware that it is virtualized and it assumes that the hwclock time it gets from the host is actually in UTC instead of the local time zone.

Any ideas how I would fix this?

---

### Post by volkswagner on 2011-06-25
You may have answered your own question.  If your hardware clock is set to local time, or Ubuntu responds as though it is, perhaps you can tell Ubuntu your hardware clock is local not UTC.

Edit /etc/default/rcS as from this [how to]("https://help.ubuntu.com/community/UbuntuTime") and change:

```
UTC=yes

```


to


```
UTC=no

```

---

### Post by infecticide on 2011-06-25
Ha!  I knew it had to be simple!

I actually had to set UTC=yes, it was already set to no.

Thank you!  The date is now correct!

---

