---
title: "Do you have problems with Sound Recorder?"
date: 2009-11-16
forum: The Cafe
---

### Post by -=hazard=- on 2009-11-16
After I did a fresh install of Ubuntu 9.10, I'm having problems with sound recorder. I notice that the Sound Input is very low. I have reviewed all audio settings and they look fine. Playback works just fine.

---

### Post by dragonboss on 2009-11-16
No problems with sound recorder for me. Actually this is the first ubuntu my internal mic and sound recorder has worked on!

Try increasing the input volume from Sound Preferences > Input. This was set low for me and had to increase it to hear what i recorded,and for skype to work.

---

### Post by -=hazard=- on 2009-11-16
> **dragonboss said:**
> No problems with sound recorder for me. Actually this is the first ubuntu my internal mic and sound recorder has worked on!

Try increasing the input volume from Sound Preferences > Input. This was set low for me and had to increase it to hear what i recorded,and for skype to work.

I know that but even if I increase the input volume, the input level is very low and recorded audio have an horrible quality. Same with Analog Input. Look @ the attachments.

---

### Post by Bungo Pony on 2009-11-16
I've got a weird problem in 8.04. Every once in a while, the input goes kaput. A reboot usually fixes it. I can only guess it's my friend Pulse Audio having fun.

---

### Post by wulfgang on 2009-11-16
Not matter what version of ubuntu I run, it has always bugged-up.

---

### Post by coldReactive on 2009-11-16
I can't use sound recorder in the first place,

A. I don't use mics,
B. My Output cannot be recorded (only in Vista and 7.)

---

### Post by -=hazard=- on 2009-11-16
65 views and only 3 votes?...

---

### Post by coldReactive on 2009-11-16
> **-=hazard=- said:**
> 65 views and only 3 votes?...

I can't vote, since my sound has good quality, but I can't use it in ubuntu atm.

---

### Post by -=hazard=- on 2009-11-16
> **coldReactive said:**
> I can't vote, since my sound has good quality, but I can't use it in ubuntu atm.

Yes you can! lol
You have the second option ```
No I dont. My recorded audio have a good quality.
``` But the answer is only for sound recording, not playback.

---

### Post by coldReactive on 2009-11-16
> **-=hazard=- said:**
> Yes you can! lol
You have the second option ```
No I dont. My recorded audio have a good quality.
``` But the answer is only for sound recording, not playback.

But I can record my playback in Windows, but not linux, how unfair is that? :|

---

### Post by -=hazard=- on 2009-11-16
> **coldReactive said:**
> But I can record my playback in Windows, but not linux, how unfair is that? :|

Problem solved :) Let me make some screens and then post them here.

---

### Post by -=hazard=- on 2009-11-16
I was messing up before and I found out that while recording, on Pulse Audio volume control, on recording tab, you must change the recording stream from Internal Audio Analog Stereo to Monitor of Internal Audio Analog Stereo. Just do that and Sound Recorder will save that settings so next time you will record immediately without doing this again. Remember first you must start recording something with Sound Recorder than go on Pulse Audio volume control recording tab, to change that settings. Hope this helps.

---

### Post by coldReactive on 2009-11-16
> **-=hazard=- said:**
> I was messing up before and I found out that while recording, on Pulse Audio volume control, on recording tab, you must change the recording stream from Internal Audio Analog Stereo to Monitor of Internal Audio Analog Stereo. Just do that and Sound Recorder will save that settings so next time you will record immediately without doing this again. Remember first you must start recording something with Sound Recorder than go on Pulse Audio volume control recording tab, to change that settings. Hope this helps.

I don't know how to get those dialogs anymore, since karmic now makes you open "Sound Preferences." :(

---

### Post by starcannon on 2009-11-16
I don't have problems, but I don't use Sound-Recorder, I use [Audacity]("http://audacity.sourceforge.net/").

---

### Post by -=hazard=- on 2009-11-16
> **coldReactive said:**
> I don't know how to get those dialogs anymore, since karmic now makes you open "Sound Preferences." :(

Do you have Pulse Audio Device Chooser installed?

---

### Post by coldReactive on 2009-11-16
> **-=hazard=- said:**
> Do you have Pulse Audio Device Chooser installed?

How do I install it?

---

### Post by -=hazard=- on 2009-11-16
> **starcannon said:**
> I don't have problems, but I don't use Sound-Recorder, I use [Audacity]("http://audacity.sourceforge.net/").

I think the problem is on PulseAudio Volume Control settings only on Karmic, and not the application. For example on Jaunty I didn't have this problem.

---

### Post by -=hazard=- on 2009-11-16
> **coldReactive said:**
> How do I install it?

On Ubuntu Software Center. Search with "pulse", select and install PulseAudio Device Chooser. It must install the other stuff too, like Pulse Audio Volume Control, PulseAudio Manager etc.

---

### Post by coldReactive on 2009-11-16
> **-=hazard=- said:**
> On Ubuntu Software Center. Search with "pulse", select and install PulseAudio Device Chooser. It must install the other stuff too, like Pulse Audio Volume Control, PulseAudio Manager etc.

Thanks, I guess.

Also, how do I get gtk-recordmydesktop to record audio from my output?

---

### Post by starcannon on 2009-11-16
> **-=hazard=- said:**
> I think the problem is on PulseAudio Volume Control settings only on Karmic, and not the application. For example on Jaunty I didn't have this problem.
Could be, I haven't had a reason to check it out since upgrading to Karmic; guess I could do a "just because" so I can see how it pans out. Is Ubuntu Studio still using the Jack plugins?

---

### Post by -=hazard=- on 2009-11-16
> **coldReactive said:**
> Thanks, I guess.

Also, how do I get gtk-recordmydesktop to record audio from my output?

You just reminded me to test it and it capture only video without sound. Still I haven't figured it out. I think gtk-recordmydesktop work only with alsa, but I'm gonna search and let you know if I resolve it.
Did you resolve sound record at least?

---

### Post by -=hazard=- on 2009-11-16
> **starcannon said:**
> Could be, I haven't had a reason to check it out since upgrading to Karmic; guess I could do a "just because" so I can see how it pans out. Is Ubuntu Studio still using the Jack plugins?

I don't know, to be honest I have never tried Ubuntu Studio.

---

### Post by -=hazard=- on 2009-11-16
coldReactive Open gtk-recordmydesktop, go to Advance then on Sound tab and instead of DEFAULT write "pulse" without quotes. Then start recording something random while playing audio, then open PulseAudio Volume Control, go on recording tab and change from Internal Audio Analog Stereo to Monitor Internal Audio Analog. Just like the audio I explained you before. Then close volume control. It must save that settings so the next time you record video+audio you don't have to do this again.

---

### Post by coldReactive on 2009-11-16
> **-=hazard=- said:**
> coldReactive Open gtk-recordmydesktop, go to Advance then on Sound tab and instead of DEFAULT write "pulse" without quotes. Then start recording something random while playing audio, then open PulseAudio Volume Control, go on recording tab and change from Internal Audio Analog Stereo to Monitor Internal Audio Analog. Just like the audio I explained you before. Then close volume control. It must save that settings so the next time you record video+audio you don't have to do this again.

lol, thanks, it works!

---

### Post by -=hazard=- on 2009-11-16
> **coldReactive said:**
> lol, thanks, it works!

U'r welcome. This was the 3 day I was figuring out how to manage it, and now I feel so much relaxed :D

---

### Post by dmccasland on 2009-12-12
Thanks for this easy but arcane solution!  Now I can record again.  


> **-=hazard=- said:**
> I was messing up before and I found out that while recording, on Pulse Audio volume control, on recording tab, you must change the recording stream from Internal Audio Analog Stereo to Monitor of Internal Audio Analog Stereo. Just do that and Sound Recorder will save that settings so next time you will record immediately without doing this again. Remember first you must start recording something with Sound Recorder than go on Pulse Audio volume control recording tab, to change that settings. Hope this helps.

---

### Post by premamotion on 2009-12-29
> **wulfgang said:**
> Not matter what version of ubuntu I run, it has always bugged-up.

 same to me! good point...

---

### Post by -=hazard=- on 2009-12-29
> **premamotion said:**
> same to me! good point...

Well is a community maintain os, what do you expect... Even winzoz that cost 500$ have bugs!
The nice thing for linux is that, comparing with other os, we are a helpful and friendly community :)

---

### Post by premamotion on 2009-12-31
Yes, there are problems with the sound recorder...

---

### Post by -=hazard=- on 2010-01-01
> **premamotion said:**
> Yes, there are problems with the sound recorder...

If you got the same problem I described on this thread, then go on post #12 and you find the solution. It's not really a big problem, but just a tricky one.

---

