---
title: "Sound mysteriously stopped working, other problems"
date: 2010-04-17
forum: System76 Support
---

### Post by thefinn93 on 2010-04-17
Hello all,
I've been playing with stuff ever sense I got my computer, and at one point all of the sound drivers (except ALSA) tried to send every sound to my bluetooth headphones, even if they weren't plugged in. I never managed to fix this problem, but yesterday my trusty ALSA stopped working out of the blue. I have no idea why. I fire up VLC, give it something to play and it plays fine except that I can't hear it. It gives me no error messages or anything. I tried to reinstall the drivers using the system76 Driver tool, but that insists that I'm not connected to the Internet (which I'm guessing may have to do with the fact that I installed wicd to replace nm-applet, but i really have no idea). Any help would be appreciated.

---

### Post by thefinn93 on 2010-04-17
Wow ok so i was poking around the forums a bit after posting that and found something in a previous thread that I had apparently totally overlooked telling me to to remove a the Software Modem driver as it had a nasty bug in it. I check to see if it was there and sure enough it was, and after removing it and turning up the volume sound works fine. This driver thing is still troubling though

---

### Post by thomasaaron on 2010-04-19
I've run into this driver issue a few times, but I've not been able to duplicate it in the shop. 

I wouldn't *think* it has anything to do with wicd, as it simply pings system76.com to see if you're connected.

If you're behind a firewall, maybe that has something to do with it.

---

### Post by thefinn93 on 2010-04-19
Nope. i pung system76.com from the terminal fine.

---

