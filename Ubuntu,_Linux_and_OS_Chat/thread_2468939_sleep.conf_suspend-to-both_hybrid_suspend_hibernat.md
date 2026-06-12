---
title: "sleep.conf suspend-to-both hybrid suspend hibernation"
date: 2021-11-15
forum: Ubuntu, Linux and OS Chat
---

### Post by lucmorizur on 2021-11-15
Hi;

in **/etc/systemd/sleep.conf** , after having setting following line this way:

```

SuspendMode=platform standby

```

my laptop (Dell Latitude E5570 with Ubuntu Studio 20.04.3 LTS (Linux 5.4.0-90-lowlatency) and Xfce 4.14.2 (which personally I will keep when Ubuntu Studio will switch to Kde)) has the following behaviour: when suspending (either by closing the lid or requesting so directly), the system first writes the RAM to the disk, and then suspends. This way, if I open the lid back, the system gets out from suspension immediately, as usual after suspending. But if for any reason the battery reaches an empty state, then when starting the laptop again (after powering it of course), it comes back from hibernation, getting the state it was having at the suspend request.

This is the best suspension to my opinion ( a "true" "**suspend-to-both**"), as this way, the state of the system is preserved whatever the state of the battery is. And as it is the default suspension mode which is set, this behaviour occurs for each suspend request, ie when battery reaches critical value, if suspend is requested in such case.

Attention, /etc/systemd/sleep.conf has the lowest priority value after /usr/lib/systemd/*.conf.d/, /usr/local/lib/systemd/*.conf.d/, and /etc/systemd/*.conf.d/ .

Of course, first check if your system is able to proceed to hibernation.

If anyone knows how to do the same with Windows 10... it would be great. Thanks!

---

