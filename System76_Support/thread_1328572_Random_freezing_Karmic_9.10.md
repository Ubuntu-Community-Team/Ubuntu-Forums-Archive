---
title: "Random freezing Karmic 9.10"
date: 2009-11-16
forum: System76 Support
---

### Post by gpstar on 2009-11-16
Any other people with system76 systems getting random freezing in 9.10 karmic 64 bit?

I've done a fresh install of 64 bit karmic on my bonobo laptop, pulseaudio eats up all the system memory after a few hours of operation, so I kill the process at startup now.

a bug related to this is posted already here

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/424655](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/424655)

The system will also randomly freeze every few hours, everything locks up, total screen freeze. syslog shows nothing in it that could be related to the problem. I've tried the latest 2.6.32-rc7 kernel and nvidia 190.45 drivers, they do not help.

[http://ubuntuforums.org/showthread.php?t=1313536](http://ubuntuforums.org/showthread.php?t=1313536)

---

### Post by gpstar on 2009-11-16
just minutes after posting this thread. System froze up yet again.

new logs attached.

---

### Post by Gundahar on 2009-11-17
I've got them too.    I also attempted a clean install, but that hasn't helped in the least.  This is on a Leopard.  One crash was severe enough that I had great difficulty getting X back working again.    I can't get an uptime of greater than 3 days :-(

---

### Post by 3Miro on 2009-11-17
This is probably related to your specific systems and/or settings. On kubuntu 9.10 I have seen no freezes (the good news is that this may be easily fixable).

---

### Post by thomasaaron on 2009-11-17
gpstar, your logs are filled with "invalid query packet" errors from the avahi-daemon, which I've seen cause freezes on a few other systems. Let's try disabling the avahi-daemon to see if the freezing stops...

sudo stop avahi-daemon
sudo sed -e '/^start/,+1s/^/#/' /etc/init/avahi-daemon.conf

...if that doesn't work, it is easy to re-enable the daemon.

---

### Post by gpstar on 2009-11-17
ok i'll give disabling the avahi-daemon a shot and report back in a day to see how stable it is.

---

### Post by gpstar on 2009-11-17
well that didn't work. just froze up again.

gonna start disabling some of my programs one at a time until it is stable. The only thing i'm running that isn't on a fresh install is gnome-do docky (latest bzr version), 3 instances of a terminal screenlet and a custom conky script setup.

---

### Post by thomasaaron on 2009-11-17
There is a ton of stuff in your logs, but I'm not seeing any restarts. 

Is your system completely freezing up and staying that way, or is it just freezing and then releasing?

Please delete your old tar.logs in your home directory and then completely re-create them each time.

---

### Post by gpstar on 2009-11-17
the computer just completely freezes up and stays that way. I have to hard reboot with the power button to restart the system.

i've been creating the logs each time i've had to restart the system.

i'll post another set again the next time it freezes up again.

---

### Post by gpstar on 2009-11-18
So far so good. I believe the problem was the Terminal Screenlets was causing the issue. I have since turned them off and so far have 8hr up time and no freezing. Will do the ultimate test tonight and leave it on over night, if it's not frozen when i wake up, then it should be good.

---

### Post by VertexPusher on 2009-11-18
In case the system locks up again, try the magic SysRq key sequence (Alt + SysRq + R E I S U B) to reboot the machine. If that works, it means that the kernel is still responding, and only the graphics subsystem has locked up. This could indicate an issue with the display driver.

---

### Post by gpstar on 2009-11-18
well i spoke a bit too soon. system just froze up on me again.

tried the ALT + SysRq + R E I S U B and that did not do anything.

logs attached from right after the reboot. Freeze happened at 10:46am on the system clock. Last thing in the syslog before the freeze was

```
Nov 18 10:45:01 michael-laptop CRON[11890]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
```

---

### Post by thomasaaron on 2009-11-19
Those "invalid query packet" errors are still there, which relate to the avahi daemon. I think the problem might be caused by a combination of things, namely...

1. The avahi daemon
2. vnstat (which is monitoring your network traffic every 5 minutes)
3. ??...and are you using ssh? There are reports of ssh and vnstat conflicting and causing lock-ups.

Try removing vnstat for testing...

sudo apt-get --purge remove vnstat

...and see if the lock-up occurs again.

---

### Post by Gundahar on 2009-11-24
For what its worth, I disabled the Avahi daemon, and have been three days with no crash--a HUGE improvement.  It looks like this was the culprit, at least at this point.  

Thanks for the tip TA!

---

