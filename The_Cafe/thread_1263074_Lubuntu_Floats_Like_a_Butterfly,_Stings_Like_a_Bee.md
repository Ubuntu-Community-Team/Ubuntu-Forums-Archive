---
title: "Lubuntu: Floats Like a Butterfly, Stings Like a Bee"
date: 2009-09-10
forum: The Cafe
---

### Post by karlmp on 2009-09-10
[http://www.linux-mag.com/cache/7520/1.html](http://www.linux-mag.com/cache/7520/1.html)

---

### Post by NormanFLinux on 2009-09-10
I emailed Lubuntu to let them know about their lack of support for wireless cards and the fact their beta has no installer. What good is even a half finished beta if you can't install to the hard drive? And it doesn't have a decent GUI bootup screen - just verbose mode.

---

### Post by chris4585 on 2009-09-10
> **NormanFLinux said:**
> I emailed Lubuntu to let them know about their lack of support for wireless cards and the fact their beta has no installer. What good is even a half finished beta if you can't install to the hard drive? And it doesn't have a decent GUI bootup screen - just verbose mode.

Actually, I think you can install it to the hard drive.... Its just not obvious.  It may work if  you install ubiquity and install it that way... I might be wrong though.

---

### Post by earthpigg on 2009-09-10
> I emailed Lubuntu to let them know about their lack of support for wireless cards

are you sure it isn't just that they haven't chosen to use Ubuntu's default networking applet, and are using LXDE's default?

```
sudo apt-get install network-manager-gnome
sudo sed -i 's/OnlyShowIn/#OnlyShowIn/g' /etc/xdg/autostart/nm-applet.desktop
```

done - log out and back in. Ubuntu's default networking applet will be in your LXDE system trey.

the same trick also works for gnome's power manager and LXDE.

there are also a couple of other networking applets that are far easier to use than lxde's default.

i cannot comment on why they would not include any of the multiple wireless-friendly applets by default.... the Ubuntu/lxde-based project in my sig was thrown together in my spare time, and includes it.

part of the "blame" (if you want to call it that) also rests with Debian -- why is NetworkManager packaged to only work with xfce and gnome by default? LXDE is pretty damn freedesktop.org complaint, too.

---

### Post by NormanFLinux on 2009-09-10
Ubuntu standard sees the onboard wireless card. Lubuntu beta acts like it isn't there and l grep reports no wireless extensions found. Its a stock Broadcom 4312g card that works under Ubuntu.

---

### Post by earthpigg on 2009-09-10
> **NormanFLinux said:**
> Ubuntu standard sees the onboard wireless card. Lubuntu beta acts like it isn't there and l grep reports no wireless extensions found. Its a stock Broadcom 4312g card that works under Ubuntu.

how the heck did they manage to break that???

if you are up to it, i would be very interested to know if your wireless works with my project, in my sig. 325mb dload.

---

### Post by NormanFLinux on 2009-09-11
It works in eeebuntu lxde though. No problems seeing it there but they're using 9.04 Jaunty while Lubuntu is Karmic Koala - very bleeding edge.

---

