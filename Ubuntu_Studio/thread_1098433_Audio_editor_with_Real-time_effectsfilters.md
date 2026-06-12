---
title: "Audio editor with Real-time effects/filters"
date: 2009-03-17
forum: Ubuntu Studio
---

### Post by happinesskills on 2009-03-17
I'm looking to start a podcast & I need an audio editor with Real-Time effects, meaning: I can apply an effect while I'm recording it. I am currently using Audacity, which does it's job, but doesn't let you add effects while recording. So, is there any audio editor for Ubuntu that has Real-Time effects.

---

### Post by Stochastic on 2009-03-17
Just add jack rack into the chain before hitting audacity.  This is of course assuming you're running audacity through the jack audio server (you'll probably need to for this task).

Your chain should look like:
mic->soundcard->jack input channel->jackrack->audacity

Then you'll want to make sure you have the ladspa plugins installed ```
sudo apt-get install ubuntustudio-audio-plugins
``` then you can use most of those plugins in real time in jackrack.

---

### Post by kayosiii on 2009-03-18
Ardour immediately springs to mind

---

### Post by cb951303 on 2009-03-18
Latest [Jokosher]("http://www.jokosher.org") with [Jack-Rack]("http://jack-rack.sourceforge.net/").

You have to install Jack of course. With [Qjackctl]("http://qjackctl.sourceforge.net/") from repos you can easily configure Jack to your liking.

---

### Post by gfxguy on 2009-03-18
Ok, don't mean to hijack this thread, but it's related...

I need to make my voice sound like a computer or robot.  I hate to say it, but I ended up in Windows to get it done.

First, I couldn't get the mic to work at all.  Output works fine.

Secondly, I couldn't find any FOSS software that did what I needed.

I did discover that the real-time programs I tested out on Windows were wonderful in the sense that, while they didn't apply effects live (while recording), you could adjust parameters DURING playback and get immediate feedback, which you couldn't do with audacity.

I did use audacity (on windows) for a few of the tweaks I ended up using.

Ok, I know this seems like mindless babble now, but the question is if there's software for Linux (I'll even pay, if it works) that will allow me to record and then LAYER adjustable filters on (as opposed to always directly modifying the data)?

I found one program like this on Windows (can't remember the name) and it didn't do what I needed (or, at least, I couldn't make it do that), but it reminding me, in style, of a lot of higher end software I've used for video and image editing, where you've got layers of filters you can tweak to adjust the final output as opposed to continuously modifying your source data.

On a side note, I found some really nice Stephen Hawking sounding synthesizers, but I can't figure out how to capture the output so that I can burn it to a CD.

---

### Post by Stochastic on 2009-03-18
> **kayosiii said:**
> Ardour immediately springs to mind

You're totally right! That's the easiest method to use - bar none!  Why didn't I think of that.


Edit:
gfxguy, you should give Ardour a try too - it will allow layering of filters without direct writing until export.  Also, many of the online text-to-speech generators have a download button that will give you a wav file (if that's all you're looking for).

---

### Post by cb951303 on 2009-03-18
[QUOTE=Stochastic;6917486]You're totally right! That's the easiest method to use - bar none!  Why didn't I think of that.

I wouldn't say easiest. It has a learning curve. It's totally **overkill** for podcast editing.

---

### Post by happinesskills on 2009-03-19
for some reason, Ardour doesn't record

---

### Post by happinesskills on 2009-03-19
Nup, Ardour doesn't record from my line-in or my in-built microphone in my monitor. Audacity can record from both, but not at the same time, which is where my next problem comes in: How can I record from 2 inputs (the Line-in & the Built-In - hey, that rhymes.. kind of). I know Audacity can't do it, but is there like a.. virtual mixer or something that creates fake inputs & outputs?

PS: A "Mixer" is one of those boxes that bands have with a whole lot of cords coming from it, & a bunch of knobs & sliders on it.

---

### Post by Stochastic on 2009-03-19
Here's the Ardour tutorial for beginners:
[http://www.out-of-order.ca/tutorials/ardour/](http://www.out-of-order.ca/tutorials/ardour/)  
That will cover the steps required to get it to record (and add effects pre-fader).

**If** your soundcard treats the two inputs as separate channels, and doesn't just switch between them, most likely ardour can record from both at the same time.

Another reason why ardour is probably the best method (despite the tiny learning curve) is that after you've recorded, you can go back and adjust your effects.  Using Jack Rack and a separate recorder will not allow this.  Okay, maybe recording live effects (recording effects automation) takes a bit of a steeper learning curve on ardour, but overall it's easier and more flexible than other methods IHMO.

---

### Post by thorgal on 2009-03-19
you need jack, the low latency audio server, properly set up. Then you can use ardour. Ardour only sees what jack ports there are available. 
Jack is talking to the lower level audio layer, can be ALSA for PCI and USB cards, FFADO (or formerly freebob) for firewire card, it can also talk to the deprecated OSS layer, and also PortAudio (which is used by audacity) although I am not sure there'll be developed / enhanced support for it in the future.

Get jack up and running and ardour will record from any input jack reports there are.

You will even be able to drive two soundcards thanks to something called alsa_in (provided with netjack, which should be part of the latest jack development version).

I am sure you can find tons of howtos in this forum and other places that will guide through setting jack up. If I remember well, markbuntu has a nice discussion thread about it. Can't give you a link right now.

---

### Post by gfxguy on 2009-03-19
Thanks for the replies, guys, I'll give ardour a try.

The speech synthesizers, though... I've only used command line.  I'll have to see what GUI's are available that have a "button" to record to wave.

---

### Post by Stochastic on 2009-03-19
> **gfxguy said:**
> Thanks for the replies, guys, I'll give ardour a try.

The speech synthesizers, though... I've only used command line.  I'll have to see what GUI's are available that have a "button" to record to wave.

This is a nice easy one: [http://www.research.att.com/~ttsweb/tts/demo.php](http://www.research.att.com/~ttsweb/tts/demo.php)
You're limited to a certain length, but a wave editor can work around that.
I imagine command line versions would have a save feature in some output flag or pipe command, but haven't needed to look into it before.

---

### Post by happinesskills on 2009-03-20
What's Jack & where can I get it? I tried Synaptic but that returns this (only things I don't have installed):

jackeq - routes & manipulates audio from/to multiple sources
jackd - JACK Audio Connection Kit (server and example clients)
jackbeat - a drummachine-like audio sequencer with JACK support
libjackasyn0 - The Asynchrounous JACK Library
libjack-dev - JACK Audio Connection Kit (development files)
jacksum - computes checksums, CRCs and message digests
libjack0.100.0-0 - JACK Audio Connection Kit (libraries)
libjack0.100.0-dev - JACK Audio Connection Kit (libraries)
creox - real-time guitar effects
jack - Rip and encode CDs with one command
jack-tools - various JACK tools: plumbing, play, udp, ctl, scope, clock

I don't know which one's actually JACK, but JackEQ didn't start (possibly because I have Intrepid)

---

### Post by thorgal on 2009-03-20
install a package called qjackctl
It's the GUI frontend to the jack audio server.
You will have to set it up. If you have more than one sound card (like onboard chip + extra PCI / USB / firewire card, which seems to be very common these days), you will have to look through the forum for howtos as jack has a few limitations (can only handle on piece of h/w at a time, etc, even though there are work-arounds). If your default audio server is pulseaudio (which to my mind was premature to introduce in the last ubuntu releases) you will have to follow markbuntu's recipes. Look for his posts, he posted a very comprehensive one abotu how to set up your audio depending on what you want as the main audio server. It should be a sticky as more and more users are asking the same questions again and again.

if you want to know more about jack, you can always read about it at  [www.jackaudio.org](www.jackaudio.org)

---

### Post by happinesskills on 2009-03-20
Alright, I've got qjackctl installed.. now what? It looks confusing & I can't figure it out.

---

### Post by thorgal on 2009-03-20
OK, that's a good start.

Now, what soundcards do you have ? post the output of (from a terminal):

```

cat /proc/asound/cards

```

```

lspci

```

---

### Post by simtaalo on 2009-03-20
setting jack up is confusing but once its done your life should be made a million times easier

[https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration)

that should help

---

### Post by happinesskills on 2009-03-20
here's the output of the first one:

```
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf5300000 irq 22
```

& the second one:

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
08:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
08:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
```

---

### Post by thorgal on 2009-03-21
so you've got the intel HDA ... not the best out there but you'll have to do with it:

the setting that seems to work best with this chip is:

jackd -R -P 70 -d alsa -dhw:0 -r 48000 -p 1024 -n 3

try this from a terminal. If you get the server up and running, then you can configure qjackctl with these parameters. When you are doing so, you can leave all other parameters to their default values (things like input / output latency, etc).

I can explain the options of the command line above:

-R : realtime operation, You will need elevated user privilege to access the RT mode. Usually, it depends on a setting found in a file at /etc/security/limits.conf You will need to google around to find out about it, I am not in front of my DAW right now.

-P 70: priority to give the jackd audio thread. 100 is the maximum but you should not use 100 for this thread. 70 seems good enough. This option only makes sense with the -R option

-d alsa : jackd will use the ALSA backend to talk to the low level audio layer (ALSA in this case)

all options after -d alsa belong to the jackd backend, not the jackd server :

-d hw:0 : tells the backend to use the audio hardware indexed at 0 by ALSA. Since you have only one audio chip, it is the only one available and is indexed at 0 by ALSA during boot.

-r 48000 : sample rate to use. You can also use 44100 (used in audio CDs)

-p 1024: number of audio frames per period. It is related to the size of the audio buffer the audio chip will process. The bigger the buffer, the higher latency. You can try low sizes (32, 64, 128, 256, etc) but you have to be aware that you will have more instabilities. Some chips cannot cope very well with small chunks of audio data, and you risk to experience the famous "buffer underrun" or "overrun", generically called Xrun. It's a sign that the card cannot cope with the buffer size and you will hear glitches (pops and clicks) in the audio stream due to card failure to deliver the data in time. The realtime operation (-R option) should minimize these things as the kernel will prioritize audio processes. The best thing to do is to get a patched kernel for complete preemption, it will ensure that the kernel will deliver in terms of realtime operations (i.e. deterministic processes). 

-n 3: 3 periods per buffer. A buffer has a certain number of periods. Usually 2. But the intel HDA works best with 3. It increases the latency a bit but n = 2 will definitely be a bad choice in your case. 

the combination of n and p options determine the buffer size:

buffer size = n x p frames. So 1024 x 3 in this case.

You can try 256 or 128 frames and see if you get good result (lower latency but still acceptable for your card).

---

### Post by happinesskills on 2009-03-21
I don't know why, but it pops up an error. I ran it through the terminal with the code you supplied, but it didn't work (even as root) & I tried it manually through qjackctl itself & now it won't start again. I'll try rebooting.

---

### Post by happinesskills on 2009-03-21
through a process of elimination I've found that it's the realtime. It works unticked & doesn't when it's ticked

---

### Post by thorgal on 2009-03-22
you need to configure your system to enjoy realtime operations:

you will have to tweak /etc/security/limits.conf
it's a system file you will need root privileges to do so (sudo)

can you report the outputs from the following terminal command:

to know your kernel version:
```

uname -r

```

to know which unix groups you belong to
```

id

```

to know whether a unix group called audio exists:
```

grep audio /etc/group

```

to know whether this audio group has RT privileges:
```

cat /etc/security/limits.conf

```

---

### Post by happinesskills on 2009-03-23
Here's the output of all consecutively:

```
matt@matt-laptop:~$ uname -r
2.6.27-11-generic
matt@matt-laptop:~$ id
uid=1000(matt) gid=1000(matt) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),107(fuse),109(lpadmin),115(admin),124(vboxusers),1000(matt)
matt@matt-laptop:~$ grep audio /etc/group
audio:x:29:pulse,matt
matt@matt-laptop:~$ cat /etc/security/limits.conf
# /etc/security/limits.conf
#
#Each line describes a limit for a user in the form:
#
#<domain>        <type>  <item>  <value>
#
#Where:
#<domain> can be:
#        - an user name
#        - a group name, with @group syntax
#        - the wildcard *, for default entry
#        - the wildcard %, can be also used with %group syntax,
#                 for maxlogin limit
#
#<type> can have the two values:
#        - "soft" for enforcing the soft limits
#        - "hard" for enforcing hard limits
#
#<item> can be one of the following:
#        - core - limits the core file size (KB)
#        - data - max data size (KB)
#        - fsize - maximum filesize (KB)
#        - memlock - max locked-in-memory address space (KB)
#        - nofile - max number of open files
#        - rss - max resident set size (KB)
#        - stack - max stack size (KB)
#        - cpu - max CPU time (MIN)
#        - nproc - max number of processes
#        - as - address space limit (KB)
#        - maxlogins - max number of logins for this user
#        - maxsyslogins - max number of logins on the system
#        - priority - the priority to run user process with
#        - locks - max number of file locks the user can hold
#        - sigpending - max number of pending signals
#        - msgqueue - max memory used by POSIX message queues (bytes)
#        - nice - max nice priority allowed to raise to values: [-20, 19]
#        - rtprio - max realtime priority
#        - chroot - change root to directory (Debian-specific)
#
#<domain>      <type>  <item>         <value>
#

#*               soft    core            0
#*               hard    rss             10000
#@student        hard    nproc           20
#@faculty        soft    nproc           20
#@faculty        hard    nproc           50
#ftp             hard    nproc           0
#ftp             -       chroot          /ftp
#@student        -       maxlogins       4

# End of file
matt@matt-laptop:~$
```

---

### Post by thorgal on 2009-03-23
the audio group and your belonging to it is fine. Now you need to tweak the limits.conf file:

add the following at the end of /etc/security/limits.conf

```

@audio - rtprio 99
@audio - memlock unlimited
@audio - nice -19

```

be careful with spaces, you'd better copy / paste it.
You need sudo to edit this file. From the terminal, you could use whatever text editor (nano, vi, emacs, etc)

or use the echo shall command:
```

sudo echo "@audio - rtprio 99" >> /etc/security/limits.conf
sudo echo "@audio - memlock unlimited" >> /etc/security/limits.conf
sudo echo "@audio - nice -19" >> /etc/security/limits.conf

```


you may want to use half your RAM (in kB) instead of unlimited. So if you've got 2GB or RAM, use 1000000 (not half but about that). I used unlimited without any side effect, so just experiment.

You will have to log out log in again each time you make a change in this file.

I suggest you get an RT kernel, you only have the generic. However, the 2.6.27 version of the RT kernel is buggy. Either you can compile one with complete preemption, or you can download a packaged kernel made by someone else. I think there's something floating around in a recent thread (kernel 2.6.29-rc6 with RT patch). 

You don't have too but it will improve the realtime side of things. The generic kernel is also doing a good job nowadays so don't jump to kernel changing right away.

---

### Post by happinesskills on 2009-03-24
Right. I put it in & set qjackctl to use Realtime with 70 as priority (like your previous instructions). I logged out & in again, but my internet connection wouldn't connect. So, I took it out of the limits.conf & logged out & in again (leaving qjackctl as is) & voila! It works. Realtime doesn't pop up an error. however, the icon in the system tray has an orange play icon instead of a green one (the play is in the bottom left of the Jack icon)

---

### Post by thorgal on 2009-03-24
you're making progress :)

This network connection issue ... are you sure it has to do with the security thing ? I doubt it. If you have removed the changes to security.conf, you will lose your RT privilege when you reboot. The orange color of the qjackctl icon is also suspicious to me.

I suggest you do the following:
- put back the changes to security.conf
- reboot completely

- log in and never the mind the network if it craps out (I do think that the network device should be activated at boot time, not by the user during logging. What I have in my linux PCs is some entries in /etc/network/interfaces and an init script /etc/init.d/networking which will go through this interfaces file and activate what can be at boot time. The KDE or GNOME environment comes up with its own applet to set up the network. I think it's a bit crappy but that's just my opinion). 

- instead of launching qjackctl, open a terminal and execute the jackd command line I gave you earlier.

- report log messages that you will see in the terminal

---

### Post by happinesskills on 2009-03-25
Right. I had COMPLETELY forgotten what we were trying to get to work. I read over the thread again, & apparently I couldn't get Ardour to record. Well, guess what. It does. I just hadn't done it right.

But. How do you get Ardour to record from 2 inputs. I've tried adding 2 tracks & setting 1 to record from 1 input & the other track to record from the other input, but no luck. Unfortunately they both change when I change where ALSA records from (under options tab in Volume Control).

---

### Post by thorgal on 2009-03-25
hehe, it's good you refocus on the issue :)

ardour records from what you tell it to record from.
If you have an onboard chip only, my guess is that you only have a stereo input socket (mini-jack).  Jack will see this as two mono input ports.

All audio jackd ports (the ones you see in the GUI connection window) are mono by definition. In ardour, what you can do given the h/w limitation is create a stereo track and assign system: capture_1 to track:input_1 and system: capture_2 to track:input_2. 

But you will only record from stereo sources. 

If you really have this h/w limitations, I strongly encourage you to get another soundcard (USB, PCI or firewire, depending on your PC). If you can go PCI, then a M-Audio Delta 44 or 66 (66 includes MIDI) would do a good job for you. It all depends on your needs at the end. I have an RME Hammerfall DSP and external IO box with 8 analog inputs / outputs, MIDI in/out, SPDIF, etc. This is high-end h/w but I need all this because I run a home studio where I need to record from many sources. So first, define what your needs are, then get a proper device for it. The onboard chip is very limited, believe me. Sure you can use it but with time, you'll only be frustrated as you get the hang of linux audio.

I also think that it is better to work with mono sources than stereo if you plan to produce music.

---

### Post by happinesskills on 2009-03-26
thanks for all your help. I'm gonna play around with Ardour & try to get it recording from both inputs.

Thanks

---

