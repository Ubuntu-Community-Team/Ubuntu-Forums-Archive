---
title: "Trying to get my video card to use dynpm power mode at start up."
date: 2013-02-26
forum: Ubuntu Development Version
---

### Post by rfw2nd on 2013-02-26
I am trying to make my video card (Radeon HD4670 on open source drivers under 13.04) use the 'dynpm' power mode at boot.  I cannot seem to make this happen, either through upstart or udev.

My upstart script: /etc/init/radeon-dynpm.conf
```

start on starting lightdm 
script
    echo dynpm > /sys/class/drm/card0/device/power_method
end script

```It works if I manually run 'service radeon-dynpm start'  but it does not work from boot.

I found that others had similar issues with init scripts, so I decided on writing a udev rule:
/lib/udev/rules.d/10-local.rules
```
KERNELS=="0000:01:00.0",SUBSYSTEMS=="pci", DRIVERS=="radeon", ATTRS{power_method}="dynpm"
```output of udevadm here: [http://pastebin.com/maxH2DCs](http://pastebin.com/maxH2DCs)

:( no effect.  After reboot power_method is "profile", power_profile is "default", and my laptop sounds like a windtunnel.

Any help with this issue will be much appreciated.

---

### Post by brainwash on 2013-02-26
Did you check /var/log/upstart/ for a radeon-dynpm.log file? Changing the "start on" parameter might help. You can find more information about the event triggers here:
```
man upstart-events
```

Not sure about your udev rule. Here's an alternative approach:
```
KERNEL=="card0", SUBSYSTEMS=="drm", DRIVERS=="radeon", ATTRS{device/power_method}="dynpm"
```

One last thought, you should use the directory for custom rules instead:
```
/etc/udev/rules.d/
```

---

### Post by rfw2nd on 2013-02-27
Thank you for the replies.  I found a solution that worked here:
[http://www.techytalk.info/ubuntu-open-source-ati-radeon-driver-power-usage-tweaks/](http://www.techytalk.info/ubuntu-open-source-ati-radeon-driver-power-usage-tweaks/)

---

