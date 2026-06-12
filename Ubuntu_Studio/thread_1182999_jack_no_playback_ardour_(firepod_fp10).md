---
title: "jack no playback ardour (firepod fp10)"
date: 2009-06-09
forum: Ubuntu Studio
---

### Post by Firepod on 2009-06-09
I have no playback in ardour (or any other recording software). I CAN record (the waveform is apparent on the track). 

Could it be my connections? Please see attached screen shots of my jack connections page. Hopefully it is a simple connections problem (although I have tried many combinations)

I set my mixer editor options in ardour according to the ardour manual. 
Here is the link: [http://ardour.org/files/manual/ch-recording.html#sn-basic-recording](http://ardour.org/files/manual/ch-recording.html#sn-basic-recording)


Attached is the standard connection that occurs after I load ardour

If I quit jack and play the file I recorded I can here the sound using the system playback. When using jack I hear nothing... 

What could be wrong? help would be greatly appreciated

---

### Post by Stochastic on 2009-06-10
Everything looks good, other than that waveform being a little on the quiet side, but you should still hear it.  Check which outputs you've plugged your amp into on the firepod.  Can you hear the track through the headphones if you turn the mix knob the farthest to the right (to monitor the output mix) and turn the headphone volume up?

If you can hear the file without jack, I'm assuming you mean through a different soundcard right?

---

### Post by Firepod on 2009-06-11
Thanks for the reply stochastic.

Do you mean that I can only get sound to playback through speakers if I plug them (or say headphones) into the output jack of the firepod? Is there no other way of routing the output back to the system playback through my desktop computer? If not, i guess ill have to get some new connections!

Thanks again for your help

---

### Post by Stochastic on 2009-06-11
Essentially, yes.  Jack is playing out of the Firepod.

In theory jack can use two soundcards (one for input, one for output) but I'm pretty sure they need to be using the same driver.  Chances are you don't have a second ffado card lying around to use, and the firepod won't run with ALSA drivers, so in your case this won't work.

---

### Post by Eduardo Curi on 2010-07-08
I&#7743; having a similar problem

I m running ubuntu 10.04 and i&#7743; using a m audio nrv10 mixer as a soundcard. It works fine with ffado, the blue light is on, and I can hear everything fine when I&#7743; recording, but when I playback nothing happens and all I hear is silence 

I&#472;e done all the connections through ardour and it should work fine, but it does not

also, on audacity, I can hear when I&#7743; recording but not when I&#7743; playing it back

And audacity doesn t even appear on the connections window in jack... on the preferences windows in it, I set up for using the system as the playback device, but even though, nothing happens

help me, please!

---

### Post by Pablo_F on 2010-07-08
I don't have a clue but did you follow these notes?

 [http://www.ffado.org/?q=node/29](http://www.ffado.org/?q=node/29)

If I were you I would ask/search in the ffado forums or mailing list.

BTW, Audacity (portaudio) works with jack if you configure it properly (preferences, audio server) but it is far from an ideal jack client. For example, the input ports only appear in the qjackctl connections when you press the record button. I wouldn't use it to record with a firewire card. 

Cheers! Pablo

---

