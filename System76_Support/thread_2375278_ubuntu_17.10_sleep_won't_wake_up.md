---
title: "ubuntu 17.10 sleep won't wake up"
date: 2017-10-23
forum: System76 Support
---

### Post by david7838 on 2017-10-23
I have a serval laptop from June 2017, and upgraded to ubuntu 17.10 (with Gnome3). When I lock the screen, the display quickly blanks. Soon after, the system appears to go to sleep, and will not wake up. I've tried moving the mouse, pressing a key, and brief presses of the power button, to no avail. I had similar problems before with this machine (and a previous serval) when running 17.04, but managed to avoid the problem by uninstalling the gnome screensaver with installing xscreensaver, then using that screen saver's config screen. The usual Ubuntu settings dialog (Power Management) to turn off sleep mode didn't solve the issue in 17.04, and doesn't solve the issue in 17.10 either. In 17.10, I have Blank screen=Never, and Automatic suspend=Off.

Another issue that is likely related:
I have 2 BenQ GW2765 monitors attached via displayport. When I encounter the above issue, and have to hold down the power button and restart, I often run into a problem where one or the other of these external monitors are no longer recognized by Ubuntu. Lets call them monitor 2 and monitor 3 (as does 17.10). Assume monitor 2 was not working. I switched monitor 2 and 3 to use the other displayport connection on the laptop. Monitor 3 still works, and monitor 2 still does not work. So, it isn't the displayport failing. I switch the displayport cables. Same result. So, it isn't a problem with the cables, either. That would leave the monitor itself. However, if I unplug the power from monitor 2, unplug the displayport cable, then plug them back in again, the system recognizes both external monitors again (though sometimes I need to do this several times), and everything is good until the next time I have the hard-reboot problem.

Any ideas?
Thanks.

---

### Post by untrustytahr on 2017-10-23
You probably already did this, but just to make sure... you did re-install their driver after the upgrade?  Problems like this are what usually get addressed by it.  I'd like to be able to offer more, but you're system is far more complex than what I use (multi-monitor/discrete gpu etc), so I'm not well versed in video issues.

---

### Post by david7838 on 2017-10-23
Well, that was interesting.
I just uninstalled the system76-driver and system76-nvidia-driver, then reinstalled them, and restarted.
I now have version 17.10.3 of these packages.
I tried locking the machine, and experienced what appeared to be a nervous breakdown of the system.
I got the lock screen, that then blanked out, then the lock screen re-appeared, then blanked out, then re-appeared, then blanked out, and I needed to do a hard-reboot to recover.
:-O

---

### Post by david7838 on 2017-10-23
By the way, nvidia-settings says that I am using nvidia driver version 384.90.

---

### Post by david7838 on 2017-11-06
It turns out that the issue was entirely due to the monitor. The problem vanished when I replaced the BenQ GW2765 monitors with Dells.

---

### Post by Hasimir on 2017-11-07
In my experience this is a nVidia driver problem.
With xorg nouveau drivers I never have this problem, which instead reappears the moment I use nVidia drivers of any kind

---

### Post by abean on 2017-12-10
I too narrowed it down to the nvidia drivers. I had the same problem on the previous version of ubuntu (17.04?). After the upgrade that seems to fix things, but the same freeze happens after a wake up attempt and a hard reset is necessary.

---

### Post by prashu20 on 2018-01-18
I don't have any Nvidia drivers or hardware but I still face the same problem on Ubuntu 17.10.I have an external monitor connected sometimes to my Dell laptop. I am not sure if this is issue too since I sometimes face the situation of ubuntu not waking up or taking a very long time. I hope somebody fixes this issue in ubuntu 18.04.

---

### Post by whatif987 on 2018-01-21
I have vanilla 17.10 installed on a System76 Kudu Laptop, resume from suspend doesn't work about 50% of the time, and I have to hard reboot by holding down the power key. 
One thread I read suggested running "journalctl -p crit" which had this error: 
```
Jan 21 11:23:46 galactica gnome-session-binary[1411]: CRITICAL: Unable to create a DBus proxy for GnomeScreensaver: Error calling StartServiceByName for org.gnome.ScreenSaver: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.gnome.ScreenSaver exited with status 1
```

This is a brand new Kudu laptop that I received about a week ago. It originally had Pop! on it but I replaced it with Ubuntu 17.10.

---

