---
title: "Windows Guest loosing time"
date: 2009-04-28
forum: Virtualisation
---

### Post by schoonbee on 2009-04-28
Hi,

I have an XP guest on my Ubuntu Laptop. I suspend my laptop for the night and then and on resume the next morning all is coming up fine.

The problem is that my XP machines are stuck in the past ;) Ie. on resume the XP guest does not sync with the host system clock.

I would not want to start playing with an ntp client on XP and the XP internet time sync will not help since I'm not always on the net in some cases of resume.

Is there an easy workaround/fix/setting for this?

Rgds,
D.

---

### Post by antiram on 2009-04-29
i have the same problem, but:
[http://support.microsoft.com/kb/q307897/](http://support.microsoft.com/kb/q307897/)

resync with default internet ntp server
w32tm /resync
should be set as Windows cron job 5 minutes(tasks in system control or so)

resync with host ntp server (package ntp) should be
w32tm /resync /computer:host-ip

but looks like /etc/ntp.conf must configured (and restarted), default is
```

# Local users may interrogate the ntp server more closely.
restrict 127.0.0.1
restrict ::1

# Clients from this (example!) subnet have unlimited access, but only if
# cryptographically authenticated.
#restrict 192.168.123.0 mask 255.255.255.0 notrust

```
should be changed to
restrict 192.168.122.0 mask 255.255.255.0 
for kvm default subnet or so...

---

### Post by schoonbee on 2009-04-29
Thanks for that. But my XP machine just did not wanna work. Something about some "stratum" error... :confused:

So I've got Automachron from One Guy Coding running on XP guest (systray) connecting to my VM host set to 60sec. So when I resume it should be fine.

I just had to add this line to /etc/ntp.conf on my host:
```

restrict 192.168.0.0 mask 255.255.0.0 nomodify notrap

```

Works great now :)

---

### Post by schoonbee on 2009-04-29
Hmmm... how do I mark this thread as [sloved]?

---

