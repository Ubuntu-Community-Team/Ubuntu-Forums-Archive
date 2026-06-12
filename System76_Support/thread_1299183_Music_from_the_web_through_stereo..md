---
title: "Music from the web through stereo."
date: 2009-10-23
forum: System76 Support
---

### Post by MarkID on 2009-10-23
OK.  I have my Starling hooked up to a DAC and the DAC to my stereo.  I have Ubuntu recognizing the DAC. :)  Downloaded and ripped music plays through the stereo.  Sounds great. Boogie city :guitar: But web-based music, like Pandora and other services does not play through the stereo, using Firefox. :mad:  I get sound only through the laptop's speakers.  What's up?  How do I make this work? :confused:  (BTW, same is true for my Daru1.)

---

### Post by MarkID on 2009-10-25
Can no one help me play steaming music?

---

### Post by Derath on 2009-10-25
Okay, well, depending on how you have everything hooked up (and assuming DAC is referring to something like a SanDisk/Zune/iPod, etc) I would actually say by-pass that altogether. At home I have a stereo receiver, and I have used a 1/16th" headphone jack to stereo RCA adapter (iirc it's about 6' long) and hook my laptop's headphone jack up to the TV or Receiver that way. basically just eliminate the middleman...

---

### Post by Derath on 2009-10-25
Also note: You may have the sound system designed to use the DAC, but you may have to configure mplayer to use those same options... (i.e. if you're using pulse and pulse setup to use DAC, but mplayer is using alsa or something)

---

### Post by MarkID on 2009-10-26
A DAC is a Digital-Analog Converter.  It converts a digital signal into a usable analog signal.  Every CD player has one built in.  So does an IPod and every other MP3 player.  The point of using an outboard DAC is that the DAC in most (every?) desktop and laptop (and the IPod, for that matter) is not of sufficient audio quality for hi-end audio.  But the same digital stream can be run through a good DAC and converted into good audio.  Indeed, MP3 itself is a fairly lo-fi, lossy, standard, adequate for earbuds, but not much else.  But it is possible to download lossless files, like CD quality FLAC files, or even higher resolution (96khz FLAC) files from many online sources.  Also, CDs ripped to a hardrive are often higher quality than MP3.  In my case, ripped files and downlaoded files stored on a harddrive play perfectly through Rhythmbox through the outboard DAC through the stereo.  Streaming audio, like Pandora, plays through the laptop's speakers.  I have to configure something, somehow so the audio streams through the USB port (to which the DAC is connected) and not through the laptop's speakers.

---

### Post by jmwink on 2009-10-26
What about streaming audio through a program like VLC? Does it also only play through the speakers? Or is this problem unique to web-based streaming services like Pandora?

Also, for my own curiosity, what DAC are you using?

---

### Post by MarkID on 2009-10-26
> **jmwink said:**
> What about streaming audio through a program like VLC? Does it also only play through the speakers? Or is this problem unique to web-based streaming services like Pandora?

Also, for my own curiosity, what DAC are you using?

It seems to be web-based streaming.  If the file "originates" in the computer, it seems to work.

I'm currently using the HRT Musicstreamer, which I bought to experiment with the set up before spending more money on a better DAC.  I have a pretty sweet Naim set-up (282/200/SBL with lots of 'Caps) and will probably end up with the new Naim DAC, once I get everything working and get to home audition the Naim DAC.  But the HRT Musicstreamer is one heckuva DAC, and for the price nothing can touch it.  You can easily spend more, and get less.  Highly recommended.

Now, to solve my problem . . . .:confused:

---

### Post by jmwink on 2009-10-27
It's a strange problem that I've never heard of before. So, YouTube videos and stuff, their sound all only comes out through the laptop speakers, too, huh?

---

### Post by MarkID on 2009-10-27
> **jmwink said:**
> It's a strange problem that I've never heard of before. So, YouTube videos and stuff, their sound all only comes out through the laptop speakers, too, huh?

I didn't try YouTube.  But Pandora and some streaming radio stations play from the laptop and not the stereo.

I wonder, do I need to change the plugin configuartions for all the music related plugins in Firefox from VLC to something else (gxine?)  If so, is it all of the plugins?  If not, which ones?

---

