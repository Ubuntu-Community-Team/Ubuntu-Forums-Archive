---
title: "Record Flash sound output - jack - how ?"
date: 2010-06-01
forum: Ubuntu Studio
---

### Post by interzoneuk on 2010-06-01
Hi.

Every since I have had my new desktop (with HDA sound) I have never been able to directly record my sound cards output as I do not have dmix/mix in alsa - its annoying really as I have a old 1.7G desktop with rubbish onboard sound that can ...

It was suggested to try jack so I thought that the easiest way would be to try ubuntu studio.

I have managed to record Audacious's output - using jack using audacity (with jack) - this works well, I select the program to record - so for the first time I have managed to record my soundcards output.

My issues are with recording standard alsa.

As soon I I start jack no alsa sound will play - is this normal ?

If not have I missed something?

As an exampple I am trying to record sound from flash (using beta amd64 flash) - this has no jack output...  How do I do it ?

All i'm trying to do is to be able to record what you can hear from the sound card - there has to be an easier way. 

Any suggestions will be very welcomed - this used to be so easy on older hardware....





Here is some soundcard  info (from alsa)

--------------------------------------
For example - in KDE mixer I have the following options for input source
- Mic
- Front Mic
- Line
- CD

= none of these record soundcard.

As an example I am trying to record in Audacity - It doesn't matter what option I choose as the recording device - all I get is nothing or static.
The options I have are
- Default
- spdif
- HDA Nvidia :ACL888 Analog (hw0,0)
- HDA Nvidia :ACL888 Digital (hw0,1)
- HDA Nvidia :ACL888 Analog (hw0,2)

I am just trying to record my soundcard's output, not mic / line in - I have muted mic and linein - same.

--------------------------------------

---

### Post by thorgal on 2010-06-01
hello,

you have a few options:

1- get this: 
[http://old.nabble.com/-ANN--jack-enabled-flash...-td22796276.html](http://old.nabble.com/-ANN--jack-enabled-flash...-td22796276.html)

and compile as described here
[http://linuxmusicians.com/viewtopic.php?p=9131#p9131](http://linuxmusicians.com/viewtopic.php?p=9131#p9131)

2- or, for a more permanent ALSA to jack bridge, try this:
[http://alsa.opensrc.org/index.php/Jack_and_Loopback_device_as_Alsa-to-Jack_bridge](http://alsa.opensrc.org/index.php/Jack_and_Loopback_device_as_Alsa-to-Jack_bridge)

---

### Post by cchhrriiss121212 on 2010-06-01
Also: you could just download the flash video to your /home folder (use downthemall or some other firefox extension) and play it using vlc, which has a jack output option under audio output.

---

### Post by trulan on 2010-06-01
Yet three more options:  (we'll get you confused yet!)

1. If you've got the flash video downloaded to you home folder anyway, load it up in WinFF and convert it to an audio file.  Okay, that's not exactly recording, but it's actually a quicker way of getting the job done.

2. Install the Pulse Audio and Jack packages from this ppa:
[https://launchpad.net/~falk-t-j/+archive/lucid]("https://launchpad.net/%7Efalk-t-j/+archive/lucid")
This will add Pulse audio support for Jack.  A warning:  I had trouble downgrading from this ppa.  It changes some configuration files and Pulse Audio (ie, all non-jack sounds) were non-functional until I re-installed these packages.  Consider this option experimental.

3. Purchase a cord with 1/8" stereo male plugs on each end and plug your line out into you line in.  Not exactly a glorious solution, but again, it can be a very effective way to do the job.

And yes, when you start Jack from Jack Control, Pulse Audio (Ubuntu's sound server) is suspended, so all non-jack sounds are disabled until Jack Control is closed.  When using FalkTX's packages (#2 above) Jack will be started automatically (if everything behaves) and absolutely every sound will be run through Jack.  This will definitely do the job if you can get it to work.  #2 in thorgal's post would also be an excellent permanent solution to your problem, alas I have so far failed to get it working (due I think to issues with my custom kernel.)

---

### Post by thorgal on 2010-06-01
hi trulan, what's your issue with the snd-aloop module ?

if you have an error at modprobe similar to this one:

```

FATAL: Error inserting snd_aloop (/lib/modules/2.6.32-4-686/kernel/sound/drivers/snd-aloop.ko): Invalid module format

```

and a dmesg output with stuff like:

```

[44975.889756] snd_aloop: no symbol version for module_layout

```

or other kind of error messages, try to force the module loading:

```

sudo modprobe -f snd-aloop

```

see if this help. If it does, then I suggest you put this command in /etc/rc.local

---

### Post by trulan on 2010-06-01
thorgal - I thought you'd never ask!

Here's my setup:
Debian (AVLinux) with self-compiled 2.6.33.4-rt20 kernel.
Alsa version 1.0.21 or .22 - some alsa packages say one thing and some say another.

Now I need to say right up front that the only version of alsa-driver that will build on 2.6.33-rt is the latest, 1.0.23.  But it does build, and yes, the module fails to load unless I force it, as you suspected.  So I added that line to rc.local, and as you can see,
```
trulan@avlinux:~$ lsmod | grep aloop
snd_aloop               3904  0 
snd_pcm                45977  4 snd_aloop,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd                    31435  15 snd_aloop,snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

```
```
trulan@avlinux:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Loopback [Loopback], device 0: Loopback PCM [Loopback PCM]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Loopback [Loopback], device 1: Loopback PCM [Loopback PCM]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7

```
It looks like we are all good so far.  But that's about as far as I get.  When I try this,
```
trulan@avlinux:~$ mplayer -ao alsa /home/trulan/silence.mp3 
MPlayer SVN-r30656 (C) 2000-2010 MPlayer Team
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/trulan/silence.mp3.
Audio only file format detected.
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
[AO_ALSA] alsa-lib: pcm_hw.c:1293:(snd_pcm_hw_open) open /dev/snd/pcmC1D0p failed: Invalid argument
[AO_ALSA] alsa-lib: pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
[AO_ALSA] Playback open error: Invalid argument
Failed to initialize audio driver 'alsa'
Could not open/initialize audio device -> no sound.
Audio: no sound
Video: no video


Exiting... (End of file)

```
As you can see it fails to play anything.  If I remove the -ao switch from that last command, I get playback through my system speakers.

And that's as far as I've gotten.  I'd love to make it work, though I don't particularly need this functionality.

---

### Post by thorgal on 2010-06-02
hi trulan,

you're almost there. I corrected the howto with a new .asoundrc and removed the ugly mplayer hack (which was needed  because of a non optimal .asounrc). Have you checked the latest version of the howto ?

---

### Post by trulan on 2010-06-02
I did, and I'm using a copy/paste of the .asoundrc you put on there.  But anything I try to do with the loopback device fails with an 'invalid argument'.  Like this:
```
trulan@avlinux:~$ alsa_in -j cloop -dcloop
ALSA lib pcm_dsnoop.c:593:(snd_pcm_dsnoop_open) unable to open slave
Capture open error: Invalid argument
```If I try to play a file with mplayer, Alsa will fail,
```
trulan@avlinux:~$ mplayer /home/trulan/silence.mp3
(...insert joystick warnings here ;) )
Playing /home/trulan/silence.mp3.
Audio only file format detected.
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
[AO_ALSA] alsa-lib: pcm_hw.c:1293:(snd_pcm_hw_open) open /dev/snd/pcmC1D0p failed: Invalid argument
[AO_ALSA] alsa-lib: pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
[AO_ALSA] Playback open error: Invalid argument
Failed to initialize audio driver 'alsa'
```..and then it goes on to try all the various sound servers, settling either on Jack if it is running or OSS if it is not, and it proceeds to successfully play the file.  But anything Alsa tries to do fails with the same 'invalid argument'.

I am suspicious that this is failing for me because the loopback driver is from a different version of alsa than is on my system.  I guess I ought to try rolling back to 2.6.31.rt so the older alsa-driver will build.  I'll let you know what happens.

---

### Post by thorgal on 2010-06-02
yeah, must be a backward incompatibility. Some of it belongs to the alsa-driver, some to libasound2 (the user space API). You can also check which version of libasound2 you have installed, and which version ALSA reports in /proc/asound/version

---

### Post by interzoneuk on 2010-06-02
Thank you to everybody, the combination of this thread and one at arch forums - [http://bbs.archlinux.org/viewtopic.php?pid=765075](http://bbs.archlinux.org/viewtopic.php?pid=765075) helped in enabling me to record sound.

Particular thanks to thorgal for writing the howto and the asoundrc file - In this day and age this really should be a lot easier...


Trulan: I was having the same issue as you, i.e :-

[AO_ALSA] alsa-lib: pcm_hw.c:1293:(snd_pcm_hw_open) open /dev/snd/pcmC1D0p failed: Invalid argument

The really hand-bangingly annoying thing was it worked at first in Ubuntu Studio, but after rebooting never got it to work again.

I set up Arch and the same thing happened, i.e it worked , after rebooting it never did again.

I found out why though....

In my case after successfully getting it to work I  setup so that the snd-aloop module would automatically start on boot (in ubuntu /etc/modules) - this is a bad idea !

- the reason why its a bad idea it that it causes loopback to be the default soundcard, try using alsamixer and see if loopback is the default for you - this would ruin the asoundrc (and explain why alsa isn't working)

As soon as I disabled the auto loading of the module (i.e I used sudo modprobe snd-aloop before starting qjackctl) after rebooting it now always works...

I added the modprobe line to /usr/local/bin/loop2jack (i added  %audio ALL = NOPASSWD: /sbin/modprobe to sudoers..)


EDIT: Ignore the part about loading the module in  /usr/local/bin/loop2jack

- when I load the module that way for some weird reason that game me (loud)  static....  

I now auto load the module in an init script I created in /etc/init.d/snd-aloop and got it to modprobe the module, I got it to start late (99) on runlevel 2

I have also got qjackctl to autoload and autostart when loading the desktop - everything works really well - I am running the preempt kernel and now everything is working fine I never have any xruns at all.

Thanks everybody.

(btw I got it working in Ubuntu Studio, haven't tried this in Arch yet)

This should go on the ubuntu wiki, its really useful.

---

### Post by thorgal on 2010-06-03
hey! that's great :)

Sorry it took some more hacking to get it to work! You see, I have usually no .asoundrc on my system, and I compiled the kernel myself, including snd-aloop, so all was fine from the start. I don't understand why this module is not compiled by default in any kernel (be it RT or not). It is a useful virtual device, not only for a jack environment.  And it can stay unloaded if not needed (takes hardly any space anyway).

But to check that normal desktop environments should also take advantage of this trick, I tried it on my laptop. It runs debian sid, KDE4, with a sidux kernel I believe. I compiled the loop module against this kernel (linux-headers) by picking alsa-driver-1.22.1 (from memory) which was the version reported in /proc/asound/version

This laptop has an intel audio chip (ICH5) using snd-intel8x0. I have no user asoundrc either, this audio chip just works out of the box. There is NO pulseaudio as debian does not include it by default (I find it wise ...). Anyway, after I compiled the module, I could not load it due to ALSA version mismatch (bugger!). So I forced the module loading as I said to trulan. It worked fine. Then I tried the loop2jack script of mine from qjackctl, it all worked fine. Next, I added the command

```

modprobe -f snd-aloop

```

in /etc/rc.local

I rebooted, and all was fine again.

Since I am not using jack all the time on this laptop, only for the occasional ardour recording or some guitarix fiddling, I added another automated action in qjackctl. First I save the asoundrc into $HOME/.asoundrc_aloop. Then, in qjackctl's options, **on server startup**, I added

```

cp $HOME/.asoundrc_aloop $HOME/.asoundrc

```

(replace $HOME by your /home/username)

Since the loop2jack script is executed **after the server startup**, it will use the new ALSA default. I only restore the original asoundrc (in my case, I remove it since I did not have any) **on server shutdown**:

```

rm -f $HOME/.asoundrc

```

If jack or qjackctl crashes, well, yeah, I have to think about it and clean up by hand. That's why this loop trick is best in a pure jack environment (like firewire audio based PCs which can only use jack).

---

### Post by trulan on 2010-06-03
Well, everything worked like a charm using 2.6.31-rt and alsadriver 1.0.22.1.  After all my problems with this the other day it seemed really easy - it just worked!  Loading snd-aloop via /etc/rc.local did not cause any problems either - except I get no sound output if Jack isn't running, but I think that makes sense now.  (What was confusing about that was that at first, when snd-aloop wasn't working, my sound output worked - but that was because Alsa would fail and the system would default to OSS.  Now with snd-aloop functional, everything just gets played to the loopback device, which of course isn't hooked up to anything unless Jack is up and running.)

Unfortunately, no success with 2.6.33-rt.  Only alsadriver 1.0.23 will compile against it, and snd-aloop compiled against 2.6.31-rt does not work in it either.  So, I guess if I want to use this trick under that kernel I'll either need to upgrade Alsa (scary) or figure out how to include snd-aloop when building my kernels.

Where is that in the config file anyway?  I was looking for it but couldn't find it.

---

### Post by thorgal on 2010-06-03
after browsing the kernel git tree (at least 2.6.32, 33 an 34), it looks like this module is simply not part of the kernel source. I must have compiled ALSA from outside when I compiled 2.6.32 for myself, don't remember now. But no loopback device in the kernel unless it is located somewhere else(I compared the alsa-driver source and the kernel tree under 'sound').

by the way, trulan, you can look at my previous post about temporary use of jack and asoundrc automation.

---

### Post by thorgal on 2010-06-09
@trulan,

maybe you can get a little inspired by my experience with 2.6.33.5-rt22:

[http://linuxmusicians.com/viewtopic.php?p=12754#p12754](http://linuxmusicians.com/viewtopic.php?p=12754#p12754)

---

### Post by trulan on 2010-06-09
Looks inspiring indeed!  Though it will be a day or two before I'll have a chance to really play with it...

It looks like the symlink to 'generated' must have been the key to getting alsa-driver 1.0.22 to build.  1.0.23 builds without that.  But currently, I have upgraded my alsa packages to 1.0.23 from the Debian Sid repos, and everything but the loopback driver is working.  Thanks again for all your work on this!

---

### Post by trulan on 2010-06-11
And, success!  I followed "the hard way" on your tutorial and all is well.  Compiled alsa-driver 1.0.23 with this configure line:
```
./configure --with-cards=hda-intel,loopback,hrtimer --with-oss=yes --with-sequencer=yes
```
Which completed with no errors, as did 'make'.  Then I held my breath and did 'make install', and rebooted.  It still didn't work and I went off to work.  This evening, I re-read your tutorial and saw something new:
```
sudo alsa force-reload
```
Whether that did anything that a reboot didn't, I don't know.  But this time modprobe snd_aloop completed without any errors, and without being forced.

The rest was easy.

I was a bit disappointed by the quality of -q 1 (for music playback), and surprised by how much cpu usage increases when that setting is increased.  (A firepod at 64 frames takes around 9% cpu on my machine, setting the quality to 3 adds another 5 or 6% cpu load).  So the needed quality and system load may need to be taken into account when using this.

But thanks Thorgal for the excellent guide, and for yet another useful Linux audio trick!

---

