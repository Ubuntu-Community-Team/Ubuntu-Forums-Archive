---
title: "Hydrogen is choppy and distorted"
date: 2008-05-11
forum: Ubuntu Studio
---

### Post by drunkmatador on 2008-05-11
Actually it's mostly just distorted, but a little choppy too. Just installed it onto my x64 Hardy and Jack was on as well.. should it be this choppy?

I have a hp dv2000 notebook with on board sound, not that great but surely it can handle Hydrogen, right?

---

### Post by Stochastic on 2008-05-11
Actually it's not Hydrogen's processing that's chopping up/distorting the sound, if anything it's the audio processing of Ubuntu.  The vanilla kernel is just not built to handle Jack or any serious sound app.  I'd highly recommend trying out the reatime kernel (and the rest of the UbuntuStudio packages) if you want to work with audio on Ubuntu.  Also if things are distorting, try turning the volume down - both in alsamixer and hydrogen (sometimes people overlook these simple troubleshooting steps).

---

### Post by grizzly69 on 2008-07-17
I am experiencing the same thing. When I am using Hydrogen with or without Jack it happens. When a sound is played like kick drum or snare I get a clicking/popping distortion with it. I am using the UbuntuStudio 8.04 rt kernel 64bit. I have an AMD Athlon 64 3800+ with 2GB DDR2 ram and a soundblaster live card. I do not have this distortion problem with other apps like Ardour. Just Hydrogen.

It is odd that I also have Ubuntustudio 8.04 i386 rt kernel running on a Athlon XP 1.3Ghz computer with 512MB sdram and a Sound blaster Ensoniq PCI sound card without any distortion at all. It works just fine.

I may take the time to do some hardware troubleshooting and see if it is my soundcard or the _x64 version that makes a difference.
But I would like some ideas to check as far as software I could do first.

---

### Post by Ed J on 2008-07-18
I am also hearing lots of popping using Hydrogen.  I created my "song" in Hydrogen, exported it as a .wav. Next I imported it into Ardour.  It sounded great there.
  I also checked it out by playing it in Kaffine, it also sounded better there then it did while playing in Hydrogen.

  Now maybe we can find out why...Maybe my friend ALSA?

  If I turned the drum levels down in Hydrogen to eliminate popping, the track would be too low later on when mixing with others. Sure I could lower the levels of the other tracks to compensate but I worry about would losing some of that fat headroom. Also I wouldn't want to be in a position where I have to increase the level of the drums, lower vocals, guitars, etc and crank the master at mixdown, that has always produced a thin and/or noisy finished product.

---

### Post by deadgobby on 2008-07-18
A little choppy never hurt Trent Reznor of NIN. HA! Is it a certain drum kit that it is happening. What are your bass levels like on the kick or toms? 
Gobby

---

### Post by Ed J on 2008-07-18
> **deadgobby said:**
> A little choppy never hurt Trent Reznor of NIN. 
Gobby

Were those drums? I thought they were steel mills.:)

---

### Post by unclestick on 2008-07-20
I'm a beginner and trying to get ubuntustudio working for me. I had the same problem (just a couple of guitar tracks and a hydrogen drum track) but it seemed like not only was the drum seq choppy/distorted, but so was the audio..I think...I couldn't listen to it very long...I knew it wouldn't cure itself.

Once I figured out how to access and use my 2nd hard drive for the music files, no choppy, no distortion (using the same tracks as before).

So far, I've found the answers to all my problems here and I'm getting over my command-line phobia. Thanks, folks! I'm getting sound in, recording it and playing it back. I'm tickled!. - unc

---

### Post by arthursucks on 2008-07-23
Sometimes it might be Jacks buffer.  The default is like 2 but if I don't bump it up to 6 I get chop city.  Just a stab in the dark, maybe it'll help.

---

### Post by Co.Sinecure on 2008-09-03
I had this problem just now, but I found that if I started up jack, and restarted hydrogen it sounded fine!

I don't know if that would help you folks, still don't get what the cause would be. Seems to be related to the frequency - i.e. the lower the sound, the worse it is. I could hear it on the kick and snare, and a little on the low tom (on the default kit)

---

### Post by Stochastic on 2008-09-03
Frequency itself should have no bearing on the audio processing load - in theory.  In practice however, the lower drums (kicks, toms, etc...) will be longer samples, and thus their playback will take more horsepower.

In general these steps should fix any issues with choppy sound in Hydrogen:
-use Jack, not direct alsa
-use the realtime kernel
-turn on the realtime flag in jack
-increase your jack buffer size if you still experience choppiness

---

### Post by saturni on 2011-10-28
same problem. hydrogen is choppy. don't know how to change jack settings. had it working on here before with no problems.

---

### Post by sgx on 2011-10-29
> **saturni said:**
> same problem. hydrogen is choppy. don't know how to change jack settings. had it working on here before with no problems.
Hi, the 4th and 8th links from the list at the wiki link

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

cover jackd/qjackctl with screenshots and info.
The others are good as well. And youtube has several videos
about using hydrogen, and also ardour for recording it.
Plus related linux audio sidebar videos. A usb soundcard
should have a qjackctl Periods/Buffer setting of 3,
Raising the Frames/Period settings to the next highest increment
should help, and maybe also adjust the Timeout/Msec
keep notes of what helps.

Cheers

---

### Post by Totalchaos on 2011-10-29
> **saturni said:**
> same problem. hydrogen is choppy. don't know how to change jack settings. had it working on here before with no problems.

if the problem is jack related you will see Xruns jumps like hell. If this is the case increse frames/period until it stops
another solution might be changing the sample rate to 48000
adjust the realtime priority to 89 (so no process can outrun jack in the queue)
in my experience adjusting the timeout/msec is related only if the server is crashing on startup or on start of an application.
and here is some advises that you guys doesn't want to hear, but thay might be the trouble maker :-(
choppy and distorted sound is a trademark of puleaudio sound system "in action". When using pulseaudio there are always several programs which sounds choppy and there is only one solution if that is the case - remove the pulseaudio. The painless way if you are using Gnome as DE is with this ppa: 
ppa:dtl131/ppa

another reason that might be causing this sorts of problems is if you are using 64bit platform on 32bit optimised hardware. There is a very popular misunderstanding that if your CPU can manage 64bits you must use it by default. Well hmmm.. NO after all your computer is more than a CPU and it is very likely that your other components  are not 64bit optimised. In this case even if your system in common is working fine, the bubble is popped whenever the jack server says "come on hurry up, some realtime please". I can almost bet on this, 'cause i was experiencing this issue some time ago and learnt my lesson.

PS: Hope this helps, if not don't judge me i was only trying to help. After all everyone of these advises has been helpful for me over time

---

### Post by sgx on 2011-10-29
I love good advice, opinions based on facts and experience, and reminders about certain villains lurking in /usr/bin  :popcorn:

Cheers

---

### Post by jejeman on 2011-10-30
> **Totalchaos said:**
>  remove the pulseaudio. The painless way if you are using Gnome as DE is with this ppa: 
ppa:dtl131/ppaThe most painless way is to just turn off pulseaudio. No need for removal.

> I love good advice, opinions based on facts and experience, And as far experiances goes, after replacing jack2 with jack1 (11.04) i don't have any problems, or xruns.

---

### Post by sgx on 2011-10-31
Maybe it should be renamed Jack Toobadd :)

---

### Post by breek on 2011-11-18
yep, i had the same problems (lots of xruns) but seems that turning off pulseaudio everything is ok.

edit /etc/pulse/client.conf and change from "; autospawn = yes" to "autospawn = no"


then in qjackctl preferences set
```

pulseaudio -k ; sleep 5

```
in the "execute script on startup" field

and
```

sleep 3 ; pulseaudio -D

```
as "execute script after shutdown"

---

