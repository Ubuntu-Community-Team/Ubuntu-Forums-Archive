---
title: "PulseAudio Mute/Unmute Button"
date: 2012-09-26
forum: Ubuntu Studio
---

### Post by jameh on 2012-09-26
Hey, I'm running Ubuntu Studio 12.04.1 on a Macbook Pro 5,2
Out-of-the-box, the volume keys on my keyboard work, and show an overlay of the effect they have on the volume in the top right.

Except for the "unmute" command - I get the visual overlay feedback showing that audio 'is' muted, but it has no real effect (audio stays muted) until I manually go into PulseAudio menu, and click "unmute".

So, media keys mute, increase volume, and decrease volume, but do not unmute.

Anyone else with similar problem, or proposed solution?

---

### Post by Sylos on 2012-09-27
Hello.

There should be a 'keybindings' menu somewhere under system (not at an ubuntu machine so cant remember where exactly). It may be worth having a look there and checking if the mute/unmute key is actually bound to the unmute command.

Cheers

---

### Post by jameh on 2012-09-27
The key bindings menu (under settings -> keyboard) don't have the media keys listed. It seems like PulseAudio itself is listening for those presses?

---

### Post by Sylos on 2012-09-30
Hmmm.... well I have to admit I dont really use pulseaudio (or media keys for that matter). Last time I set it up I think I had already removed pulse and was using just alsa.

Try looking here [http://ubuntuforums.org/showthread.php?t=987149](http://ubuntuforums.org/showthread.php?t=987149)

The ideas near the bottom of the page sound promising. Maybe binding the mute one of those one liners to your mute key might work.

Good luck.

Cheers

---

