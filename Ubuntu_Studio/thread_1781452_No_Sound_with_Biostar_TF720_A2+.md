---
title: "No Sound with Biostar TF720 A2+"
date: 2011-06-13
forum: Ubuntu Studio
---

### Post by ERRRIMMAD on 2011-06-13
I want to pull my $%^#^% hair out, I have been using computers for a long time now, my first CPU was a VIC 20 with an analog tape deck, so I'm not a noob.

I have searched every where and tried everything I have found in response to this issue, no sound with TF720 A2+ mother board.

I have three sound cards, and one on board sound card, I disabled the on board sound card.

My other sound cards are, Sound Blasters Audigy 2zs and live, plus a delta 1010 lt.

Have tried terminal options, pulse, gnome mixer, on down the list.

What the $^% can I do to figure out what the problem is, I want to pull all my &^$*%$ hair out at this point.

I can provide answers to any question asked, and the problem is no sound at all, zero, not even to boot up sound.

Please help with some guidance, I have been using Ubuntu exclusively for one year now, I hate windows and OSX and want nothing to do with them, please if you can help me get audio I would greatly appreciate it, plus you'll save me from going bald. LOL

---

### Post by Flaggmann on 2011-06-13
You might want to read my response to besserdark's post re ardor & aeoleus.

I am not sure what setup you use, wrt jack, alsa and pulse audio but depending on what you have, you may want to read tutorials and project web site info on alsa, jack when used with pulseaudio.

there was a problem I ran across that was corrected by making a few changes to a couple of files like  asound.conf  etc. asound.conf is master file affecting all users, whereas there is a hidden one in the home directories as well. So if you don't see the main one check for hidden files and folders in the home directories.

What I found with multi cards, is the default system grabs one card for system notification sounds, and then you have to configure the other cards so that jack and alsa can make use of them. When you first start up the box the hardware resources of snd card 0 get grabbed and if you are set up to operate using the other cards with your apps, they may not work because alsa isn't aware they exist.

pulseaudio, alsa and jack all have to be aware of what you want as a setup. initially jack audio connection kit would see only one card; recently there have been comments if forums that jack-net and other improvements will allow multiple instances of jack to run so that multiple sound cards can be used as you have. 

If the system grabs the SB for system sounds and you have jack set for the 1010, then unless you have the system configured for the multi instance setup of jack and selected the TF720 in the 2nd instance, TF720 will appear u/s.

I presume, but am not personally experienced at it, one should be able to allow the on board snd card to operate the system sounds and notifications, and then run three instances of jack to use the other three sound cards simultaneously, as long as the box hase the cpu and memory horsepower. Can't say I made it work though.

You should be able to use two cards independently as realtime outputs, and use the third card as a CUE monitor as an example. If you use jack, you should also see Darksnow, Darkice, and icecast/icecast2 streaming servers as well all working simultaneously, although the icecast server should be on a different box to avoid have to share CPU and memory resources for that. but darkice/darksnow combination should show up in jack connection panel so you can patch whatever jack-aware source application's output you want to the streaming server.

Hope this is some help to you.

---

### Post by ERRRIMMAD on 2011-06-13
Thanks, any help offered is appreciated, even if my question is misunderstood, you did not misunderstand me by the way, but the effort from anyone trying to help is appreciated. =D

I'll look into your suggestions.

---

### Post by jejeman on 2011-06-13
You didnt say what you want to setup. Which card you want to use and for what.

---

### Post by Pablo_F on 2011-06-13
There is this [alsa-info.sh script]("http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh") which was written for 2 main reasons:

> 1. Remove the need for the devs/helpers to ask several questions before we can easily help the user.
2. Allow newer/inexperienced ALSA users to give us all the info we need to help them.

You can copy it to a text file and rename the file as "alsa-info.sh". Then run it from a terminal with *bash alsa-info.sh*, upload the result and give the URL. 

And also do what jejeman suggested.

Note that, when using multiple cards, their numbers tend to change in different reboots. This is a PITA because it confuses the sound serves. It can be solved by editing an alsa configuration file, /etc/modprobe.d/alsa-base.conf

---

### Post by ERRRIMMAD on 2011-06-13
Alright, here is the information requested.

As for the other request about what I want to do with my sound cards, all in good time, let's just get one card working first. XD

[http://www.alsa-project.org/db/?f=337df0f01083cb7f654edecc34498164b358fbc3](http://www.alsa-project.org/db/?f=337df0f01083cb7f654edecc34498164b358fbc3)

---

### Post by jejeman on 2011-06-14
> let's just get one card working first. XD
Which one for what?
To work for system sounds, playing music, etc. I'm talking about pulseaudio, alsa.

---

### Post by ERRRIMMAD on 2011-06-14
I like the Sound Blaster Audigy 2zs best over all, recording is best on this card, the 2zs also has some alright Midi tone banks.

The Sound Blaster live is good for Midi tone banks only.

And the Delta 1010lt, I guess would be best for playback as it has 8 analog outputs, so I imagine system sound could be set to the 1010 as well, also the 1010  has a great midi input interface.

---

### Post by ERRRIMMAD on 2011-06-14
Oh, sorry< misunderstood you a bit.

I don't know why Ubuntu Studio has Alsa and Pulse competing for dominance over my sound cards, from what I understand G streamer is causing the the conflict between these apps, seems people say version 9 worked, then they made this switch and everyone started to have problems, same with grub when Ubuntu changed from 9 to 10.

In short, I want to just get my sound blaster Audigy to work, then I can figure out why it works and apply the same principles to the rest of my audio cards, was this a bit more clear? =)

---

### Post by jejeman on 2011-06-14
I saw that you have 3 sound cards:
> 01:06.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
01:08.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
01:09.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)

Do you really need all of them? I think that you should at least  pull out SB Live! card. You can copy its soundfonts bank and use it without the card.

If you want to use Audigy for recording, you can easily tell Jack to use that card.

M-audio is 0 card, so it should be the default card. All sounds should come out of it right now.

---

### Post by Pablo_F on 2011-06-14
Hi, 

I recommend giving the cards consistent numbers in the alsa-base configuration file. This file is /etc/modprobe.d/alsa-base.conf

See [http://alsa.opensrc.org/MultipleCards](http://alsa.opensrc.org/MultipleCards)

Most apps don't use alsa directly but the random reordering can confuse the sound servers (pulseaudio and jack).

Once you make sure that the order is the same in different reboots (check with *cat /proc/asound/cards*), use sound preferences (a pulseaudio frontend) to select the default card. 

If you use jack, you have to select the card, normally in the interface field.

---

### Post by Pablo_F on 2011-06-14
> I saw that you have 3 sound cards:

He has 4. Three PCI and a USB one. 

cat /proc/asound/cards:

```
 0 [M1010LT        ]: ICE1712 - M Audio Delta 1010LT
                      M Audio Delta 1010LT at 0xc480, irq 18
 1 [Interface      ]: USB-Audio - EV-10 USB MIDI Interface
                      Evolution Electronics Ltd. EV-10 USB MIDI Interface at usb-0000:00:04.0-1, full
 2 [Audigy2        ]: Audigy2 - SB Audigy 2 [Unknown]
                      SB Audigy 2 [Unknown] (rev.4, serial:0x20041102) at 0xcc00, irq 17
 3 [Live           ]: EMU10K1 - SB Live! Value [CT4871]
                      SB Live! Value [CT4871] (rev.8, serial:0x80321102) at 0xc880, irq 16
```

---

### Post by jejeman on 2011-06-14
The usb one is just a midi interface, it does not have sound playback/record capabilites.

---

### Post by Flaggmann on 2011-06-14
This may be of some help



When using more than one **soundcard and Alsa**… the sound cards sometimes swap around so sometimes one card is card 1 and the next time it is sound card 0. 
If you edit the alsa-base file **/etc/modprobe.d/alsa-base** by adding options to hard code which sound card is which. For example…. 
options snd-emu10k1 index=0 
options snd-hda-intel index=1 
options snd-bt87x index=2 

type the below line to find out the exact driver name for each sound card 
cat /proc/asound/modules 
and the resulting readout will tell you what your sound cards are... (except change the underscore to a hyphen) 
 0 snd_intel8x0 1 snd_emu10k1x

---

### Post by ERRRIMMAD on 2011-06-15
LOL, so it turns out sound is coming out of the Sound Blaster Live.

LOL, Don't want that. XD

I love the Idea of ripping the sound banks to sound fonts, which program might I ask will do this. =D

The ideal setup  will be with Just the Delta 1010 lt, as I actually do my analog recording outboard on a workstation.

The Delta 1010 is in this case desired for its MIDI input, I use lot's of strange MIDI devices and the Delta 1010 lt does MIDI interfacing well.

---

### Post by jejeman on 2011-06-15
Soundfont bank is on cd wich came with the card. It's not in the hardware, at least that is the case with my Audigy card. I don't see why Live! would be any different.
If you want to use just Delta 1010, the easiest (and best) way is to pull out the other cards. No need for them to waste power ;)

---

### Post by ERRRIMMAD on 2011-06-15
ERRR I'm Happy! XD

Yeah, pulled the other two, in this situation I want to simplify Ubuntu Studio from playing shuffle the sound cards. =D 

Got sound from he Delta 1010, Goofy card it is, it's audio out is great, but as I mentioned the MIDI interface is the treasure on this card. XD

If I may ask one more ridiculous question before we consider my mindless rant solved and leave this thread behind for other TF720 A2+ owners to find, where can I get to the Jacked interface, I figure it must be terminal driven as I can't find it in my GUI.

---

### Post by jejeman on 2011-06-15
If you instaled jack you should also have JACK Control, if not then install qjackctl.
Of course you can run jack straight from terminal. Jack it self does not have GUI.

---

### Post by Pablo_F on 2011-06-15
Also, to access the DCA levels, internal mixer, etc. for your m-audio 1010LT you need a program called *envy24control*. *envy24control* is installed by a software package called *alsa-tools-gui*.

---

