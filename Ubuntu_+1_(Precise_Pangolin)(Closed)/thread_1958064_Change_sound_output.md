---
title: "Change sound output"
date: 2012-04-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ELD on 2012-04-13
So in 11.10 you can just go into sound settings and change output but in 12.04 only 1 output is shown?

Any ideas how to change sound output?

---

### Post by ELD on 2012-04-16
Bump

---

### Post by Skaperen on 2012-04-16
I guess you are using the default PulseAudio.  I just posted about how it was essentially useless now in 12.04 (though the post disappeared ... may have to do over).  A colleague tells me many of the problems I described started happing when he upgraded to 11.04 (I previously was on 10.10 until I just tried 12.04 Beta2 with a fresh install).  That's on my netbook.  My plans for going to 12.04 for my full desktop are now put on hold.  I will explore alternatives to PulseAudio to see if that is the problem, or if it's a driver issue for my sound device (ASUS S101 netbook).

---

### Post by ELD on 2012-04-16
Well in 11.10 the sound settings had the option to use hdmi audio output, this 12.04 only has my inbuilt speakers listed?

---

### Post by ayozito on 2012-04-16
Do you have drivers installed? I have analogic stereo audio and HDMI digital stereo audio outputs.

---

### Post by Mr. Picklesworth on 2012-04-16
Close the System Settings dialog, if you have it open. Run this in a terminal&#8230;
```
env XDG_CURRENT_DESKTOP=GNOME gnome-control-center
```
&#8230;and use the sound panel there. Does it list the HDMI output?

As ayozito says, this could be related to drivers. Your graphics driver plays a role in this, for example.

---

### Post by ELD on 2012-04-16
Interesting, doing it that way you suggested gives me the option of changing the profile to HDMI, it used to give you that option via the sound settings via the sound indicator but it was removed.

It has dual graphics, intel and nvidia.

---

### Post by Mr. Picklesworth on 2012-04-16
> **ELD said:**
> Interesting, doing it that way you suggested gives me the option of changing the profile to HDMI, it used to give you that option via the sound settings via the sound indicator but it was removed.

It has dual graphics, intel and nvidia.

That means the new sound settings (sound-nua) might be detecting something incorrectly. If you'd like to file a bug report, this will be a good place to start: [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center)

Note that the new panel technically displays a list of *ports* instead of internal audio devices. (So, with everything working nicely, it can be more tactile: it can say "Play sound through Plantronics Headset" instead of "Play sound through [sound card]").
If I recall correctly, on this same line of thinking, it tries to hide ports that have nothing attached. Is there an audio device connected to your HDMI port? If not, try doing so. And think speakers, not sound cards.

---

### Post by ELD on 2012-04-17
Gah didn't know that at all, worked great when i just tested it - only thing that doesn't work, is it doesn't detect it has been disconnected until I manually go to settings -> displays, my screen flashes and then bam back to one monitor and hdmi audio dissapears.

Any idea on when Unity will be able to detect an external monitor has been disconnected?

---

### Post by Mr. Picklesworth on 2012-04-17
> **ELD said:**
> Gah didn't know that at all, worked great when i just tested it - only thing that doesn't work, is it doesn't detect it has been disconnected until I manually go to settings -> displays, my screen flashes and then bam back to one monitor and hdmi audio dissapears.

Any idea on when Unity will be able to detect an external monitor has been disconnected?

Aha, good to know! I only use analog outputs so far, so I haven't been able to see it really working. Do you think it's something the panel could communicate better? I wonder if people who haven't used Ubuntu before would have a problem with that, or if it's just an issue if you're used to the old sound panel (which, barring some layout changes, looks and feels similar enough that you might expect it to behave the same).

Hotplugging seems to be one of those graphics driver things that refuses to go away. Works in some cases, completely doesn't in others. You don't happen to be using an NVidia GPU, do you?

---

### Post by ELD on 2012-04-18
I think it does need better communication to the end user, there is nothing telling you it has recognised a new input anywhere, nothing tells you where to go. Even for an experienced user like me i didn't know it.
 
I have dual graphics intel and nvidia, so it would use the intel graphics for all of this since it only uises the nvidia graphics when i run "optirun" from the bumblebee project.

---

