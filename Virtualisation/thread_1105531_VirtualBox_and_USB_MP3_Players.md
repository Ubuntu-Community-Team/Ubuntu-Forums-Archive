---
title: "VirtualBox and USB MP3 Players"
date: 2009-03-24
forum: Virtualisation
---

### Post by kw1502 on 2009-03-24
I'm using Virtualbox 2.1.4 (PEUL) with Intrepid as host OS and Windows
XP as guest OS. Other than the "seamless windows", things work very well
except I can't use my Sansa e250 MP3 player in the XP. I've installed
guest additions and can access USB thumb drives in the XP. I can access the mp3 player from the host OS.

When I connect the MP3 player, it shows disconnected on the player's LCD
and is not usable. Does anyone know how to make this work?

[http://www.virtualbox.org/ticket/574](http://www.virtualbox.org/ticket/574) seems to document the problem but
does anyone have a workaround?

Thanks
kwat

---

### Post by kw1502 on 2009-04-01
bump

---

### Post by KCG102282 on 2009-04-01
Why aren't you using it in Ubuntu?

---

### Post by kw1502 on 2009-04-01
I want to use iTunes to manage my music library and want to run iTunes and a few other critical Windows applications in the VM.

---

### Post by KCG102282 on 2009-04-01
Is the player set to msc?

---

### Post by kw1502 on 2009-04-01
The player is set to MSC mode.

---

### Post by itendo on 2009-04-02
a) i am assuming other USB devices are among the things that are working fine; b) i am assuming that you have tried to boot your Sansa in Ubuntu (or other host) and it has worked (because in my experience if it doesnt get through the host machine it wont make it upstream to the Guest);

but c) are you having an issue where it will recognize the device on the host, then when you mount the device to VM, the guest steals it from being recognized by the host?

i am having this issue with a thumb drive (I.I. host to XP guest) and XP will even show the 'safely remove hardware icon', but wont recognize any hardware to actually remove.

---

