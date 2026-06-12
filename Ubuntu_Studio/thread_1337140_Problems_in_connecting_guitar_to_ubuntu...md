---
title: "Problems in connecting guitar to ubuntu.."
date: 2009-11-25
forum: Ubuntu Studio
---

### Post by Guitar-maniac on 2009-11-25
I connected my guitar to my ubuntu 9.10 but no sound/it didn't regognize it.
I'm ubuntu noob still so what have i not noticed? I'd have to record stuff and it's pretty urgent.

I have the right adapters, i plugged it in the right hole to my soundcard (it worked perfectly when i was still runnin Windows)

I tried to look at the setting => sounds but there was no sign of any external device.

Thanks in advance for the help :)

---

### Post by kayosiii on 2009-11-25
What type of soundcard do you have and what sort port /hardware are you using to connect... (are you using the microphone port, the line in port or something else?)...
What software are you trying to connect to your guitar software wise?
How far down the rabbit hole do you want to go anyway?

---

### Post by drangu on 2009-12-14
same problem here,i am new to ubuntu also.since i upgraded to latest version there is no sound when i connect my guitar.i noticed that in audacity i can record sounds,but i cant hear my guitar when i record ,i can only playback what i have recorded.
thanks.

---

### Post by FLMKane on 2009-12-23
Same problem here. Please help.

---

### Post by nick_geetar on 2009-12-26
Did you guys go to /system/pref/sounds hit play on all of them and verify they are all functioning. Try selecting default for the ones you can. Pulse Audio is what i have all of mine set on. I use audacity also.

---

### Post by cjmabry25 on 2009-12-26
> **drangu said:**
> same problem here,i am new to ubuntu also.since i upgraded to latest version there is no sound when i connect my guitar.i noticed that in audacity i can record sounds,but i cant hear my guitar when i record ,i can only playback what i have recorded.
thanks.

You have to set software playback in Audacity. When you plug your guitar in your not just going to hear it, you'll have to have a program to output the sound of your guitar. 

If you want to hear what you record as you record it though, go to (in Audacity) Edit > Preferences > Recording and check "Software Playthrough." However, this could have a delay from when you play to when the sound outputs. Depends on your hardware.

If you want to just hear your guitar through your computer, I think Creox c will do the job, and you can add efects. I haven't been able to try this though.

---

### Post by nick_geetar on 2009-12-27
Creox will play playback. It's kind of a basic program. But overall it's alright. I recommend rakarrack.:guitar:

---

### Post by transmogrifox on 2009-12-28
You need to be able to get guitar going through your system dry before trying to use stuff like Creox and Rakarrack or anything else.  This sounds like a really simple deal.  Have you opened the sound mixer from your task bar and tried turning up the volume or unmute channels like Line in and things?  Often Line and Mic inputs are muted by default because you would otherwise take a chance of hearing static all the time.  

If you can record in Audacity, then the sound card driver is working fine...it's just a matter of getting the settings on your mixer right.

On mine with an SB Audigy (this is about a 4-year old computer) it has a Digital/Analog switch output check button on the sound mixer.  This needs to be checked for me.  Either way, the point is to open the mixer and play with things until it works.  It will start to make sense after a little bit.

Just a few ideas...Then when you get that part figured out you can start messing with things like Creox or Rakarrack.

BTW, Rakarrack will be default packaged with Lucid Lynx...just a flash for those who don't watch the Ubuntu dev lists (which is probably not many who aren't devs).

---

### Post by bluesscream on 2010-01-01
if you're seriously interested in software guitar effects give guitarix a try [HTML]http://sourceforge.net/projects/guitarix/[/HTML] it's not as hard as you might think to compile a deb yourself...

---

