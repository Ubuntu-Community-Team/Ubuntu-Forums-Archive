---
title: "[recording] recording stereo mix through &quot;arecord&quot;???"
date: 2008-09-08
forum: Ubuntu Studio
---

### Post by kakyoism on 2008-09-08
I used to record "stereo mix" of soundcard output on Windows.
Read a few tutorials about using the "arecord" command to do the same thing on Linux,

However, using the following command only gives me the microphone input:
```
arecord -d 10 -f cd -t wav -D hw out.wav
```

which means, if I unplug the mic, I will hear nothing.

Is there a way to record the digital output or even back-end audio samples of the "stereo mix"?

Thanks!

---

### Post by eye208 on 2008-09-19
You can select the recording source in the desktop volume control or in alsamixer. If your soundcard does not offer a stereo mix source you can use the ALSA loopback driver instead. This will add a virtual soundcard to your system which can be used to route audio from one application into another.

To load the loopback driver enter
```
sudo modprobe snd-aloop
```

If you have only one physical soundcard in your computer (card #0) the virtual one will be card #1. You can make this the default soundcard for all apps by creating a file ".asoundrc" in your home folder with the following content:
```
pcm.!default {
    type hw
    card 1
    device 0
}
```

While this file exists, any application you start will use the loopback soundcard instead of the real one. The loopback driver will just capture the app's output at hw:1,0 and route it to hw:1,1 (or vice versa). You can have up to 8 independent loopback streams between applications:

hw:1,0,0 <-> hw:1,1,0
hw:1,0,1 <-> hw:1,1,1
hw:1,0,2 <-> hw:1,1,2
...
hw:1,0,7 <-> hw:1,1,7

Here's an example: With the ".asoundrc" file in place, start up Firefox and look for a site that plays sound through Flash, e.g. YouTube, MySpace Music, Imeem etc. You won't hear the sound until you enter this command to route it back to the physical soundcard:
```
arecord -D hw:1,1 -f cd | aplay -D hw:0 -f cd
```

You can now record the audio to a wav file in the same way, either through arecord or some other application such as Ardour.

Delete or rename the ".asoundrc" file to make card #0 your default soundcard again.

---

### Post by Ripfox on 2008-09-19
I still use Audacity for recording in Linux

---

### Post by eye208 on 2008-09-19
Audacity doesn't work properly with the loopback driver. That's why I recommend Ardour.

---

### Post by kakyoism on 2008-09-19
Thanks, eye208.
I currently use pulseaudio instead of ALSA and I have a builtin soundcard 
and a USB external one. Does your method apply to this situation as well?

---

### Post by eye208 on 2008-09-19
As far as I know, PulseAudio comes with its own routing capability. I don't know exactly how that works because I removed PulseAudio shortly after making the switch to 8.04.

---

### Post by kakyoism on 2008-09-19
Do you have a reason not to use pulseaudio?
I just found that it became much more straightforward to set up surround with pulseaudio than with ALSA....haven't evaluate it over other aspects of audio applications....

---

### Post by eye208 on 2008-09-20
> **kakyoism said:**
> Do you have a reason not to use pulseaudio?
Yes. Most of Hardy's audio-related issues have been caused by PulseAudio. Removing it from the picture results in a trouble-free audio setup.

Most of PulseAudio's advertised features are redundant. ALSA and Jack can do the same things. I can use ALSA's loopback driver to route audio from any application into Jack and then out to some other application. This means I can use Jack-Rack to apply LADSPA effects in realtime, or use NetJack to transport audio over the network.

Another purported myth about PulseAudio is that it would enable multiple apps to use the soundcard at once. ALSA has been doing that for years by adding software mixing capability to its default device. In fact PA often prevents just that by hogging ALSA's hw:0,0 device. That's why there is a "pasuspend" command after all.

Furthermore, PulseAudio promised to act as a drop-in replacement for ESD but is currently failing to do so. This is why most of the Linux-using residents of Second Life cannot use voice chat. Once you remove PulseAudio and replace it with ESD, voice chat works flawlessly. Unfortunately it's somehow difficult to explain to a Linux noob why removing the "ubuntu-desktop" metapackage won't hurt the system. Many of them are actually afraid to remove PA because ubuntu-desktop lists it as a dependency.

There are many other examples (Audacity not working, Flash not working etc.). You can read dozens of pages of guides and tutorials to work around PulseAudio's incompatibilities and still won't get a 100% working setup. In my opinion it's a waste of time. Whoever came up with the idea of a Grand Unifying Audio Subsystem should have made it work before inflicting it on the majority of users by pushing it into mainstream distributions. Will Ubuntu 8.10 feature a trouble-free PA setup? I doubt it.

---

### Post by markbuntu on 2008-09-21
> **eye208 said:**
> Yes. Most of Hardy's audio-related issues have been caused by PulseAudio. Removing it from the picture results in a trouble-free audio setup.

Most of PulseAudio's advertised features are redundant. ALSA and Jack can do the same things. I can use ALSA's loopback driver to route audio from any application into Jack and then out to some other application. This means I can use Jack-Rack to apply LADSPA effects in realtime, or use NetJack to transport audio over the network.

Another purported myth about PulseAudio is that it would enable multiple apps to use the soundcard at once. ALSA has been doing that for years by adding software mixing capability to its default device. In fact PA often prevents just that by hogging ALSA's hw:0,0 device. That's why there is a "pasuspend" command after all.

Furthermore, PulseAudio promised to act as a drop-in replacement for ESD but is currently failing to do so. This is why most of the Linux-using residents of Second Life cannot use voice chat. Once you remove PulseAudio and replace it with ESD, voice chat works flawlessly. Unfortunately it's somehow difficult to explain to a Linux noob why removing the "ubuntu-desktop" metapackage won't hurt the system. Many of them are actually afraid to remove PA because ubuntu-desktop lists it as a dependency.

There are many other examples (Audacity not working, Flash not working etc.). You can read dozens of pages of guides and tutorials to work around PulseAudio's incompatibilities and still won't get a 100% working setup. In my opinion it's a waste of time. Whoever came up with the idea of a Grand Unifying Audio Subsystem should have made it work before inflicting it on the majority of users by pushing it into mainstream distributions. Will Ubuntu 8.10 feature a trouble-free PA setup? I doubt it.

How would you know? 
You don't use Pulse Audio and never took the time to figure out how it works or how to set it up. I have, and it works great and does things that ALSA cannot, like sync playback for my two sound cards so I can use them both at the same time or individually and send streams to either one or to my network with just a few clicks.

Let me put it this way, if you are planning on using Ubuntu into the future, it would be a good idea to get a grip on Pulse Audio. Setting up Pulse Audio is covered in my guide here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by Buttons840 on 2009-06-23
I found a suitable solution for myself near the bottum of the fallowing page.

[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

It said:

> 
For Jaunty 9.04:

    *

      There's no longer any need to start Audacity with padsp, so remove this again from the Main Menu using System -> Preferences -> Main Menu if you had changed it in 8.10 and then upgraded to 9.04 automatically. Otherwise there should be no need to change the start-up command for Audacity.
    *

      Open up 'Applications -> Sound and Video -> PulseAudio Volume Control'.
    * Open up the source of the sound, e.g. Totem music player or a web page that plays audio. Once the sound starts, pause it and go back to the start if you can.
    *

      Go back to the Playback tab of the PulseAudio Volume Control. It should be showing the sound stream. Right click, choose Move Stream and point it to the stream that you listen on e.g. 'USB Headphone set'.
    *

      Open up Audacity and select 'Edit -> Preferences'. In the 'Audio I/O' section, de-select the two checkboxes under Playthrough. Under Playback, choose Device: ALSA: pulse. Under Recording choose Device: ALSA: pulse and Channels: 2 (Stereo). Click Ok to save the changes, then close down Audacity and open it up again.
    * In Audacity, click on Record, and then Pause.
    * Go back to the Pulse Volume control and look for the new entry for Audacity on the Recording tab. It will probably be called 'ALSA plug-in [audacity]: ALSA capture'. Right-click on the stream, choose Move Stream and then select the Monitor for the device that you listen to e.g. 'Monitor for USB Headphone set'.
    * Release the pause in Audacity and start playing the audio. When the recording has finished, press stop in Audacity and remove and superfluous sections at the start and end of the track using Audacity's editing features. Then export as an MP3 file. 


Check the page, they may have updated the instructions.  I also had to download the PulseAudio Volume Control using Add/Remove programs.

---

### Post by jjross on 2009-06-23
Here, this will record in stereo and output as an mp3 with a date and time title
you need to have lame installed.
it is the -c that designates how many channels.

arecord -d10800 -r44100 -c2 | lame -v --preset standard - /home/your music folder/$(date +%Y-%m-%d-%H%M).mp3

---

### Post by kgiraldin on 2009-09-17
Hello,

I am trying to record audio from a streaming video. I can do it fine at work with a different laptop and Windows. At home I have a Lenovo ThinkPad X61s, Ubuntu, and my sound card is an ad1984. I can record with Audacity but via the pc speaker and the pc internal mike so naturally it sounds very bad. What do I have to do to be able to record directly from the card so it sounds great like it does at work? I will provide whatever details are needed to help. 

Thanks!

---

### Post by jlinkels on 2013-01-19
> **Buttons840 said:**
> I found a suitable solution for myself near the bottum of the fallowing page.

[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

It said:



Check the page, they may have updated the instructions.  I also had to download the PulseAudio Volume Control using Add/Remove programs.

I know your post is quite some time ago, but this is the first time I found an instruction as of how to record through Pulse. My audio cards do not provide an internal mixer so capturing thru ALSA is not possible. Now I did it through Pulse using these instructions.

Although it is a bit awkward that you have to start your application, go back to Pulse to configure it, and then continue, but overall it works wonderfully well.

THANK YOU!

jlinkels

---

