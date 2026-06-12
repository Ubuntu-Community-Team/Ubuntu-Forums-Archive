---
title: "System info displayed at login"
date: 2010-10-01
forum: Server Platforms
---

### Post by Karl1982 on 2010-10-01
I've been trying to figure this out... What command does the system use to display this at login:

> 
System information as of Fri Oct 1 08:35:54 CDT 2010

System load: 0.28
Usage of /: 10.8% of 17.89GB
Memory usage: 51%
Swap usage: 3%

Processes: 112
Users logged in: 1
IP address for eth0: <ip.address>
It's not uname, free, top, df, uptime, etc... Also doesn't appear to be anything in /proc that I've found.  Anyone know what it is?  I want to grab its output as part of a script.  I could use other commands I suppose, but this system info output is neat and concise.

Thanks

---

### Post by SlugSlug on 2010-10-01
> **Karl1982 said:**
> I've been trying to figure this out... What command does the system use to display this at login:

It's not uname, free, top, df, uptime, etc... Also doesn't appear to be anything in /proc that I've found.  Anyone know what it is?  I want to grab its output as part of a script.  I could use other commands I suppose, but this system info output is neat and concise.

Thanks


whats the output of 

cat /etc/motd

---

### Post by Karl1982 on 2010-10-01
I actually just found that a few minutes ago.  /etc/motd is a link to /var/run/motd which is a compilation of the output from scripts in /etc/update-motd.d.  However, it seems it only updates at login, which won't do what I need.

There's supposed to be a utility called "update-motd" that you can use to trigger an update on /etc/motd... I installed it via apt, but it seems I still don't have it.  Any idea what I need to do there?  I need the info to be current with no users logged in or it's useless.

---

### Post by SlugSlug on 2010-10-01
/etc/update-motd.d   see if you can rummage something from there <<

---

### Post by Karl1982 on 2010-10-01
Yeah, it's definitely the guts of what I'm looking for, but it would be so much simpler if I knew how to just trigger an update of /etc/motd.  I tried *sh /etc/update-motd.d/** but that isn't working.  I thought it would since apparently they're just a collection of *#!/bin/sh* scripts that run in sequence at login...

There must be some simple, no-nonsense way of manually triggering an update to /etc/motd, I just don't know what it is.

---

### Post by Karl1982 on 2010-10-01
Think I've got it:

*run-parts --lsbsysinit /etc/update-motd.d > /etc/motd*

... updates /etc/motd with current info.  But I may actually just take that command rather than /etc/motd.

---

### Post by CharlesA on 2010-10-01
That looks like landscape-sysinfo.

```
landscape-sysinfo
```

```

  System information as of Fri Oct  1 13:58:58 PDT 2010

  System load:  0.0                 Processes:           108
  Usage of /:   30.1% of 281.49GB   Users logged in:     0
  Memory usage: 24%                 IP address for eth0: 192.168.1.2
  Swap usage:   0%

```

---

### Post by ricerider1 on 2010-10-01
When I ssh from another comp I show 0 users, but it still uses the first login time where the landscape info shows 1 user and the first login time. I don't know if that would suit you or not. I am not sure what info you are looking for, but I have also installed webmin 1.520 and you can view all running processes with it as well as have a secure login. I haven't much experience so far, but it seems to be a very nice gui with plenty of tools to make things easier

---

