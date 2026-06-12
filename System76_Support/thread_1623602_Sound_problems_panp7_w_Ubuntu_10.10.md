---
title: "Sound problems: panp7 w/ Ubuntu 10.10"
date: 2010-11-16
forum: System76 Support
---

### Post by jarmot on 2010-11-16
I've been experiencing some sound problems on my panp7.  When it arrived a couple weeks ago the sound was great, but after a couple days it went out.  Sound on the login screen still works, but sound from speakers and out of headphone jack does not.  Once I'm logged in I can't hear a thing.

Here's what I've done so far:

Updated all ALSA drivers in attempt to fix problem.

Opened terminal.  Created an ALSA INFORMATION SCRIPT.
[http://www.alsa-project.org/db/?f=41a10a013df48553a1935711aa725998ab278b27](http://www.alsa-project.org/db/?f=41a10a013df48553a1935711aa725998ab278b27)

Attempted Restore in terminal with
<ls-lt/lib/modules/`uname~r/kernal/sound/>

Attempted restore through System 76 utility

Opened alsamixer in terminal to make sure all the levels were up and nothing was muted.


---

Nothing so far has worked.  Please let me know if have a direction you can point me in to get this sound fixed.  I'm as green as they come so speak slowly.

---

### Post by isantop on 2010-11-17
I have a feeling that the updated Alsa may be interfering with our ability to fix this. I'll go ahead and try, but I may be stuck.

You'll want to go to System > Preferences > Sound. On the hardware tab, click on the "Internal Audio" device, and set the "Profile for the selected device" to "Analog Stereo Duplex".

Then, go to the output tab and click on the "Internal Audio Analog Stereo" option. Also check that the output volume is up and the mute box is unchecked.

---

### Post by jarmot on 2010-11-17
Thanks so much for the help.  It turns out that I was set to Analog Stereo Input the whole time.  That helps tremendously.  Thanks again for the support.

---

### Post by Ketobbey on 2011-01-26
This worked for me to.
Just installed the linux install of DOOM3, sound lagged and Crackled...
The only thing this did not fix was the sound crackling... Turns out this was easily fix in the game settings by turning down the ingame volume settings.

Thanks heaps for post your thread and thanks for posting the solution


THIS THREAD SHOULD GET THE [SOLVED] mark of approval.. Would the poster/threader like to do that so other know this is the right place to go for the solution?

---

