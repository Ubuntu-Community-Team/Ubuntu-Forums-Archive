---
title: "HOW TO: Equalize You Music"
date: 2008-09-26
forum: Tutorials
---

### Post by ENigma885 on 2008-09-26
It's just a mini "How to" to show u how to experience a new equalized taste of ur music. Oriented specially to the 4-only-colors-so-called OS migrants who used to use SRS Audio Sandbox. It can also help _laptop users_ for specific amplification and equalizing.

[[IMG]http://img510.imageshack.us/img510/705/audacioushow2ss6.th.jpg[/IMG]](http://img510.imageshack.us/my.php?image=audacioushow2ss6.jpg)[[IMG]http://img510.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

[SIZE="4"]_What you will need_ :-[/SIZE] 

**1-** *Audacious* (1.5.1 preferred) 
**2-** *Audacious Plugins*, Ubuntu splits them into Plugins and Extra-plugins, (1.5.1 also preferred)
**3-** *LADSPA plugins *

- For the Audacious parts they are available by default in the Intrepid repository and for Hardy users only 1.5.0 is available but u can compile it from source or *_download ready made 1.5.1 debianized packages as follows:*_
**I-** Download and install libaudid3tag1 1.5.1 from [[COLOR="Red"]HERE[/COLOR]]("http://ftp.ubuntu-tw.net/apt/getdeb/ubuntu/hardy/li/libaudid3tag1_1.5.1-1~getdeb1_i386.deb") 
**II-** Download and install libaudclient1 1.5.1 from [[COLOR="Red"]HERE[/COLOR]]("http://ftp1.srv.endpoint.nu/pub/software/getdeb/ubuntu/hardy/li/libaudclient1_1.5.1-1~getdeb1_i386.deb")
**III-** Audacious Plugins 1.5.1 from [[COLOR="Red"]HERE[/COLOR]]("http://getdeb.fastbull.org/ubuntu/hardy/au/audacious-plugins_1.5.1-1~getdeb1_i386.deb") 
**IV-** Audacious 1.5.1 from [[COLOR="Red"]HERE[/COLOR]]("http://ftp.ubuntu-tw.net/apt/getdeb/ubuntu/hardy/au/audacious_1.5.1-1~getdeb1_i386.deb")
**V-** Audacious Plugins Extra 1.5.1 from [[COLOR="Red"]HERE[/COLOR]]("http://ftp.ubuntu-tw.net/apt/getdeb/ubuntu/hardy/au/audacious-plugins-extra_1.5.1-1~getdeb1_i386.deb")

Thanks to GetDeb

- For the LADSPA u can install them by
```
sudo apt-get install swh-plugins ladspa-sdk
```

[SIZE="4"]_Next Step_ :-[/SIZE]

- By now u should have a working Audacious and its plugins installed. 

**1.** ***Configure Audacious to use PulseAudio***
- As Hardy uses PulseAudio as a sound server we have to configure Audacious to use PulseAudio output to avoid conflicts. 
Launch Audacious >> RightClick and Preferences >> Audio from the left menu >> Audio System >> Select PulseAudio Output Plugin.

**2.** ***Audacious Effects Plugins***
- From the same Preferences menu select Plugins from the left menu >> Switch to Effects tab.
- Enable _*Crystalizer*_, not available in 1.5.0, 
- Enable _*Extra Stereo Plugin*_ 
To configure the plugin select it then click Preferences "down"

*_[COLOR="Blue"]Advice I[/COLOR]_* - The values of Crystalizer and Extra Stereo plugin are dependent on ur audio quality (mp3 bitrate for example), the type of music (Metal, Techno, Pop..etc), and ur speakers capabilities. But an average value of ***1.7*** for both of them is just fine.

**3.** ***Configure LADSPA plugins ***
- From the Effects tab in Plugins, enable *_LADSPA Host_*. Select it then Preferences to configure it.
- You will find a huge number of plugins. I tried many of them and the most effective ones and really usable are;
 a- *_C* Eq2x2 - stereo 10-band equalizer_*
 b- *_Stereo Amplifier_*
 c- _*DJ EQ*_
 d-_* Multiband EQ*_
 e- _*Surround Matrix encoder*_
and to get them to work select the plugin name from the left menu (Installed plugins) and click Add "down", it should be copied to the right menu (Running plugins). And for each "running" plugin u can configure also from the Configure button "down". You can run them altogether for best results.

*_[COLOR="Blue"]Advice II[/COLOR]_* - For Stereo Amplifier an average value of 1.2 is pretty good. 
- The DJ EQ plugin offers a simpler and easier way to control over low, mid and high bands presented in other plugins by many separated bands.
- You can try other plugins for fun and then select them from the right menu and click Remove "down" to stop them. examples could be Multivoice Chorus and C* Click - Metronome.

*_[COLOR="Blue"]Advice III[/COLOR]_* - When using equalizer parts remember 
a- Lower Frequency bands (&#8776; 16 - 200 Hz) control bass and low pitched voices. Mainly these voices can be physically felt by other senses than hearing.
b- Higher Frequency bands (&#8776; 8000 Hz = 8 KHz - 16 KHz) control brilliance and high pitched voices.
c- Between the two extremes mid voices lay. Like intelligible human speech (&#8776; 512 - 2048 Hz)
- As we r talking here about digital amplifying, higher equalizer bands values can cause distortion and clipping. so avoid high values completely!
and if u want to increase the level of a certain frequency u'd better decrease other values and raise ur speakers volume if rising that certain frequency causes distortion.
- For additional adjustments u can enable the *_Audacious built-in equalizer_*.

*_[COLOR="Blue"]Advice IV[/COLOR]_* - it's off topic, but u have to check other Audacious plugins from the General plugin tab, not considered with output, ..specifically;
a- *Audacious OSD 0.1beta5*
b- *Global Hotkey*
c- *Status Icon 0.5*

---

### Post by go_beep_yourself on 2008-09-27
I won't ever be using Audacious because it doesn't have as many features as a bigger Music app such as Amarok where I can find my files quickly and easily to make playlists rather than having to open up a file browser looking through different directories, but I do have some questions so that I can learn from this. I'll number them.

[LIST=1]
[*]You said SRS Audio Sandbox is an application for automatically adjusting the sounds for better quality. Why would the default sound settings not already be set for the best quality?
[*]What does the LADSPA do?
[*]What is a crystalizer?
[*]You the settings you create depend on the bitrate of the audio and type of Music, so do you have to change the settings often?
[*]What exactly do equalizers do to change the sound?
[*]Are those sliders on the equalizer what you are referring to when you talk about bands?
[*]Why are Windows users referred to as 4 only colors?
[*]Can you tell me anything I probably don't know about surround sound since I am about to get some surround sound speakers like what the different specs mean and what to look for on speakers?
[*]Do you know anything about choosing about what to look for when choosing a sound card?
[*]Will there be any quality difference in a pci express 1x sound card versues a plain pci sound card?
[/LIST]

:) Told you I can ask a lot of questions.

---

### Post by Artemis3 on 2008-09-27
I have other thoughts... All that stuff is pointless, and things like "stereo amplifier" and "crystalizer" will ruin your music. The less you modify the audio, the better.

Having said that there is a real method to Equalize music, the high tech approach requires calibrated mics which hardly anyone has, the low tech (tuning to specific individual) method is described here: [How to compensate for suboptimal frequency response of your speaker using EQ](http://shibatch.sourceforge.net/eq/index.html).

This method can be applied to all types of EQ, including hardware. What you need to do is generate sine waves (audacity works) of each frequency your EQ has. Be careful with bad resampling, to be safe i recommend you use 48khz (ac97) sampling rates. Then you are going to play the generated tones in succession, the goal here is to have the same perceived volume on each tone, moving the EQ slider as needed. Usually the one near to 1k is the loudest. Make sure you don't clip, some EQs have pre-amp to prevent this.

I think this is called flat EQ calibration, sound engineers do this to their monitors in studio, so they adjust music against this. Monitors shine because they are the most approximate to this, but as each room acoustics is different, the calibration is necessary to compensate small deviations. This is very useful to do with headphones as well.

---

### Post by ENigma885 on 2008-09-27
*_[COLOR="Red"]@ go_beep_yourself[/COLOR]_*

Unfortunately Amarok does not directly support LADSPA ... and i prefer Audacious to Amarok, it's about personal taste and wat u need in ur musicplayer,.

1. SRS Audio Sandbox is a Windows audio enhancement software. I didn't say it "automatically" adjusts. (check the post again).
So ur question is not right in the 1st place. No answer then.
2. I don't have to explain what LADSPA does. It's enough to know that they r sound effects plugins and that Audacious has a plugin to configure them. more info can be obtained from _[here]("http://www.ladspa.org/")_
3. For more info about Audacious plugins visit [http://audacious-media-player.org/index.php?title=Plugins]("http://audacious-media-player.org/index.php?title=Plugins").
4. Not very often. That's y i gave u average values.
5. Search
6. Right
7. May be u have never seen a _[COLOR="Red"][Windows logo ]("http://readerszone.com/wp-content/uploads/2008/04/windows-logo-readerszone.jpg")[/COLOR]_ and it's the OS not the users.
8. No
9. A quick search gave me [http://www.ehow.com/how_8232_buy-sound-card.html]("http://www.ehow.com/how_8232_buy-sound-card.html") and [http://www.cyberwalker.com/article/170]("http://www.cyberwalker.com/article/170")
10. Generally PCI Express slots offer a lager data transfer rate than normal PCI ..so an answer to ur question could be "Yes"
______________________________________

*_[COLOR="Red"]@ Artemis3[/COLOR]_*

> **Artemis3 said:**
> All that stuff is pointless,...Thanks. :)
[QUOTE=K.Mandla]**Criteria for threads in the Tutorials and Tips section** ...
3. Tutorials should be easy to read and follow. [/QUOTE]

And ur previous post is ideally like that.

---

### Post by oldsoundguy on 2008-09-27
> **Artemis3 said:**
> I have other thoughts... All that stuff is pointless, and things like "stereo amplifier" and "crystalizer" will ruin your music. The less you modify the audio, the better.

Having said that there is a real method to Equalize music, the high tech approach requires calibrated mics which hardly anyone has, the low tech (tuning to specific individual) method is described here: [How to compensate for suboptimal frequency response of your speaker using EQ](http://shibatch.sourceforge.net/eq/index.html).

This method can be applied to all types of EQ, including hardware. What you need to do is generate sine waves (audacity works) of each frequency your EQ has. Be careful with bad resampling, to be safe i recommend you use 48khz (ac97) sampling rates. Then you are going to play the generated tones in succession, the goal here is to have the same perceived volume on each tone, moving the EQ slider as needed. Usually the one near to 1k is the loudest. Make sure you don't clip, some EQs have pre-amp to prevent this.

I think this is called flat EQ calibration, sound engineers do this to their monitors in studio, so they adjust music against this. Monitors shine because they are the most approximate to this, but as each room acoustics is different, the calibration is necessary to compensate small deviations. This is very useful to do with headphones as well.

The above is absolutely dead on!

Basically, it boils down to using good stuff FIRST.. Putting up a sound system based on 5 buck speakers you got at Wally's and is a wall wart powered system and then spending hours trying to beat a quality sound out of it is a total exercise in futility.  

Start with good stuff .. then the processing is at a minimum.

A studio engineer friend of mine (with several dozen platinum and double platinum and triple platinum albums to his credit) had this theory of "using the right microphone for the job" instead of spending an inordinate amount of time tweaking at the console. 
Same can be said for setting up your speaker system in your room. An 18" 400 watt sub in an 8 x 12 room is slight OVERKILL!

Amarok (which HAS a small 8 band equalizer) on a good system works quite well without spending hours setting something up.

I can move furniture with mine. And it clean!

(and I DO have a calibrated microphone and a sound generator/sampler)

---

### Post by johnnyxxxcakes on 2008-11-16
Personally, I love to equalize my music. I don't like the plain, empty sound the original music sounds like without any type of equalization.

This toturial has made my setup sound *beautiful*. I currently have a 5.1 Logitech X 540 system, with a Creative T3000 Inspire joined together, while having Y-splitters on each channel to double the amount of speakers all over the room. My opinion is that this sounds just beautiful.

---

### Post by ENigma885 on 2008-11-16
WOW...Am i hearing some support over here?

---

### Post by Enarc on 2009-05-21
Thanks man. Now the sound is really amazing =)

---

### Post by xycris on 2009-05-22
hey ENigma885 great post you have in here and very informative. however, I recently learned about amarok and find it built with more capabilities than audicious. though amarok is built for kde, but, it works quite fine in the gnome environment. cheers! ;)

---

### Post by ENigma885 on 2009-05-28
*@xycris*...

As i wrote above, it all depends on wat u need in ur player. Audacious lacks many features when compared to major music players like KDE's Amarok and GNOME's Rhythmbox.
But neither of them, unfortunately, officially supports LADSPA plugins.

I found an article in Amarok's Wiki describing how to install LADSPA filters in Amarok. Though, it's pretty old, June 2007, and personally i haven't tried it. (u can visit the page [[COLOR="Red"]here[/COLOR]]("http://amarok.kde.org/wiki/Ladspa_HowTo")) 
Obviously, Audacious' way is much pretty simpler than this to control LDSPA.

---

### Post by amits on 2011-09-17
Thanks a lot for the post! I was used to srs audio sandbox in windows. Now music in Ubuntu sounds awesome ;)

---

