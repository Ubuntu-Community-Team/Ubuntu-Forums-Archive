---
title: "Twin screens?"
date: 2006-12-05
forum: The Cafe
---

### Post by haxer on 2006-12-05
Hello im off tomorrow the 6th to by an 27" samsung lcd tv and i have to wounder if i connect it to my linux box with dvi cabel and nvidia drivers from automatix will it work or just collaps? ;) Im not to scard "whats the worst thing that could happen" ? I hope that the insurance will cover it ;)  but will it work from scratch how to "copy" the image to tv like i did in windows xp?:-k

---

### Post by IYY on 2006-12-05
It will probably give you a copy screen in the console and while booting, but then one screen will go black. You will need to modify your xorg.conf file to set it up correctly.

---

### Post by haxer on 2006-12-05
and how to do that the newbie way? Becuse when i used s-video cabel the tv screen was blackandwhite :-k

---

### Post by TLE on 2006-12-05
[This]("https://help.ubuntu.com/community/NvidiaTVOut") should get you started. Remember it requires the binary drivers from NVIDIA to work, don't know if you use those otherwise we're gonna have to find something else. It is a good idea to the entire thing before you start, and ask if you're in doubt.

---

### Post by haxer on 2006-12-06
Everytime anyone says "binary files" and specielly from Nvida i get crazy and scared ;)

---

### Post by TLE on 2006-12-06
Well if you installed something called NVIDIA drivers with automatix then it is probably the binary drivers from NVIDIA because the open sourve "nv" driver is installed per default. But it doesn't really matter, just remember to backup your /etc/X11/xorg.conf before you start and then you wont do anything that can't be undone if it doesn't work

---

### Post by haxer on 2006-12-06
Btw deosnt automatix2 installed drivers automaticly gets backuoped? sudo cp /etc/X11./xorg.conf_backup_200612030040/etc/x11/xorg.conf? 8)

---

