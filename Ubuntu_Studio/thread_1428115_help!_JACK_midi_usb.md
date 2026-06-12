---
title: "help! JACK? midi? usb?"
date: 2010-03-12
forum: Ubuntu Studio
---

### Post by Beowulf.1000 on 2010-03-12
I don't have Ubuntu Studio, but I figure those here are into art and more importantly music which is what I need help on! The whole **JACK** and Alsa and midi completely confuses me. I want to be able to play my Oxygen 8 midi keyboard and hear it in programs like Ardour and Rosegarden, and record to those programs. But the whole JACK thing is most confusing.

Any help on this appreciated. And importantly, I am willing to shell out the $$$ if needed and buy an **external midi/usb box** if needed to simplify this-- I have heard that that negates a log of the real-time low latency issues. So should I buy an external midi/usb box to plug my midi keyboard into to then route to my PC, rather than using my existing sound card (Soundblaster Titanium XFi)?

I have a nice Ubuntu 9.10 Karmic Koala 64 bit system set up, including a virtualized Windows XP using virtualbox. Nvidia graphics running nice, audio okay for listening to music, Compiz desktop effects. I even has **Sibelus 6** with Sibelius Sounds (Garritan samples) running in my virtualized Windows XP.

If I can just get midi working I will be rocking. Any tips greatly appreciated.

---

### Post by Capoeira on 2010-03-12
the keyboard is USB? than it should show up in the alsa-tab of qjackctl. there you connect it to an instrument (synth, sampler, whatever), and than the output of the instrument to Ardour or Rosegarden.

---

### Post by trulan on 2010-03-12
You shouldn't need a separate USB - midi adapter, you should be able to plug your keyboard directly into a USB port and use it that way.  I highly doubt latency will be an issue.

Jack is a sound server - the coolest thing ever - but I know it's confusing at first.  Basically what it does is connect your hardware to your programs and your programs to each other.

So you need to have Jack up and running, then you can start Ardour or Rosegarden.  Ardour is an excellent with audio, but it doesn't really handle midi yet, that is coming in version 3.  And I find Rosegarden - at least the version in Karmic - very confusing.  For recording Midi, currently, I like to use Qtractor.

Here's how I do it:
1. Jack Control running (To start and control Jack)
1. Jack running (to hook everything together)
2. Qsynth running, with the GM soundfont loaded (to actually generate the sounds)
3. Qtractor running (to record and play back midi, it can also do audio)
4. Then make the Jack connections - you can use Jack Control's connect window)

So, using Jack Control's connect window, under the 'Alsa' tab, I connect my midi keyboard to Qsynth (it calls it Fluidsynth), and when I play my keyboard it makes sound.  Or, I connect my midi keyboard to the midi input in Qtractor and connect the midi output of Qtractor to the midi input of Qsynth.  In both those cases, the audio output of Qsynth needs to be connected to my soundcard, (that's in the first tab of the connect window) but it should do that automatically.

Remember, all those connections are virtual, and they are handled by Jack.  You can connect anything to just about anything else, adding effects, recording from whatever point in the audio chain you want, pulling the sound from anywhere to send it to your speakers, just as if you had a whole room full of audio equipment and a whole mess of patch cables.

Are you confused yet?  Sorry...It's actually very intuitive once you get to using it, and it's incredibly flexible and useful.

Maybe an easier way to get sound from your midi keyboard would be to use ZynAddSubFX instead of Qsynth to generate the sound, then you don't need to mess with loading a soundfont.  Just connect your midi keyboard to Zyn and hear the music you're playing.

---

### Post by Beowulf.1000 on 2010-03-13
Thank you all, I am going to give it a try, albeit slowly and progressively, it is all so confusing especially given it is all virtual cables to and fro inside the linux system. I need to learn about JACK because right now I do not know jack-sh&^.

I did order a midi box to route my usb keyboard (Oxygen 8) into, then route that box to the pc through a usb cable. I have heard that eliminates latency and soundcard issues. But I will try it both ways.

I will likely be back here for more questions as I learn and explore this jack thing and the other apps. I was able to get sound from my midi kbd into Sibelius 6 running in virtualized WinXP on virtualbox, but the audio has horrible issues, not usable, something is amiss trying it that way. I want to get it all working in native linux.

My brain is about to explode though because this past week I have done so many installs and reinstalls of linux on my desktop and laptop to get the right setup, and also installed virtualbox and vmware and virtualized linux and Windows. My brain needs to a bit slow now as I tackle learning JACK and midi and recording apps in linux.

Thank you all, and keep an eye out for me here!
:) Beowulf

---

### Post by madeinfamous on 2010-03-13
allo Beowulf.1000,

just go listen to this tutorials, (Music Editing/Creation)

he will show you how to run and connect everything :)

[URL="http://www.filmsbykris.com/"]http://www.filmsbykris.com/
[/URL]

and go browse his youtube channel, he cover a lot of music editing software

[URL="http://www.youtube.com/user/metalx1000"]http://www.youtube.com/user/metalx1000
[/URL]

---

### Post by AutoStatic on 2010-03-15
> **madeinfamous said:**
> allo Beowulf.1000,

just go listen to this tutorials, (Music Editing/Creation)

he will show you how to run and connect everything :)

[URL="http://www.filmsbykris.com/"]http://www.filmsbykris.com/
[/URL]

and go browse his youtube channel, he cover a lot of music editing software

[URL="http://www.youtube.com/user/metalx1000"]http://www.youtube.com/user/metalx1000
[/URL]I've scrolled through the extensive list of uploads but couldn't find any specific tutorial. To which tutorials are you referring?

@Beowulf.1000, what kind of MIDI box are you referring to? If it's USB then it doesn't make any difference at all when it comes to latency compared to an ordinary USB MIDI keyboard as far as I know.

I'll put up a YouTube ultraquick MIDI tutorial on [my YouTube channel]("http://www.youtube.com/user/autostatic3000") later on today along the lines of trulan's post because our workflows are very similar. I prefer Qtractor also for MIDI, I've never had the urge yet to take a look at Rosegarden for MIDI or Ardour for recording.

---

### Post by AutoStatic on 2010-03-17
[Tiny Tutorial: Connecting a MIDI USB Keyboard to a Softsynth in Ubuntu]("http://www.youtube.com/watch?v=kBEzMC35gt8")

---

