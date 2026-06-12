---
title: "Touchpad doesn't work after upgrade"
date: 2009-04-28
forum: System76 Support
---

### Post by 982000971 on 2009-04-28
Upgraded my Serval Performance to 9.04, rebooted and the touchpad doesn't work any more.

Advice?

---

### Post by thomasaaron on 2009-04-29
See if it works while booted into a live cd. If it does, your hardware is good. If not, your hardware is bad.

If your hardware is good, try running this command...

sudo modprobe psmouse

If that makes it work, we can fix it. Otherwise, you have a hosed upgrade and their are probably other problems waiting for you. I'd re-image.

---

### Post by 982000971 on 2009-04-29
Re: sudo modprobe psmouse
-------------------------
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
-------------------------
I'll get a LiveCD to test later...

---

### Post by 982000971 on 2009-05-21
LiveCD tested. Mousepad does NOT work on 9.04 LiveCD. Mousepad DOES work on 8.10 LiveCD. Using a USB mouse right now...

---

### Post by thomasaaron on 2009-05-22
Which Serval Performance do you have? (System > Administration > System76 Driver will tell you)

I'm not getting any other reports on this problem.

Did you try...

```
sudo modprobe psmouse
```

...?

---

### Post by king EZi on 2009-05-24
Im having almost the same problem, it worked on 8.10 and 8.04 but now whenever i boot or resume after suspend and hibernate touchpad seems to be disabled and i have to disable it and enable to make it work...quite annoying.

---

### Post by 982000971 on 2009-05-24
System Name:  Serval Performance
System Model: serp1

Re: sudo modprobe psmouse
-------------------------
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
-------------------------

---

### Post by thomasaaron on 2009-05-26
> -------------------------
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
-------------------------

That's pretty bizarre. I don't get that on any of our computers.

Was the live CD you used freshly downloaded, or is it pretty old? If it's old, do a fresh download. Email me at support(at)system76(dot)com with the results. I need to get your order number to look up more info about your configuration.

---

