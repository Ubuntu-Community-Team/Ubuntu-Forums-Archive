---
title: "Any RAID Monitoring Tools?"
date: 2009-05-11
forum: Server Platforms
---

### Post by kevmev12 on 2009-05-11
Hi guys,
 
I've built a Jaunty Server Edition running as a basic file and media server, with fuppes connecting to my Xbox running almost perfectly. Under the hood, I've got an 80GB HDD with / installed in it (with 4.096GB swap area), and 2 x 1TB HDD running as RAID1 under the Ubuntu software RAID with /home installed in that.
 
I just wanted to know if there's any RAID monitoring tools so I can check up on the health of my RAID partition. What would be even sweeter would be a RAID monitoring tool that's web based that can also monitor how much space is left in all my other partitions.
 
This is my first foray into Linux and I've dived right into the deep-end by building a home file server and I'm never looking back because I don't think I've ever learnt so much (and used Google so much!) in just 2 or 3 weeks of tinkering with Ubuntu Desktop and Server.
 
Thanks for your help.

---

### Post by ikonia on 2009-05-11
if it's a software raid partition, the mdadm init script has monitoring and basic alerting set up in it, 

look up mdadm --monitor

---

### Post by slick666 on 2009-07-06
Are there any graphical apps that can do this in gnome? You can monitor just about everything else from the panel is there an app out there to do this?

---

### Post by Cheesemill on 2009-07-06
You could use 'cat /proc/mdstat' with conky to get monitoring on your desktop.

---

