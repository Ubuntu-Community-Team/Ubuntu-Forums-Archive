---
title: "ubuntu server 10.04 64bit reboots randomly"
date: 2010-05-13
forum: Server Platforms
---

### Post by MartinsBalodis on 2010-05-13
I have just installed ubuntu server 10.04 64bit. For few days it was going ok.  But now it reboots randomly once 1-3 hours. I have installed these packadges: lamp, gammu-smsd, gnome-core, tightvncserver The server is [Intel SR1625URSASR]("http://ark.intel.com/Product.aspx?id=48664")

messages.log : [p2p.lv/messages.log]("http://p2p.lv/messages.log")  (1.37 MB)
Reboot times I noticed:
17:03,17:25,18:07

---

### Post by cdenley on 2010-05-13
I don't see anything which indicates software is rebooting your system. I would suspect a hardware problem. Are the fans on your CPU heatsink and power supply still working?

---

### Post by KnottyMars on 2010-05-13
I would vote hardware too, i had a regular PC do that to me and it ended up being the power supply. Id bet a c note thats what is causing the reboot. 

You can also look for bulging capacitors on the motherboard, Ive had weird problems when Ive seen bad capacitors, but its more likely its the power supply.

---

### Post by MartinsBalodis on 2010-05-14
The system is brand new. It is running on dual PSU configuration. I even run a cpu benchmark for about 20 minutes. All cpus went 100% and that didn't cause a reboot.

---

### Post by dragos2 on 2010-05-14
How do you know its rebooting ? From logs? 

--MARK-- in logs means that 20 minutes passed between logs.
And from your times looks like that.

---

### Post by MartinsBalodis on 2010-05-14
I can see that apache, tightvnc,ssh servers go down. And if I can quickly enough get to the server I can see it starting up.

---

### Post by HermanAB on 2010-05-14
So, you haven't looked at the log files.  Do that.  Read the tail man page and do something like:
$ sudo tail -n 10000 /var/log/messages

You should quickly get a feeling for what the file looks like when it reboots.  Whatever killed it happened immediately before.

---

### Post by cdenley on 2010-05-14
> **HermanAB said:**
> So, you haven't looked at the log files.  Do that.  Read the tail man page and do something like:
$ sudo tail -n 10000 /var/log/messages

You should quickly get a feeling for what the file looks like when it reboots.  Whatever killed it happened immediately before.

He posted that log file, and as I already said, there doesn't appear to be anything logged about a reboot or any crashes. It appears as if the power plug was pulled as far as the software is concerned. This is why I would suspect a hardware problem.

---

