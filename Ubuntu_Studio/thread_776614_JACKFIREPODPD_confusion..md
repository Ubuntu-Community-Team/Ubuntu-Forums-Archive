---
title: "JACK/FIREPOD/PD confusion."
date: 2008-04-30
forum: Ubuntu Studio
---

### Post by steve k on 2008-04-30
Hi,

Recently I got access to a Presonus firepod (a roommate got one) and I heard that it works well with Linux so I thought I'd give it a try.  Right now, I do most of my recording on an antiquated XP computer with a MOTU deal...anyway, My primary Linux box is a Thinkpad X40 laptop.  I have a PCMCIA firewire card for it and that is plugged into the Firepod. I've used Jack before, it works fine with shittier, simpler USB devices, and the sound card that comes with the X40.  However, the built in sound card is absolutely terrible, the latency on the USB devices I'm using is unnacceptable and really, this is all that stands between me and my long held dream of giving up on windows entirely.  I briefly tried using the ubuntustudio realitme kernel but it completely screwed the power management on this laptop, and since I use it as a laptop I desperately need it to suspend and resume properly.  

Anyway, so I plug the Firepod in, turn it on, change those permissions on raw1394 and mess around a bit with the settings on qjackctl and lo and behold, the little blue light on the firepod turns on indicating that it is connected and running properly.  In the qjackctl connections panel I can see all the firepod's inputs and outputs.  Looks great!  However, after that weird things start happening: the transport controls in jack don't seem to work, any time I start a jack-aware program and then terminate it it's connections remain visible and ostensibly active in the connections panel, even though the program should have vanished.  Further, each application I run, doesn't work as normally: for example, sooperlooper cannot start recording at all, PD cannot open files and ardour's transport is suddenly broken.  I have all of these things working (if poorly - bad internal microphone, high latency) using the soundcard that is IN the laptop.  

What can I do?  Any suggestions?  I'm still using gutsy at the moment if that helps anyone out?  Anything?

---

### Post by robeast on 2008-05-01
Sounds pretty bad, steve. I've been using a Firepod with Gutsy on my desktop with no issues whatsoever for many months. I just upgraded to Hardy and now I have problems: constant jack crashes and the occasional freeze. If I hadn't had such success before I'd have been through the configuration troubles to be able to help out, but right now I'm in the same boat. Can you list the output in your jack message window as well as your jack settings and any log messages from Ardour or your other programs?

---

### Post by steve k on 2008-05-01
I'll post my Jack output tomorrow when I can get my hands on the firepod again, but I did notice that my PD window generated NO information at all: no news.  No extras.  I didn't try running ardour from the command line or sooperlooper (i frankly use PD more, so getting it going matters to me most).  

Tell me, back when all this was running great on your gutsy system: what exact configuration steps did you take?

---

### Post by Stochastic on 2008-05-01
I'd guess that the issues you're having are arising from the lack of a realtime kernel.  I've got a firepod and it's worked fine under Gutsy and Hardy.  The only needed setup step I've had to get working was the raw1394 permissions.  I'd load up a realtime kernel, turn on jack's realtime mode, then see if the problems go away.

You can use two different kernels on the same machine, just boot into your "recording" setup when you want to record.  Lots of people actually do this, and configure the recording boot to be much more stripped down to save on processing power and memory usage (some even use fluxbox etc..).  That's not needed to get you firepod working (I've got enough horsepower to run XGL in gnome as my recording boot), but since you may need to reboot into the realtime kernel anyway...

---

### Post by steve k on 2008-05-01
See, the weird thing was that after installing the realtime kernel neither kernel seemed to handle basic power management tasks.  I could neither suspend nor resume.  When I got rid of the RT-Kernel everything worked fine again.

My friend Jonathan has the same problem on his totally different laptop.  The Gutsy RT Kernel just hates the acpi stuff.  I'm really reluctant to go back to the RT Kernel, and since all these Jack apps run properly (if not in full realtime) using lesser soundcards I'd assume that they should just run better using a better soundcard with or without a rt kernel, y'know?  I'll get that jack message up here this afternoon.

---

### Post by steve k on 2008-05-01
See, the weird thing was that after installing the realtime kernel neither kernel seemed to handle basic power management tasks.  I could neither suspend nor resume.  When I got rid of the RT-Kernel everything worked fine again.

My friend Jonathan has the same problem on his totally different laptop.  The Gutsy RT Kernel just hates the acpi stuff.  I'm really reluctant to go back to the RT Kernel, and since all these Jack apps run properly (if not in full realtime) using lesser soundcards I'd assume that they should just run better using a better soundcard with or without a rt kernel, y'know?  I'll get that jack message up here this afternoon.

---

### Post by Stochastic on 2008-05-01
Are any of the other soundcards you've tried firewire?  I think that's the major difference you're running into (the freebob driver is not the best, ffado should be better once it's ready).  You may also want to explore the possibility of installing the realtime kernel then troubleshooting the acpi stuff on a dev list somewhere (having a different kernel installed shouldn't affect things if you're not running it, in theory).

---

### Post by steve k on 2008-05-02
> **Stochastic said:**
> You may also want to explore the possibility of installing the realtime kernel then troubleshooting the acpi stuff on a dev list somewhere (having a different kernel installed shouldn't affect things if you're not running it, in theory).

Tell me about it! I love that theory! (sigh)

anyway, before I give the realtime kernel another swing:
here's what happens when I run: ```
jackd -v -d freebob
```

```
~$ jackd -v -d freebob
getting driver descriptor from /usr/lib/jack/jack_dummy.so
getting driver descriptor from /usr/lib/jack/jack_oss.so
getting driver descriptor from /usr/lib/jack/jack_freebob.so
getting driver descriptor from /usr/lib/jack/jack_alsa.so
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
server `default' registered
loading driver ..
Freebob using Firewire port 0, node -1
showDevice: not implemented
FreeBoB MSG: Register MIDI IN port dev1c_MidiIn 1
FreeBoB MSG: Register MIDI OUT port dev1p_MidiOut 1
FreeBoB MSG: Streaming thread running without Realtime scheduling
FreeBoB MSG: Registering capture port dev1c_Mic/InstIn 1
FreeBoB MSG: Registering capture port dev1c_Mic/InstIn 2
FreeBoB MSG: Registering capture port dev1c_LineIn L
FreeBoB MSG: Registering capture port dev1c_LineIn R
FreeBoB MSG: Registering capture port dev1c_SPDIFIn L
FreeBoB MSG: Registering capture port dev1c_SPDIFIn R
FreeBoB MSG: Don't register capture port dev1c_MidiIn 1
FreeBoB MSG: Registering playback port dev1p_MainOut 1L
FreeBoB MSG: Registering playback port dev1p_MainOut 2R
FreeBoB MSG: Registering playback port dev1p_LineOut 3L
FreeBoB MSG: Registering playback port dev1p_LineOut 4R
FreeBoB MSG: Registering playback port dev1p_LineOut 5L
FreeBoB MSG: Registering playback port dev1p_LineOut 6R
FreeBoB MSG: Registering playback port dev1p_SpdifOut L
FreeBoB MSG: Registering playback port dev1p_SpdifOut R
FreeBoB MSG: Don't register playback port dev1p_MidiOut 1
FreeBoB MSG: MIDI threads running without Realtime scheduling
FreeBoB MSG: MIDI queue thread started
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
new client: freebob_pcm, id = 1 type 1 @ 0x806e658 fd = -1
new buffer size 1024
registered port freebob_pcm:dev1c_Mic/InstIn 1, offset = 4096
registered port freebob_pcm:dev1c_Mic/InstIn 2, offset = 8192
registered port freebob_pcm:dev1c_LineIn L, offset = 12288
registered port freebob_pcm:dev1c_LineIn R, offset = 16384
registered port freebob_pcm:dev1c_SPDIFIn L, offset = 20480
registered port freebob_pcm:dev1c_SPDIFIn R, offset = 24576
registered port freebob_pcm:dev1p_MainOut 1L, offset = 0
registered port freebob_pcm:dev1p_MainOut 2R, offset = 0
libiec61883 warning: Established connection on channel 0.
You may need to manually set the channel on the receiving node.
registered port freebob_pcm:dev1p_LineOut 3L, offset = 0
registered port freebob_pcm:dev1p_LineOut 4R, offset = 0
registered port freebob_pcm:dev1p_LineOut 5L, offset = 0
registered port freebob_pcm:dev1p_LineOut 6R, offset = 0
registered port freebob_pcm:dev1p_SpdifOut L, offset = 0
registered port freebob_pcm:dev1p_SpdifOut R, offset = 0
++ jack_rechain_graph():
client freebob_pcm: internal client, execution_order=0.
-- jack_rechain_graph()
libiec61883 warning: Established connection on channel 1.
You may need to manually set the channel on the transmitting node.
9770 waiting for signals
load = 1.3289 max usecs: 567.000, spare = 20766.000
```

At this point, the little blue light is on on the front of the box (I tried this out with both a firepod and a firebox hoping that maybe the firebox would work when the pod didn't).  I can see all the input and output channels in patchage.  But I can't load PD files, I can't get sooperlooper's recordings 'transport' (it doesn't really have one but...) to start rolling... it ALMOST works.  

I've tried a few more precise, maybe 'better' settings in qjackctl and that also works nicely, engages the whole thing, produces very few xruns right off the bat (usually, running the soundcard that came with my computer i get an xrun within seconds of the jack server starting, weather I'm doing anything or not)...it's looking great except for not being able to do anything.

---

### Post by Stochastic on 2008-05-02
When I say "you may want to explore" it means "I don't want to explore" as I too know how time-consuming that would be. :rolleyes:  But if you never ask a dev, then the problem won't get fixed (launchpad bugs?).



You look like you have freebob loaded and your firepod running.  Can you open anything in a lightweight wav editor to save on processing power and attempt playback through it?

Honestly, before the low-latency kernel came out (then its successor, the realtime) I was having all types of troubles with audio on debian-based systems; particularly Ubuntu.  Not much, if anything, (of complicated sound apps that is) ran well on ALSA supported hardware.  Ubuntu Studio actually started as a series of how-tos to get your system geared for sound processing.  Those how-tos are migrated here: [https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound) and you may find some useful info in the General Configuration section, but keep in mind that those were written for Edgy/Feisty time frame.

The only other idea I have is to start looking at error logs etc.. and I'm hit/miss with understanding the ones I can find.  maybe to ```
man strace
``` to start troubleshooting.

If I was in your spot (I guess I kinda am, with a laptop and a firepod) I'd forget about that kernel and go realtime.  I have a hard trouble believing you really need suspend and resume capabilites as I live without them (well I guess I'm not in the same spot, as your firepod is merely borrowed from a roommate, so....).

---

### Post by steve k on 2008-05-03
Weird news is that things worked almost exactly the same under the realtime kernel as on the not-realtime kernel.

Same weird lockups and stuff.

ok. fine. fine. computer.

---

### Post by kayosiii on 2008-05-04
yeah Hardy has been less stable for me on the firebox than gutsy... But everthing basically seems to work.

The symptoms you get remind me when I had two copies of libjack on the system. Jack control would try to hook up to one version and everthing else to the other.... 

Though sometimes I find that Jackd crashes and leaves the blue light on the soundcard - (you have to unplug it replug it to get the soundcard going again.

Try upping the frames/period setting....

Finally what chipset is your Firewire card -- some are known to be very buggy....
(try lspci command in console/shell/command prompt to figure this out -hint Texas Instruments = good, Ricoh = Very bad)

---

### Post by steve k on 2008-05-04
Well, my firewire bus is "VIA" whoever that is: it's a generic PCMCIA card plugged into my laptop.  It works great with my external harddisk and stuff.  Anyway, things got a bit better, I started using the RT Kernel and now Jack will actually start running more or less normally, programs can start, transports can run and then it gets 'zombified' and just aborts itself after a second or two.

Any ideas about how to stabilize that situation?

---

### Post by Stochastic on 2008-05-05
The zombified issue is something that I've experienced before and I believe it stems either from poor drivers (freebob has many faults that ffado should fix when it's ready), bad firewire connection (actually quite a likely culprit), or too many apps hogging some resources - though I've never researched this issue deeply, as the problem magically disappeared for me (yay for that horseshoe up my *&#).  As for your firewire chipset, it should be okay.  Though harddrives and low-latency audio are two different horses; harddrives have no time crunch associated with them.  Data transfer can wait for a lost packet to be resent, whereas freebob considers these things as major issues - as it should.  When you find jack zombifies, just unplug the firewire cable, plug it back in, then start jack back up and hope the issue magically disappears, as it did for me, or that ffado gets released soon.

---

### Post by steve k on 2008-05-15
So I've moved on from that residency I was at where everyone had firepods and now I totally don't have access to one.  So I can't really try anything new, one thing about the zombifying, is that it would happen in seconds, with pretty much nothing else running.  But as I said, I've waited this long to use Firewire soundcards on linux, I can wait a bit longer, some time next year, we'll all just be plugging them in with complete reliable stability and laughing.  

A few years ago the situation was way worse.

---

### Post by zettberlin on 2008-05-25
I have tried the Firebox (wich is more or less the same as the Pod only with fewer channels) today with Hardy and it looks like this:

the interface is recognized as needed and I can initialize it for jack like this:

jackd -R -v -r96000 -p512 -n3 -dfreebob

it starts and shows its ports and I can play and record with Ardour.

For about 5-10 Minutes - then it dies.

So basically the device works so far but it is not usable for real work.

Quite sad a thing: on 64Studio the very same device works flawlessly for 6-7h-sessions with bands. I had some high hopes, that 8.04 could bring the same stability to Ubuntu also but it didnt....:mad:

---

### Post by ethanay on 2008-05-27
sorry I am coming into the conversation late

as Stochastic said, I recommend having a special "recording setup" except I go as far to recommend a completely different boot environment for the realtime kernel.  This is from experience:  I ran into problems simply trying to load the realtime kernel into Hardy, which I use with the generic kernel.  Things stopped working, etc, and the problems did not go away when I removed the realtime kernel!

So I recommend using a dual-boot system with a second, stripped-down operating system installed on a completely different partition operating a realtime kernel.  I boot into a 64studio (32-bit) environment with gnome and use only about 200mb of ram on startup (of 2gb).  if 64studio didn't work, then i was considering a similar setup with rt-kernel + Hardy (since I am now intimately familiar with it :)  

advanced power management + realtime kernel/daw environment doesn't make much sense to me.  suspend/hibernate works well for me in Hardy, but I don't care to try to get it to work in 64studio, and haven't even bothered testing it. same with cpu frequency scaling. 

the reason is that a low-latency environment is specialized and isn't good for normal (non-audio/video) computer work, because it is less interactive.  for example, network response (NOT throughput!) is sloow because it is deprioritized, I believe (someone correct me if I am wrong here).  so it is partially a tradeoff between latency and "interactive responsiveness" which can actually increase latency.  IMHO, it is best to leave it as a specialized thing that does what it is intended to well, and not beat our heads against the wall trying to make a realtime kernel "be everything to everyone" and replace the generic kernel.  kernel developers haven't been successful at this yet, which is why there are two separate kernels to being with!  so I (a lowly, ignorant end user) will not even bother trying :)

also, if you mess around with optimizing something or updates and it breaks something, it is nice to have the environments separate so both do not break.  or have the frustration of fixing something, which breaks something else...

I recommend 64studio -- it took a bit to get it setup but since it is debian and gnome-based it should be very familiar, and is a very good system.

Lastly, I will be compiling ffado soon (this week) to work with my Echo Audiofire2 -- I will post back with the results/problems (probably to a different thread).

---

