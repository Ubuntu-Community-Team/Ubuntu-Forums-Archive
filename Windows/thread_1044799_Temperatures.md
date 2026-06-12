---
title: "Temperatures"
date: 2009-01-19
forum: Windows
---

### Post by joshh88 on 2009-01-19
Is there a function in msdos or somewhere in windows where you can see the current temperature of the internals? Like how in terminal we can type $ sensors. It's not my computer so I really don't want to install an unfamiliar program. Thanks in advance.

---

### Post by coffeecat on 2009-01-20
> **joshh88 said:**
> Like how in terminal we can type $ sensors.

Well....

```
coffeecat@ubuntu8:~$ sensors
The program 'sensors' is currently not installed.  You can install it by typing:
sudo apt-get install lm-sensors
bash: sensors: command not found
coffeecat@ubuntu8:~$
```.... which means that if I want to run sensors on this machine, I'm going to have to install an unfamiliar program. :wink:

Seriously... Windows or Linux, you're going to have to install some sort of application **and** hope that the motherboard has the sensors that the application reads. Some cheap motherboards don't.

I did manage to find a couple of free GUI utilities for Windows that gave a lot of useful output. I can't remember what they're called atm, and I can't remember what I googled to find them, but they weren't difficult to find. If I do boot up Windows later today I'll have a look and post back, but I can't promise anything - busy day.

---

### Post by WiFi Ed on 2009-01-21
Try HWMonitor from [http://www.cpuid.com/hwmonitor.php]("http://www.cpuid.com/hwmonitor.php")

It doesn't install as such, no writing to the registry or putting a folder in Program Files, etc. It will give you CPU temps, hard drive temps and most likely graphics card temps too...

---

