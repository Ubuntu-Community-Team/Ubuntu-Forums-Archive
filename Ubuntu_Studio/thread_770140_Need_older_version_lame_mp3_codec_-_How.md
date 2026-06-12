---
title: "Need older version lame mp3 codec - How?"
date: 2008-04-27
forum: Ubuntu Studio
---

### Post by 4Orbs on 2008-04-27
I would like to switch the lame mp3 codec to an older version that works better with my old sound card editing sound files with Audacity. Is this feasible and easy. I'm powered by Ubuntu Studio Hardy. Thanks.

---

### Post by Stochastic on 2008-04-27
Well before we can help you downgrade, you need to give us a bit more info such as which older version?  
It seems strange that your hardware (soundcard) would somehow have a preference for mp3 encoding codec; could you explain what you mean? Also editing audacity files has nothing to do with the lame encoder as the conversion process is done as you open the mp3 file.  Audacity stores the decoded data as a temp .aup file (raw format audio) then you do whatever editing you need to that raw data and export through the lame encoder (if desired).

So what troubles are you having exactly, or at least which version do you want to downgrade to?

---

### Post by 4Orbs on 2008-04-27
Thanks for your reply. The problem I have with the lame 3.97 codec is an unpleasant distortion (sounds like underwater choppiness) when I export an Audacity project to mp3. The same project sounds correct when exported to ogg or wav but bad with mp3. I have been making music podcasts for the past 3 years on my Windows XP and found the same distortion (in XP) when I would use the 3.97 codec. The 3.93 codec does not distort. I now have the 3.96 codec on the XP and it does not distort either which is weird because (if I understand correctly) lame 3.96 and 3.97 are the same. Yesterday I made my first podcast with Ubuntu Studio using Audacity and the distortion surfaced on the mp3 but not the ogg export. I might add that when I rip dvd movies using AcidRip, the distortion is not present even though the soundtracks are rendered as mp3. Maybe I only need to use a higher bitrate or true stereo rather than joint-stereo. I cannot find any place in Audacity to alter the settings.

---

