---
title: "Fuzzy Sound in LMMS, Hydrogen, etc."
date: 2009-12-22
forum: Ubuntu Studio
---

### Post by cjmabry25 on 2009-12-22
I just installed ubuntu 9.10, and all is going well except sound. Whenever I make a beat in Hydrogen, it is very fuzzy, almost like the volume is too high so it clips, but no matter how much I adjust the volume whether it be the master volume in the program or the volume of my computer, it's still fuzzy. When I export is as a WAV however it sounds perfect. Does anyone know what's going on?

I have the same problem in LMMS. Every sound is so fuzzy you can't even hear what the sound is supposed to be. 

This happens with headphones, speakers, everything, so I know it's not my speakers or headphones.

Any help fixing this problem would be greatly appreciated.

Oh, and also, hydrogen beats will lag, slow down, speed up, and will not keep a constant BPM, but I'm sure this is because of my 512mb RAM. It may be related to the problems before though.

**EDIT:**

Well, I've decided to move to Ubuntu Studio, because it's logical that if I'm mostly going to be doing music editing/production, graphic design, etc. then why not install studio. Maybe that will fix my problem , but if not I'll be back.

Thanks again.
And if anyone could provide me with the terminal command to see pc info such as RAM, sound card, mobo, etc., that would be great.

Thanks for all the help so far. This community rocks.:guitar:

---

### Post by AutoStatic on 2009-12-23
RAM: **sudo dmidecode**
**free -m**
**cat /proc/meminfo**

Soundcard: **aplay -l**
Specific codecs: **cat /proc/asound/card*/codec* | grep -i codec**

Mobo: **lspci**

And are you using JACK?

---

### Post by cjmabry25 on 2009-12-23
> **AutoStatic said:**
> RAM: **sudo dmidecode**
**free -m**
**cat /proc/meminfo**

Soundcard: **aplay -l**
Specific codecs: **cat /proc/asound/card*/codec* | grep -i codec**

Mobo: **lspci**

And are you using JACK?

I think I'm using ALSA, but I'm so new to this sound stuff, I have no idea what ALSA, JACK, etc. really is. :confused:

Thanks. I'll do some more research to see if I can figure it out. Thanks for the help so far!

---

### Post by cjmabry25 on 2009-12-23
> **cjmabry25 said:**
> I think I'm using ALSA, but I'm so new to this sound stuff, I have no idea what ALSA, JACK, etc. really is. :confused:

Thanks. I'll do some more research to see if I can figure it out. Thanks for the help so far!

Ok so I read up on the subject a little, and realized that JACK is a plugin for ALSA. From what I've read, it seams like it is for inputting and outputting (is this i/o?), such as plugging in MIDI stuff and outputting it to speakers and stuff? But I'm not using any external hardware like a MIDI keyboard. So would I need this? I'm sort of confused on what JACK does...

thanks again.

---

### Post by AutoStatic on 2009-12-23
You don't need JACK. In LMMS you can check which soundstack/soundserver you are using (Edit - Settings - Audio Settings). You could try selecting PulseAudio, maybe that improves the quality a bit in your case. For Hydrogen I have no idea, other programs don't have that fuzzy sound issue?

---

### Post by cjmabry25 on 2009-12-23
> **AutoStatic said:**
> You don't need JACK. In LMMS you can check which soundstack/soundserver you are using (Edit - Settings - Audio Settings). You could try selecting PulseAudio, maybe that improves the quality a bit in your case. For Hydrogen I have no idea, other programs don't have that fuzzy sound issue?

Whenever LMMS would boot before, it was selecting ALSA, and it would be extremely fuzzy where all sounds sounded the same - just fuzz. Now it was selecting dummy (no sound output), so I put it back to ALSA and it's still fuzzy. Hydrogen is the same, except when I try to change from ALSA it says audio driver could not be loaded to every one I select, even ALSA.

I can listen to youtube videos fine though, and hear the beats (.wavs) played back in movie player perfect. I just don't get it.

Anyways, I am going to install Ubuntu Studio right now, so if the problem persists there, I'll be back.

Thanks so much for your help so far.

---

### Post by cjmabry25 on 2009-12-24
Well, I just installed Ubuntu Studio and same problem. Hydrogen is much clearer now, almost not fuzzy at all, but in LMMS it's still so fuzzy I can't tell the difference between different samples. I'll play around with driver selection in LMMS and let you know. 

Thanks so much.

---

### Post by cjmabry25 on 2009-12-24
Alright so I've officially made a major breakthrough lol.

I opened up JACK Control, selected the JACK Drivers in LMMS (previously this wouldn't work, I guess its cuz I hadn't started JACK) and finnally sounds are playing like they should. It really sounds great. Now to the bad news...

I get popus that say something along the lines of LMMS has been kicked by JACK, or something, and these will popup a lot, I'll hit OKAY, and another pops up, until randomly they go away. However, the appear again, and it's really wierd. Anybody have any idea on why this is happening?

I'll read up on JACK tonight and tomorrow, and I'll ask my questions about it tomorrow.

Thanks sooooooooooooooo much.

---

### Post by AutoStatic on 2009-12-24
LMMS doesn't work very well with JACK. But it can be tweaked, I have LMMS and JACK work together pretty well.
What are your current JACK settings? Could you post a screenshot of the 'Setup' window of QjackCtl?

---

### Post by alexfish on 2009-12-24
> **AutoStatic said:**
> LMMS doesn't work very well with JACK. But it can be tweaked, I have LMMS and JACK work together pretty well.
What are your current JACK settings? Could you post a screenshot of the 'Setup' window of QjackCtl?

Hi

Have you Set  LMMS to use Pulse (the bad) 

  Try Kill LMMS
   
  Then Restart LMMS

---

### Post by cjmabry25 on 2009-12-24
> **AutoStatic said:**
> LMMS doesn't work very well with JACK. But it can be tweaked, I have LMMS and JACK work together pretty well.
What are your current JACK settings? Could you post a screenshot of the 'Setup' window of QjackCtl?

I haven't messed with any settings because I don't really know what I am doing, but I'm going to do some reading on JACK and sound in Linux today.
[IMG]http://img15.imageshack.us/img15/4843/jacksetup.png[/IMG]

> **alexfish said:**
> Hi

Have you Set  LMMS to use Pulse (the bad) 

  Try Kill LMMS
   
  Then Restart LMMS

I get no sound in Pulse :(
Is there something I should start like I did for JACK?

---

### Post by cjmabry25 on 2009-12-26
Well, since JACK doesn't work well with LMMS, I think I'm just going to learn how to use Rosegarden or Qtractor with Ardour and Hydrogen. 

Thanks for the help.

---

### Post by khopek on 2010-01-07
This may not apply to your exact problem, but I was have an issue with fuzzy sound in 9.10 and you know what fixed it for me?

Go to Sound & Video->Gnome Alsa Mixer

The fourth control in says Front Mic. I muted it and VOILA! No more fuzzy sound! :D

---

### Post by Cajhne on 2012-06-28
I was having similar problems with Ubuntu 12.04 and hearing the popping static when playing notes with my external MIDI keyboard (Yamaha PSR-E333) in LMMS. I found that a reboot, starting JACKd, and switching the "Audio Interface" LMMS > Edit > Settings > Audio settings > Audio Interface from ALSA to JACK (then re-staring LMMS) cured my static problem entirely. It's like magic, in fact. I'm not using a real time (rt) kernel, just the regular 12.04 Ubuntu (64 bit edition).
I looked everywhere for the answer to this, so I'm trying to post this solution in all the places I looked. Hope it helps someone else.

Interesting solution with the mic... have to try that. It could be that Jackd disconnects it automatically when the sound server starts... that would be horrible if it was simply that. lol :)

[Edit]: Turning off the mics (all of them) did nothing for the static sound (for me). However, I did find out that it is not necessary to start JACKd before opening LMMS to fix it. Just setting "Audio Interface" LMMS > Edit > Settings > Audio settings > Audio Interface from ALSA to JACK (then re-staring LMMS), does it fine. Mmmmm cleaaaan. lol

---

