---
title: "Increase volume - slider at 100%. Would amixer do the job?"
date: 2015-10-28
forum: Ubuntu Phone and Tablet
---

### Post by callmebruce on 2015-10-28
The speaker volume on my Nexus 5 running ubuntu-touch/ubuntu-rtm/devel 15.04 (r23) is low. When I answer a call in the car by putting it on speakerphone, I can hardly hear the person talking, even though I have the volume slider all the way to 100%. I tried running alsamixer under sudo to see if I could give it a boost, but get "cannot load mixer controls: Operation not permitted" error message in terminal.

Would I use amixer? How would I go about increasing volume? I can run amixer --help, but haven't figured out how to increase speaker volume.

Or would I edit /system/etc/mixer_paths.xml, and if so - what settings would I change?

---

### Post by callmebruce on 2015-10-29
Well, I tried amixer -D pulse sset Master 100%   - still not very loud. Might be a Nexus 5 thing. I still haven't messed with /system/etc/mixer_paths.xml, but that directory is read only. I need to figure out if I want to go into read/write mode.

(think I'm going about this wrong - cat /proc/asound/card doesn't work. Not sure how to increase volume)

---

