---
title: "Ubuntu midi interface mapping?"
date: 2016-08-07
forum: Ubuntu Studio
---

### Post by jonas-thornvall on 2016-08-07
I've always been curious about midi interface mapping and software synths, i noticed the only software synth that i have found in the interface of ubuntu midimapping is timidity.
I wonder how come there is so few devices mappable in the synth settings. Somtimes you do not want to run a daw to try out soundsettings.

For a while MS Windows had the excellent SoundCanvas synth "not soundfont" and the Yamaha XG as mappable midiout devices, but they are no longer available. I know that Munt MT32 had dll's that let it run as a mapped midi out device.

I wonder what prevent having a simple VSTI host running as a mapped midiout device, do they not follow the GM,GS, XG standard for general midiout devices?

If someone know howto get Munt MT32 running as a choseable midi out device in the "general application" interfaces or have a link to how it can be done i would love to hear about it.

Intel Compute stick Ubuntu 1 GB memory 6 GB internal storage, but running LXDE from SD card 64 GB.
Just purchased a Behringer UMX 490 and UCA222 interface that i hope will work nice with UBUNTU. 

Best regards Jonas Thörnvall

***I think the ability to be able to map VSTI and Ladspa? GM,GS XG plugins as midi interfaces using a simple midi interface plugin host would be a great advantage, somtimes you just want to listen to the music using different devices and not poke around with a DAW or complicated PLUGIN host and sequenser to make it happen.

---

### Post by marseille2 on 2016-08-07
For recording purposes ... use [ALSA MIDI]("http://alsa.opensrc.org/AlsaMidi").

IMO... Timidity is okay for fooling around ... For instance... you want to sing Kareoke and you need to play a MIDI file. But when it comes to recording... ALSA MIDI:)

To get an idea, look through the forums over at [linuxmusicians.com]("https://linuxmusicians.com/"). 

Also... when it comes to VST, you probably have to set it up on Ubuntu and/or UbuntuStudio. LADSPA and probably Linux VST will work out of the box (you may have to turn on Jackd to use it for certain apps). But Windows VST tends to take some additional work. I recommend taking a look at "[Carla]("http://kxstudio.linuxaudio.org/Applications:Carla")" to use Windows VST.

And when it comes to mapping... it's usually mindless. You fire up your application, and pick your MIDI device. Some apps -- like LMMS and Ardour -- will go one step further and map your faders, pots ... but it's not always perfect, and it really depends on your gear. So it's always best to take a look at the program's compatibility lists. 

That said... any GM device is a no-brainer with ALSA MIDI. ... IMO... Timidity is good for singing along to a MIDI file for KAREOKE... and maybe some elementary stuff... like learning how to play piano or something... but (while others may disagree) I've never seen Timidity cut it for recording.

---

### Post by jonas-thornvall on 2016-08-07
Well that is my point why so few devices can be accesible thru midimapping directly using something like VMPK midi thru and Timidity. Sometimes you do not want to record just play music without firing up and configure a DAW or a Plugin Host. Just select software device from the midimap list and use gs,gm or xg to play music.

But to do that you need an external module, or you have to use Timidity.
I do think you can do music though, i heard Gorillaz made their tunes on a SC-7 and band in a box for dos, so gm synths can absolutely produce music ;)

---

### Post by marseille2 on 2016-08-07
IMO... MIDI is a long discussion no matter the gear or the operating system. It just depends on how we choose to route MIDI to trigger the sound sample ... be it through outboard gear or OS. 

That said... you might want to take a look at this [discussion]("http://askubuntu.com/questions/34391/virtual-midi-piano-keyboard-setup").

---

### Post by jonas-thornvall on 2016-08-08
Agree but sometimes you just want to get tunes and play something or try things out, and then a midiLoopback like hubis come handy. You don not necessarily want to configure a DAW or complex plugin Host to start play, just select the route to the instrument weither the instrument is a VSTI/plugin, Soundfont containe/sampleplayer or an external module is not so much of importance.

I think the option to have them mappable is what counts, but it is lacking in all Operating Systems, one could say that microsoft midimapper was a try but a fail. Because they never offered to map VSTI and it probably was a pain to fork in the softsynths like Yamaha SXG and VSC-88 it did not even let you load soundfonts beyond the SC GM tunes.

And that is the only reason it still isn't there in microsoft products anymore.

---

