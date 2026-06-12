---
title: "How to check CPU load in command line"
date: 2006-07-28
forum: Server Platforms
---

### Post by Swiss2K on 2006-07-28
I've an Ubuntu server running with no desktop. Is there a way to check the CPU load (and maybe also network load) in command line?

If there is no tool in command line, I’m willing to install Xfce. Does Xfce Standard come with a cpu monitor?

Appreciate any help:D

---

### Post by paul.maddox on 2006-07-28
**top** displays all sorts of CPU/Memory/Process information.

I believe that there is also **ntop** for monitoring network stuff but I've never used this myself.

**free -m** will show you stats about RAM usage in MB

**uptime** will show you the load average for the past 1min, 5mins and 15mins

**cat /proc/cpuinfo** will give you general information about the CPU(s)

A great program for monitoring network traffic is **iptraf** which is in the repositories.

---

### Post by Swiss2K on 2006-07-28
Thank you very much!

---

### Post by lamego on 2006-07-28
Installing the sysstat package and using the "sar" command is also a very good option.

---

### Post by Kurt` on 2006-07-28
> **lamego said:**
> Installing the sysstat package and using the "sar" command is also a very good option.
I apt-get install'ed sysstat, and sar returns this:

# Cannot open /var/log/sysstat/sa28: No such file or directory

Shouldn't that directory be created when it's installed?

---

### Post by fdoving on 2006-07-29
I use 'htop' and i like it.
It's in universe.

- Frode

---

### Post by paul.maddox on 2006-07-29
htop gets a thumbs up from me, never seen it before but it looks much nicer than top.

---

### Post by Kurt` on 2006-07-29
Wow, htop is really cool!

---

### Post by bicchi on 2006-09-11
> **Kurt` said:**
> I apt-get install'ed sysstat, and sar returns this:

# Cannot open /var/log/sysstat/sa28: No such file or directory

Shouldn't that directory be created when it's installed?
Happened to me also. Just reconfigure the application from the command line and it will work. You can have it start from /etc/init.d and uninstall it when you will not longer use it.

For now just type:
```

sudo dpkg-reconfigure sysstat
```

---

### Post by rastilin on 2006-09-11
I'm surprised no one's mentioned vmstat. Type "vmstat #" and you'll get a run down of memory use, disk operations and cpu usage every # seconds. The first line's a running average.

---

### Post by paul.maddox on 2006-09-12
Can you just give a quick explanation of what the various columns represent in vmstat and which ones we should be looking at to determin different performance problems?

---

### Post by ruedu on 2006-09-12
> **paul.maddox said:**
> Can you just give a quick explanation of what the various columns represent in vmstat and which ones we should be looking at to determin different performance problems?


type man vmstat

---

### Post by mobilehavoc on 2006-09-12
Nice. htop is great. Just ssh'd into my box, apt-get installed it and ran it...remote monitoring FTW!

---

### Post by etcpool on 2006-09-20
htop is cool!!!! :D ;)

---

### Post by karsteb on 2007-08-16
> **rastilin said:**
> I'm surprised no one's mentioned vmstat. Type "vmstat #" and you'll get a run down of memory use, disk operations and cpu usage every # seconds. The first line's a running average.

> **Kurt` said:**
> I apt-get install'ed sysstat, and sar returns this:

# Cannot open /var/log/sysstat/sa28: No such file or directory

Shouldn't that directory be created when it's installed?


Sar needs to be enabled before it can be used. I agree that the error message is completely uselsess, but anyways:

Enable sysstat data collection by doing 

[INDENT][FONT="Courier New"]# dpkg-reconfigure sysstat[/FONT][/INDENT]

or manually by changing value of ENABLED from "false" to "true" in /etc/default/sysstat 

Then start sysstat by doing 

[INDENT][FONT="Courier New"]# /etc/init.d/sysstat start [/FONT][/INDENT]

Check var/log/sysstat/ and you will find the file that were missing.

Run 

[INDENT][FONT="Courier New"]$ sar [/FONT][/INDENT]

---

### Post by netlogic on 2007-08-16
Also, it is good to understand how to read the /proc
There are plenty of docs on the net explain about the /proc

---

