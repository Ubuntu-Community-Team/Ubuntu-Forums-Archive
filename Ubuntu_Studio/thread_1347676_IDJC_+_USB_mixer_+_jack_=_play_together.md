---
title: "IDJC + USB mixer + jack = play together?"
date: 2009-12-06
forum: Ubuntu Studio
---

### Post by eveningshift on 2009-12-06
Hi,

I'm trying to get a podcast set up using the following;

[LIST]
[*]Ubuntu 9.10 (Karmic)
[*]Alesis 4 USB mixer
[*]Internet DJ Console (IDJC)
[*]jack
[*]Icecast server
[/LIST]

I can get the mixer to work and record with Audacity. I can't, however, get IDJC to see the mixer as an input (so we can broadcast to Icecast live)

I know it's possible to configure jack to make this work, but I'm not having much luck with getting this working.

Has anyone tried something similar? Am I making a rookie mistake? (Yes, it's switched on! :)  )

Thanks,
EveningShift

---

### Post by bobince on 2009-12-07
That's a USB Audio device, is it?

You will have to configure JACK to use the device. From qjackctl hit &#8216;Setup...&#8217; and pick the mixer from the &#8216;Input Device&#8217; dropdown. It may be called something like &#8220;hw:1,0 USB Audio&#8221;.

Of course the problem now is that the output device (your soundcard) is different to the input device. Being separately clocked they will drift and you'll get occasional xruns. JACK 1 is designed to work with a single audio clock and won't resample one device to match another.

How bad this sounds is a matter of luck and what you're using them for (for my purposes and with my USB mic it's acceptable; YMMV). If you are doing your whole broadcast from the mixer with no additional sounds sourced from idjc, you could ditch the output device completely (Audio->Capture only) and just listen to the built-in output of the USB device (using idjc's volume meters to ensure no clipping). Or if the worst comes to the worst, just use the mixer's line out to go into the sound card's line in instead of using a USB connection. Then JACK can happily use the same sound card for input and output.

(Has anyone tried JACK 2 for multi-device audio? Does it fix this kind of problem? Is it usable/stable in Ubuntu?)

---

### Post by VertexPusher on 2009-12-07
> **bobince said:**
> JACK 1 is designed to work with a single audio clock and won't resample one device to match another.
If you connect Jack to plughw instead of hw PCMs, resampling will be performed by ALSA.

---

### Post by bobince on 2009-12-07
That would be only a straight resample from one bitrate to another based on the same clock though... it wouldn't be able to fine-tune one clock to match another that was ostensibly the same bitrate, but in reality very subtly different (and potentially even very slightly varying).

---

