---
title: "Turn off all power saving features for a laptop running Ubuntu Server"
date: 2022-02-11
forum: Server Platforms
---

### Post by onlineapps on 2022-02-11
I have a really old Asus U31S laptop that has a broken screen, and I'm trying to run it as a home server (some mix of media server, smart home automation, and/or file storage). I leave it fully plugged in.

I installed 20.04 LTS Server using a borrowed monitor (the laptop is so old it only supports VGA...). I also disabled sleep, suspend, hibernate, and hybrid-sleep using systemctl ( [https://linux-tips.us/how-to-disable-sleep-and-hibernation-on-ubuntu-server/](https://linux-tips.us/how-to-disable-sleep-and-hibernation-on-ubuntu-server/) ).

However, every so often, I am no longer able to ssh in. Because I no longer have the monitor, I can't actually see what went wrong. When I hard power down and hard power back up, everything seems to work fine, so I am fairly sure the machine just went to sleep.

Any ideas on how to debug this? (even if I had the monitor, I am not sure what I would be looking for).

---

### Post by LHammonds on 2022-02-11
Could it be the lid closing causing the issue?

[https://ubuntuhandbook.org/index.php/2020/05/lid-close-behavior-ubuntu-20-04/](https://ubuntuhandbook.org/index.php/2020/05/lid-close-behavior-ubuntu-20-04/)

I don't have a lot of suggestions since I do not run Ubuntu on a laptop or use a desktop GUI. 

LHammonds

---

### Post by onlineapps on 2022-02-11
I don't think so... the machine still works with the lid closed.

---

### Post by onlineapps on 2022-02-11
Sorry, I should mention&#8212;I had also set:

HandleLidSwitchExternalPower=ignore

Which is what I think the link you posted recommended.

---

### Post by MAFoElffen on 2022-02-12
Remember to disable it at the Linux kernel level...

In 'etc/default/grub' at line that starts with 'GRUB_CMDLINE_LINUX_DEFAULT=', add the boot parameters "acpi=off apm=off"... After saving, remember to update the grub files, via:
```

sudo update grub

```

---

### Post by uninvolved on 2022-02-12
This link may be of interest:

[https://linux-tips.us/how-to-disable-sleep-and-hibernation-on-ubuntu-server/](https://linux-tips.us/how-to-disable-sleep-and-hibernation-on-ubuntu-server/)

Full disclosure: It is mine.

---

### Post by linux-sysop on 2022-02-12
If you had xsession running, I would drop this into ~/.xsessionrc

```

xset s off
xset s 0 0
xset -dpms
```

I assume you didn't bother to install it with a broken monitor and all.  

Is there a switch in the BIOS perhaps?  That could be a real issue, since you have no way to view the BIOS.  It might be time to ask around for a VGA monitor, I would check the local pawnshops. I think Walmart has a few but I would never pay more than $10 for something I could pull out of my neighbor trash pile.  Good job keeping the old PC off the streets! +1

---

