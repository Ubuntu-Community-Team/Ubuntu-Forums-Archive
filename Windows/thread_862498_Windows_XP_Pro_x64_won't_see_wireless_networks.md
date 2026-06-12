---
title: "Windows XP Pro x64 won't see wireless networks"
date: 2008-07-17
forum: Windows
---

### Post by Erdaron on 2008-07-17
So, I have recently put together my first box. I'm very excited. And to be forward-minded, (and since the CPU supports it) I decided to go with a 64-bit OS, specifically Windows XP Pro x64 (will eventually dual-boot with Ubuntu).

I'm also trying to use a wireless network adapter (Linksys WMP54G v4.1 PCI). Linksys itself doesn't provide 64-bit drivers, but [RaLink does]("http://www.ralinktech.com/ralink/Home/Support/Windows.html"). Now, Windows recognizes the device, however, when it scans it cannot locate any networks.

My laptop, sitting right next to the box, detects networks just fine, and there is plenty of signal strength.

Also, occasionally, the box will suddenly have a wireless epiphany, detect networks and connect to the right one. Once that happens, it works very well, until I reboot (and since I'm just loading the box, there is a lot of rebooting).

I have tried googling, but could only find posts about installing the drivers - and I got that to work. This happens whether I use RaLink's configuration utility or Windows Zero. I have tried picking various devices listed under RaLink when picking the driver, and that seems to have no positive impact.

So. Windows XP Pro x64. Linksys WMP54G v4.1. Does not like detecting wireless networks.

Thanks for the help!

---

### Post by sysdrum on 2008-07-17
Are you using the Windows XP WL app that is built in or the third party app provided by RAlink?

You may be able to strip just the drivers and install only the base INF drivers in to the XP pro X64 and us the WL app that xp SP2 put in place.

If that does not work then you may need to find a third party 64bit connecter app that suppports your card.

---

### Post by Erdaron on 2008-07-17
I have tried using both RaLink's own wireless configuration utility, and Windows Zero Configuration tool (shutting down RaLink's utility). RaLink also allows you to declare which utility to use (its own or WZC), and I've tried both settings. This did not seem to have any effect.

You're right, though. This does feel like a software conflict somewhere. I've had similar troubles with Broadcom's utility trying to take over.

---

### Post by Erdaron on 2008-07-24
Couple of developments (for the benefit of anyone looking to solve the same problem).

Removing the RaLink utility from the startup sequence seem to speed this up.

When I created my own account on the machine, instead of using the default Administrator, things seem to have gone even faster.

---

