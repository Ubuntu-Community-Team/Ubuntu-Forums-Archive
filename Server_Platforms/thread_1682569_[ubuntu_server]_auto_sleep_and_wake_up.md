---
title: "[ubuntu server] auto sleep and wake up"
date: 2011-02-06
forum: Server Platforms
---

### Post by maximmai on 2011-02-06
Hi all,

I have a ubuntu 10.04 server serving django applications for my clients, and recently my clients and I have agreed to take the server offline everyday from 1am to 6am on weekdays, and 9pm to 6am in the weekends. (trying to be more eco friendly and to save more energy)

So, I was wondering if it's possible to setup a schedule for the server, to auto shutdown/suspend and auto start/wakeup.

I know that the "shutdown" command will work, but how do you start the machine from a cold shutdown?

additional info:
Machine: IBM M55p (Intel dual core@1.85Ghz, 3GB DDR2)
OS: Ubuntu Server 10.04


Thanks,

Maxim

---

### Post by CharlesA on 2011-02-06
If the BIOS supports wake by alarm, you might be able to set a time to power it on and just run a cronjob to shut it down at the appropriate time.

---

