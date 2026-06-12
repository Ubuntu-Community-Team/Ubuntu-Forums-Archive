---
title: "Gazp6 - Fan running at full speed"
date: 2012-03-08
forum: System76 Support
---

### Post by TheSqueak on 2012-03-08
My laptop fan has decided this morning that it wants to run at full speed all the time. Obviously this is a little annoying, and I was wondering if anyone could help shed some light ...

 I think there's a couple of possibilities;

1) I'm in the habit of fn+1-ing fairly quickly after boot to turn the pad off because I use the mouse, but I was reading on these forums that that key combo also turns the fan up to full speed? I've tried booting and hitting it again before the OS loads to try and get the BIOS to turn the fan down, but that doesn't help.

2) I updated a lot of the KDE SC yesterday to the latest version, and that might have caused a fan issue, but I can't find anything from google.


(For reference:

```
james@alia:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +43.0°C  (crit = +154.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +44.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +44.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +41.0°C  (high = +86.0°C, crit = +100.0°C)
Core 2:         +41.0°C  (high = +86.0°C, crit = +100.0°C)
Core 3:         +43.0°C  (high = +86.0°C, crit = +100.0°C)
```

and

[top]top - 09:11:04 up 17 min,  3 users,  load average: 0.13, 0.17, 0.14
Tasks: 229 total,   1 running, 228 sleeping,   0 stopped,   0 zombie
Cpu(s):  9.7%us, 13.6%sy,  0.0%ni, 76.2%id,  0.2%wa,  0.0%hi,  0.2%si,  0.0%st[/code]

So it's not under particularly heavy load, or running particularly hot.


Any ideas?

---

### Post by isantop on 2012-03-08
The touchpad key you're looking for is Fn+F1, rather than Fn+1. If you don't hit Fn+1, the fan will stay at a normal level.

---

