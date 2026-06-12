---
title: "Headphone Jack, Volume Control"
date: 2007-08-03
forum: System76 Support
---

### Post by ackey on 2007-08-03
I apologize in advance if I should have been able to sort this out on my own, but I haven't been able to find a solution straightforward enough to implement.  I have the new Darter Ultra and am a complete newb.

When I plug in headphones into the front, the main speakers aren't muted.  Additionally, the volume options (front/headphone/PCM) seem to control the "main" (headphone/speakers) volume at the same time.

What do I need to do to have the headphone volume up and the speakers muted?  Thanks!

-Nicole

---

### Post by palintheus on 2007-08-03
I can confirm that when headphones are plugged in the main speakers stay on, and when you try to use the volume control to turn down 'front' the headphones turn down as well, although the actual volume setting doesn't move and vice-versa.

---

### Post by thomasaaron on 2007-08-06
Thank you. Could you please file a bug report at:

[http://launchpad.net/system76](http://launchpad.net/system76)

---

### Post by palintheus on 2007-08-06
[https://bugs.launchpad.net/system76/+bug/130669](https://bugs.launchpad.net/system76/+bug/130669)

---

### Post by ackey on 2007-08-08
I've been able to get the headphones to have an ok output volume (still rather quiet) and very low speaker output (quiet enough to not be heard by others) by turning the front and headphone volume all the way up and the PCM volume down to about 5%.

---

### Post by greg_g on 2007-09-14
I am having the issue again, even though it was fixed from the driver update.

See my comment on the bug link above.

---

### Post by thomasaaron on 2007-09-14
I'll have to check it out on a Darter. There have been a bunch of updates to come down lately.

A couple of things, you have to mute the "front" when you have the headphones in. Are you doing that?

Also, did you try running the driver again just for the fun of it?

---

### Post by greg_g on 2007-09-15
Preface: just re-ran the "install drivers" function on the System76 driver.

Ok.  So, here is what is going on:
play a song, adjust level of sound via the Fn-f7/f8 keys.
plug in headphones, speakers mute (good).
now, if I adjust the volume via the Fn keys the speakers turn back on (unmute).

The reason I want to use the Fn keys to adjust the volume while I have my headphones on is two-fold.  A) convenience, I don't want to have to click on the speaker icon. B) the volume is a combination of PCM and Front values.  If I had my speakers really quiet before plugging in my headphones then the headphones are quiet no matter how high I put the PCM value.

I think the issue I am having is that I want the Fn-f7/f8/f9 keys to adjust the PCM values, not the Front values.  That way, when I use those keys with the headphones on it won't turned the speakers back on.  They would be master volume controls, instead of just speaker volume controls.

And, ideally, when headphones are plugged in the speakers are not able to play sound.

I'm not sure how other laptops do it (I forget how my HP does it, I'll test it later tonight).

Am I just doing things differently than I should?  Am I being clear on what I am doing and what my expectations are?

So, to summarize, this is not a bug, it is a quirk.  If it is a possibility to change which value the Fn keys adjust to PCM instead of Front that would probably do what I want.

And again, if I am just wanting something that is different from common practice, then tell me to shut up.

---

### Post by thomasaaron on 2007-09-17
You can mute the front speakers by going into your volume control (double-click the speaker icon), go to Edit>Prefs and make sure everything is checked. Then find the "Front" slider and mute it.

To make your function keys control headphone volume, go to System > Prefs > Sound and at the VERY bottom, select headphones.

---

