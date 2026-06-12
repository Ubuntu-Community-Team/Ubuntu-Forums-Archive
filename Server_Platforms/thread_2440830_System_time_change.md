---
title: "System time change"
date: 2020-04-15
forum: Server Platforms
---

### Post by oskarschlierenzauer on 2020-04-15
The system time changed on my Linux server when we moved the time by an hour a few weeks back. Tried to solve the issue myself (I have very limited experience with bash) and I seem to have changed the time but I don't think I did it the way I should have. Anybody able to tell me the proper procedure to have the time change? The issue is I'm running a Minecraft server on Ubuntu server, and the system time change seems to affect the server quite badly.

---

### Post by VMC on 2020-04-15
From a terminal what does ```
timedatectl
``` show?

---

### Post by oskarschlierenzauer on 2020-04-15
I'm in north west England.
Current time is 02:04

The code timedatectl give;

Local time: Thu 2020-04-16 02:04:23
Universal time: Thu 2020-04-16 01:04:23
RTC time: Thu 2020-04-16 01:04:23
time zone: europe/london (bst, +0100)
system clock syncronized: yes
systemd-timesyncd.service active: yes
RTC in local TZ: no

I don't think I changed system clock since somewhere I read about it being cmos related so I assumed that shouldn't be part of the issue.

---

### Post by SeijiSensei on 2020-04-16
You can set the hardware clock to match the computer's local time with the command
```
sudo hwclock --systohc
```

---

### Post by oskarschlierenzauer on 2020-04-16
Ty seiji.

---

