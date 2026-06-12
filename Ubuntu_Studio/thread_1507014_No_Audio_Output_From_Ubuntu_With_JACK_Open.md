---
title: "No Audio Output From Ubuntu With JACK Open"
date: 2010-06-11
forum: Ubuntu Studio
---

### Post by Dynamata on 2010-06-11
I am using Ubuntu 10.04 with Realtime Audio setup & audio output is working, when I open the JACK application audio output stops. I am using the Motherboard audio (hw:0) although I do have an M-Audio Audiophile 24/96 card (hw:2) installed. The ALSA tab in the connections panel shows 14:Midi Through & 24:M Audio Audiophile but no Motherboard audio, is this normal?

Is there a basic manual or tutorial for JACK? :confused:

Messages (JACK open):

07:10:48.494 Patchbay deactivated.
07:10:48.554 Statistics reset.
07:10:48.616 ALSA connection graph change.
07:10:48.775 ALSA connection change.

Messages (JACK running):

07:10:48.494 Patchbay deactivated.
07:10:48.554 Statistics reset.
07:10:48.616 ALSA connection graph change.
07:10:48.775 ALSA connection change.
07:11:43.314 Startup script...
07:11:43.314 artsshell -q terminate
sh: artsshell: not found
07:11:43.716 Startup script terminated with exit status=32512.
07:11:43.716 JACK is starting...
07:11:43.717 /usr/bin/jackd -t2000 -dalsa -dhw:0 -r44100 -p128 -n3
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    1545855
07:11:43.746 JACK was started with PID=4212.
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|128|3|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 128 frames (2.9 ms), buffer = 3 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 3 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 3 periods for playback
07:11:45.892 Server configuration saved to "/home/t/.jackdrc".
07:11:45.894 Statistics reset.
07:11:45.951 Client activated.
07:11:45.955 JACK connection change.
07:11:46.015 JACK connection graph change.

---

### Post by thorgal on 2010-06-11
the ALSA tab is legacy MIDI stuff, not sound. To inspect audio, look into the Audio tab.

---

### Post by cchhrriiss121212 on 2010-06-11
If you have a sound card like the audiophile then you should use it as the main interface, it will be much better than any onboard audio.

---

### Post by Pablo_F on 2010-06-11
Also, you can't expect any sound from a non-jack-aware application when jack is running. Most multimedia players are not jack-aware by default but you can achieve this, easily in most cases. See for example [http://www.linuxmusicians.com/viewtopic.php?f=19&t=2507](http://www.linuxmusicians.com/viewtopic.php?f=19&t=2507)). 

There are other possibilities. You should make clear what you want / expect, then maybe ask for suggestions. 

Jack talks to one card at a time, at least in the audio part.

Alsa tab stands for alsa midi whereas midi tab stands for jack midi which is being adopted by some sequencers and synths lately, but you will probably see this tab empty. There is no alsa audio because audio is managed by jack. However, jack uses the alsa driver (and others, but for your cards you need the alsa driver). 

Beware of the interface you choose in the jack setup. Use the alphanumeric ID, not hw:somenumber. When you have more than one card numbers can be assigned differently to each soundcard when you reboot the computer and you can be confused by this. This alphanumeric ID you can find from the output of the command:

cat /proc/asound/cards

between brackets. For example, I wrote hw:M2496 in the interface field even if it doesn't appear as an option. I learned this from thorgal, by the way ):P

Confusing? Welcome to linux audio. It is great but a little confusing for beginners. But then you learn a lot.

Cheers! Pablo

---

### Post by Dynamata on 2010-06-11
> **cchhrriiss121212 said:**
> If you have a sound card like the audiophile then you should use it as the main interface, it will be much better than any onboard audio.
I know the M-Audio card is better that's why I bought it & M-Audio Studiophile Monitors as well. The card stopped working under Windows so I switched to Motherboard audio, till I could fix it.

My WinXP is pretty trashed & eventually the Internet connection stopped working so I switched to Ubuntu, I just wanna figure out the Linux audio before I try the Audiophile again. :neutral:

---

### Post by Dynamata on 2010-06-12
I plugged in the Audiophile card & it works! :cool:

---

### Post by Dynamata on 2010-06-13
> **Pablo_F said:**
> 

cat /proc/asound/cards


Good tip, here is the output:

t@mythtv:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf9ffc000 irq 16
 1 [Webcam         ]: USB-Audio - Monitor Webcam
                      OmniVision Technologies, Inc.538-2640-09.07.24.1 Monitor Webcam at usb-0000:00:
 2 [M2496          ]: ICE1712 - M Audio Audiophile 24/96
                      M Audio Audiophile 24/96 at 0xec00, irq 16 

I am following tutorials on JACK & Rosegarden here:

[http://www.youtube.com/watch?v=fMz6fDGBnA4](http://www.youtube.com/watch?v=fMz6fDGBnA4)
[http://www.youtube.com/watch?v=65PjTKt8xFc](http://www.youtube.com/watch?v=65PjTKt8xFc)

I can't get any sound from Rosegarden.

When streaming from the Web, soon as JACK opens the player continues but audio stops. Streaming audio from the hard drive, the player stops.

The avaliable drivers are: dummy*,sun,oss*,alsa*,portaudio,coreaudio,freebob,firewire, JACK will only start with the ones checked*. In the connections box, under the Audio tab both boxes are empty.

I followed the tutorials on linuxmusicians.com, modified vlc & mplayer but nothing changed. I think you have to tweak JACK to make these things work. I want to be able to watch a YouTube tutorial while working on JACK/Rosegarden without losing OS audio.

I followed the YouTube one as far as:

git clone git://repo.or.cz/libflashsupport-jack.git (I have no idea what "git clone" is) & the web link is dead.

I tried:

"t@mythtv:~/src$ cd libflashsupport-jack" and got:

"bash: cd: libflashsupport-jack: No such file or directory"

where to from here? :confused:

---

### Post by cchhrriiss121212 on 2010-06-13
> The avaliable drivers are: dummy*,sun,oss*,alsa*,portaudio,coreaudio,freebob, firewire, JACK will only start with the ones checked*. In the connections box, under the Audio tab both boxes are empty.
Run jack with alsa as the driver every time.
> 
When streaming from the Web, soon as JACK opens the player continues but audio stops. Streaming audio from the hard drive, the player stops.
Jack is designed to be an audio server for music production, so it does not support things like firefox natively. You can get alsa to run all system sounds through jack, which is shown by thorgal [here]("http://ubuntuforums.org/showthread.php?t=1498780").
> 
I followed the tutorials on linuxmusicians.com, modified vlc & mplayer but nothing changed. I think you have to tweak JACK to make these things work.
No tweaking required, just download the plugins and select jack as audio output in vlc. Make sure jack is open and running before you open vlc, then connect it up in the connections window, or use patchage.

---

### Post by Pablo_F on 2010-06-13
git clone will download whatever it is in a git repository. Basically, you need the "git-core" package from ubuntu (synaptic, sudo apt-get install, whatever). You also need some other packages to actually build the plugin, as explained. 

However, I am not sure if the jack flash plugin is the best thing for you: 

Now you can't hear sounds in youtube if jack is running. Then you won't hear sounds in youtube if jack is **not** running. Neither of them is ideal and there are other possibilities as chris and thorgal suggest. 

Cheers! Pablo

---

### Post by Dynamata on 2010-06-13
> **Pablo_F said:**
> .

Now you can't hear sounds in youtube if jack is running. Then you won't hear sounds in youtube if jack is **not** running. 

Cheers! Pablo

Guess you're right, I thought git://repo.or.cz/libflashsupport-jack.git was a web URL, anyway I ran the commands & now all my web browsers have lost sound, how do I fix it? :shock:

---

### Post by Pablo_F on 2010-06-14
> t@mythtv:~/src$ sudo make uninstall
make: *** No rule to make target `uninstall'. Stop.

I deleted makefile without success so I deleted the libflashsupport-jack folder, that didn't work so I restored it.

So no uninstall option. Don't worry. If theflash jack plugin was not the ideal solution we would help you manually uninstalling it from your system. Anyway, anything you delete in your home folder (libflashsupport folder, the makefile, whatever) does nothing. You have installed the plugin in a directory of your OS. Think as if you had installed a .dll file in your windows or system32 or whatever system directory, if you were using windows. In this case, you have compiled the library which is the hard part, then install it (copy the binary file to a system directory)

Anyway, don't panic, you are there! See, patchage is a tool for making virtual connections between apps and audio card. There are 3 types of connections. Audio is blue (this is jack audio), jack MIDI is red, alsa MIDI is green. You probably don't see red connections, this is normal at this stage. There is no "alsa audio". When jack is running, audio is always managed by jack. You can't connect audio to midi, blue to green, certainly not.

I know it is confusing at first but alsa tab has the "normal" MIDI ports and midi tab has other kind of MIDI ports. Forget both tabs. You can forget patchage even. It is a nice app for making virtual connections but let's start as simple as possible. By the time being focus on the audio tab of Jack Control, exclusively. Well, if you don't want to forget patchage, go for it, but blue lines only!

Blue ports in patchage = Ports in the audio tab of qjackctl

So you see flash audio ports and they autoconnect to the system playbacks?? Then you have it!

So what's the problem. You probably have jack talking to another card. Again, don't get confused by the fact that you see your card in the alsa midi tab. It really has nothing to do with jack, let alone with audio. 

Please close firefox. Write down the following in the interface field of Jack Control setup:
hw:M2496
Stop and start Jack Control. Launch firefox and try again. You should have sound in your M-audio 2496.

This is a working jack setup for the m-audio 2496 (decrease the frames/period for better latency if you need it):

[http://imagebin.org/101361](http://imagebin.org/101361)

[IMG]http://imagebin.org/101361[/IMG]

---

### Post by Dynamata on 2010-06-15
I did select hw:M2496 but here's the thing, I asked someone to swap the audio out cables from onboard to Audiophile & assumed they'd done it. I tried hw:intel & it worked! the speakers were still plugged into the Motherboard audio, all Browsers now have audio. I spent 3 nights on this, how sick do I feel, like Sherlock Holmes sez "when you have eliminated the impossible, whatever remains, however improbable, must be the truth". Anyway thanks for being patient. #-o

I fired up Rosegarden & it showed up in the patchbays but using General MIDI piano, can't get any sound. :)

---

### Post by Pablo_F on 2010-06-15
> I fired up Rosegarden & it showed up in the patchbays but using General MIDI piano, can't get any sound. 

Rosegarden does not produce sounds on its own. It is a sequencer. You need either a external synth (hardware or software) or a dssi instrument, i.e., an instrument plugin.

The first approach is more flexible so take it easy and go for the dssi plugin for starters. I suggest hexter, based on a Yamaha DX7 hard synth. Install it from synaptic. Then, in Rosegarden:

Right click on a track and choose "synth plugin" (#1 or whichever). In "Intrument parameters" it will appear a "No synth" push button. Press that. In the dialog that pops up choose hexter as your plugin and select a program. In the track, draw a segment with the pencil. Right click and open it in whatever editor is better for you (matrix or notation).

Make sure Rosegarden master audio outs are connected to the system playbacks (audio tab of qjackctl). You should be hearing something if you draw notes or press the piano roll in the matrix editor.

I hope this helps, Pablo

---

### Post by Dynamata on 2010-06-15
> **Pablo_F said:**
> Rosegarden does not produce sounds on its own. It is a sequencer. You need either a external synth (hardware or software) or a dssi instrument, i.e., an instrument plugin.

Could I not start with a GM MIDI instrument, to hear some sound before I move on to plugins?. :|

---

### Post by Pablo_F on 2010-06-15
> I thought I would start with a GM MIDI instrument, to hear some sound before I moved on to plugins. 

An instrument plugin is very easy to setup in Rosegarden. There is no more to it than what I wrote in my previous post. 

However, if you want an external synth, go to Studio -> Manage Midi Devices, MIDI playback. General MIDI Device is the default name of your default "playback device", but in fact it doesn't imply anything because Rosegarden... I told you, doesn't make any sound!. However, Rosegarden tries to be smart so you will see instrument names and so on. And you can choose an instrument from within Rosegarden and it should work if you connect a GM synthetiser.

So you have to send the midi data trough something, i.e., a synth. See the available outputs. You will see the MIDI out of your m-audio card. You can plug a hardware synth to it. Otherwise, you have to use a software synth.

Oh, and you have fluidsynth-dssi (another package you can easily install from synaptic). It is a dssi but you can load a GM soundfont in it and you are done. 

Cheers! Pablo

---

### Post by Dynamata on 2010-06-18
Ok Pablo, thanks to your help I used the plugins & am up & running. Having the notation input is handy, as that is the way I work. All I need now is a good drum machine plugin. 8-)

---

### Post by Pablo_F on 2010-06-18
Hi Dynamata!
I am glad you are up and running. as far as I know, there is not a drum machine as a dssi plugin, but you can always launch hydrogen, which is a great drum sequencer and sampler (you can load drumkits for hydrogen and even make your own). You can sequence the drums in rosegarden and send the midi data to hydrogen (Studio -> manage midi devices, add playback device and send its midi data to hydrogen).

You can also use the hydrogen sequencer and use the jack transport to synchronize hydrogen and rosegarden. jack is wonderful.

Cheers! Pablo

---

