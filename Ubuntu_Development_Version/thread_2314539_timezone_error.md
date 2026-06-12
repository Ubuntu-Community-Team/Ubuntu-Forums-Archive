---
title: "timezone error"
date: 2016-02-22
forum: Ubuntu Development Version
---

### Post by VMC on 2016-02-22
My timezone is off by +8 hours ahead.

Heres the files and settings:
/etc/timezone: America/Los_Angeles
/etc/default/rcS: UTC=no (changing UTC from no to yes to nothing has no effect. Originally it was not set)
ln -s /usr/share/zoneinfo/US/Pacific /etc/localtime

As you can see below, using the default and 'correct' setting has RTC ahead by +8 hours.
```
$ timedatectl ('timedatectl set-local-rtc 0')
      Local time: Sun 2016-02-21 22:08:45 PST
  Universal time: Mon 2016-02-22 06:08:45 UTC
        RTC time: Mon 2016-02-22 06:08:45
       Time zone: America/Los_Angeles (PST, -0800)
 Network time on: yes
NTP synchronized: no
 RTC in local TZ: no
```

The only way to get the correct RT setting is setting RTC=1 : "timedatectl set-local-rtc 1", but then I need to change it  when daylight savings rolls around.
```
$ timedatectl
      Local time: Sun 2016-02-21 22:13:47 PST
  Universal time: Mon 2016-02-22 06:13:47 UTC
        RTC time: Sun 2016-02-21 22:13:47
       Time zone: America/Los_Angeles (PST, -0800)
 Network time on: yes
NTP synchronized: yes
 RTC in local TZ: yes

Warning: The system is configured to read the RTC time in the local time zone.
         This mode can not be fully supported. It will create various problems
         with time zone changes and daylight saving time adjustments. The RTC
         time is never updated, it relies on external facilities to maintain it.
         If at all possible, use RTC in UTC by calling
         'timedatectl set-local-rtc 0'.
```

Its fruitless making another bug report, unless someone else has issues.

You  will NOT see the issue unless you dual boot. This is NOT a Windows  issue because I have Ubuntu Trusty installed on another partition, and  it works correctly as has all previous releases. The only way to tell if you have issue with one install is to check your RTC.

---

### Post by P-I H on 2016-02-22
I don't know if this is related, but I had a problem with time & date on my custom kernel, 4..5 RC1.
With the setting "Automatically from the Internet" i got wrong time and the error message
"systemd-timesyncd[5766]: Failed to call clock_adjtime(): Invalid argument"
After installing ntp and ntpdate I get the correct time and no error message.

---

