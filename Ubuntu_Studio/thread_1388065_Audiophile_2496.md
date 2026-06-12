---
title: "Audiophile 24/96"
date: 2010-01-22
forum: Ubuntu Studio
---

### Post by ghed on 2010-01-22
Need help to install my sound card Audiophile 24/96. I have checked many threads but none of them seems to help me. The card is ok, it works with OSS, WXP but not on ALSA applications.:confused:

---

### Post by RaumTrug on 2010-01-22
you don't bring enough info...please at least tell us which version of ubuntu you use (i.e. 9.10, 9.04, 8.04...), what you have altered (uninstall pulse or whatever), wether jack does work or not...

in case you're using 9.10:

my first bet is lacking support for m2496 with pulse. look here: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/63](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/63)
create/edit the 2 files, then go to the system menu -> preferences -> sound/audio and select something with analog out.

be aware that pulse in 9.10 is buggy as /$&"§, I deinstalled it, running pure alsa now happily.

some alsa (as opposed to pulse/pulse emulating alsa) programs won't like pulse; you can stop it by creating a text file "~/.pulse/client.conf" with "autospawn=no" as content, and then using "pulseaudio -k" in a terminal, then running your alsa prog when the sound control icon in the taskbar is gone. when finished, you can restart pulse to have browser/mp3 sound working again with "pulseaudio -D" in a terminal. there can be done more, but try this first to see if your card is working at all :P

[edit] hmm, you said you've tried to apply other fixes from other posts...please list (in the order you've applied) the changes you did (linking the threads you've followed if possible) so we have any chance to help you. I assume you'd like to use jack or stuff like lmms, because this forum is about production and not general sound output issues.

---

### Post by ghed on 2010-01-23
I run Ubuntu 9.10, the problem is that the computer does not find the soundcard at all. I dont know what PULSE is. After all trial and error it seems that it is a total error. the command aplay results in :no soundcard found....

Today I did a total reinstallation of the system, UBUNTU 9.10, then the system found the card

[COLOR=Blue]h@h-desktop:~$ aplay -l
**** Lista över PLAYBACK hårdvaruenheter ****
kort 0: M2496 [M Audio Audiophile 24/96], enhet 0: ICE1712 multi [ICE1712 multi]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0

[COLOR=Black]But still no sound. Is there a solution to this problem?

If it is not, is there anyone who know if there is a soundcard with MIDI that works on Ubuntu, which is on sale (on [http://www.thomann.de/se/index.html?track=rmsarcar.com](http://www.thomann.de/se/index.html?track=rmsarcar.com)). Before I bought this card I looked in the listings of supported soundcards on the homepage of ALSA [http://www.alsa-project.org/main/index.php/Matrix:Vendor-MAudio](http://www.alsa-project.org/main/index.php/Matrix:Vendor-MAudio). Now I know that it gives wrong information.  [/COLOR]
[/COLOR]

---

### Post by RaumTrug on 2010-01-23
man, cool down: the card is detected, and also loaded by alsa. look at the link in my post above on how to get "pulseaudio" working. see, alsa is the low-level sound card driver (i.e. grants direct access to the pcm inputs/outputs). alsa also has some mixing/converting stuff preloaded, but that isn't active while pulse is running. pulse (pulseaudio) is a background program that mixes different applications together, and routes the sound to your soundcard(s). some programs use pulse directly (mainly gstreamer based applications, and some few others), while most use the alsa interface, and here pulse does a "bad job" in my opinion sometimes, but more on that later. when pulse is running, it is used by default also by all alsa apps.

as I said, with ubuntu 9.10 the analog in/outputs (the rca jacks on the card) with pulseaudio aren't working by default: see the link in the above post (or here: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/63](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/63)) and do what is said there, or come back & ask how to do it, if you don't understand what is written there. it will make pulseaudio work for the analog outputs, to get some standard mp3 player, firefox/flash or whatever sound working. remember to restart the pc after creating the 2 text files & setting "analogue out" (then the 5.1,7.1 etc digital stuff in the sound preferences should have disappeared and be replaced with analog entries). you might have to use volume of each _application_ once, to get the sound up, or mute/unmute _in the application_ (if possible) - that did it for me with most stuff!

once pulse is working (or not) and you find a prog. that is really sucking bad with pulse, do the "client.conf" + "pulseaudio -k" stuff mentioned above, and try again. now the pulseaudio stuff is not running, and the prog. will use the alsa interface!

but first: have you tried using "jack" and got any sound from it? you should try that first, install "qjackcontrol", or also called "Jack Control" or whatever? try to get jack up running (hmm, just untick "realtime" in options, select the ice1712 as "interface", apply, and then hit the start button...will give crackles, but is ok as a test for the card working at all!) and then start a prog that's capable of interfacing with it - say aqualung as mp3 player is a good test for a start. (however a little complicated)

I've got the same card up on 9.10, and I get dope sound from it. required some hacking, but nothing "serious". if you don't really understand something here, please ask before trying blindly.

in case nothing above gives any sound, please do "lspci | grep ICE1712" in a terminal, there's rumors around about newer versions of the card that won't work with alsa at all.

the alsa matrix lists it, because it's working with the alsa drivers normally. but just not with pulse in 9.10 without the fix above. see, linux is no big company that buys infos from hardware manufacturers and whips/pays many programmers to get it working foolproof, but most stuff is done on voluntary basis mostly without payment. that means it is not always perfect, and not always foolproof. but it also is free: you don't pay for it, and you can see the sourcecode. that's it. peace.

---

### Post by ghed on 2010-01-24
I am calming down. Gives it a new try. This is what is done.
1. Logged in as root, with the rigt to write in root library (is it possible to give the right to my own login?).
2. Opened the link [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/63](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/63)
3. made the files  /etc/udev/rules.d/ice1712-pulseaudio-workaround.rules
and
4. /usr/share/
pulseaudio/alsa-mixer/profile-sets/via-ice1712.conf wit the contents from  [http://launchpadlibrarian.net/34620379/via-ice1712.conf](http://launchpadlibrarian.net/34620379/via-ice1712.conf)
5. Restarted the computer
6. Yes !! it is sound in filmplayer, rythmbox and firefox.

Thanks a lot for the help.

Now I am going to try sound in!!!
I was not lucky, niether soundrecorder or Audacity got any sound in

[URL="http://launchpadlibrarian.net/34620379/via-ice1712.conf"]
[/URL]

---

### Post by RaumTrug on 2010-01-24
congrats!

sorry, can't help with generic sound in via alsa or pulse, for recording (clean guitar preamp plugged into the input rca's) I always use jack, as it's possible to apply fx in realtime to the guitar sig & record the clean & the effected signal simultaneously...the card really likes my computer, I'm able to run jack with latencies < 1ms, playing feels like a normal guitar amp!

I'm not using pulse anymore as it caused problems (heavy cpu usage/dropouts) with my lame duck pc, but have you tried padevchooser or pavucontrol (or whatever they are called)...? I think you can choose an input device somewhere (must enable an input&output device as main dev, and then the right device in the input tab), and you'll also have to set the input volume somewhere. but can't help further, no pulse here...maybe someone else?

btw, in the package "alsa-tools-gui" there is an alsa level mixer prog called "envy24control", which is a nice too to control the cards options (much better than alsamixer, install the package, then the envy24control prog is in the programs->multimedia main menu!).

---

### Post by ghed on 2010-01-24
Hello. Loaded the controler envy24, changed the in and outputs I also changed the units (soundcard) in Audacity, yes !!! managed to record sound into the program. Things are going the right way at the moment.:D

---

### Post by tgalati4 on 2010-01-24
Those are decent cards.  The ice1712 is a decent chip for home use and M-Audio preamps and switching make it a decent card for linux use.  It does take some fiddling to get it to work, but it's worth it.

---

### Post by horaz on 2010-01-25
Dear Mr RaumTrug, 
finally I found people like you.
I got an Audiophile 24/96, too, and i found - before reading you - that page [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/63](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/63)
I read, I printed. I tried. Consider I am Italian, so my english is not so good, I think. I ADDED 2 lines, as written in the link, in the file /etc/pulse/default.pa using "sudo gedit". Now, here I read your "pupil" ;) Ghed *made* some files: "made the files  /etc/udev/rules.d/ice1712-pulseaudio-workaround.rules".
This confused me.
If you think it should be enough, I'll tell you that my skype on ubuntu 9.10 works perfectly, as the jack with midi files, in rosegarden.
BUT: I really can't hear ANY sound in other ways. No Youtube, no mp3 and so on.
I use Ubuntu since only one year. I really can't understand all this.
Thank you for reading
Horaz
PS: I tried to stop pulse, but I don't know this: "[...]can stop it by creating a text file "~/.pulse/client.conf", I mean, that strange sign that spanish people use. Thank you again.

---

### Post by RaumTrug on 2010-01-25
the "~" sign is a shortcut for "/home/username/". with using it in any file name path, you direct it to the current user's home directory. so "~/.pulse/client.conf" is in reality, for example for me with username "traumflug": "/home/traumflug/.pulse/client.conf"

you can create/edit the file for example with <alt>+<f2> (execute program), or from a "terminal", and then enter "gedit ~/.pulse/client.conf". then type in / copypaste "autospawn=no", and save the file! it is for telling pulseaudio not to "respawn" itself again automatically, i.e. if you kill pulse without it, it will immediately start again without that file!

now when you enter "pulseaudio -k" in a terminal (or execute with alt+f2), pulseaudio is shut down (you see that the loudspeaker icon in the top bar vanishes). you can then use programs, that don't "like" pulse. with "pulseaudio -D" you start pulse again for normal multimedia stuff.

as for the ...63 link above: it is one of the possible "sollutions" for the no generic multimedia sound/pulseaudio problem, and I think it is the best!

note you have to create 2 files, like with the "client.conf", you just have to start gedit with "sudo" or "gksudo" to be able to save the files, as they're in the system, and not your home directory.

for example "gksudo gedit  /etc/udev/rules.d/ice1712-pulseaudio-workaround.rules", enter your password, and the editor starts. you then put the first 7 lines in there:

```

SUBSYSTEM!="sound", GOTO="ice1712_end"
ACTION!="change", GOTO="ice1712_end"
KERNEL!="card*", GOTO="ice1712_end"

SUBSYSTEMS=="pci", ATTRS{vendor}=="0x1412", ATTRS{device}=="0x1712", ATTRS{subsystem_vendor}=="0x1412", ATTRS{subsystem_device}=="0xd634", ENV{PULSE_PROFILE_SET}="via-ice1712.conf"

LABEL="ice1712_end"

```safe the file, close, and open another editor from terminal with "gksudo gedit /usr/share/pulseaudio/alsa-mixer/profile-sets/via-ice1712.conf"

now put this in there:

```
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as
# published by the Free Software Foundation; either version 2.1 of the
# License, or (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software Foundation,
# Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA.

; Via ICE1712 multi-channel audio chipset
;
; This chipset has up to four stereo pairs of input and four stereo pairs of
; output, named channels 1 to 8. Also available are separate S/PDIF stereo
; channels (input and output), and a separate "system-out" stereo jack that
; supports 6-channel hardware mixing.
;
; The S/PDIF stereo channels can be controlled via the mixer for hw:0, and
; additionally, the 8 main outputs can be loop-routed to a separate stereo
; input pair, available as channels 11 and 12.
;
; Many cards available from vendors do not expose all channels from this chip
; to an external port, which effectively reduces the number of channels that
; are useful to the user. However, the ALSA driver still exposes all channels
; even if they are not connected.
;
; We knowingly only define a subset of the theoretically possible
; mapping combinations as profiles here.
;
; See default.conf for an explanation on the directives used here.

[General]
auto-profiles = no

[Mapping analog-mch-in]
description = Analog Multi-Channel Main Input
device-strings = hw:%f,0
#channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe,side-left,side-right,aux0,aux1,aux2,aux3
channel-map = aux0,aux1,front-left,front-right,aux2,aux3,aux4,aux5,aux6,aux7,aux8,aux9
direction = input

[Mapping analog-mch-out]
description = Analog Multi-Channel Main Output
device-strings = hw:%f,0
#channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe,side-left,side-right,aux0,aux1
channel-map = front-left,front-right,aux0,aux1,aux2,aux3,aux4,aux5,aux6,aux7
direction = output

[Mapping digital-stereo]
description = Digital Stereo Input/Output
#device-strings = hw:%f,1
device-strings = iec958:%f
channel-map = left,right
direction = any

[Mapping analog-system-out]
description = Analog Stereo System-Out
device-strings = hw:%f,2
channel-map = left,right
direction = output


[Profile output:mch]
description = Multi-Channel Output Active (Digital Disabled)
output-mappings = analog-mch-out analog-system-out
input-mappings =
priority = 90
skip-probe = yes

[Profile output:mch+input:mch]
description = Multi-Channel Input/Output (Digital Disabled)
output-mappings = analog-mch-out analog-system-out
input-mappings = analog-mch-in
priority = 100
skip-probe = yes

[Profile output:spdif]
description = Digital Output (Multi-Channel Disabled)
output-mappings = digital-stereo analog-system-out
input-mappings =
priority = 80
skip-probe = yes

[Profile output:spdif+input:spdif]
description = Digital Input/Output (Multi-Channel Disabled)
output-mappings = digital-stereo analog-system-out
input-mappings = digital-stereo
priority = 90
skip-probe = yes

[Profile output:system]
description = System Output Only
output-mappings = analog-system-out
input-mappings =
priority = 60
skip-probe = yes

```this is what ghed used, I had used this with success (as alternative):

```

# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as
# published by the Free Software Foundation; either version 2.1 of the
# License, or (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software Foundation,
# Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA.

; M-Audio Delta Audiophile 2496
;
; This card, based on the Via ICE1712 chipset, has two stereo audio channels
; (1 in and 1 out) and a separate S/PDIF digital stereo channel. Like with
; all ICE1712-based cards, this is exposed by ALSA as a single 10-channel
; device with some of the channels not connected.
;
; See default.conf for an explanation on the directives used here.

[General]
auto-profiles = no

[Mapping analog-stereo-in]
description = Analog Stereo Input
device-strings = hw:%f,0
channel-map = front-left,front-right,aux0,aux1,aux2,aux3,aux4,aux5,aux6,aux7,aux8,aux9
direction = input

[Mapping analog-stereo-out]
description = Analog Stereo Output
device-strings = hw:%f,0
channel-map = front-left,front-right,aux0,aux1,aux2,aux3,aux4,aux5,aux6,aux7
direction = output

[Mapping analog-digital-stereo-out]
description = Analog/Digital Stereo Output
device-strings = hw:%f,0
channel-map = front-left,front-right,aux0,aux1,aux2,aux3,aux4,aux5,front-left,front-right
direction = output

[Mapping digital-stereo-out]
description = Digital Stereo Output
device-strings = hw:%f,0
channel-map = aux0,aux1,aux2,aux3,aux4,aux5,aux6,aux7,front-left,front-right
direction = output

[Mapping digital-stereo-in]
description = Digital Stereo Input
device-strings = hw:%f,0
channel-map = front-left,front-right,front-left,front-right,front-left,front-right,front-left,front-right,front-left,front-right,front-left,front-right
direction = input

[Mapping digital-stereo]
description = Digital Stereo Input/Output
#device-strings = hw:%f,1
device-strings = iec958:%f
channel-map = left,right
direction = any

[Profile output:stereo]
description = Analog Stereo Output
output-mappings = analog-stereo-out
input-mappings =
priority = 80
skip-probe = yes

[Profile output:stereo-da+input:stereo-analog]
description = Analog Stereo Input/Output
output-mappings = analog-stereo-out
input-mappings = analog-stereo-in
priority = 100
skip-probe = yes

[Profile output:stereo-da+input:stereo-analog]
description = Analog Stereo Input/Output, Digital Stereo Output
output-mappings = analog-digital-stereo-out
input-mappings = analog-stereo-in
priority = 90
skip-probe = yes

[Profile output:spdif]
description = Digital Stereo Output (Analog Disabled)
output-mappings = digital-stereo-out
input-mappings = 
priority = 60
skip-probe = yes

[Profile output:spdif+input:spdif]
description = Digital Stereo Input/Output (Analog Disabled)
output-mappings = digital-stereo-out
input-mappings = digital-stereo-in
priority = 70
skip-probe = yes

```again save, close the editor and you're finished!

restart the computer, and select some non-spdif output from your sound preferences. before there were only "digital" and "surround" entries, but no sound output through analog

anything that uses pulse should have sound now, i.e. firefox/flash, the video player, system sounds, rythmbox etc...

I hope this helps you!

---

### Post by horaz on 2010-01-27
> **RaumTrug said:**
> the "~" sign is a shortcut for "/home/username/". with using it in any file name path, you direct it to the current user's home directory. so "~/.pulse/client.conf" is in reality, for example for me with username "traumflug": "/home/traumflug/.pulse/client.conf"

Thank you.

I did'n t anything about you wrote because i was tired, that night. I just tried, for kidding, to kill pulseaudio as you told me. (Today pulseaudio is still running)
But after two days, everything works! Without any reason! Everything but the player. I mean, flashmovies like youtube work, and so do movies in facebook. 
If I open an mp3 in audacity, or a midi with rosegarden and jack, it works. Skype goes like a rock. 
The strange thing is that the player Totem doesn't work, although i can see it "listens" to the song because I see colors changing (you know) whit the Rhythm of a song I know very well and, of course, time goes on.

But the worst: now, the whole system is horribly SLOW. Example? a little bit less than ONE second to change from desktop 1 to 2.
And so on.
I really do not know what this could be. Maybe I played too much with compiz config, yesterday, but, ok, man: I got a quadcore and 8Gb RAM!

Help me again , if you can, if you want.
Horaz

---

### Post by horaz on 2010-01-27
UPDATE! ;)
About slow system: two days ago I put this lines INTO my "/etc/pulse/default.pa"

###load-module module-alsa-sink sink_name=M2496_out device=hw:M2496 format=s32le channels=10 channel_map=left,right,aux0,aux1,aux2,aux3,aux4,aux5,aux6,aux7
###load-module module-alsa-source source_name=M2496_in device=hw:M2496 format=s32le channels=12 channel_map=left,right,aux0,aux1,aux2,aux3,aux4,aux5,aux6,aux7,aux8,aux9

As you see, I put ### today and I CHANGED my nVIDIA drivers from 185 (raccomanded) to 173, and everything works, about system: it's fast again.
But audio on Youtube is down again, although Skype works. Non midi working on rosegarden, whit a lot of xrun (ok, I'm not in RT kernel, now, but anyway two days ago in same conditions I had only 1 xrun), no sound from mp3 in Audacity.

I think I should now start to do what you wrote in your last post, but I prefer to wait an answer.
Thank you, RaumTrug, and you all, people!
Horaz
PS: As you said, the icon of volume vanished and I can't make her come back. I miss her... :(

---

### Post by horaz on 2010-01-27
I've done. Everything. Everything in fact wotks. Now, Skype doesen't!!!:!:
I try to give you some images: in fact, I actually don't know precisely what of analogue using...
Still, thanx.
Horaz

---

### Post by ghed on 2010-01-31
Hello. I have tried Jack and even begin to understand how it works. Managed to connect Rosegarden to Qsynth and so on, is seems also that Spotify works well with Jack. 
All audio works with Jack except sound from the web-browser (Youtube, web-radio). The sound stops when Jack is started to retund when it's closed. Jack is ran at the same time as Pulseaudio (-D).

---

### Post by horaz on 2010-01-31
> **horaz said:**
> I've done. Everything. Everything in fact wotks. Now, Skype doesen't!!!:!:
I try to give you some images: in fact, I actually don't know precisely what of analogue using...
Still, thanx.
Horaz

Everything works, now. Jack creates some problems, with kernel rt, sometimes. But, in the end, I can hear every sound from every source. Closing jack while I'm on the web, of course.

---

### Post by stratojaune on 2010-03-15
Hi,

have read here that you use ALSA and Maudio 2496, that's what I try to do these 2 days ago, with no luck !

May I take some of your time for help ?

---

### Post by horaz on 2010-03-15
I could try, but I'm a nearly newbie.
My language is Italian, try to write simply, and I'll do what I can.
:)

---

