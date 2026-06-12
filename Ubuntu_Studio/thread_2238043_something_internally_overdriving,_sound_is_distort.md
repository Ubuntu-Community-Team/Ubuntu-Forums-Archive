---
title: "something internally overdriving, sound is distorted"
date: 2014-08-05
forum: Ubuntu Studio
---

### Post by a-you on 2014-08-05
I've been denoising wav files with Gnome Wave Cleaner and twice while doing that I had increased the volume of the playback just by selecting "Sound Settings..." with the mouse, when clicking the speaker icon that generally controls audio volume on the panel. One time I swear that the dialog that opened actually showed a set of horizontal faders for Gnome Wave Cleaner itself, though never again have I been able to get that to display. That time I had pushed the playback volume up past 100%. And then another time even though those faders never appeared again, I increased the playback volume of "Built-in Audio Analog Stereo" to above 100%.

That was a few restarts ago. Now I discover that if I try to play any file with Gnome Wave Cleaner the sound is distorted, as if the output of GWC into the next virtual device is hugely amplified. But "Sound Settings..." now displays the default 100% value for the output volume, and of course reducing that volume only reduces the final output volume, but the sound is still distorted. It's impossible to bring that *internal* level down, so as to eliminate the distortion.

I'm guessing that it might have to do with GWC being relatively old, and maybe there's still some setting somewhere in between it and the modern output that has been forgotten, but which can still be modified, and when it is it saves the new setting, but the "Sound Settings..." dialog doesn't "know" about it. BUT that's really just a guess.

Only GWC is affected; if I play the same file with any other app it sounds fine, but it seems to me possible that it could have happened with any app, or maybe any older gnome app.

Purging and reinstalling GWC didn't fix it.

I'm sure JACK was not running the *second* time I had pushed up the  volume slider, though I don't recall for sure whether it was perhaps  running the first time (but I did try starting JACK then GWC on the idea  that that might again reveal the extra volume sliders, but it didn't).

If anybody has any idea how to fix this---I'm trying to get the volumes  normalized along the signal pathway from GWC to the headphones, to eliminate the distortion---I would  appreciate it! Thanks in advance!! I have no idea where to start, and  interwebs searches don't turn up anything relevant.

---

### Post by a-you on 2014-08-06
Just an update, in case this bit of info might help somebody else---frankly the solution seemed not at all obvious!!!

Turns out that only when Gnome Wave Cleaner was actually playing a file, not just when it was running, only then was the elusive volume setting visible in the "PulseAudio Volume Control" gui, accessed by clicking "Sound Settings..." from the speaker icon in the panel.

I imagine that this would be true for other apps too.

---

