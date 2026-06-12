---
title: "Late night 100% cpu usage..."
date: 2006-10-14
forum: Server Platforms
---

### Post by FeraTech on 2006-10-14
Every night my server jumps to 100% cpu useage. System monitor shows the max should be 40% and Firestarter shows none connected or blocked. Someone has control of my server and I wanna know how or what to do.

Please help!

---

### Post by Klaidas on 2006-10-14
Hmmm
Try using the > top command

---

### Post by bobosity on 2006-10-14
Does it last for quite awhile? If it only does that for a few minutes or so, it might be all your cron jobs kicking in......

---

### Post by FeraTech on 2006-10-14
I don't have any cron jobs scheduled and even if I did I should be able to see them using the system monitor.

---

### Post by MJN on 2006-10-14
Does /var/log/syslog show anything or give any hints during these periods of high activity? As another poster says, what does 'top' reveal as the most active processes at the time?
 
You're a million miles away from being able to deduce someone's hacked your box so relax!
 
Mathew

---

### Post by FeraTech on 2006-10-14
So I've been watching the system monitor output. Wierd thing is that Firestarter is the program that's running up the CPU. For no reason it will start going nuts and hogging the CPU like crazy. The blocked list once it reaches a certain point stops updating. When it is cleared it remains empty without showing blocked IPs.

Could Firestarter not be set up properly?

---

### Post by MJN on 2006-10-16
Unfortunately I am not familiar with Firestarter so someone else will have to confirm if this is normal behaviour (and what it is).
 
Mathew

---

