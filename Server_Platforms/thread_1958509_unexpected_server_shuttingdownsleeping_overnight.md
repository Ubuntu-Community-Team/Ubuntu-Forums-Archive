---
title: "unexpected server shuttingdown/sleeping overnight"
date: 2012-04-14
forum: Server Platforms
---

### Post by jeliocranch on 2012-04-14
Hi,
I've had an 11.10 server up for several months now.  Its got lxde installed and hosts a Windows 7 VM and runs Marsienne Prime from GIMPS in the background. 

Over the past two days, each morning when I check the server, the hardware is running but I cannot rouse the machine.  I'm not able to ssh into it either, getting the "no route to host" message.  I've had to restart it each time.

I'm looking for clues as to why this could be happening.  I've checked through most everything in /var/log, but I'm not seeing anything.  

Where else should I look?

---

### Post by CharlesA on 2012-04-14
Is anything listed in the system logs?

You could try having a script that writes the date/time to a file and have that run every 5-10 minutes to try to narrow down when the machine becomes unresponsive.

---

### Post by Jonathan L on 2012-04-14
Hi jeliocranch

>  date/time to a file and have that run every 5-10 minutesCharles's advice is excellent, but I suspect him of using floppy disks for main storage.

I'd have a script putting the output of ifconfig, uptime, and sysctl -a into a file _every few seconds_.  I'd also ensure the clock is synced (with NTP) and have another computer logging ping to the bad box.

Might also want to see when ssh goes down:
```
while true; do ssh badbox logger `date`; sleep 1 ; done
```Kind regards,
Jonathan.

---

