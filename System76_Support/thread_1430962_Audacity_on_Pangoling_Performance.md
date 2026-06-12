---
title: "Audacity on Pangoling Performance"
date: 2010-03-16
forum: System76 Support
---

### Post by efone on 2010-03-16
Hi guys,

One year ago I got my Pangolin performance and I am very happy with it. Lately I started to play around with music and I installed audacity, everything works fine but I cant record from the sound card. I read a bunch of article about this problem with this chip, but no solution so far. Here is the info:

Card: HDA Intel
Chip: Nvidia ID 3

and "lspci | grep Audio" gives:
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

The problem is that audacity shows only "Mic:0" and "Front Mic:0" and not "wave out" or "Stereo Mix"; this may be a driver problem or codec.
  
Has anybody got audacity recording from streams? 

Thanks in advance.

Efo

---

### Post by miniyak on 2010-03-16
In karmic, under the sound preferences in the hardware tab there is a drop down menu for hardware profiles

test out "analog stereo" duplex thats what im using. I would also try the others if that fails to work

Which pangolin do you have? Which version of ubuntu are you using?

---

### Post by efone on 2010-03-16
Hi miniyak,

Thank you for the reply.
I am not sure how to check the Pangolin version, I bought it 1 year ago, but I can give you all the specs you need.

I installed gentoo, and my rationale is: if that feature in audacity  works with my model/version on ubuntu, then it has to work on gentoo too. It's just that I hit a wall and I cant get it to record streams with audacity, and after I read different posts about the chip used on my Pangolin; I started to think there may not be a way around.

Efo

---

### Post by miniyak on 2010-03-17
The model should be labeled at the bottom of your laptop. Should be either a pangolin 4 (n or i) or a pangolin 5 if you bought with in the last year. 

sorry, i was getting back to you yesterday.... halve-way through was  distracted then my panp5 crashed in stand-by (happens only once in a while) almost forgot about this thread..

I would try the karmic live cd (you will be able to install audacity in the live environment).  This way you can see if gentoo needs to be tweaked vs. this being a hardware issue. All i know about gentoo is that it is very customizable. May be I'll try it out sometime.

---

### Post by efone on 2010-03-17
Hi miniyak,

No problem, during the week I get caught up with work and I am not too efficient towards fixing my box.

Bottom you said... let me check... panp4n, I had it for a year and I didnt know about that :o) I think the new model came out as I received this one :o(

I will try keramic live cd then and see if it works. 

I am pleased with gentoo, you get to learn a bunch of stuff and you can really make it exactly like you want it. The problem is that sometimes there is some head-banging activities going on (part of the learning process), but when everything is set up it is beautiful!

---

### Post by isantop on 2010-03-19
Also note that going to System > Administration > System76 Driver Will also tell you what model computer you have, in case you don't want to flip over the laptop or the label has worn down.

---

### Post by miniyak on 2010-03-19
> **isantop said:**
> Also note that going to System > Administration > System76 Driver Will also tell you what model computer you have, in case you don't want to flip over the laptop or the label has worn down.

Right, and if one is using a different distro, remember that the driver can be installed with in the ubuntu live cd. In case the label has been somehow rendered illegible.

---

### Post by efone on 2010-03-21
I found it!
I think the problem was in the setting of my kernel (build in driver).
I followed the wiki suggestion and it worked: [http://en.gentoo-wiki.com/wiki/ALSA](http://en.gentoo-wiki.com/wiki/ALSA)
I think (not 100% sure) that what made the difference was

Device Drivers --->
Character devices --->
<*> Enhanced Real Time Clock Support
...
<*> RTC Timer support

[*] Use RTC as default sequencer timer

Thanks for the help and suggestions.

Efo

---

### Post by efone on 2010-03-23
Hi again miniyak and isantop,

I have a quick question: is it possible to disable the front microphone on my panp4n?
If I mute the front mike from alsamixer, only its way to the speakers is muted; however, the front mike is still captured. Just wanted to know if this is a hardware limitation or if it can be fixed with the software.

Thanks a bunch.

Efo

---

### Post by isantop on 2010-03-23
> **efone said:**
> Hi again miniyak and isantop,

I have a quick question: is it possible to disable the front microphone on my panp4n?
If I mute the front mike from alsamixer, only its way to the speakers is muted; however, the front mike is still captured. Just wanted to know if this is a hardware limitation or if it can be fixed with the software.

Thanks a bunch.

Efo

I'm not exactly sure, but it sounds like you're trying to mute the mic just above the touchpad. I'm not sure which Pangolin you have, but I'm guessing that it's either a panp5 or panp6. 

Unfortunately, my Pangolin is a panp7, so I'm not sure if this will be entirely relevant to you. However, if I right-click on the volume icon in the top panel, then click "Sound Preferences", then go to the "Input" tab, I can select between two mics, I think one for the built-in one and one for the external port. For me, mic1 is the external one, so selecting it mutes the built-in one.

You may need to reverse the order for your specific model, but this should get you working. If you need any more help, feel free to ask. :)

---

### Post by Derath on 2010-03-23
I believe if you lower the volume control AND hit mute, it should take care of it (while I am looking at both KMix and alsa) and making sure the "input source" is mic, not front mic.

---

### Post by efone on 2010-03-23
Hi Derath,

Thank you for the suggestion. The problem is that after I fixed the driver in the kernel the input source disappeared from audacity...

---

