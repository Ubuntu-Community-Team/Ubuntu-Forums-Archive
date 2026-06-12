---
title: "Serval Pro v3 shutting down due to heat (?)"
date: 2008-12-11
forum: System76 Support
---

### Post by Trevor Bramble on 2008-12-11
Hello,

I've had a Serp3 for about a year and had not experienced any instability until recently.  Twice now, the system has powered off suddenly and cannot be powered on for 5+ minutes.  Most of the left side of the system has been hot to the touch (more so underneath) both times.

Both times the system was under light-to-moderate load, doing the same things I usually ask of it.  A few Firefox windows, Thunderbird, Eclipse, Amarok, SQL Developer, Pidgin, maybe a few other small things like Nautilus windows, Gedit, gnome-terminal.

I always have Compiz running, though of late I have disabled other workspaces, the cube, and all the related plugins for managing those.

The only thing I can identify that might have changed things for the worse is attempting to use hibernation.  Support for suspend and hibernate has always been dodgy in Ubuntu in my experience, and it was  as well when I first got the Serval, so I just lived without it.

Because I shuffle the system back and forth from home and office every day, I tried hibernate again.  And while I know for a fact that this morning I resumed a hibernated session, I can't recall (but do suspect) that I did on the previous time when the system over-heated as well.

Trying to find some info on the problem here, I came across [this thread]("http://ubuntuforums.org/showthread.php?t=854746") and following [the instructions]("http://www.techthrob.com/tech/linuxsensors.php") referenced within I set up temperature monitoring on my system.

The results are very concerning.  The processors are sitting steady at an acceptable 55 degrees celsius, but the video chip has stayed elevated between an alarming 69 and 72 degrees celsius.

Purely because I didn't know what else to try, I disabled Compiz (by way of selecting "None" on the "Visual Effects" tab of "Appearance Preferences".  That was more than half an hour ago and the only change appears to have been a drop from 71 to 69 degrees celsius.

Are these readings correct?  Is the system not being active enough with cooling that chip?  The cooling fan(s?) do wind up quite a bit sometimes, so I know they're dynamically addressing heat in some fashion.

Any help is appreciated.  I rely heavily on this system and while I can probably avoid the heat cut-offs by not using hibernation, I don't want to shorten its lifespan by burning out the components with undue heat.

---

### Post by thomasaaron on 2008-12-11
None of the temperatures you mentioned are alarming. They are pretty normal.

If you are using 32-bit Ubuntu, we've seen problems with cooling after hibernating. This is fixed in 64-bit Hardy and 64-bit Intrepid. I'm not sure about 32-bit Intrepid.

Also, remove the large panel on the bottom and make sure there are no dust bunnies dwelling in or around your fan or vent openings.

---

### Post by Trevor Bramble on 2008-12-11
I suppose my overclocked celeron-related cooling experience isn't quite applicable then.  I just fired up Unreal Tournament 2004 and played for a few minutes, which lifted the CPU temperatures to 70, and the GPU to 80.  So that's not climbing into dangerous territory?

Yeah, this is 32-bit Hardy (upgraded from Gutsy).  Haven't braved the Intrepid upgrade yet.  I'm thinking of upgrading the hard disk and doing a fresh 64-bit Intrepid install instead.

I did find a nickel-sized clot of dust packed between the fan and the heatsink.  CPU temps are holding at 54, GPU at 66, so I guess removing that helped some.  (Climate control is a bit better at home, so maybe that has something to do with it as well.)

Thanks for your help!

---

### Post by thomasaaron on 2008-12-12
70 for the CPU is higher-end, but certainly not critical. That GPU temp is getting worrisome, though.

 Re-locating the dust bunny should help.

---

