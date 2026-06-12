---
title: "force gigibit connection"
date: 2010-06-29
forum: Virtualisation
---

### Post by chrismitt2002 on 2010-06-29
i was on winmx 2day and noticed my icon for network wasnt in the taskbar in my vbox install of xp i also noticed that it wasnt running in 10/100 not 10/1000 i have a 8port 10/1000 switch and so i checked my server and shure enough it was runnin 10/1000 not 10/100 like my every day pc is so i tryed a few things unpluging and pluging the switch back in =no go disableing networking re enableing =no go also tryed restarting networking =no go 
so the question is how can i force 10/1000 in windows when it does that i just unplug the switch and plug it back in and that usely does the job but isnt doing it this time
well i tryed a reboot and now my host os is running in 10/1000 but xp running in vbox is still useing 10/100 how can i fix this

---

### Post by chrismitt2002 on 2010-06-29
bump

---

### Post by chrismitt2002 on 2010-06-30
pleezzzzz help
bump

---

### Post by bodhi.zazen on 2010-06-30
Virtualization does not directly use your hardware, so it depends on the emulation offered by virtualbox not your physical hardware.

There is a discussion here :

[http://forums.virtualbox.org/viewtopic.php?f=6&t=31576](http://forums.virtualbox.org/viewtopic.php?f=6&t=31576)

---

### Post by TheFu on 2010-06-30
Your hostOS needs to have GigE drivers and they need to work.
Your VM settings need to specify a GigE network adapter - this is in the "advanced" settings. I like the Intel PRO/1000 MT myself. I suppose you could use the AMD GigE virtual NIC, but I never have.
WinXP does not include Intel PRO/1000 MT drivers, so you'll need to get them from Intel and install them inside the guest OS AFTER the VM settings are changed. There is a chicken/egg problem with this, so download the drivers before you change the NIC settings.

Then will your WinXP client have GigE connectivity.  With an Ubuntu hostOS, I routinely get 650Mbps throughput doing this.

---

