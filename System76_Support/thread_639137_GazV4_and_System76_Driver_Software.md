---
title: "GazV4 and System76 Driver Software"
date: 2007-12-12
forum: System76 Support
---

### Post by rdemars on 2007-12-12
FYI:  I had to use the System76 Driver (v2.1.3) restore function the other day to reload my wireless driver.  After it ran the wireless worked, but the sound stopped working.  I finally got the sound back by adding "options snd-hda-intel model=3stack" to the /etc/modprobe.d/alsa-base file.

---

### Post by thomasaaron on 2007-12-13
Hi, Rich.

I just sent you an email on this. But since it is here on the forums, I'll post my response for the community, in case anyone else is having difficulties:

1. The System 76 driver doesn't support the wireless on any of our computers. That is done by Ubuntu out of the box.

2. I just tested a GazV4, and sound worked fine after running the System 76 driver, which should install ALSA v.15rc3 in it. The one catch was, I had to check the "mix" box in the sound controls and uncheck the "external amp" box.

Adding model designations to the alsa-base file has blown many good speakers. And even if it gives you sound, there is a fair chance that *something* will not work...headphones, mics, etc...  I don't recommend doing it yourself. It is better if you let me do it for you (if I can't find a way around it). That way, if a speaker blows, it is here in my shop where... who cares. Speakers are generally not covered under warranty as damage to them is considered user-inflicted.

If you're happy with how your computer is running, that works for me. If you want to get it back into its oem configuration, I can help you with that too.

Best,
Tom

---

### Post by IgnacioMiller on 2007-12-14
Hey,

Same thing happened here on my Gazv4 and Tom's fix, well, fixed it.

Thanks again Tom!
Dan

---

### Post by sandwormblues on 2008-01-03
Same on my gaz 4.  I upgraded kernel versions and I lost sound.  Switching back to system76-driver 2.1.1 worked in ubuntustudio, but not ubuntu.  tom's fix worked.

---

