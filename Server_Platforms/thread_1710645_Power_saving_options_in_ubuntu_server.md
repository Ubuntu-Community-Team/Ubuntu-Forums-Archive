---
title: "Power saving options in ubuntu server?"
date: 2011-03-20
forum: Server Platforms
---

### Post by slewis1972 on 2011-03-20
Hi

I have just myself a Hp Proliant Microserver - 4 bay server. Currently installing ubuntu server on a usb stick. The server is going to replace my readynas duo as need more  as power as plan to run vmware server on it.

Anyway - as its going to be on all the time, I want to reduce the power consumption. Already plan to spin the drives down after 10minutes if no use.
Is there any other tweeks and tips anyone can advise?

I did have Win2008 server installed and got that down to 21W with 3 drives but would prefer a linux OS.

Use of the server - fileserver, utorrent box and vm's (eventually)

Any advice appreciated.

---

### Post by stmiller on 2011-03-20
You can do things like disable bluetooth modules, usb modules, wifi modules (if any) which all take power. That is, if you don't need usb, or those other things.

(/etc/modprobe.d/blacklist.conf)


It is also possible to set cpu speed limits IF the cpu/motherboard support different cpu speed states. Check out cpufreq utilities,

---

### Post by tgalati4 on 2011-03-20
You can turn it off with a cron script (say at 1 am) then set up wake-on-lan to boot when sending a magic packet.  I put a launcher icon on each desktop/laptop that calls a wakeup script:

#!/bin/sh
# Super cheesy script to wake my server and put up a notification to that effect
#
/usr/bin/wakeonlan 00:0D:56:FE:B9:D6
sleep 3
/usr/bin/wakeonlan 00:0D:56:FE:B9:D6
sleep 3
/usr/bin/wakeonlan 00:0D:56:FE:B9:D6
sleep 2
notify-send --icon=/home/tgalati4/Projects/scripts/server.svg "GC-Development Server is Booting"  "You'll be up in 3 minutes."
sleep 200
notify-send --icon=/home/tgalati4/Projects/scripts/server.svg "GC-Development Server is Alive" "You can login now."
exit 0

If you need it on every day, then you can normally set a wakeup in BIOS.

---

