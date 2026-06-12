---
title: "Wine doesn't recognise audio and graphics cards"
date: 2009-08-10
forum: Wine
---

### Post by Rrasyrogenees on 2009-08-10
every post i looked at or website i visited does seem to address my need here.  

i downloaded wine a while ago and my system was working fine except maybe a few things that i have learned since.  however, with my excellent noobness i have botched a perfectly good setup and ruined my os and had to reinstall the os.  and my noobness gets better as i tried to do all of the same things i did before but couldn't find the same sites until after i already noob'd another os... reinstalled and tried again... i just wanted to play WoW...

9950 phenom 2.6 ghz black edition quad core
8gb kingston  4x2GB 800MHz DDR2 Non-ECC CL5 (5-5-5-15) DIMM
nvidia 9800gt 180.44 driver
1.1.27 wine version (on my 64bit but not sure now on my 32bit, maybe 1.1.24)
onboard audio on asus m3a78-em

i  first did this on an i386 version on 9.04 and i just tried it on my 64 bit 9.04, both do not recognize my audio or graphics so it put in a default set.  i have not installed WoW on my 64 bit yet but on my 32bit i cannot use my graphics or audio although i can see fine and hear sounds fine on it from the defaults... i still cannot change my resolutions or refresh rate nor can i use my microphone for voice chats in the game.  it seems that i need to find a way to get the registry to recognize these so that wine will give that to my games... can anyone give me what i need to put into registry?

or anything else that i may need to check or do?

---

### Post by Rrasyrogenees on 2009-08-11
well... i did find that my biggest problem is that the driver for the asus is not available... that should say enough... thanx

---

### Post by Rrasyrogenees on 2009-08-14
well... i put my creative x-fi back on and it still gives me problems but not out of the mix.  i am in the registry now and finding a whole lot of fun things to change... i can change my resolutions, refresh rates, and all kinds of things... if i screw it up too much i can always put it back to normal later.   this is too much fun now... i am beginning to be an intermediate noob now... :P:lolflag:

why the registry doesn't recognize my cards is beyond my noobness... but i am learning and having more fun figuring things out because of it too

---

### Post by hikaricore on 2009-08-14
Errr.... WINE isn't responsible for recognizing your hardware... your OS does this.

Have your tried changing the audio between oss/alsa and such in **winecfg**?

If you system sound/video is working then WINE should work without a hitch.

---

