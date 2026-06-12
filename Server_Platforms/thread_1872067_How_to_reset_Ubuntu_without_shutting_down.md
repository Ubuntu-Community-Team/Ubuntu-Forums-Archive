---
title: "How to reset Ubuntu without shutting down"
date: 2011-10-30
forum: Server Platforms
---

### Post by Twilding on 2011-10-30
I am running a Minecraft server (its a game using java) on a old laptop that boots Ubuntu server from a USB stick (it has no hard drive). the problem is after a while it gets very laggy so i need to restart it but i have to pull out the USB stick each time and put it back in or it will not boot from USB and this means that i can not restart it remotely via ssh. is there a way to restart Ubuntu without fully shutting down?

---

### Post by bruno9779 on 2011-10-30
Why do you need to remove the USB stick each time?

Probably you can mess with fstab to work around this

---

### Post by WasMeHere on 2011-10-30
Hello Twilding,

Try ```
sudo reboot
``` from the terminal window, where you run the ssh session

Have fun finding out about Ubuntu :-)
Olle

---

### Post by papibe on 2011-10-30
Hi Twilding. Welcome to the forums!

I think the problems is either Java or minecraft itself. Most people create a set of scripts to restart a laggy minecraft process. Here are a couple of examples of that. This [thread]("http://ubuntuforums.org/showthread.php?t=1840956&highlight=minecraft") and this [other]("ubuntuforums.org/showthread.php?t=1809501&highlight=minecraft") one.

Hope it helps,
Regards.

---

### Post by Twilding on 2011-10-30
sorry papibe but i cant work out those scripts (i can write basic scripts but those are to confusing).

bruno9779 the BIOS will not detect the USB stick other wise.

Olle Wiklund sudo reboot powers off the laptop

the laptop uses a second USB stick as swap space so i assume that to much of the ram fills up and it starts using the swap so is there a way to clear the ram with out restarting or restarting but not powering off.

---

### Post by WasMeHere on 2011-10-30
> **Twilding said:**
> ...
Olle Wiklund sudo reboot powers off the laptop
...
```
sudo reboot
``` should reboot, not poweroff. Maybe you can find a setting in the bios meny of your laptop, where this behaviour can be changed.

---

### Post by patryk_w on 2011-10-30
maybe that's drive related issue.
some time ago i was running debian server from a pendrive on embadded system.
i had problems booting up from time to time. changing the drive solved it. maybe that will work for u too ;)

---

### Post by Twilding on 2011-10-30
patryk_w i fell silly now it seems to be fine on 1 out of the 4 USB ports thank you :) just wondering if there is a way to do a reboot without powering off just to clear the ram it might be faster.

Olle Wiklund i could not find anything about how it reboots in the BIOS

---

### Post by WasMeHere on 2011-10-30
Maybe you can kill some processes, that use cpu and ram. A good tool for that is ***htop***
```
sudo apt-get install htop
``` that can be run via a remote terminal (e.g. ssh).

---

### Post by Twilding on 2011-10-30
Thank you very much htop is good

---

