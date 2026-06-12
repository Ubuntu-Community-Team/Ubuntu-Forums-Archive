---
title: "Line-In Play through in 9.10"
date: 2009-11-07
forum: Ubuntu Studio
---

### Post by lexen on 2009-11-07
Hello everyone.  I love the new ubuntu and I think if far surpasses everything that came before it, but like always, I am having some trouble getting it to work the way I like after the upgrade.

   I record a lot of audio with my band and we have a mixboard hooked up to the line-in spot on the computer.  The way it should work is that when you are recording you can hear the track that is playing on the computer and you can also hear the track that you are recording because it is in the line in spot via line-in play through.  But the new volume control program does not have that option (or many of the other options I used to use), so I was wondering how I can get that to work.  I would like to get this volume control to work, but I wouldn't mind just installing the old one if anyone knows the package name.


Thanks,
Lexen

---

### Post by sgx on 2009-11-07
gmixer
gnome-alsamixer
alsamixergui
kmix
envy24control (For m-audio/envy24 chip soundcards)
xfce4-mixer (for the xfce4 winowdow manager environ)
aumix

probably many others

---

### Post by Astrals on 2009-12-07
I tried this with no success.

The input level meter shows there is an audio signal coming through but no audio to be heard, this situation is for a xbox360 console.
I turned on the line in through alsamixer and this made no difference at all.
I'm using 5.1 surround straight from my motherboard **(ASUS M4A78 PRO)** with stereo input.
The audio works above expected for everything else but not for line in play through.
I'm using **ubuntu-9.10-alternate-amd64**

Any help with this will be greatly appreciated, thank you.

---

### Post by lexen on 2009-12-07
Which program are you using?  I am using gnome-alsamixer and I have had success on two computers, but I could not getting it working on another.  If you are using gnome-alsamixer, you might have to mess with capture volume and obviously the Line volume.  On the computer that we could not get it to work with, there was on option that was simular to "analog in" or something like that.  It's a friends computer so I can't remember the exact name, but it was a check box in the bottom left hand corner.  

   gnome-alsamixer has different options depending on what audio card you are using, so some of the options that I utilized, may not be on your screen.  It would help if you could start up gnome-alsamixer and give us a screen shot.


   I hope some of that helped.


Later,
Lexen

---

### Post by Astrals on 2009-12-07
[IMG]http://i50.tinypic.com/qzhylk.jpg[/IMG]Here is my alsamixer screenshot.
[IMG]http://i50.tinypic.com/qzhylk.jpg[/IMG][http://i50.tinypic.com/qzhylk.jpg](http://i50.tinypic.com/qzhylk.jpg)

Thanks for any help with this.

---

### Post by lexen on 2009-12-08
wow, I don't know.  I don't see anything that seems out of place.  You should try gnome-alsamixer.  It might not help you out, but I am a lot better with that program.  It will also give you some option that alsamixer won't, so that could help things.

---

### Post by Astrals on 2009-12-08
Tried gnome-alsamixer which leaves no sound as well.
If i use the "sound recorder" it recordds the sound for playback perfectly, so i know the sound coming in is no problem and the system records it perfectly but play through for something so simple has me stumped.

---

### Post by lexen on 2009-12-09
Hmm... well I am stumped.  You could try to hook it up to the mic and get a software play through.  I know that Audacity can do that, though it would be a hassle having Audacity open all the time.

---

### Post by DerickX on 2009-12-09
why not use Ardour for recording? That is a DAW, Audacity is essentially a audio file editor...

With JACK you don't have troubles with pulseaudio (if it suspends pulseaudio).


This is a good starting point: [http://en.flossmanuals.net/Ardour/Introduction](http://en.flossmanuals.net/Ardour/Introduction)

See also: [http://www.openstudioproductions.org/ardour](http://www.openstudioproductions.org/ardour)

If you want to do quick recording, other useful tools might be:

mhWaveEdit
qtractor
rezound

But I recommend to learn Ardour.

---

### Post by Astrals on 2009-12-11
Trying ardour with jack, so far no luck with it. For me there is way too many options fo this simple task of line in play back in real time. I'm not used to playing with apps of this nature and i don't have the time to spend months learning an app for a simple audio issue.

Your input is very much appreciated in this matter, what i need is a simple solution for this. 

Thank you.

---

### Post by madeinfamous on 2009-12-11
allo Astrals,

in your pics, these are the "Playback" setting,

you need to press "TAB" to go in "Capture" and enable your line-in,

hope this help,

have a nice weekend,

---

### Post by lexen on 2009-12-11
The simplest solution would be to go back to 9.04.  After every release, I seriously consider going back a release because of the new problems you get with every release.  In this release, for me, the good outweighed the bad.  It sounds like your situation is different then mine.

---

### Post by Astrals on 2009-12-16
Here is my findings.

Computer 1 motherboard **ASUS M4A78 PRO** with onboard 5.1 audio, did not allow for sound play through at all, sound is setup for line in and alsamixer is set correctly.

Computer 2 motherboard **ASUS M2A-VM** with stereo input, line in play through works great, with same line-in and alsamixer setup, no problem.

From what i can work out it comes down to a lack of hardware support for this motherboard, if this is not the case please do let me know how to fix this issue.

I hope this helps. Thank you for all your help so far with this issue, i would really like to find a solution for this for computer 1.

---

### Post by AutoStatic on 2009-12-16
> **Astrals said:**
> [IMG]http://i50.tinypic.com/qzhylk.jpg[/IMG]Here is my alsamixer screenshot.
[IMG]http://i50.tinypic.com/qzhylk.jpg[/IMG][http://i50.tinypic.com/qzhylk.jpg](http://i50.tinypic.com/qzhylk.jpg)

Thanks for any help with this.Both Front Mic and Mic inputs are muted. You can unmute them by selecting them and pressing 'm'. You will then see the 'MM' indication disappear.

---

### Post by Astrals on 2009-12-16
I have tried the variations for the mics as well, made no difference, plus i don't need the use of the mic inputs, well not yet anyway.

Thanks for the advice anyway, this really does seam to be an issue with this motherboard, the only other thing i can derive this to is maybe the issue is going from a stereo port to a 5.1 output. I don't really know but it's what i have put it down to.

---

### Post by AutoStatic on 2009-12-17
Ah, my bad, I didn't read carefully enough, could you post a screenshot of the capture settings? The screenshot you posted only contains the playback settings.

---

### Post by Astrals on 2009-12-17
[IMG]http://i50.tinypic.com/16axk4y.jpg[/IMG]

These capture settings are the same in use on the other motherboard that allows for play through to work, also i have tried all the variations for these.
Thank you for your help with this.

---

### Post by jack.herbert on 2009-12-30
Hellodiyo!

I had the exactly the same problem with ardour since the upgrade: I couldn't hear what was being recorded (fine for an acoustic guitar or vocal track, but most annoying for synths)
For days I was moody, snapping at people for no good reason, considering going back to the older version, swearing at Pulse Audio (even tho I don't think it's to blame), when suddenly...
an epiphany!
Open JACK Control, click on "connect", form the left side system->capture1&2 make links to the right side ardour->master1&2
So easy.
Now I feel like a bloody genius!

---

### Post by Astrals on 2010-01-08
In jack control it only offers me my system default for midi.

But I did find a solution for this.
I installed **"JAMin"**
Set the input ports to system and the same for output ports, then it was only a matter of tweaking the audio settings to get good sound.
Had to adjust alsamixer line input sesitivity and JAMin's.
The sound is not perfect but now I don't have to muck around swapping leads for computer or xbox.

So thank you for your inspiration on jackaudio to lead me to this successful outcome.

The real problem from the start is onboard 5.1 instead of using a sound card. If i'm patient enough the support in linux will grow enough to fix these small issues.

Thank you to everybody for your help with this.

If anybody in the future has a better way of fixing this sound issue please send me a pm or post it here.

This is one of the reasons i love this forum, we all try to help each other.

---

