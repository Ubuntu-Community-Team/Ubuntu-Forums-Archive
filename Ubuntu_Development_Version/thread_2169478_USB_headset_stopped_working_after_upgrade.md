---
title: "USB headset stopped working after upgrade"
date: 2013-08-22
forum: Ubuntu Development Version
---

### Post by Wise Ferret on 2013-08-22
Mu USB headset stopped working after upgrading from raring to saucy on a Dell xps 13 laptop.

It appears as "digital stereo headset" in the  sound settings in gnome control center, but choosing it does nothing now, and when I close and re-open the sound settings and the  chosen sound is still "internal sound" (or something similar - my system language is not English).

In pavucontrol, my headset does not appear at all in the "Output Devices" tab - only internal sound and analogue headphones. Oddly it does appear in "Configuration" tab, where it is set to "combined analogue stereo".

In lsusb I see: Bus 003 Device 010: ID 03f0:8c07 Hewlett-Packard Digital Stereo Headset

Any idea about what I can do next?

---

### Post by sudodus on 2013-08-22
Since you are running Saucy, I suggest that you help the developers find the problem by filing a bug

```
 apport-bug package
```

Maybe the package is ***pavucontrol*** or ***pulseaudio***

[COLOR=#808080]If you have no account at Launchpad, this is a good time to get one in order to write a description and continue a dialogue in the bug report.
[/COLOR][URL="https://help.launchpad.net/YourAccount/NewAccount"][COLOR=#808080]
[/COLOR][/URL][COLOR=#808080][https://help.launchpad.net/YourAccount/NewAccount](https://help.launchpad.net/YourAccount/NewAccount)[/COLOR][COLOR=#808080]

I think the login can be combined with the new login to Ubuntu Forums.[/COLOR]

---

### Post by Wise Ferret on 2013-08-22
ok, silly me. This problem solved itself magically after rebooting.
Ubuntu sometimes acts like windows in that respect...

---

### Post by sudodus on 2013-08-22
Yes, I agree. Reboot is one of the first things to try with a desktop installation. Glad you solved it so easily :-)

*Edit*: Particularly after upgrading I can understand why reboot can help.

---

### Post by Wise Ferret on 2013-08-22
I did reboot, twice, after upgrading. Apparently, third time was the charm.

---

