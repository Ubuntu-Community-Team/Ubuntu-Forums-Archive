---
title: "Sound recording"
date: 2007-06-09
forum: System76 Support
---

### Post by godtvisken on 2007-06-09
I just got my system76 laptop and it's so great! I love it. 

But one thing that i've run into: I can't seem to record from the microphone. I've tried in audacity, jokosher, and sound recorder. Maybe i must change something in alsamixer? 

Thanks for the help!

---

### Post by palintheus on 2007-06-09
You might try searching the System76 forums there are several threads about configuring the microphone.

---

### Post by godtvisken on 2007-06-09
I tried messing with the options by double clicking the volume icon on the main toolbar. I unmuted the microphone, but still no luck. I've tried using every device listed to record. The ones list are:

OSS: /dev/dsp
ALSA: HDA Intel: AD 198x Analog (hw: 0,0)
ALSA: front
ALSA: surround40
ALSA: surround51
ALSA: surround71

Another problem in audacity is that no device is listed for playback. There is simply nothing there to select.

---

### Post by godtvisken on 2007-06-10
I meant, I've tried using every device in the drop down menu in audacity for recording devices. 

See attached for screenshots

---

### Post by sgtron on 2007-06-10
You're probably not going to like this reply.. I know I don't.  But what worked for me finally was trying all those different configs people listed in the forums and *gasp* rebooting.  I have no idea why it started working, but after I set the configs, rebooted and logged back in, I was good to go.

---

### Post by godtvisken on 2007-06-10
Alright, i guess i'll keep playing with it. Just to note, i'm trying to record from the built in microphone on the laptop, not one plugged into the port.

---

### Post by tedrampart on 2007-06-10
I was fooling around at work with gazelle performance, trying to record from the built in mic, but couldn't record anything other than this loud static noise (similar to the sound of a tattoo gun, best comparison on noise I could think of).  is this similar to you?  I couldn't get it to work though either.

---

### Post by thomasaaron on 2007-06-11
What recording program are you using?
Sound Recorder is broken.

I usually use GnuSound. But if you try it, make sure you set it to OSS. Otherwise it will crash too.

It sounds like what you are hearing is feedback???

If so, try muting your speakers while you're recording.
This stuff generally turns out to be related to settings.

---

### Post by perce on 2007-06-11
I don't know what laptop you have. I have a Darter, and I've just been able to record with Sound Recorder from the built-in microphone, even if with a lot of background noise. The trick was that Sound Recorder didn't play back the recorded sound, and when I tried to save it, it said it couldn't save it, but when I tried to quit the program it asked me if I wanted to save it and I said yes. Then it created a perfectly working ogg file.

---

### Post by tedrampart on 2007-06-12
I couldn't get my gazelle to record from the built in mic at all.  its either completely silent, or has digital feedback.  tried different programs, tried muting the speakers, tried both oss, and alsa, tried different bitrates, tried selecting all the configurations possible with the alsamixer and oss mixer.. no dice.  it worked like a dream when I plugged a mic into the front, but not the internal mic.

however, I think my situation is just a hardware problem thats plaguing my system (acpi, nvidia, and now the internal mic.. leads me to believe I got a lemon that needs fixin.)  I'll see after I flash the bios..

---

### Post by thomasaaron on 2007-06-12
I've been trying to figure out if you have tried the settings listed in other posts.
Could you check these out and let us know if it helps?

[http://system76.com/forums/viewtopic.php?t=1561&highlight=microphone](http://system76.com/forums/viewtopic.php?t=1561&highlight=microphone)
[http://ubuntuforums.org/showthread.php?t=469597&highlight=system+76+mic](http://ubuntuforums.org/showthread.php?t=469597&highlight=system+76+mic)
[http://ubuntuforums.org/showthread.php?t=467957&highlight=system+76+mic](http://ubuntuforums.org/showthread.php?t=467957&highlight=system+76+mic)

These things are almost always a matter of finding the proper settings. Rarely are they a hardware defect.

Best,
Tom

---

