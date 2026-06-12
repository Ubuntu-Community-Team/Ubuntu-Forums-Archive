---
title: "Whose getting prority here?"
date: 2011-04-23
forum: Ubuntu Studio
---

### Post by mikee55 on 2011-04-23
Hello again, I have my system set to give Jack priority, but when I play a YouTube video on firefox, I get drop outs in my music? I'm listening to online streams in Aqualung, so I have Aqualung open and the Jack control panel. My Frames/Period is 1024, Sample rate 96000 Periods/Buffer 4 Latecy 42.7. I can get a lower Latency, but get more interuptions or dropouts when I surf the web.

Any ideas?
Thank you
Mike :D

---

### Post by sgx on 2011-04-23
> **mikee55 said:**
> Hello again, I have my system set to give Jack priority, but when I play a YouTube video on firefox, I get drop outs in my music? I'm listening to online streams in Aqualung, so I have Aqualung open and the Jack control panel. My Frames/Period is 1024, Sample rate 96000 Periods/Buffer 4 Latecy 42.7. I can get a lower Latency, but get more interuptions or dropouts when I surf the web.

Any ideas?
Thank you
Mike :D
Hi, I'd bring down the sample rate, nothing on the net will yield
96000, I would set everything at 44100 or 48000, so no resampling gets involved. Are you using mozplugger, or mplayer plugin for the youtube? It sounds like you are trying to listen to youtube and a separate audio stream at the same time? (wish I new more about mozplugger, flash, streaming, give weight to other opinions!
Cheers:)

---

### Post by mikee55 on 2011-04-23
Hello sgx, I've got a alsa jack module installed and now I can just lsten to my stream with Movieplayer, and it gets patched through Jack, I'm doing the same as I did  with Aqualung, except I'm not getting issues. I now have JAMin and Audacity running, and I'm EQ'ing in RT and recording it at the same time.  I think I must be using less resources this way. I played a video and its fine.

So I guess this is sort of solved :)

Thank you

Mike:guitar::guitar:):P

---

### Post by sgx on 2011-04-24
> **mikee55 said:**
> Hello sgx, I've got a alsa jack module installed and now I can just lsten to my stream with Movieplayer, and it gets patched through Jack, I'm doing the same as I did  with Aqualung, except I'm not getting issues. I now have JAMin and Audacity running, and I'm EQ'ing in RT and recording it at the same time.  I think I must be using less resources this way. I played a video and its fine.

So I guess this is sort of solved :)

Thank you

Mike:guitar::guitar:):P
Reminds me to get some books and writings written by
Sir Winston Churchill. He probably got a migraine
when Obama dissed the Queen!

---

