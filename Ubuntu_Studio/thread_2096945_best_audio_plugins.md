---
title: "best audio plugins"
date: 2012-12-21
forum: Ubuntu Studio
---

### Post by mmetelko on 2012-12-21
hello! I'm looking  for the best audio instrument  plugins for use with Ardour or lmms.
Please tell me your preferences..

---

### Post by CrocoDuck on 2012-12-21
Hi. I am a fanatic of any LADSPA and LV2 plugin that actually exists, but CALF plugins ([http://calf.sourceforge.net/](http://calf.sourceforge.net/)) are my favourite ones. Here you can find DISTRHO plugins, I think they are really interesting: [http://distrho.sourceforge.net/](http://distrho.sourceforge.net/) . Here some plugin that are very cool, but I experienced some difficult trying to run them under ubuntu 12.04 (they are out of the box with 10.04) [http://code.google.com/p/juced/downloads/list](http://code.google.com/p/juced/downloads/list) (for more infos: [http://www.anticore.org/jucetice/](http://www.anticore.org/jucetice/)). Here some cool software (even if not all of them are LADSPA or LV2 plugins or VST): [http://kokkinizita.linuxaudio.org/linuxaudio/](http://kokkinizita.linuxaudio.org/linuxaudio/) , [http://non.tuxfamily.org/](http://non.tuxfamily.org/) , [http://www.rncbc.org/drupal/](http://www.rncbc.org/drupal/) , [http://tombaran.info/autotalent.html](http://tombaran.info/autotalent.html) , [http://www.linux-vst.com/](http://www.linux-vst.com/) , [http://www.joebutton.co.uk/fst/](http://www.joebutton.co.uk/fst/) .

EDIT: Today I've installed the invada studio plugins... they seems well made (I tried just the compressor and I found it comfortable and accurate) [https://launchpad.net/invada-studio](https://launchpad.net/invada-studio) .

---

### Post by mmetelko on 2012-12-27
thank you very much,crocoduck!

---

### Post by milozeta on 2013-04-05
> **CrocoDuck said:**
> Hi. I am a fanatic of any LADSPA and LV2 plugin that actually exists, but CALF plugins ([http://calf.sourceforge.net/](http://calf.sourceforge.net/)) are my favourite ones. Here you can find DISTRHO plugins, I think they are really interesting: [http://distrho.sourceforge.net/](http://distrho.sourceforge.net/) . Here some plugin that are very cool, but I experienced some difficult trying to run them under ubuntu 12.04 (they are out of the box with 10.04) [http://code.google.com/p/juced/downloads/list](http://code.google.com/p/juced/downloads/list) (for more infos: [http://www.anticore.org/jucetice/](http://www.anticore.org/jucetice/)). Here some cool software (even if not all of them are LADSPA or LV2 plugins or VST): [http://kokkinizita.linuxaudio.org/linuxaudio/](http://kokkinizita.linuxaudio.org/linuxaudio/) , [http://non.tuxfamily.org/](http://non.tuxfamily.org/) , [http://www.rncbc.org/drupal/](http://www.rncbc.org/drupal/) , [http://tombaran.info/autotalent.html](http://tombaran.info/autotalent.html) , [http://www.linux-vst.com/](http://www.linux-vst.com/) , [http://www.joebutton.co.uk/fst/](http://www.joebutton.co.uk/fst/) .

EDIT: Today I've installed the invada studio plugins... they seems well made (I tried just the compressor and I found it comfortable and accurate) [https://launchpad.net/invada-studio](https://launchpad.net/invada-studio) .

hi all,
if I download a native plugin with .so extension, where I have to place  it to be used in LMMS? how do install .so plugin for LMMS?

thanks in advance

---

### Post by zequence on 2013-04-05
> **milozeta said:**
> hi all,
if I download a native plugin with .so extension, where I have to place  it to be used in LMMS? how do install .so plugin for LMMS?

thanks in advance

Depends on what kind of plugin it is. I don't know where lmms keeps builting plugins, and if it's even possible to add plugins that way, but..

you can find ladspa plugins at /usr/lib/ladspa
and lv2 at /usr/lib/lv2

---

### Post by Koori Graywolf on 2013-04-27
What are the best free VSTs, soundfonts, LADSPA, LV2, etc, instrument and effect plug-ins? For instruments, I would need drumkits, bass, acoustic and electric guitars, orchestral and choir, and techno stuff.

---

### Post by Sylos on 2013-04-29
> **Koori Graywolf said:**
> What are the best free VSTs, soundfonts, LADSPA, LV2, etc, instrument and effect plug-ins? For instruments, I would need drumkits, bass, acoustic and electric guitars, orchestral and choir, and techno stuff.

For drums I would recommend you use a standalone sequencer such as Hydrogen and then record it in Ardour or something similar. I dont know of any drum plugins as such.

As for the other instruments - it somewhat depends on the sound you are looking for. When going for free soundfonts you tend to find a lot sound very artificial with a relatively limited number that sound reasonably authentic. Have a google for Belatrix Orchestra - there are some donwloads available for this that I used recently. A lot of the soundfonts are a little poor for me (I also had trouble with some scratchy sounds on some of them but I think that may have been a resampling issue that could be fixed at my end) but there are a few very nice sounding ones tucked away in there as well. For orchestral stuff the Squidfont Orchestra is good - other thna that you just need to trawl through them all and see what you like.

For choir stuff I really cant help. I have been looking for a decent choir soundfont for quite a while and still havent found one I like. The only option may be to break out the wallet and pay for something better. Or find some free samples and make my own (dont think I have the skill for that).

For effects again it depends on what you need. I expect Linux DSP are among the best but as they are not Free I havent got them to test (keep meaning to buy them but cant quite bring myself to do it). I would suggest just download all the free ones you can find and test them. TAP make good ones as do CALF. INVADA arent bad either. Then there are a whole host of others.

Hope that helsp in some way.


Cheers

---

### Post by Koori Graywolf on 2013-05-02
> **Sylos said:**
> For drums I would recommend you use a standalone sequencer such as Hydrogen and then record it in Ardour or something similar. I dont know of any drum plugins as such.

As for the other instruments - it somewhat depends on the sound you are looking for. When going for free soundfonts you tend to find a lot sound very artificial with a relatively limited number that sound reasonably authentic. Have a google for Belatrix Orchestra - there are some donwloads available for this that I used recently. A lot of the soundfonts are a little poor for me (I also had trouble with some scratchy sounds on some of them but I think that may have been a resampling issue that could be fixed at my end) but there are a few very nice sounding ones tucked away in there as well. For orchestral stuff the Squidfont Orchestra is good - other thna that you just need to trawl through them all and see what you like.

For choir stuff I really cant help. I have been looking for a decent choir soundfont for quite a while and still havent found one I like. The only option may be to break out the wallet and pay for something better. Or find some free samples and make my own (dont think I have the skill for that).

For effects again it depends on what you need. I expect Linux DSP are among the best but as they are not Free I havent got them to test (keep meaning to buy them but cant quite bring myself to do it). I would suggest just download all the free ones you can find and test them. TAP make good ones as do CALF. INVADA arent bad either. Then there are a whole host of others.

Hope that helsp in some way.


Cheers

Very helpful, thanks a lot!

---

### Post by gnuman on 2013-05-06
> **Sylos said:**
> For drums I would recommend you use a standalone sequencer such as Hydrogen and then record it in Ardour or something similar. I dont know of any drum plugins as such....


There are drum plugins, like [ADM]("http://www.musicradar.com/computermusic/audiorealism-adm-cm-drum-plug-in-free-with-computer-music-178-542022") from Audorealism, and the [CM-505]("http://www.kvraudio.com/product/cm_505_by_computer_music") by Linplug.  Hydrogen is more of a stand-alone application, but I it's my favorite drum machine software synth.  You can export your loops in Hydrogen as MIDI or audio files, but you could also route it into a DAW, as Sylos said.

---

### Post by mmetelko on 2013-05-14
> **gnuman said:**
> There are drum plugins, like [ADM]("http://www.musicradar.com/computermusic/audiorealism-adm-cm-drum-plug-in-free-with-computer-music-178-542022") from Audorealism, and the [CM-505]("http://www.kvraudio.com/product/cm_505_by_computer_music") by Linplug.  Hydrogen is more of a stand-alone application, but I it's my favorite drum machine software synth.  You can export your loops in Hydrogen as MIDI or audio files, but you could also route it into a DAW, as Sylos said.

thank you, but vsts don't work well on my sistem. Does any one know of a linux native drum synth plugin or standalone? Something like roland tr-909.

---

