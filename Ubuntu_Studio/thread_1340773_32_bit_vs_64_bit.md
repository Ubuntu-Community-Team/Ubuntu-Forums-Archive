---
title: "32 bit vs 64 bit??"
date: 2009-11-28
forum: Ubuntu Studio
---

### Post by jitup on 2009-11-28
Ok here is the skinny, I need a powerful platform for media productions (digital video student) and want to go linux. I am more of an end user out of the box sort of linux user. I am good with learning programs, but I do not have a lot of spare time to learn how to run linux command line sort of stuff. (especially now that I just ordered Blender for Dummies) My system is capable of runing 64 bit and 32, is there any advantage to one over the other for ubuntu studio?(I belive my board can only handle 4gb of ram, at least bios Dram) Also can some body tell me if Blender, Cinelerra (which ever is the newest), Gimp or gimp shop, cine paint, Ardour (again the newest) are included in the distribution of these? These are the programs I plan to run mainly on this system (of course there will be others)Has good ATI support been added to ubuntu yet? (was the problem last time I gave this a try)
Thanks for all your help

---

### Post by cotcot on 2009-11-29
With the apps you mention go for 64 bit. I have 3 GB ram and an AMD Athlon X2 3800+. 
I am running all the applications you mention a lot on 64 bit on jaunty and hardy. Karmic will be OK as well. (I am running ubuntu, not ubuntu studio but the installation of the apps should be the same).
For blender I use the version that I download directly from the blender site. No install needed. Just extract the downloaded file and run the blender executable in the extracted file. If blender does no have sound then start it with "blender -g noaudio"

---

### Post by jitup on 2009-11-29
so, now the question is 9.10 64bit vs 9.04 64 bit of ubuntu studio? I have read that alsa dose not work properly, I know in 8.10 ubuntu 32 bit and 9.04 Ubuntu 32 bit, alsa worked well for my card (Emu 0404 usb) I want to use the machine for audio as well as video and graphics. Thanks a lot!

---

### Post by trulan on 2009-11-29
I'd say there are enough of advantages to 9.10 that it is worth it.  If you are going to do serious audio work, you'll want a real time kernel, and 9.04's kernel just isn't that great.  9.10 has a much better real time kernel.

Alsa works under 9.10, some things like the main gnome volume control have been turned over to Pulse Audio rather than Alsa and there are some folks who hate Pulse Audio.  It's never been a problem for me but I'm using ffado (firewire) for my audio so Alsa isn't a big deal to me anyway.  The few times I have used it though, it works.

---

### Post by jitup on 2009-11-29
OK! Thanks for all the help! I'm going to go for ubuntu studio 9.10 64 bit! Thanks alot!
I'm sure if I have a problem, (or the rare occurance where I can actually answer some ones question) you will hear from me again.

Thanks 
Jitup

---

