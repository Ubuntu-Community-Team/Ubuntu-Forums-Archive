---
title: "Driver Installation Soundcard Dell VostroA90"
date: 2010-01-15
forum: Ubuntu Moblin Remix
---

### Post by firewalldevil on 2010-01-15
Hello,
 
i hope for Help.
 
I use Mobil 2.1
 
I have the System Vostro A90 from Dell. I have replace the wirelesscard is does not work. Now i have a Intel Card install and it works. The same problem with the sound card. I can control the Sound but i dont hear something. So how can i check is the sounddriver installed and works. And how can i install the driver, give a compatible sound driver for Dell ?
 
so many thanks

---

### Post by nanotube on 2010-01-24
> **firewalldevil said:**
> Hello,
 
i hope for Help.
 
I use Mobil 2.1
 
I have the System Vostro A90 from Dell. I have replace the wirelesscard is does not work. Now i have a Intel Card install and it works. The same problem with the sound card. I can control the Sound but i dont hear something. So how can i check is the sounddriver installed and works. And how can i install the driver, give a compatible sound driver for Dell ?
 
so many thanks

hi
i have the vostro a90
this worked for me to get sound working on ubuntu karmic:
[http://www.ubuntumini.com/2009/11/fix-audio-on-dell-vostro-a90.html](http://www.ubuntumini.com/2009/11/fix-audio-on-dell-vostro-a90.html)  

(summary: edit /etc/modprobe.d/alsa-base.conf, and add "options snd-hda-intel model=dell" to the file)

also, you probably didn't need to change the wifi to an intel card, i found that the broadcom STA wifi driver (install package 'bcmwl-kernel-source', and reboot) works fine. though it's nice to have an intel chipset, so you can use a fully-open-source driver. :)

---

