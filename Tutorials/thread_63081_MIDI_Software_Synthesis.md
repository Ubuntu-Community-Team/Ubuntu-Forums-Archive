---
title: "MIDI Software Synthesis"
date: 2005-09-06
forum: Tutorials
---

### Post by fishfork on 2005-09-06
The thread is for questions about the [MIDI Software Synthesis HOWTO](https://wiki.ubuntu.com/MidiSoftwareSynthesisHowTo)

---

### Post by fishfork on 2005-09-06
Ask questions here, and the answers will be gradually incorporated into the Wiki page.

---

### Post by sanchico on 2005-09-08
the HOWTO is very clear if you want to use a software synthesis, but I want to use my Sound Blaster Live! hardware synthetizer. what MIDI player should I use? I've tried with other distros and It never runs. I think its beacuse I must load the soundfonts, How can I do it?

---

### Post by zero0w on 2005-09-08
[QUOTE=sanchico]the HOWTO is very clear if you want to use a software synthesis, but I want to use my Sound Blaster Live! hardware synthetizer. what MIDI player should I use? I've tried with other distros and It never runs. I think its beacuse I must load the soundfonts, How can I do it?[/QUOTE]
 Regarding playing MIDI on Sound Blaster Live! and Audigy series, I have written a [how-to for Mandriva distro before](http://mandrivausers.org/index.php?showtopic=22604), recently I have tested it with Sarge but there's something need to be tweaked to make it work. I am installing Ubuntu tonight so I will find out how it goes and once I get it working I will post my feedback here.

Note: A guide for SB Live! hardware synthesizer can be found in this thread:
[http://ubuntuforums.org/showthread.php?t=30963](http://ubuntuforums.org/showthread.php?t=30963)

---

### Post by RastaMahata on 2005-09-18
I hope you read this.

I'm having the strangest bug. I've configured timidity correctly in Hoary, along with Scummvm (using alsa and timidity's midi server on port 128:0). Yesterday, I upgraded to Breezy. Now, when I launch a midi game in scummvm, I cant hear the music, only the voices. If I create a new timidity client, and make scummvm use it (129:0), it all works correctly.

I really hope you can help me :(

---

### Post by jrincon87 on 2005-11-11
I installed Timidity and the freepats and the manual says that only with that installed I should be able to hear some midi file, but I don't. What's the problem?
(Running on a AMD 3400+, 256MB Ram)
Thanks.

---

### Post by fishfork on 2005-11-12
[QUOTE=jrincon87]I installed Timidity and the freepats and the manual says that only with that installed I should be able to hear some midi file, but I don't. What's the problem?
(Running on a AMD 3400+, 256MB Ram)
Thanks.[/QUOTE]
It's difficult to say, without more information. Does normal (ALSA) sound play? (Set XMMS to ALSA output and try to play an mp3.) Are you sure the MIDI file you're using is valid? Do you get any errors or any output at all when you run 'timidity [file.mid]'?

---

### Post by jrincon87 on 2005-11-12
> It's difficult to say, without more information. Does normal (ALSA) sound play? (Set XMMS to ALSA output and try to play an mp3.) Are you sure the MIDI file you're using is valid? Do you get any errors or any output at all when you run 'timidity [file.mid]'?

I normally play all my files in XMMS with the ALSA output. When I run the midi files I don't get any error, it simply doesn't sound. This is a terminal output when I run timidity:
Playing 2600mts.MID
MIDI file: 2600mts.MID
Format: 1  Tracks: 3  Divisions: 1024
Track name: Acoustic Grand Piano
Track name: Instrument2

Yet I don't hear anything.

---

### Post by fishfork on 2005-11-13
You could try some different midi files. Other than that, I've no idea I'm afraid. Perhaps someone else can help?

---

### Post by Snargle on 2005-11-14
I'm achieving terrible performance with timidity.

Even after disabling all the settings in the cfg file, timidity still uses most of my cpu.(Ath XP 1800.)  Why is this?  I remember running a midi sequencer under a 486.

---

### Post by fishfork on 2005-11-14
[QUOTE=Snargle]I'm achieving terrible performance with timidity.

Even after disabling all the settings in the cfg file, timidity still uses most of my cpu.(Ath XP 1800.)  Why is this?  I remember running a midi sequencer under a 486.[/QUOTE]
Weird. I had it running fine on my old AMD K6-2 450, so your hardware certainly should be up to it.

---

### Post by jrincon87 on 2005-11-22
> You could try some different midi files. Other than that, I've no idea I'm afraid. Perhaps someone else can help?

Hey, this is the second time I try to get MIDI on Ubuntu to work. I still don't hear anything. But, I found that timidity does play the files but throughout the wrong sound card. I have two soundcards. Timidity is playing the files through the hw:0,0 (first sound card), and the soundcard I have the speakers plugged into is hw;1,0 (second sound card). Everything is set up to go through the second card (Preferences -> Sound->*2nd sound card*). It seems that Timidity is configured by default to sound through the first sound card. How can I make Timidity to play the files through the second sound card?
Thanks.

---

### Post by jrincon87 on 2005-11-30
> Hey, this is the second time I try to get MIDI on Ubuntu to work. I still don't hear anything. But, I found that timidity does play the files but throughout the wrong sound card. I have two soundcards. Timidity is playing the files through the hw:0,0 (first sound card), and the soundcard I have the speakers plugged into is hw;1,0 (second sound card). Everything is set up to go through the second card (Preferences -> Sound->2nd sound card). It seems that Timidity is configured by default to sound through the first sound card. How can I make Timidity to play the files through the second sound card?
Thanks.

Any ideas? Please, I'm really urged to make the MIDI work (that's the only thing that's preventing me from totally switching to linux)

---

### Post by zoarre on 2005-12-14
[QUOTE=fishfork]Ask questions here, and the answers will be gradually incorporated into the Wiki page.[/QUOTE]

I have questions abvout three errors I get while using timidity with dosbox. I did not install any soundfonts.

After installing timidity as described in the HOWTO, sound began to work in dosbox when run from the terminal. I do still get the following errors, however:
```
ALSA:Can't subscribe to MIDI port (65:0)
MIDI:Opened device:oss
```
1. What does the first error mean and how do I correct it?
2. Why is dosbox using OSS instead of ALSA? Is there a way to correct this? Does it matter?

Also, sound doesn't work when running dosbox from an application launcher. I get the following errors:
```
MIXER:Can't open audio: No available audio device , running in nosound mode.
ALSA:Can't subscribe to MIDI port (65:0)
MIDI:Opened device:oss
```
3. Why do I have to run from the terminal to get sound to work? Is it a permissions issue? How do I fix this?

Any help would be greatly appreciated.

---

### Post by jobezone on 2006-01-14
[QUOTE=zoarre]I have questions abvout three errors I get while using timidity with dosbox. I did not install any soundfonts.

After installing timidity as described in the HOWTO, sound began to work in dosbox when run from the terminal. I do still get the following errors, however:
```
ALSA:Can't subscribe to MIDI port (65:0)
MIDI:Opened device:oss
```
1. What does the first error mean and how do I correct it?
2. Why is dosbox using OSS instead of ALSA? Is there a way to correct this? Does it matter?

Also, sound doesn't work when running dosbox from an application launcher. I get the following errors:
```
MIXER:Can't open audio: No available audio device , running in nosound mode.
ALSA:Can't subscribe to MIDI port (65:0)
MIDI:Opened device:oss
```
3. Why do I have to run from the terminal to get sound to work? Is it a permissions issue? How do I fix this?

Any help would be greatly appreciated.[/QUOTE]
Hi, you'll have to use a customized dosbox.conf file. First, copy /usr/share/doc/dosbox/dosbox.conf.example.gz into your home directory. Gunzip it:
```
gunzip dosbox.conf.example.gz
```, and edit it, go to the [midi] section, and add **128:0** next to **config=** . So it looks like this:
```

mpu401=true
intelligent=true
device=default
config=128:0

```

Now this will be your default dosbox.conf file. I advise you to have a dosbox.conf file inside each game directory, specifically tuned to it. Then, in the game's launcher, make the command be something like this:
```
/usr/bin/dosbox -conf "/home/ines/jogos/Heart of China/dosbox.conf" "/home/ines/jogos/Heart of China/HOC.EXE"
```

You also said "I did not install any soundfonts" . But you must install at least one. ```
sudo apt-get install freepats
```

P.S.-I haven't tested this yet with a midi game in dosbox, but now it won't give you errors.
P.S.S.-Hope these instructions aren't too confusing...

---

### Post by boow on 2006-01-28
I've just installed timidity and it works but the startup script that came with it refuses to work but I am able to start it up like this.

timidity -iA -B2,8 -Os1l -s 44100 &

is anyone else having this problem. 

#!/bin/sh
#
# TiMidity      /etc/init.d/ initscript for TiMidity++
#               $Id: timidity.init,v 1.6 2004/09/30 01:04:04 hmh Exp $
#
#               Copyright (c) 2004 by Henrique M. Holschuh <hmh@debian.org>
#               Distributed under the GPL version 2
#

PATH=/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/bin/timidity
DESC="TiMidity++ ALSA midi emulation"
PMIDI=/usr/bin/pmidi
PIDFILE=/var/run/timidity.pid

set -e

test -x ${DAEMON} || exit 0
test -x ${PMIDI} && pmidi_enabled="true" || pmidi_enabled="false";

. /lib/lsb/init-functions

TIM_ALSASEQ=true
TIM_ALSASEQPARAMS="-iA -B2,8 -Os1l -s 44100"
[ -r /etc/default/timidity ] && . /etc/default/timidity
[ "${TIM_ALSASEQ}" != "true" ] && exit 0
PARAMS="${TIM_ALSASEQPARAMS} -iAD"

START="--start --quiet --exec ${DAEMON} --pidfile ${PIDFILE} -- ${PARAMS}"

case "$1" in
  start)
        [ -d /proc/asound ] || {
                log_warning_msg "ALSA is not active, cannot start $DESC"
                exit 0
        }
        log_begin_msg "Starting $DESC..."
        if start-stop-daemon ${START} >/dev/null; then
                log_end_msg 0
                #if [ $pmidi_enabled = "true" ] ; then
                #       sleep 1
                #       echo -n "Emulating midi on ports: ";
                #       pmidi -l | grep "TiMidity" | cut -f 1 -d ' ' | xargs
                #fi
        else
                log_end_msg 1
                exit 1
                #if start-stop-daemon --test ${START}  >/dev/null 2>&1; then
                #       echo "(failed)."
                #       exit 1
                #else
                #       echo "already running."
                #       exit 0
                #fi
        fi
        ;;
  stop)
        log_begin_msg "Stopping $DESC..."
        if start-stop-daemon --stop --quiet --pidfile ${PIDFILE} \
           --exec ${DAEMON} --retry 10 ; then
                log_end_msg 0
        else
                log_end_msg 1
                exit 1
        fi
        ;;
  restart|force-reload)
        $0 stop
        exec $0 start
        ;;
  *)
    echo "Usage: $0 {start|stop|restart|force-reload}" >&2
    exit 1
esac

exit 0

---

### Post by Zooropa on 2006-03-27
[QUOTE=jobezone]Hi, you'll have to use a customized dosbox.conf file. First, copy /usr/share/doc/dosbox/dosbox.conf.example.gz into your home directory. Gunzip it:
```
gunzip dosbox.conf.example.gz
```, and edit it, go to the [midi] section, and add **128:0** next to **config=** . So it looks like this:
```

mpu401=true
intelligent=true
device=default
config=128:0

```

Now this will be your default dosbox.conf file. I advise you to have a dosbox.conf file inside each game directory, specifically tuned to it. Then, in the game's launcher, make the command be something like this:
```
/usr/bin/dosbox -conf "/home/ines/jogos/Heart of China/dosbox.conf" "/home/ines/jogos/Heart of China/HOC.EXE"
```

You also said "I did not install any soundfonts" . But you must install at least one. ```
sudo apt-get install freepats
```

P.S.-I haven't tested this yet with a midi game in dosbox, but now it won't give you errors.
P.S.S.-Hope these instructions aren't too confusing...[/QUOTE]


Bit of a bump here, but this is a great bit of advice - I was constantly getting the 65 error, but editting the dosbox.config to 128 worked a treat!

---

### Post by Ariod on 2006-06-14
Hey guys,

I followed the instructions and I can play MIDI files using solely Timidity. However, what I need is playing MIDI files within programs such as TuxGuitar (Java-based) or KGuitar. Both won't work properly if they can't play MIDI files.

Do you have any suggestions on how to fix this?

---

### Post by Efnian on 2006-06-23
[QUOTE=boow]I've just installed timidity and it works but the startup script that came with it refuses to work but I am able to start it up like this.

timidity -iA -B2,8 -Os1l -s 44100 &

is anyone else having this problem. 
[/QUOTE]


I have the same problem with my system. It seems that the snd-seq-* -modules aren't automatically loaded at the startup.

---

### Post by function1 on 2006-11-17
I ran through the HowTo, but I did achieve the desired result. I did not install the timidity-patches-eaw package, and I do not think I need to: playing a midi file with timidity on the command line (i.e. `timidity mymid.mid') works. I modprobe'd all the modules listed (snd-seq-device, snd-seq-midi, snd-seq-oss, snd-seq-midi-event, and snd-seq) and then ran `timidity -iA -B2,8 -Os1l -s 44100'. I got the following message: ```
Requested buffer size 2048, fragment size 1024
ALSA pcm 'default' set buffer size 7524, period size 3760 bytes
TiMidity starting in ALSA server mode
Opening sequencer port: 128:0 128:1 128:2 128:3
```
Looks good. I have a look at `pmidi -l':
```
 Port     Client name                       Port name
 14:0     Midi Through                      Midi Through Port-0
128:0     TiMidity                          TiMidity port 0
128:1     TiMidity                          TiMidity port 1
128:2     TiMidity                          TiMidity port 2
128:3     TiMidity                          TiMidity port 3

```
Cool. So then I try to play a midi with pmidi `aplaymidi --port 128:0 mymid.mid' and I hear nothing. No output in the pmidi terminal window, and in the timidity terminal I see: ```
Requested buffer size 2048, fragment size 1024
ALSA pcm 'default' set buffer size 7524, period size 3760 bytes
```
Looks normal to me, but I hear nothing. Again, playing the file directly with timidity as `timidity mymid.mid' works.
I was speaking with someone on the #ubuntu chan on freenode and he recommended that I look at `strace -fF aplaymidi --port 128:0 mymid', the output of which I have pastebin'd at [http://pastebin.com/826804]("http://pastebin.com/826804"). (Note the "<unfinished ...>" bit at the bottom--I had to ctrl+c it, because nothing was happening). I am not sure how a midi session is supposed to work, so I can really only look for explicit error messages in the strace output. I see "No such file or directory" for the files "ld.so.nohwcap' and "/etc/asound.conf". The asound.conf file sounds perhaps like its a bit more generic that just dealing with midi playback, yet audio seems to work fine overall on my system. I did not get anywhere with googling 'ld.so.nohwcap'.

P.S. I am running Edgy on a Thinkpad T60, audio chipset AD1981HD with Intel HDA interface.

---

### Post by dwhsix on 2006-12-22
Any suggestions on getting lmms or rosegarden4 or anything to play back with timidity?  I have timidity running in a command window:

timidity -iA -B2,8 -Os1l -s 44100

and if I use kmid or pmidi, the file plays fine.

If I use lmms or rosegarden4 I can't get anything to play.  For example with lmms I get these errors:

ALSA lib rawmidi_hw.c:231:(snd_rawmidi_hw_open) open /dev/snd/midiC0D0 failed: No such file or directory
cannot open MIDI-device: No such file or directory
Couldn't create MIDI-client, neither with ALSA nor with OSS. Will use dummy-MIDI-client.

Thoughts?

Thanks...

dwh

---

### Post by mandavi on 2007-01-03
I ran all the module commands and to play a file like *timidity myfile.mid* works great, but when i enter the line *timidity -iA -B2,8 -Os1l -s 44100*, I get a:

```
ALSA lib pcm_dmix.c:862:(snd_pcm_dmix_open) unable to open slave
Can't open pcm device 'default'.
Couldn't open ALSA pcm device (`s')
```

So far I didn't experience any problems with the sound at all.

thanks for help...

---

### Post by mandavi on 2007-01-04
problem was somehow solved by rebooting - now the server serves kmid without problems...

---

### Post by ggaaron on 2007-04-23
I made timidity work without problems. Command timidity sth.mid works very good, but when I'm running some other program using midi (kmid for instance), it works very slow... How can I make it's performance better? I need midi support for some guitar programs.

Thanks in advance.

Aaron.

---

### Post by McTek on 2007-06-19
How do I fix this?
> ubu32@ubu32-laptop:~$ timidity '/home/ubu32/Desktop/Midi/ATT10141414.mid' 
/etc/timidity/HSSynthCollectionI.sf2: Permission denied
timidity: Error reading configuration file.
Please check /etc/timidity/timidity.cfg
ubu32@ubu32-laptop:~$ 


---

### Post by AmyRose on 2007-06-20
Uh, you can just install Timidity and edit the /etc/default/timidity file, then run a "sudo /etc/init.d/timidity start" if you want to run Timidity as a daemon.

Doesn't anyone ever check this stuff out?

Also, if you have the lowlatency kernel, I recommend trying QSynth, a nice FluidSynth GUI.

---

### Post by McTek on 2007-06-20
> Doesn't anyone ever check this stuff out?
I followed the HOWTO to the letter.....I thought.

> lowlatency kernel,
Huh?

Somehow I get the feeling I was RTMFed

---

### Post by AmyRose on 2007-06-20
> **McTek said:**
> I followed the HOWTO to the letter.....I thought.
I was saying the HOWTO is by FAR NOT the easiest way to have Timidity running as a daemon.
> **McTek said:**
> Huh?

Somehow I get the feeling I was RTMFed
Well, if you install the package "linux-lowlatency" and reboot, you can have smoother MIDI performance. And you can install "qsynth" and get a nice GUI for FluidSynth. I have switched to FluidSynth because it sounds better than Timidity if you have the lowlatency kernel.

If you want to use SoundFonts, you definitely want to use qsynth/fluidsynth instead.

McTek, your problem is that you are not able to read the sf2 file. Try this command:
```
sudo chmod a+r /etc/timidity/HSSynthCollectionI.sf2
```
to fix this and allow all users to read it.

---

### Post by bmhm on 2007-06-28
[FONT="Verdana"]The path to the eaw-patches has changed, there was an update.

It should now read: 
sudo vim **[COLOR="DarkRed"]/etc/timidity/timidity.cfg [/COLOR]**
```
dir /usr/share/midi/eawpatches
```

Regards[/FONT]

---

### Post by Schuenemann on 2007-07-05
> **bmhm said:**
> [FONT="Verdana"]The path to the eaw-patches has changed, there was an update.

It should now read: 
sudo vim **[COLOR="DarkRed"]/etc/timidity/timidity.cfg [/COLOR]**
```
dir /usr/share/midi/eawpatches
```

Regards[/FONT]

Sorry, can you be more clear? I don't understand. I only got freepats working.

Thanks

---

### Post by Schuenemann on 2007-07-08
I got it working.

It seems that this line:
```
sudo cp /usr/share/doc/timidity-patches-eaw/examples/timidity.cfg /etc/timidity/eawpats.cfg
```
Is not needed anymore, as now the eawpats.cfg is copied by default to etc/timidity/

---

### Post by musicologist1964 on 2007-07-23
> **Schuenemann said:**
> I got it working.

It seems that this line:
```
sudo cp /usr/share/doc/timidity-patches-eaw/examples/timidity.cfg /etc/timidity/eawpats.cfg
```
Is not needed anymore, as now the eawpats.cfg is copied by default to etc/timidity/


Hi,

I followed all the instructions on your page and got midi working first time beautifully.  Thanks.  I can confirm that you don't need the above code, as the patches are installed in the directory /etc/timidity/eawpatches, and the file /etc/timidity/eawpatches.cfg is already created for you.  All I needed to do was change the line in the /etc/timidity/timidity.cfg file to read: "source /etc/timidity/eawpatches.cfg".  This is slightly different to your instructions, as you refer to the file as "eawpats.cfg".

Cheers.

---

### Post by Artemis3 on 2007-07-24
> It will probably complain about JACK not running, but JACK isn't required to run Qsynth. Change the audio output driver to "alsa" if you want to run it without JACK. Once you do this, you should be able to use any MIDI player to play MIDI files.

I don't recommend you do this, as the current (Feisty Fawn) fluidsynth package version contains a bug (fixed in a later version) that will trigger a 100% cpu usage condition, but only if you use the alsa output.


So the sane thing to do is not switch the output to alsa, but instead install qjackctl (jackd) start the daemon from it and then run fluidsynth.

---

### Post by lilbugleboy09 on 2007-08-10
I've installed timidity, but I'm not able to save the changes made to /etc/timidity/timidity.cfg 
It says it's read only?

Edit: Fixed, but now new problem... here's me trying to play my midi file

```
jd@jd-desktop:~$ timidity '/home/jd/Desktop/Trumpet One q 144.mid' 
/etc/timidity/eawpats.cfg: No such file or directory
timidity: Error reading configuration file.
Please check /etc/timidity/timidity.cfg
```

---

### Post by lilbugleboy09 on 2007-08-14
Can anyone help me with this? I really need to play midi files.

---

### Post by lilbugleboy09 on 2007-08-17
Ok i found the problem myself...I can't install the timidity patches
I get this error:
Error dependancy is not satisfiable: eawpatches
anyone know how to fix this?

---

### Post by UphillSkier on 2007-08-22
I need help getting timidity working on my home machine.  It works on my office desktop.  At home I get no sound.  The problem may be associated with having two sound cards.

Here's what I've done most recently. I am running feisty.
```
mullera@happy:~$ uname -a
Linux happy 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

```

I  have two sound cards. 
```
mullera@happy:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: VT82xx [HDA VIA VT82xx], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8738MC6 [C-Media PCI CMI8738-MC6], device 0: CMI8738-MC6 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8738MC6 [C-Media PCI CMI8738-MC6], device 1: CMI8738-MC6 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8738MC6 [C-Media PCI CMI8738-MC6], device 2: CMI8738-MC6 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Right now Card 0 seems to be working.  Rhythmbox works and plays mp3 files.  But I want a midi player.  I removed timidity and then reinstalled
 ```

mullera@happy:~/music/deutscheLieder$ sudo apt-get install timidity
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libt1-5
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  freepats
Suggested packages:
  pmidi
The following NEW packages will be installed:
  freepats timidity
0 upgraded, 2 newly installed, 0 to remove and 17 not upgraded.
Need to get 29.5MB of archives.
After unpacking, 35.8MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://ca.archive.ubuntu.com feisty/universe freepats 20060219-1 [29.0MB]
Get:2 http://ca.archive.ubuntu.com feisty/universe timidity 2.13.2-11ubuntu1 [555kB]
Fetched 29.5MB in 33s (881kB/s)                                                
Selecting previously deselected package freepats.
(Reading database ... 187971 files and directories currently installed.)
Unpacking freepats (from .../freepats_20060219-1_all.deb) ...
Selecting previously deselected package timidity.
Unpacking timidity (from .../timidity_2.13.2-11ubuntu1_i386.deb) ...
Setting up freepats (20060219-1) ...
Setting up timidity (2.13.2-11ubuntu1) ...
 * Starting timidity                                                             * Starting TiMidity++ ALSA midi emulation...                            [ OK ] 


```

I enabled the ALSA sequencer in /etc/default/timidity
```
# Defaults for TiMidity++ scripts
# sourced by /etc/init.d/timidity
# installed at /etc/default/timidity by the maintainer scripts
# $Id: timidity.default,v 1.3 2004/08/07 14:33:26 hmh Exp $

#
# This is a POSIX shell fragment
#

# Enable MIDI sequencer (ALSA), default is disabled
TIM_ALSASEQ=true

# Setting overrides (of /etc/timidity.conf) for the ALSA sequencer daemon
TIM_ALSASEQPARAMS="-B2,8 -Os"

```

Now I try to run timidity
```
mullera@happy:~/music/deutscheLieder$ timidity dervogel.mid 
Playing dervogel.mid
MIDI file: dervogel.mid
Format: 0  Tracks: 1  Divisions: 384
Instrument `acpiano' can't be found.
Couldn't load instrument acpiano (tone bank 0, program 0)
Instrument `acpiano' can't be found.
No pre-resampling cache hit
(Track 1)

```

Nothing happens!  I get no sound, no nothing.  I escape from timidity with a ^C  and wonder what to do.  Can anyone point me in the right direction?

Thanks

---

### Post by pacesie on 2008-01-06
Following
[https://help.ubuntu.com/community/MidiSoftwareSynthesisHowTo](https://help.ubuntu.com/community/MidiSoftwareSynthesisHowTo)
I installed timidity, and
```
timidity mysong.mid
```
played it fine.

But, when I open kmid and configure it to use timidity, it only plays the first note and holds there.

I tried pmidi + timidity, kmid + fluidsynth, the same problem. Seems something is wrong communicating with the midisynth server.

I run 64bit, could this be a problem?

---

### Post by efrens on 2008-08-11
I believe this link here to download eawpatches is dead already.
```
http://www.fbriere.net/debian/dists/etch/misc/deb/
```

Anyone who knows an alternative to this?

---

### Post by schaumkeks on 2008-11-05
> **efrens said:**
> I believe this link here to download eawpatches is dead already.
```
http://www.fbriere.net/debian/dists/etch/misc/deb/
```

Anyone who knows an alternative to this?

Seems the release name etch was removed and directory indexing is not allowed :-(. Use the direct link via right-click and save as:
[eawpatches by fbriere]("http://www.fbriere.net/debian/dists/stable/misc/deb/eawpatches_12-1~fbriere.5_all.deb")

or include a more general line in your sources.list:
```
deb http://www.fbriere.net/debian/dists/stable misc/
```

---

### Post by Mark_in_Hollywood on 2009-01-21
The * Midi*SoftwareSynthesisHowTo page says:

**You may then install the package 'eawpatches' (a 31 MB download). Alternatively, if you don't want to add this repository, you may download the package here: [COLOR="DarkOrange"]http://www.fbriere.net/debian/dists/etch/misc/deb/[/COLOR]**

the link is dead for me as of 1-21-09.

Please tell me how to install the 24 meg patch.

---

### Post by schaumkeks on 2009-01-22
> **Mark_in_Hollywood said:**
> The * Midi*SoftwareSynthesisHowTo page says:

**You may then install the package 'eawpatches' (a 31 MB download). Alternatively, if you don't want to add this repository, you may download the package here: [COLOR="DarkOrange"]http://www.fbriere.net/debian/dists/etch/misc/deb/[/COLOR]**

the link is dead for me as of 1-21-09.

Please tell me how to install the 24 meg patch.

I just updated the URL for eawpatches package. Mentioned this already but forgot to change the HowTo.

---

### Post by schaumkeks on 2009-02-16
I just updated the HowTo with the link for the latest version of eawpatches package 12-1~fbriere.5 for those who do not use the repository.

---

### Post by PMBDaKing on 2009-10-12
I can't get permissions to edit the /etc/timidiy/timidity.cfg file. I am new to Ubuntu and don't know how to gain the necessary permissions. Can someone do a step-by-step on how to edit such files through the terminal?

---

### Post by alainhenry on 2009-10-15
did you try 
sudo gedit /etc/timidity/timidity.cfg
and keying in your user password when the system asks for a password ?

Alain
[www.comitedequartiermessidor.be](www.comitedequartiermessidor.be)

---

### Post by JohnE1 on 2010-03-28
> **schaumkeks said:**
> I just updated the URL for eawpatches package. Mentioned this already but forgot to change the HowTo.

Neither `sudo apt-get install eawpatches` nor Synaptic could find 'eawpatches'. I visited the site and found the verification key and installation instructions. After adding the key, Synaptic found 'eawpatches' and it is installing as I write this.

The verification key and instructions to install it can be found at: [http://www.fbriere.net/debian/](http://www.fbriere.net/debian/)

As of this date, Sun March 28, 2010 03:17, the instructions read (I'm quoting the web page above):

"How to verify package signatures

All packages in this collection can be verified against my OpenPGP public key. (Of course, since this key isn't signed by anybody else at the moment, the web of trust doesn't extend far, but it's somewhat better than nothing.)

To enable this verification, you need to add this key to apt's keyring. Here's one of the various possible ways to do this:

wget -O- [http://www.fbriere.net/public_key.html](http://www.fbriere.net/public_key.html) | sudo apt-key add -

Running apt-get update will then verify this archive's signature.

(See Debian Wiki for a thorough explanation of secure apt.)"


Hope this helps others as it helped me!

John

---

### Post by kblood on 2012-05-24
Hello,

I am trying to get TiMidity to start on boot on Ubuntu 12.04.
I followed the instructions on the Help wiki, and when I start it manually, it works, and I can use TuxGuitar to play through the new Midi ports.

I start it manually with, per the wiki:
timidity -iA -B2,8 -Os1l -s 44100

I also added the modules to /etc/modules, and changed /etc/default/timidity line:
TIM_ALSASEQ=true

Can anyone help? Thanks!

---

### Post by DemonSharkKisame on 2012-05-26
> **kblood said:**
> Hello,

I am trying to get TiMidity to start on boot on Ubuntu 12.04.
I followed the instructions on the Help wiki, and when I start it manually, it works, and I can use TuxGuitar to play through the new Midi ports.

I start it manually with, per the wiki:
timidity -iA -B2,8 -Os1l -s 44100

I also added the modules to /etc/modules, and changed /etc/default/timidity line:
TIM_ALSASEQ=true

Can anyone help? Thanks!
Wish I could, but I'm actually running into the same problem myself. :lol:

---

### Post by BozoDel on 2012-07-31
> **DemonSharkKisame said:**
> Wish I could, but I'm actually running into the same problem myself. :lol:

Same here.

Also, something strange I noticed. When I edit /etc/default/timidity, it looks like this:

```
# uncomment to override enabling triggered by availability of timidity-deamon
# TIM_ALSASEQ=false
```But, according to the wiki, it should be

```
# TIM_ALSASEQ=true
```Anyway, I changed it to true and uncommented it. Just thought it should be clearer.

I'm using Linux Mint 12 Mate, btw.

UPDATE: Well, it was working when I tried manually. Then I tried to make it work on startup. It didn't. Now I changed /etc/default/timidity and /etc/modules to the way they were before, but timidity just won't work anymore. Beautiful.

ANOTHER UPDATE: then I struggled with Qsynth, to no avail, then I uninstalled and reinstalled TiMidity, and it's working again. I'll just be satsified with that.

---

### Post by BozoDel on 2012-08-02
Good golly, now it works when I test it with some random midi, but not the server. I didn't change a thing from the time it was working.

EDIT so very sorry about this post. Turns out timidity WAS working properly, but DOSBox wasn't, cause I had overwritten some part of the config file. It's alright now.

---

### Post by anutha on 2013-03-30
I am not able install the package 'eawpatches'...and the link provided on [https://help.ubuntu.com/community/Midi/SoftwareSynthesisHowTo](https://help.ubuntu.com/community/Midi/SoftwareSynthesisHowTo)

is 
You may then install the package 'eawpatches' (a 31  MB download). Alternatively, if you don't want to add this repository,  you may download the package here (use right-click and save link as): [http://www.fbriere.net/debian/dists/stable/misc/deb/eawpatches_12-1~fbriere.5_all.deb]("http://www.fbriere.net/debian/dists/stable/misc/deb/eawpatches_12-1%7Efbriere.5_all.deb") 
Once you have installed the package, change the following line in the /etc/timidity/timidity.cfg file:


which does not work anymore...i have been to trying to get the timidity work...and got lots different information on different links but none is working...and they are confusing too:mad:.
can any one  help me getting it worked...:)
anutha

---

### Post by schaumkeks on 2013-04-08
eawpatches location is now fixed.

---

### Post by imachine on 2013-08-23
Running 13.04 amd64, also seems that it doesn't work for me to run the server.

I added myself to group 'audio' and when I run the timidity command as my user, I can successfully play DosBox games with midi through eawpats (oh the joy of midi :guitar: I'm reliving some of my past games completely anew - The Lost Vikings being one example of great thinking, how it can use SOUND effects via MIDI interface thus enabling me to skip my sbpro config alltogether - that's great programming btw, on two floppies it fits).

Still no go with the config as server with groups.

I can configure in /etc/default/timidity that the user it runs as is my user then it works obviously that is not desired in a multi user setup... so I'd think. but that doesn't work directly either, to my surprise.

It only works if I start it manually as my user. Weird!

Maybe it's to do with timidity not having libao (pulseaudio) support compiled in by default on ubuntu?

---

