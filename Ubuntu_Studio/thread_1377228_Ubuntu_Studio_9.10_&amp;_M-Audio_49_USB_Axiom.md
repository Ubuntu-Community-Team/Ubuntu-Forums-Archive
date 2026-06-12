---
title: "Ubuntu Studio 9.10 &amp; M-Audio 49 USB Axiom"
date: 2010-01-10
forum: Ubuntu Studio
---

### Post by InfamousLegato on 2010-01-10
Like the title says, that's my OS and my hardware. 

I cannot use it with Virtual Keyboard or any other software on here. 

lsusb output

:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 044e:300d Alps Electric Co., Ltd Bluetooth Controller (ALPS/UGPZ6)
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 046d:c042 Logitech, Inc. 
Bus 005 Device 002: ID 045e:00b0 Microsoft Corp. Digital Media Pro Keyboard
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05ca:1837 Ricoh Co., Ltd Visual Communication Camera VGP-VCC4 [R5U870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 006 Device 007: ID 0763:0199 Midiman Axiom 49**
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Already installed alsa-firmware-loaders alsa-tools alsa-tools gui via terminal 

Audio Card

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
Subsystem: Sony Corporation Device 9005
Flags: bus master, fast devsel, latency 0, IRQ 22
Memory at fc400000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: HDA Intel
Kernel modules: snd-hda-intel

cat check
:~$ cat /proc/asound/cards
0 [Intel]: HDA-Intel - HDA Intel
           HDA Intel at 0xfc400000 irq 22

1 [U49]: USB-Audio - USB Axiom 49
M-Audio USB Axiom 49 at usb-0000:00:1d.1-1, full speed

modinfo soundcore
filename:       /lib/modules/2.6.31-9-rt/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     3A50BBE947364A4D9DB6A97
depends:        
vermagic:       2.6.31-9-rt SMP preempt mod_unload modversions 586 

*edit* 

cat /dev/midi01
cat: /dev/midi01: No such file or directory

*edit 2* Works in Hydrogen, but I still can't get most other programs to detect my keyboard. 

Any help would be appreciated. I'm just really not sure where to go from here.

Also, I have a dual monitor set up. Whenever I reboot, the monitor I have plugged in is turned off. Is there a way to fix this?

---

### Post by AutoStatic on 2010-01-10
Hello InfamousLegato,

[http://ubuntuforums.org/showpost.php?p=8540958&postcount=18](http://ubuntuforums.org/showpost.php?p=8540958&postcount=18)

Replace 'Keystation' in the text for your Axiom.

---

### Post by InfamousLegato on 2010-01-10
It works! 

Now I just need to solve my dual monitors problem. Any ideas so I don't have to make a new thread?

Is there an easy way to make ubuntu detect my keyboard when I turn it back on?

---

### Post by AutoStatic on 2010-01-10
> **InfamousLegato said:**
> It works!Great, have fun!

> **InfamousLegato said:**
> Now I just need to solve my dual monitors problem. Any ideas so I don't have to make a new thread?This is a Multimedia Production forum, you'd better make a new thread on another forum like General Help or Hardware & Laptops.

> **InfamousLegato said:**
> Is there an easy way to make ubuntu detect my keyboard when I turn it back on?Try Patchage or the Patchbay window within QjackCtl. I think the Patchbay in QjackCtl will suit you most because you don't need to start up JACK itself in order to use it.

---

### Post by InfamousLegato on 2010-01-10
I have all that and none of it is working. 

I unplug, turn off and turn on my keyboard. Can't get it to connect.

*Edit* Tried using QjackCtl, nothing. 

High latency last time it connected. 

dmseg | tail 

[ 4139.418334] hub 6-0:1.0: unable to enumerate USB device on port 1
[ 4481.887328] hub 6-0:1.0: unable to enumerate USB device on port 1
[ 4489.754309] hub 2-0:1.0: unable to enumerate USB device on port 3


Tried to connect my regular keyboard and mouse into that USB port. No reponse. Might be the physical port

Confirmed it is my physical port. Going to buy a hub tomorrow. 

Still have unbearably high latency with midi keyboard and zynaddsubfx 

I mean I hate the keys, wait 5 seconds, then they register, soundless. The blue sound measurement thing at the bottom just freezes for a few seconds. 

It worked fine last night. Should I just uninstall the audio package and reinstall it?

---

### Post by AutoStatic on 2010-01-11
No, you could try setting the Timeout in QjackCtl a bit higher. Default is 500, try 1000 or 2000. ZynAddSubFX likes that a bit more, especially when changing instruments.
Reinstalling software or even Ubuntu to solve issues is a myth. It only helps if you really borked your installation.

---

### Post by InfamousLegato on 2010-01-11
Yes I've noticed that. 

The left USB port that had my MIDI keyboard now has my mouse and works.

My other ports have my regular keyboard and axiom and work fine now. 

Only issue I'm having is that ZynAddSubFX is zombifying. 

No other program is doing this, just ZynAddSubFX

I have uninstalled it, removed it, reinstalled it via Synaptic, Terminal and manually with no progress. 

Earlier when it was doing it I went to terminal and did

sudo apt-get remove vkeybd 

That fixed it.

Afterwards I decided I install a few other packages, STK, Rosegarden, and amsynth. Now ZynAdd doesn't work again. 

I sudo apt-get removed all of those and still can not get any output from Zynadd

zynaddsubfx --help
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_init: could not connect to server 'localhost' - disabling LASH

ZynAddSubFX - Copyright (c) 2002-2005 Nasca Octavian Paul
Compiled: Feb 11 2008 12:53:23
This program is free software (GNU GPL v.2) and 
    it comes with ABSOLUTELY NO WARRANTY.

And Yet again, after posting I have solved my own problem. I forgot to uninstall fluidsynth. 

I like ZynAddSubFx's simplicity, but my windows boot offers me access to livelite and FL Studio, which I still need to get. Are there any good synth programs that can compare to software like that?

---

### Post by AutoStatic on 2010-01-11
> **InfamousLegato said:**
> And Yet again, after posting I have solved my own problem. I forgot to uninstall fluidsynth.Normally that shouldn't make any difference at all. ZynAddSubFX is a simple binary that doesn't overlap with or depend on fluidsynth.

> **InfamousLegato said:**
> I like ZynAddSubFx's simplicity, but my windows boot offers me access to livelite and FL Studio, which I still need to get. Are there any good synth programs that can compare to software like that?You could try [LMMS]("http://lmms.sourceforge.net").

---

### Post by InfamousLegato on 2010-01-11
Yeah I'm not sure why it was affecting it but it was. 

Once semester ends in a week I'll have some time to do some research as to why I might be having that problem. 

And thanks I'll be sure to check out LMMS.

---

### Post by Th3Professor on 2010-01-17
Howdy all... so I have the m-audio axiom 49... wondering if there's a way to implement the fancy features that are available with it that come with it's windows/mac disc, only implement that on linux. I haven't tested the disc out yet in windows but it looks like it offers gobs of nifty features, and even allows for programming the keyboard's sounds and settings (beyond the basic functions immediately available on the keyboard itself). Anyway, I'd like to be able to access those features in Linux... is that possible?

---

### Post by Th3Professor on 2010-01-19
> **Th3Professor said:**
> Howdy all... so I have the m-audio axiom 49... wondering if there's a way to implement the fancy features that are available with it that come with it's windows/mac disc, only implement that on linux. I haven't tested the disc out yet in windows but it looks like it offers gobs of nifty features, and even allows for programming the keyboard's sounds and settings (beyond the basic functions immediately available on the keyboard itself). Anyway, I'd like to be able to access those features in Linux... is that possible?

bump

---

### Post by kayosiii on 2010-01-20
It's a controller keyboard it doesn't make any sounds.
AFAIK every feature of the device is available from the device itself (please correct me here if I am wrong)...

One possibility is that you may be able to get configuration sets from other people and load them onto the device using sysex commands. Is this the kind of thing you are trying to do?

---

### Post by AutoStatic on 2010-01-20
> **Th3Professor said:**
> I haven't tested the disc out yet in windows but it looks like it offers gobs of nifty features, and even allows for programming the keyboard's sounds and settings (beyond the basic functions immediately available on the keyboard itself). Anyway, I'd like to be able to access those features in Linux... is that possible?Hello The3Professor, it's a MIDI controller so it doesn't make any sound by itself. And the programming has to be done on the keyboard itself, at least on my Oxygen8 I have to do it on the keyboard itself. I know close to nothing about sysex.
And when it comes to softsynths, maybe you could give [PHASEX]("http://www.sysex.net/phasex/") a try, its knobs are all MIDI assignable. You can find it in the [frasten PPA]("https://launchpad.net/~frasten/+archive/ppa").

---

### Post by Th3Professor on 2010-01-20
Nice. Yeah, I'm definitely going to install that.

My original question - I think I was asking about assigning functions to all of the knobs and buttons on the keyboard itself via software. I haven't booted into Windows yet to test the CD that came w/ the m-audio keyboard but it appears that the windows software might provide a default set of programmed functions to "feed" into the keyboard, with which to edit and make any changes to.

Really, though, the heart of the question is this:

My keyboard has 8 trigger pads, 8 rotary encoders, 9 sliders, and 15 function buttons (including 6 reassignable transport buttons)... how can I assign or program all of those pads, rotaries, sliders, & buttons to function in various ways (in Linux)?

---

### Post by AutoStatic on 2010-01-20
> **Th3Professor said:**
> My keyboard has 8 trigger pads, 8 rotary encoders, 9 sliders, and 15 function buttons (including 6 reassignable transport buttons)... how can I assign or program all of those pads, rotaries, sliders, & buttons to function in various ways (in Linux)?This question may sound silly, and I really don't mean to be condescending but did you check the [manual]("http://www.m-audio.com/images/global/manuals/060801_Axiom_UG_EN01.pdf")?

---

### Post by Th3Professor on 2010-01-20
No it's okay, it's worth asking that.
Yes, I did check the manual.
And I went through the setting changes and such, though very little changes actually took place. It's really like "working blind". I'm looking for a more visual representation of what changes are taking place so I can both hear and see them.

---

### Post by sgx on 2010-01-20
> **Th3Professor said:**
> No it's okay, it's worth asking that.
Yes, I did check the manual.
And I went through the setting changes and such, though very little changes actually took place. It's really like "working blind". I'm looking for a more visual representation of what changes are taking place so I can both hear and see them.
Hi, first, try and learn basic functions of qtractor with a linux synth,
maybe zynaddsubfx, phasex, hexter...when you can run the transport controls, and record a few tracks, then apply the midi-learn functions
found in the axiom manual to those softwares. If you can get start, stop, and record on the Axiom to control qtractor, and assign some axiom controllers to basic synth funtions like filters and fx depth, you can expand from there. But the cart steers best with the horse in front ;)
Cheers

---

### Post by Th3Professor on 2010-01-21
Okay, I experimented for a little while tonight, primarily with qtractor, phasex, qmidiroute, aseqdump, and ams. I briefly tested midi in ardour but didn't get very far (yet).

So are qmidiroute, aseqdump, and ams primarily for "monitoring" the signals or "messages" that come from the midi keyboard/controller?

There was mention of qmidiroute for remapping. Is remapping basically assigning new sounds or control-type functions to the different buttons/knobs on the keyboard (via software)?

I liked how qtractor and phasex work well together.

I'm not really sure how I can apply the monitoring of messages sent from the keyboard/controller.

If the Axiom comes pre-programmed, I'd like to figure out just what all the knobs/buttons do. That's one thing that's lacking with this keyboard, despite it having a nice clean look, is that it has zero labels. Which is good I'm sure for reassigning/reprogramming purposes but I easily forget which button/slider/rotary thing/etc. does what kind of thing. Creating labels would help I suppose though I'd like to just establish specific functions out of each button and memorize all of it. <shrug>

Anyway, so I'm starting to get a better idea of things. I can see that I'm just gonna have to continue experimenting with things.

So how to use the program changes/etc. that are explain in the Axiom's manual along with the software... could that basically be done like this?:

1. Create sound on computer
2. Save that/program that setting onto a specific knob/button on the Axiom

Or do I have that backwards?

I'm a total rookie with all of this, thank you everybody for your patience. :KS

---

### Post by kayosiii on 2010-01-21
It's worth noting that the small blue dispay will show the CC number and the value of any knob slider,pedal or pad that is moved.... There is a standard list of what those controls are most commonly used for [http://www.tweakheadz.com/midi_controllers.htm](http://www.tweakheadz.com/midi_controllers.htm) should help. 

Many pieces of software have midi learn where you select the thing you want to control and  then move the controller you want to use.

Some pieces of software are configureable but you will have to enter the CC numbers yourself. 

Some pieces of software are not configurable. You will need to configure the keyboard to match the software (you may want to do this using one of the 20 sets of configuration the device can hold.

---

### Post by Th3Professor on 2010-01-21
> **kayosiii said:**
> It's worth noting that the small blue dispay will show the CC number and the value of any knob slider,pedal or pad that is moved.... There is a standard list of what those controls are most commonly used for [http://www.tweakheadz.com/midi_controllers.htm](http://www.tweakheadz.com/midi_controllers.htm) should help. 

Many pieces of software have midi learn where you select the thing you want to control and  then move the controller you want to use.

Some pieces of software are configureable but you will have to enter the CC numbers yourself. 

Some pieces of software are not configurable. You will need to configure the keyboard to match the software (you may want to do this using one of the 20 sets of configuration the device can hold.

Awesome - thank you for that link! I'm saving that list of commonly-used control specs. I didn't know about that, it'll definitely help with things.

Regarding the other 3 paragraphs you wrote... so basically is it like this?:

1. Set up midi sounds on computer, then move preferred controller.
(or did you mean: Move preferred controller in order to set up the midi on the computer?)

2. Enter CC numbers into computer along with other computer/software configurations or changes.

3. Computer software cannot be changed, requires all settings made on midi keyboard/controller instead.

Is that close? It sounds like "1." is easiest.

---

### Post by AutoStatic on 2010-01-21
> **Th3Professor said:**
> 1. Set up midi sounds on computer, then move preferred controller.
(or did you mean: Move preferred controller in order to set up the midi on the computer?)PHASEX does this, it has MIDI Learn capability. So what it does is when you want to assign a MIDI controller to a knob in PHASEX it waits for you to move a controller, records its CC (Continuous Controller) and stores it for you. Next time you move the MIDI controller the corresponding knob in PHASEX will move.

> **Th3Professor said:**
> 2. Enter CC numbers into computer along with other computer/software configurations or changes.I haven't come across software where you have to do this.

> **Th3Professor said:**
> 3. Computer software cannot be changed, requires all settings made on midi keyboard/controller instead.ZynAddSubFX is a good example, it uses some settings from the list of standard MIDI Continuous Controllers: [http://zynaddsubfx.sourceforge.net/doc_3.html](http://zynaddsubfx.sourceforge.net/doc_3.html)
On my Oxygen8 I reserved a program just for ZynAddSubFX where I assigned the CC's ZynAddSubFX can handle to the knobs I prefer. Whenever I use ZynAddSubFX (or [Yoshimi]("http://yoshimi.sourceforge.net/"), which I prefer at the moment) I switch to this program.

---

### Post by Th3Professor on 2010-01-21
> PHASEX does this, it has MIDI Learn capability. So what it does is when you want to assign a MIDI controller to a knob in PHASEX it waits for you to move a controller, records its CC (Continuous Controller) and stores it for you. Next time you move the MIDI controller the corresponding knob in PHASEX will move.Let's see if I understand this right...

1. Create the desired sound in PHASEX.
2. Assign "sound" to a knob. (Though, how do you do this in PHASEX? "Save MIDI Map"?)
3. Move the desired control on the MIDI keyboard/controller (to associate sound w/ the knob/button?).

Or do I have that mixed up?

Edit-

> ZynAddSubFX is a good example, it uses some settings from the list of standard MIDI Continuous Controllers: [http://zynaddsubfx.sourceforge.net/doc_3.html](http://zynaddsubfx.sourceforge.net/doc_3.html)
On my Oxygen8 I reserved a program just for ZynAddSubFX where I assigned the CC's ZynAddSubFX can handle to the knobs I prefer. Whenever I use ZynAddSubFX (or [Yoshimi]("http://yoshimi.sourceforge.net/"), which I prefer at the moment) I switch to this program.

I tried installing Yoshimi, it required ccmake or cmake or something, which I installed but it still wouldn't compile. :-\

---

### Post by AutoStatic on 2010-01-22
I have a Yoshimi checkinstall package if you really want to try it out. It's just plain ZynAddSubFX but with better JACK support, so no crackles and barely any xruns. It sounds a bit like this: [http://www.youtube.com/watch?v=18G8G9pRAxE](http://www.youtube.com/watch?v=18G8G9pRAxE)
And regarding PHASEX, just left click on the caption left of a knob (like 'Cutoff'), a window opens (see attachment) and as soon as you start moving a knob on your MIDI keyboard (first connect it to PHASEX in the ALSA tab of QjackCtl ofcourse) the 'MIDI Ctrl #' value will change.

---

### Post by Th3Professor on 2010-01-22
hmm.

...no audio on that youtube video. i tested audio on another video and it worked fine. must be my settings. :-\

I tried the steps you mentioned for the PHASEX working with the keyboard/controller, though it didn't work. :(

edit-
just a sec... i forgot to connect the keyboard, phasex, alsa, etc. via jack...

okay cool it works now! thank you.

I'm curious... any recommended patch settings per keyboard controller?

I have:

8 rotaries
9 sliders
9 buttons ("zone" 1,2,3,4; "group" a,b,c,d; and an extra nonlabeled button)
6 play-type buttons (loop (i think?), rewind?, fastforward?, stop, play, and record?)

Then there's the stuff that I think I need to use with the keyboard-only settings, not sure, like:

numberpad (0-9, and - and +)
program type buttons (null, mute, program, bank lsb, bank msb, glob chan, zone range, zone/group, data 1, data 2, data 3, chan assign, ctrl assign, store, recall, acell curve, vel curve, pad curve, vel lock, zone chan, panic, midi out, drawbar, ctrl select, device id, mem dump)

And then the easiest ones for me to figure out ;) including:

pitch bend wheel-thing
modulation wheel-thing (lol sorry for my terminology, i'm new to this stuff)
transpose (octaves)
and then the actual keys

I'd like to maximize the use of all the bells and whistles on this bad dog. :D

---

### Post by AutoStatic on 2010-01-22
> **Th3Professor said:**
> ...no audio on that youtube video. i tested audio on another video and it worked fine. must be my settings. :-\That's right, only on the very end where I connect all the apps together in QjackCtl

> **Th3Professor said:**
> I'm curious... any recommended patch settings per keyboard controller?I don't own such a controller so can't help you with that.

---

### Post by Th3Professor on 2010-01-22
Ah, okay I missed that the 1st time around... youtube is acting up now, no audio at all, had to manually download the "flv" to watch it. grrrr. Oh well. Anyway, I hear it at 1m14s into it... do you have a comparison of the difference in sounds?

---

### Post by AutoStatic on 2010-01-22
You mean between Yoshimi and ZynAddSubFX? There is no difference, they use the same banks and instruments. It's just that ZynAddSubFX produces a lot of crackling and Yoshimi doesn't. Or you mean between PHASEX and Yoshimi/ZynAddSubFX?

---

### Post by Th3Professor on 2010-01-22
> **AutoStatic said:**
> You mean between Yoshimi and ZynAddSubFX? There is no difference, they use the same banks and instruments. It's just that ZynAddSubFX produces a lot of crackling and Yoshimi doesn't. Or you mean between PHASEX and Yoshimi/ZynAddSubFX?

I initially was curious about the crackling you mentioned where Zyn[...] creates it and Yoshimi doesn't.

However, I am curious how PHASEX compares to both of the other apps. I think I'm going to experiment with PHASEX (for now at least), see if it ends up feeling like a comfortable option for the keyboard/midi work.

On another note... and this is off topic with the Axiom but will still ultimately end up using it... I've got my mixer and patch cables now, hooked it up to my new delta 1010. :D I've got levels set on the board, JACK/envy24 is running, and it appears Ardour is picking things up (it also seems to have automatically adjusted JACK's Connections when it loaded). However, I'm getting no playback. :-\ I've only tested my microphones with that gear so far. I have Line Ins on the mixer too, coming from Line Outs on guitar amps, and I have the MIDI drumset hooked up to the MIDI ports on the Delta 1010. I'm not sure how to incorporate the usb/midi keyboard/controller (axiom) and the roland electronic drumset into Ardour (or Rosegarden). The keyboard/controller is USB direct into computer while the drumset is going into the midi of the Delta. (I also have a "main out" from drumset going into the mixer.) Anyway, my *main* concern on that stuff right now is getting playback to work. :confused:

The Axiom - in general - is coming along, all of the features on it are pretty cool. :) I'm looking forward to getting it down.

---

