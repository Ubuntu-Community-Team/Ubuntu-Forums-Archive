---
title: "Delta 44 problem"
date: 2011-01-23
forum: Ubuntu Studio
---

### Post by pr2 on 2011-01-23
Hi to forums!

After seeing Studio on Youtube - it looks amazing. So I download ISO etc..I just finished installing Studio 10.10. I had a few problems getting the dual boot to work as a previous Grub was messing it all up. But it's all up now. Looks great! 

My Delta 44 Soundcard is not working. Pulse Audio Device Chooser will not open. It starts for a while, then just exits - no message. I know that there was a Delta 44 workaround for previous versions of Studio which I've read about. But now asoundconf has been removed. I'm a bit lost. My Delta is linked into everything that I use. Can anyone give me instructions on how to setup the Delta 44 in 10.10? I have Input set as Ice1712 in Sound Prefs. The system even picked up my old Phillips Webcam, and the Mic on this is working for input! Though currently. nothing works for output. Dummy Output only.

I would like to use Hydrogen, my Midi piano (for notation) and record audio stuffs all Sync'd through Jack. I've a little experience with Unix from college, but I'm fairly new to Linux. Is this possible to get fixed? Can anyone provide a few numbered instructions ?

Any help appreciated v.m.
PR

---

### Post by sgx on 2011-01-24
go online, and install alsamixergui using synaptic (package manager gui to install or
remove apps easily), or use the command

apt-get install alsamixergui (if is not installed)

unplug all peripherals except keyboard and mouse,
and reboot.

issue these commands

killall pulseaudio

jackd -dalsa -r44100


(these are 2 single commands, press enter at the last character of the string.
The first stops a competing audio setup, the second launches the jackd sound server)

If it works the command output will end something like this.

ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback

Now start qjackctl, by command, menu, or icon, and click its setup button, and on the panel that opens, at the middle-far-right,

Input Device >
Output Device >

click the  > widgets, to see your soundcards/chips. The Delta might have two entries, ice-1712, and one with an mAudio name, maybe ice-1724 or similar. If one of them is already selected, just use it. If not Choose ice-1712 to test, then stop and start the jackd server, using the button on the main qjackctl screen.
So, you don't quit the qjackctl program itself.

Now on the main qjackctl screen, press the Connect button at the lower-right,
a 3-tab panel opens. The Alsa tab should display the Delta midi ports,
and the Audio tab should show 2 System entries, click them to see the available inputs and outputs. When you start Hydrogen, or zynaddsubfx synth, they will display in these alsa and audio tabs, connect them according to needs. Hydrogen will need the Audio connection to be heard, it is automatic in some versions, and the midi connection allows it to be played by a midi keyboard, while it plays a song/sequence.

The lsmod command list kernel modules, its output should include
snd_ICE1712, or snd_ICE1724, or similar.

If it looks like the parts are in place, but no sound, start the alsamixergui, with sound going in your card, and raise levels til you
get the right ones.

Google ardour hydrogen qjackctl youtube for lots of videos

here is one  [http://www.videosurf.com/video/qjackctl-realtime-and-ardour-basics-1204802087](http://www.videosurf.com/video/qjackctl-realtime-and-ardour-basics-1204802087)

cheers

---

### Post by pr2 on 2011-01-24
Thank you so much Mr SGX!
 
I printed out and followed your instructions. I have SND_ICE1712 showing in the list after "lsmod".
 
I got some Wave files playing in DAW, the Audio level LEDS are showing in the DAW, but sadly no sound. All your instructions worked exactly as you said. I tried selected both ICE-1712 and M-Audio QJackctl. Perhaps I'm not connecting the correct patchbays. One appears according to whichever application I'm using. I tried connecting all, and various permutations. I tried connecting them in System as well. I tried playing a Movie in a Youtube channel, but no sound. In Sound->System, Dummy Audio is still only output that shows.
 
Any further suggestions I might try.
 
Many thanks again
PR

---

### Post by sgx on 2011-01-24
Forgot, envy24control is a mixer for mAudio cards, it will be part
of alsa-tools-gui

Try to install that using synaptic, or the command

sudo apt-get install alsa-tools-gui

or get it here, it will have a .deb extension:

[http://packages.debian.org/unstable/sound/alsa-tools-gui](http://packages.debian.org/unstable/sound/alsa-tools-gui)

and install manually:

sudo dpkg -i name-of-package.deb  

i386 is used for normal 32 bit system, ia64 or AMD64 for 64 bit

Make sure the file is in the same directory as your shell prompt,
if you do it manually, copied to /home/username is typical.

Also, install alsamixergui, for luck

Also, put the headphones in your motherboard sound output, in case
its getting diverted there


Look in /usr/sbin for alsaconf, or alsactl, use a filemanager, like thunar, pcmanfm, or nautilus, or 

cd /usr/sbin
ls | more   (and tap the space bar to see more of the list)


On my system, such a command 

sudo alsaconf

starts an easy configuration routine, to choose the soundcard,
and set a mixer volume.

Gettin closer! ;)

---

### Post by pr2 on 2011-01-24
Thank you SGX. That did it!!

Its a really nice sounding engine in Ardour, at least as smooth as the one by Nuendo I think. Hydrogen is very intuitive. But I realise I have much to learn here! I managed to connect System to Ardour on both sides, Ardour to Ardour. Some playing in the Envy24 patchbay and suddenly we had sound. Well done!!

It would be nice to get the sound working in Firefox, so I can watch Youtube tutorials without having to log back into Grub. Dummy sound still shows in System sound. Is there an easy way to do this.

How do I add reverb to the Audio track I just made?

Nice work and thanks again!
PR

---

### Post by cchhrriiss121212 on 2011-01-24
I have the same card, pulse audio does not work with it out of the box. Try the suggestions here for getting pulse audio working (that means system noises, firefox etc.):
[http://ubuntuforums.org/showthread.php?t=1468235]("http://ubuntuforums.org/showthread.php?t=1468235")

All you need to do with envy24 is to set the analogue volume and sample rate, the other settings are optional. You can connect apps and audio streams together with patchage which does the same job as the jack connection window.

---

### Post by pr2 on 2011-01-24
Well done Chris. That did it!

Working well now! Thanks guys! Nice!

---

