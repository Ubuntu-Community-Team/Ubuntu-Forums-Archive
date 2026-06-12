---
title: "Just get me started - please"
date: 2011-08-04
forum: Ubuntu Studio
---

### Post by sidewalkcynic on 2011-08-04
I didn't think this audio stuff would be so complicated.

I am not a musician - I'm a visual artist by training. I am getting into Blender animation, and so I would like to get some sound going with it all. A month ago I downloaded RoseGarden and QSynth and the dependencies and I could not figure out the Jack stuff and so nothing worked. Now I downloaded the Ubuntu Studio packages and now I have more stuff that doesn't work - help?

I'm downloading the whole Ubuntu Studio ISO now, and I will install it if that would that be the better plan - I'm sure I will install it for the October release. But right now I rather not do an install if I can avoid it, because I got a lot of packages that i would have to re-install.

Anyway, I am waiting for the download to complete before I re-boot for adjusting the audio group permissions.

I got the Hydrogen Drum package to give me some sounds and that was fun, but I would like to be able to work that simple synthesizer I opened - it had airplane, car crashes and other things that I would like to work with.

---

### Post by jejeman on 2011-08-04
Well, you need to give more info on your system. Hardware and software. Which version of ubuntu you are using, what is youre sound card...
After that you need to specify youre problems. One by one. And what you want to do/achive.

Here is some general info on jack
[https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration)

---

### Post by sidewalkcynic on 2011-08-04
Whatever the soundcard is that comes stock with the Acer Aspire One - I'm sure it is nothing fancy

```
  *-multimedia            
       description: Audio device
       product: N10/ICH 7 Family High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:45 memory:58540000-58543fff
```

---

### Post by triunenature on 2011-08-05
> **sidewalkcynic said:**
> Whatever the soundcard is that comes stock with the Acer Aspire One - I'm sure it is nothing fancy

```
  *-multimedia            
       description: Audio device
       product: N10/ICH 7 Family High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:45 memory:58540000-58543fff
```

I have the same netbook.  You need to be aware of its limitations.  Its not exactly designed for audio/video production.

But either way, what exactly is your problem?  If you are trying to edit sound, might i recommend audacity.

You do realize you need to setup jack, in order for it to work, right?

Either way, good luck

---

### Post by sgx on 2011-08-05
> **sidewalkcynic said:**
> I didn't think this audio stuff would be so complicated.

I am not a musician - I'm a visual artist by training. I am getting into Blender animation, and so I would like to get some sound going with it all. A month ago I downloaded RoseGarden and QSynth and the dependencies and I could not figure out the Jack stuff and so nothing worked. Now I downloaded the Ubuntu Studio packages and now I have more stuff that doesn't work - help?

I'm downloading the whole Ubuntu Studio ISO now, and I will install it if that would that be the better plan - I'm sure I will install it for the October release. But right now I rather not do an install if I can avoid it, because I got a lot of packages that i would have to re-install.

Anyway, I am waiting for the download to complete before I re-boot for adjusting the audio group permissions.

I got the Hydrogen Drum package to give me some sounds and that was fun, but I would like to be able to work that simple synthesizer I opened - it had airplane, car crashes and other things that I would like to work with.

Hi, if you study the pages and articles at this link

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

 (start at the bottom link) you'll see how to connect your software and audio hardware in linux audio/video.

"blender audio" in a google search brings lots of useful pages.

Hydrogen plays .wav samples from a kit, you can make new kits, patterns, place various patterns in a song grid, and there is a setting for midi input, so a qwerty or midi keyboard can trigger the sounds when you want them.

Here is a how-2 for making kits from your own samples

[http://ubuntuforums.org/showthread.php?t=1347693](http://ubuntuforums.org/showthread.php?t=1347693)

So if you had various samples of wind, rain, thunder etc,
you could make a custom audio storm for a blender animation

If you run the lsmod command, you should see a long list of kernel modules, one will look like snd_hda_intel, a common soundchip that
works well. It will show up in Qjackctl, click the Setup button,

then click the >widget at Input Device >   and Output Device >
(screenshots at the links)
Cheers

---

### Post by sidewalkcynic on 2011-08-07
Thanks for the responses, I will review the recommended reading, and see if I get anywhere.

But, check out what I did in the mean time.

1) I installed the whole UbuntuStudio OS

2) When I reconfigured the Gnome-Panel Menu with all the application launchers, I deleted the twenty-some audio and video launcers in the Audio/Video menu because they are in the specific Audio Production and Video Production menus; and I just wanted to clear up the Audio/Video menu so it only had the medi players.

3) Well, what happened was that deleting the launchers in the native menu deletes the launchers in the secondary menus. So, now all the production apps are missing and I do not remember all the names so as to replace them. I have tried to recover the original menu with some terminal commands I have found on the Internet, but they don't restore the original application list.

Any ideas on how to recover the original list?

How about a text list of all the applications, and I will do it one at a time???

---

### Post by psy-man on 2011-08-07
I've no idea how you managed to delete those launchers. If you tell how you did it maybe it can be undone.. The System Preferences menu includes an app for sorting your menus out its called "Main Menu". You can use it to hide items you don't want to use, with out deleting anything. You can use the Ubuntu Software utility to add and remove software packages
> I have tried to recover the original menu with some terminal commands I have found on the Internet,
If you don't keep a record of what exactly you typed in the terminal it will be very difficult for any one to help you, take care what info you use from the net its not all intended to be helpful..You can use the terminal to scroll through previously typed commands by using the up arrow button.

---

### Post by sgx on 2011-08-07
most apps will be found in /usr/bin, and can be started by typing their name in a terminal. I would open up synaptic,

sudo synaptic

and reinstall the gnome system apps and libraries. It will prompt you to add more if needed.

In the meantime, starting apps from a terminal can provide useful information if there is a problem.

Cheers

---

### Post by sidewalkcynic on 2011-08-07
I did not delete the launchers from the /usr/bin

I am talking about the icon launchers in the menu - you know, the menu that you get when you put the cursor on the Ubuntu logo on the Gnome Panel. I'm replacing them manually, now, anyway. The problem is that I do not know all the /Bin launcher designations. This is a problem I have noticed with other applications - they do not give the launch codes.


It might be a good idea for the UbuntuStudio engineers to tighten-up the menus with further hierarchy that follow the list that they divide their list of apps with.

[https://wiki.ubuntu.com/UbuntuStudio/PackageList](https://wiki.ubuntu.com/UbuntuStudio/PackageList)

This is a nice list, and if the apps were placed in a menu hierarchy that resembled this instead of just throwing them all into one menu it would help people understand what is what.

> **Basic infrastructure**

alsa-tools - Console based ALSA utilities for specific hardware
alsa-tools-gui - GUI based ALSA utilities for specific hardware
qamix - Configurable mixer for ALSA

**JACK and JACK Utilities**

jackd - JACK Audio Connection Kit (server and example clients)
qjackctl - User interface for controlling the JACK sound server
bitscope - diagnosis tool for JACK audio software
jdelay - A small command line JACK app you can use to measure the latency of your sound card.
meterbridge - A collection of Audio meters for the JACK audio server
patchage - modular patch bay for Jack audio and Alsa Midi
jack-tools - various JACK tools: plumbing, play, udp, ctl, scope, clock

**Sound editing and recording**

audacity - Swiss army audio editor
timemachine - JACK audio recorder for spontaneous and conservatory use

**Audio playback**

audacious - Versatile lightweight audio player.
audacious-plugins-extra - Plugin pack for Audacious.

**Digital Audio Workstation software**

ardour - Digital audio workstation (graphical gtk interface)
beast - music synthesis and composition framework

**Synthesizers**

fluidsynth - Real-time MIDI software synthesizer
bristol - vintage synthesizer emulator
freebirth - Bass synthesizer/sample player/sequencer similar to Rebirth
qsynth - fluidsynth MIDI sound synthesiser front-end
zynaddsubfx - Realtime software synthesizer for Linux
csound - powerful and versatile sound synthesis software
swami - SoundFont editor

**Sampling**

sooperlooper - Looping Sampler LADSPA plugin

**Sequencing**

aconnectgui - graphical ALSA sequencer connection manager
rosegarden - music editor and MIDI/audio sequencer
hydrogen - Simple drum machine/step sequencer
seq24 - Real time MIDI sequencer
jackbeat - audio sequencer
muse - Qt-based midi/audio sequencer
tk707 - drum sequencer for a sound card or MIDI device
shaketracker - MIDI sequencer with tracker GUI

**Effects and signal processing**

jack-rack - LADSPA effects "rack" for JACK
tapiir - A tool for real time audio delay and feedback effects
freqtweak - Realtime audio frequency spectral manipulation
jamin - Audio mastering from a mixed down multitrack source with JACK
creox - real-time guitar effects
jackeq - routes and manipulates audio from/to multiple sources

**DJ tools**

terminatorx - A realtime audio synthesizer
mixxx - A digital DJ interface (for beat-mixing)
MIDI Utilities

timidity - Software sound renderer (MIDI sequencer, MOD player)
vkeybd - Virtual Keyboard program

**Musical typesetting**

denemo - A gtk+ frontend to GNU Lilypond
lilypond-data - LilyPond music typesetter (data files)

lilypond - A program for typesetting sheet music

**Miscellaneous / uncategorized**

gtick - Metronome application
puredata - realtime computer music and graphics system
fluid-soundfont-gm - This is a GM SoundFont, for use with any modern MIDI synthesiser: hardware (like the emu10k1 sound card), or software (like FluidSynth).

---

### Post by sidewalkcynic on 2011-08-07
> **sgx said:**
> most apps will be found in /usr/bin, and can be started by typing their name in a terminal.

Cheers

Yeah, I know that. The problem is that some of the executes in the /usr/bin are not the same as the name of the applications and so it is difficult to figur out which execute is the one looking for.

---

### Post by sidewalkcynic on 2011-08-07
All I want to do at this time is just make some noise and musical notes that i can record with some animations that i make on Blender.

I do not want to do any live recordings of guitars, and DiscJockey stuff - I just want to put together a synthesizer and this Hydrogen drum set and save it and sequence it with an animation.

---

### Post by psy-man on 2011-08-07
You have made animations in blender! I take my hat off to you, I have not managed to get my head around blender at all. I guess I spent too much time using Gmax in windows.
What you want to do sounds easy don't it. Weather you record a guitar or the sound of a PC being dropped out of a window you still need to use an audio capture program.
Creating strange sounds with a synthesiser is easy unless you want it to sound like something! then it is hard and takes a long time. When you have audio files and synth sounds you want to trigger You must use a sequencer to trigger them at the right time. Hydrogen is a drum sequencer, its preloaded with drum sounds but you can create your own noises and load them in. it is best suited to short sounds used in a rhythmic fashion. If you want to use melody as well as percussive sounds then a more general purpose sequencer will suit you better. Before you get immersed in the details the primary thing you need to uncover is how to sync the sequencer with blender. Does blender have any options for outputting or receiving time code either smpte or midi ?

---

### Post by sidewalkcynic on 2011-08-07
Alrighty, now. I had to download some more stuff, but finally I got the Virtual keyboard and the ZynAddSyth going - now all I have to do is figure out the further recording and saving.

I am still learning Blender - I crash coursed it the past two weeks, as it has been just about all I have been doing. It took about four days of just watching tutorials on-line before I got to the point of doing anything. The tutorials I came across were kind of bland - that is they didn't go through a complete simple project to make it fun. Most of the tutorials are introductions to the interface and tools, and end there; and then you have to go through tutorials that are somewhat complete to an animation, but the person giving the tutorial is going so quick that you have to go over the sequence several times.

The best interface and tool tutorials are at [http://www.BlenderTips.com/](http://www.BlenderTips.com/)

then [http://www.BlenderCookies.com/](http://www.BlenderCookies.com/) has really good sculpting tutorials

But to be honest, it was a series of really poor tutorials that helped me get started, because the guy was so slow and the sessions were so quick, and because I have art school background I knew how to expand the concepts he was teaching into simple learning projects. Plus you can download his series of tutorials for offline - [http://nystic.com/](http://nystic.com/)

But as far as my first animation -  [http://www.youtube.com/user/SidewalkCynic?feature=mhee](http://www.youtube.com/user/SidewalkCynic?feature=mhee)
Which is just a further rendition of a tutorial of a bouncing ball from Cookies.com

I'm working on a more complex animation to teach a replacement for the Dewey Decimal system. [https://sites.google.com/site/sidewalkcynic/slclassification](https://sites.google.com/site/sidewalkcynic/slclassification)

---

### Post by sgx on 2011-08-07
For basic recording, timemachine does an excellent job,
just one record button, and a few options. Choice between recording
.w64 and .wav files is important, but Audacity can import either,
and export in many formats.

timemachine -f wav

timemachine --help

You connect zyn or hydro output to timemachine input using qjackctl, hydro may auto-connect to the soundsystem by default, but both will need manual connections to timemachine.

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

You may find it easier to export your animation to a video editor
like openshot, lives, kino, and import the audio to their timeline.

I have read that blender can manage this internally now, so your research should find what works best.

Did you reinstall the gnome files using synaptic?

I would do a reinstall and create a separate /home partition. This will
make future reinstalls trivial, saving many important configs and settings
by choosing not to reformat /home, during a new install. Not quite as important to the casual user. 

Cheers

---

### Post by sidewalkcynic on 2011-08-07
Okay. So, I got myself set up with a synthesizer. Now I unplugged from that, and I do not have any regular sound - how do I reconnect the sound?

I reinstalled applications with Synaptic after I installed UbuntuStudio. As far as reinstalling the aplication launcers in the Gnome-Panel Menu I am doing it by hand through the Gnome-Panel Menu editor.

---

### Post by psy-man on 2011-08-07
When you are finished with the sound apps use qjacktl to stop the sound server. That will release the hardware for regular use.
Well, I do not understand very much of your secular classification system, while english is my first and only language, I have always thought it is fundamentally flawed when it comes to issues like truth, maybe that is a problem with all language or perhaps it is the concept of truth itself that is flawed.  You might enjoy watching the movies at [this]("http://www.zeitgeistmovie.com/") site. But I think perhaps I have strayed far enough from purpose of this forum if not the subject of this thread. Thanks for the links to the blender tutorials I will pick them up from my other PC later, this one is dedicated to making noises and does not have any flash or "wotnot" installed.

---

### Post by sidewalkcynic on 2011-08-07
> **psy-man said:**
> Well, I do not understand very much of your secular classification system, while english is my first and only language, I have always thought it is fundamentally flawed when it comes to issues like truth, maybe that is a problem with all language or perhaps it is the concept of truth itself that is flawed.Like everyone else, chances are you do not understand the Dewey Decimal system either (it doesn't make any sense when analysed completely), and only use it when looking for the call number of a book at the library - that is why I am making an animation video so as to better explain a very boring subject that is important to understanding truth and reality better.

---

### Post by sidewalkcynic on 2011-08-07
> **sgx said:**
> I would do a reinstall and create a separate /home partition. This will
make future reinstalls trivial, saving many important configs and settings
by choosing not to reformat /home, during a new install. Not quite as important to the casual user. 

CheersI do have a separate home partition, and I do install using that method. The problem was that UbuntuStudio has a whole lot of applications in the Sound/Audio/Video Menu that are also in the specific Audio Production and Video Production Menus.

So what I did was I deleted the applications that were in the Sound/Audio/Video menu, and what happened was that Gnome also deleted the same applications that were duplicated in the Audio Production and Video Production menus.

You can try it, yourself. Go to your Audio/Video/Sound Menu and notice that it has all the applications in there that are in your Audio Production and Video Production menus - delete some of the duplicated applications from your Audio/Sound/Video menu and you will notice that it deletes the applications from the Audio Production and Video Production menus that the application is duplicated into.

---

### Post by sgx on 2011-08-09
I only use 20 or so apps in the course of a month, and I put
those on a task bar. If nested menus had boundaries for
those times my mouse drives erratically (weekdays and weekends ;) )
I would probably use them more often. 
Cheers

---

### Post by sidewalkcynic on 2011-08-09
I just did an estimate of my app usage, and of the sixty, or so, now installed, I use less than twenty. I like a blank desktop, or at least a design of my own as a background, so I do not use a taskbar. I use a hidden top panel, and I know your complaint of the wandering mouse in the nested menus, and I use nested menus for my WebBrowser menus, as well; and I have a cheapo mini mouse.

But I am going to have to spend the big money for mouse to use with Blender, because the erratic behavior is beginning to annoy.

---

### Post by youWho on 2012-01-20
By the way re earlier comments in this thread: if it's helpful to know, you can type "history" in the terminal (without the quotes of course) to see what you did there (if your ~/.bash_history file is still intact). Also in Synaptic there's a menu item File->History.

cheers

---

