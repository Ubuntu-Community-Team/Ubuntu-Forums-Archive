---
title: "Time/date change privileges."
date: 2011-03-29
forum: Security
---

### Post by cyberguijarro on 2011-03-29
Hi,

I would like to give one specific user of my system the privilege to set the system clock (i.e. change the system date and time).

AFAIK only root can do that.

Thanks.

---

### Post by sanguinoso on 2011-03-31
You can add them to the sudoers file and give them access to the one command that lets them change the system time. See this document here [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers). I'm assuming the command you want to let them use is date, so the line would look something like this ```
<your username> ALL=(ALL) NOPASSWD: /bin/date
```
The NOPASSWD means that they won't have to enter their username to execute the command date.

---

### Post by bodhi.zazen on 2011-03-31
> **sanguinoso said:**
> The NOPASSWD means that they won't have to enter their username to execute the command date.

Small clarification, NOPASSWD means the user will not need to enter a password.

Typically one does not need to enter a user name with sudo.

---

### Post by sanguinoso on 2011-04-01
> **bodhi.zazen said:**
> Small clarification, NOPASSWD means the user will not need to enter a password.

Typically one does not need to enter a user name with sudo.

Absolutely correct, I mistyped in my end of work stupor.

---

### Post by SeijiSensei on 2011-04-03
Just curious, but why do you need to change the system date and time manually at all?  If you use ntpd, your server will sync to the network time protocol servers.  If you need to set the hardware clock, run "hwclock --systohc" as root each night out of cron.

---

