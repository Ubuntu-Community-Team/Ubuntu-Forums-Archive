---
title: "Ardour Playback"
date: 2012-03-22
forum: Ubuntu Studio
---

### Post by pmains on 2012-03-22
I am having trouble playing what I have recorded through my PreSonus Firepod (FP10) back through my speakers. I am wondering what the easiest way to do this is.

I notice that when I start qjackctl, audio from youtube stops. Is there a way to have Jack simultaneously connected to Firewire and a soundcard?

---

### Post by Sylos on 2012-03-23
Hello there.

Jack is an audio server that interacts with your soundcard through alsa (which is essentially the driver). It would be normal to expect launching it to kill sound through non-jack apps such as web browsers etc. You can make some apps play through jack so that you could potentially have sound from youtube etc through jack. I dont do this - I just switch between jack and and non-jack when Im doing different things.

As for your Ardour not giving any sound I would suggest this is a simple configuration issue. Can you give some details about your jack set up? Also post the output of your jack message window once it is started and ardour is playing.

As for multiple sound cards - it is possible using and alsa config file to use both your onboard soundcard and an additional card. It means writing a config file especially for the purpose and can be a little tricky for the inexperienced. I would suggest first get it all working with one card and then try if your still interested.

Cheers

PS: Are you still using pulseaudio?

---

### Post by AndrewS1967 on 2012-03-25
Does anybody still   have this problems or has foxtel fixed it?  Few days ago I watched an  old movie -picture flickering but today just watch Escape to the Country which recorded on Friday - no problem with playback.  Cheers

---

