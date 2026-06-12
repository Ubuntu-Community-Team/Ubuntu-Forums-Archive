---
title: "No sound from Ardour on Ubuntu Studio 14.04"
date: 2014-09-23
forum: Ubuntu Studio
---

### Post by newholm1 on 2014-09-23
Hi there. I have recently got Ubuntu Studio 14.04 up and running on my  Lenovo E540 laptop, and am now trying to get Ardour working. It seems to  play smoothly and I can see the sound levels on the screen, but I am  getting no sound. I have tried a few settings in Jack but to no avail.  Another issue is that Jack seems to only run at 48000, which is  insufficient for my needs. On my desktop it runs at 96000, and the sound  plays back no problem. I assume this is a routing issue as I am trying  to get sound through the internal soundcard rather than an external  interface. I would appreciate any help anyone can give.

---

### Post by davevr on 2014-09-24
Can you explain how you fixed this? I hav econnected my Roland Quadcapture, I see the soundlevels but no sound with playback.

---

### Post by newholm1 on 2014-09-26
Hi. This is what worked for me, it may vary for you depending on your laptop.

1. Ardour master outputs set to Playback 1 & 2 (I am currently only using the internal soundcard)

2. Jack setup to use interface hw: PCH (for you this will probably be the Roland)

3. Audio Mixer (on Audio Production - Mixers and card control sub menu) - select from the list (in my case hw: PCH, in your case probably the Roland again - as long as it matches the setting in Jack) and make sure it is all turned up and nothing is muted. This third stage was the last piece in the puzzle - I had sorted the other steps but didn't realise this mixer was involved in the routing.

4. Volume Control - make sure speakers are turned up. Sounds silly, but for some reason when I alter other sound settings, somehow the sound of the speakers keeps getting turned down.

I hope this helps!

---

### Post by rgonnering on 2015-01-05
I have the same problem.

Where is the Audio Mixer (on Audio Production - Mixers and card control sub menu) - select from the list (in my case hw: PCH, in your case probably the Roland again - as long as it matches the setting in Jack)?

---

