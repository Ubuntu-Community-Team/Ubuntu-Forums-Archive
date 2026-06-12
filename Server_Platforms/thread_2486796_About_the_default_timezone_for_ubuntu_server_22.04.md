---
title: "About the default timezone for ubuntu server 22.04"
date: 2023-05-11
forum: Server Platforms
---

### Post by songfei870415 on 2023-05-11
Hello,
I am runing Ubuntu server 22.04 on my server, and set the default timezone to EST by using timedatectl set-timezone EST.But when it use apt upgrade to upgrade the software and service, it changed the timezone to [COLOR=#343541][FONT=Söhne]Adak, and said[/FONT][/COLOR]  [COLOR=#343541][FONT=Söhne]Current default time zone: 'America/Adak'. So what casue this issue , how can i found the reason for it?[/FONT][/COLOR]

---

### Post by TheFu on 2023-05-11
If the EST you want is NYC, use, 
```
$ more /etc/timezone 
America/New_York

```
Timezones are in the format of Continent/City

This avoids the need to change between EST and EDT twice a year.

---

### Post by songfei870415 on 2023-05-11
I know how to set it, but why it will be changed when i run apt upgrade? This is strange.

---

### Post by TheFu on 2023-05-11
Is "EST" valid?  I know that CST has dual meanings, depending on the part of the world you are in/from.

```
u2204-srv:~$ date
Thu May 11 13:12:47 UTC 2023
u2204-srv:~$ more /etc/timezone 
Etc/UTC

```
Ah, that makes sense.

```
u2204-srv:~$ sudo timedatectl set-timezone "America/New_York"
u2204-srv:~$ sudoedit /etc/timezone 
America/New_York

u2204-srv:~$ date
Thu May 11 09:16:54 **EDT** 2023

```
Ah ... EST doesn't make sense today.  EDT does.

The manpage for timedatectl says this:
```
       set-timezone [TIMEZONE]
           Set the system time zone to the specified value. Available timezones can
           be listed with list-timezones. If the RTC is configured to be in the
           local time, this will also update the RTC time. This call will alter the
           /etc/localtime symlink. See localtime(5) for more information.
```

/usr/share/zoneinfo/ has the timezones ... and I'm seeing EST there, along with EST5EDT. No EDT in that directory.  I did some reading 5+ yrs ago about all this stuff and my take-away was to always use the Continent/City method.

As for upgrades losing it?  IDK.  I haven't do-release-upgrade any systems to 22.04.

---

### Post by songfei870415 on 2023-05-11
yes,"EST" is valid,or i can set it to GMT-5,but sometimes,the setting will be losing for upgrades

---

### Post by TheFu on 2023-05-12
> **songfei870415 said:**
> yes,"EST" is valid,or i can set it to GMT-5,but sometimes,the setting will be losing for upgrades

How are the upgrades run?  do-release-upgrade?  Or some other method?  Wouldn't hurt to open a bug in launchpad over it, if you can figure out the exact steps to reproduce.

Of course, the workaround for most enterprises would be to use their devops tool to control the server-local timezone.  We always set our servers to UTC to make logs all line up between systems around the world, but I can see where a company might want to pick a specific TZ for all their servers based on where their engineers are located.

---

