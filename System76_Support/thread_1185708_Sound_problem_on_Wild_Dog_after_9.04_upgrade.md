---
title: "Sound problem on Wild Dog after 9.04 upgrade"
date: 2009-06-12
forum: System76 Support
---

### Post by smiley on 2009-06-12
Hi - 

Ever since upgrading to 9.04, the sound on my Wild Dog workstation has cracked and popped - even if I have sound muted using the volume control.

After reading some forums, there's some indication that pulseaudio may be the problem, but I haven't found any solution that fixes the problem.

Any ideas what might be causing this?  It's pretty annoying.

thanks!

Miles

---

### Post by thomasaaron on 2009-06-12
Turn your PCM all the way up.

If that doesn't work, please post screenshots of System > Prefs > Sound.
Then double-click your speaker icon and take screenshots of each tab. Please post those as well.

You might also have a look at this thread...
[http://ubuntuforums.org/showthread.php?t=1184519](http://ubuntuforums.org/showthread.php?t=1184519)

However, I would probably not post there, as your problem most likely is different.

---

### Post by TheBuzzSaw on 2009-06-15
I had this problem when I first upgraded. I cannot remember what I did to fix the problem. I have since done a clean install (for reasons other than this).

Are you having problems in Flash? Or is all your audio busted?

---

### Post by smiley on 2009-06-19
I cranked PCM all the way up - no change.  A screenshot of sound prefs is attached.

Thanks for looking into this.

---

### Post by smiley on 2009-06-19
More screenshots - volume control

thanks again

---

### Post by thomasaaron on 2009-06-19
Thanks. Just compared those settings to our shop Dawg. Here are the differences on mine...

1. Playback Tab... Side is unmuted.
2. Recording Tab... I don't have the mux sliders. Try turning them up.
3. Switches... just out of curiosity, try disabling IEC958 Default PCM and enabling IEC958.

Other than that, your settings look good.

---

### Post by smiley on 2009-07-01
Hey -

Thanks for the tips - I tried all that with no change.  Any further ideas?  Sounds is unusable on my workstation.

thanks,

Miles

---

### Post by thomasaaron on 2009-07-01
What is the output of...

uname -r

...and...

cat /proc/asound/version

---

### Post by smiley on 2009-07-01
$ uname -r
2.6.28-13-generic

$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.18rc3.

---

