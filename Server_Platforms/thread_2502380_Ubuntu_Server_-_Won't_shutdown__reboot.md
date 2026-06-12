---
title: "Ubuntu Server - Won't shutdown / reboot"
date: 2024-11-12
forum: Server Platforms
---

### Post by lord-emperor on 2024-11-12
Ubuntu Server 22.04.5 LTS running on my homelab, which is a Ryzen 5600G in a B450 motherboard.

This has been happening for a while now but I wasn't able to get console output because my server is headless and tucked away where I can't easily connect a monitor. Finally got myself a NanoKVM (it's awesome BTW) so I can read the console output during reboot.

On shutdown or reboot, the system hangs and requires a hard reset. Last console message is:

    [  OK  ] Stopped target System Time Set.

I've left it for hours just to make sure it's not simply taking a long time.

[IMG]https://preview.redd.it/x4jkyeosfj0e1.png?width=811&format=png&auto=webp&954a4228[/IMG]
[IMG]https://i.imgur.com/B7E9k6P.png[/IMG]

---

### Post by TheFu on 2024-11-13
Console messages are probably in the dmesg output.  Output from prior boots dmesgs are available using **journalctl -b -2 ** to see the boot logs from 2 boots ago.  It is common to have at least 10 boots of logs saved in the system, but YMMV depending on your journald.conf settings.

You can ssh into the system and run **dmesg -w** to watch the shutdown happen, if you like. You probably knew this already.

22.04 is too new for my needs, but I've never seen this issue on my B450 Ryzen 2600 or Ryzen 5600G systems. 

I use 
```
sudo shutdown now 
``` to shutdown my systems. There are a multitude of different options.  There's also the **systemctl** method, which is probably what shutdown finally calls. All that means is that the best method is probably overly documented in the systemctl manpage. You've probably already read those options. The systemctl manpages are verbose. That's certain.  Looks like 
```
sudo systemctl poweroff
```
is the approved method. Are you using that?

---

### Post by lord-emperor on 2024-11-13
The command I'm used to is
    sudo reboot now

That said, I went nuclear and did a dist-upgrade. The machine is now rebooting normally on 24.04.1. The only fallout I had to deal with was upgrading PHP.

---

### Post by TheFu on 2024-11-13
> "Nuke the site from orbit - it's the only way to be sure"

In general, I'm good with doing that to any php webapps that aren't automatically maintained for me. ;O

---

