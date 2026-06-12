---
title: "Sound Capturing"
date: 2009-03-25
forum: Ubuntu Studio
---

### Post by iamshawnrice on 2009-03-25
Howdy.

I am looking to capture some sound effects from a soundboard [http://http://www.albinoblacksheep.com/flash/smbsynth]("http://www.albinoblacksheep.com/flash/smbsynth")

Is there a simple way to do this?

---

### Post by clubsoda on 2009-03-31
Open up alsamixer in a terminal.
Tab to View: [Capture]
Left/Right arrows to PCM
Spacebar to select ("L R CAPTUR" should appear)
Up/Down arrows to adjust level.

Then in a terminal type something like```
arecord -f dat mario.wav
```and ctrl-c when you're finished.

However, if you don't have PCM capture it may get a little more tricky, like connecting a cable from your sound output to the line-in and selecting "Line" in alsamixer.

Of course any copyright implications are your own concern. :)

PS: Nice find!

---

### Post by iamshawnrice on 2009-04-04
I actually stumbled upon a firefox extension, which unfortunately is supported by Windows only (gross) called the applian freecorder, [http://applian.com/sound-recorder/]("http://applian.com/sound-recorder/")

It did the job brilliantly.

Thanks for your advice.

---

### Post by B4RR13N705 on 2009-04-04
I have a simple way to do that!
Install ardour or audacity.
```

sudo apt-get install audacity
sudo apt-get install ardour

```
Then open sound settings, and turn on the PCM capture option.
Then press record on ardour or audacity and it will be recorded!
If you dont understand you can add me in MSN --> [email]juanchi_syn@hotmail.com[/email]

---

