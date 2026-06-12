---
title: "TTS10 permissions revert on bot up"
date: 2008-03-21
forum: Server Platforms
---

### Post by dlcobb on 2008-03-21
I am using domus.link with Heyu to control my X10 setup.

In order to use Domus under apache, the ttyS1 permissions need to be 0777.

When I set this, domus works properly.  But when I reboot, the permissions revert to   0666.

Are there other setting required?

Thanks

---

### Post by volkswagner on 2008-03-22
I am newbie but I think this will require a udev rule.

This should get you started.

[http://ubuntuforums.org/showthread.php?t=168221]("http://ubuntuforums.org/showthread.php?t=168221")

I have a little experience with this.  I can possibly offer advice.  When creating your new rule, use just the name of the device if you only have one.  This will allow the rule to work even if the input number changes.

Here is a simple example for my usb remote control.



```
ATTRS{name}=="Gyration Gyration RF Technology Receiver", GROUP="groupNAMEHERE", OWNER="usernameHERE", MODE="0666"
```

---

### Post by dlcobb on 2008-03-26
It turns out that there is an entry in the startup scripts that sets the dev/ttyS1 to 660.

I put a chmod into the etc/rc.local script and all is well.

Thanks

---

