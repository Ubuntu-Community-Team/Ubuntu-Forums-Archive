---
title: "A few questions on equipment needed for recording"
date: 2009-12-13
forum: Ubuntu Studio
---

### Post by Th3Professor on 2009-12-13
Hi!

Are both USB & FireWire mixers/soundboards compatible with Ubuntu Studio? Which is kind is considered "better"?

What recording equipment, or "audio interface", is recommended for connecting the mics/instruments & MIDI into the computer?

At one point I was considering getting a flash recorder for the silence in recording but figured I'll just record straight into the computer, though I need the right audio equipment for that purpose.

I have a MIDI instrument with 1/4" jacks "direct outs" and also MIDI jacks. I'm not sure if I can hook that up directly into a soundboard (or similar device). Can I just use the 1/4" jacks instead of the MIDI jacks, and connect that into a soundboard?

If you put a list together of specific equipment to get for recording mic'd instruments and 1 or 2 MIDI instruments, what might that list look like?

Thank you very much for your help! :)

EDIT:

Currently running my sound from the motherboard.

Here are some of my motherboard's specs:

8 x audio channels

1 x HDMI

6 x USB 2.0

s/pdif out:
1 x optical, 1 x coaxial

6 x audio ports

2 x 1394a

I'm on an old version of Ubuntu Studio, I need to upgrade but first back-up things first to be safe. Also, it's 64-bit but not sure if that matters. (?)

Thank you for your help!

---

### Post by trulan on 2009-12-13
OK - I replied to your other thread before I saw this one.  Lots of good info here, lots of good questions:

1. USB vs. firewire - firewire will be a little more stable at low latencies, provided it is supported by the ffado drivers (check their website to see which devices are listed).  USB will be supported if it is a class-compliant device, or if it is - well - supported.  I use firewire and wouldn't want anything else but it depends on what you want to do with it.

2. Mics/Instruments?  A good, supported soundcard - see #1.  Midi?  If you just want the audio from your keyboard, hook it up like any other instrument.  If you want to use the midi signal (allowing you to be a lot more flexible), either through your soundcard (many good soundcards have midi inputs) or through a separate midi-USB cable.

3. My list?  Currently I have 2 PreSonus Firepods (16 channel record/playback, via firewire) and a Turtle Beach midi-USB cable.  (I could also route the midi in through the firepods.)  I've also used the onboard soundcard on my desktop but that only has two input channels.  (My laptop's onboard card refuses to record and play back at the same time in Ubuntu.)  

When I started, I was plugging in a cheap little Behringer mixer into the line in on my soundcard, and could record two channels at a time.  It worked great for multi-tracking stuff myself, but was helpless when it came to recording a band.  Depending on your needs, though, that can be a pretty good solution

Oh, and 64 bit vs. 32 bit?  My desktop is 64 bit and my laptop is 32 bit.  I honestly have never run into a situation where it made any difference.  (Maybe I need to get out more ;) )

---

### Post by Th3Professor on 2009-12-13
Thank you for the input.

I'm currently considering getting a Mackie Onyx 1220i 12-channel analog mixer with FireWire interface. I think it's a fairly new board, I believe it came out just a few months ago (around September '09).

I understand that it works like this:
1. mics (for live instruments and voice) go into that board.
2. The "direct outs" (1/4" jacks) on the MIDI instrument to go into the board.
(If I can hold off on MIDI-gear for right now, get that later, that'll be fine.)
3. Then the firewire from the board into the computer.
4. Load JACK & Ardour (and/or any other applications?).

Does that sound about right?

I'm guessing I'll need to make some adjustments to the settings/options in JACK & Ardour.

Is there a check-list that helps with confirming settings in the audio programs?

If there are any specific programs that would come in handy too I can use those. I know Ubuntu Studio has a plethora of audio apps, it's kind of overwhelming.

How would the software and recording equipment be set up to allow for playback of tracks while recording tracks simultaneously?

Thanks for the help! :D

---

### Post by AutoStatic on 2009-12-14
> **Th3Professor said:**
> Hi!

Are both USB & FireWire mixers/soundboards compatible with Ubuntu Studio?USB: class compliant USB1 devices, you can check the compatibility [here]("http://www.alsa-project.org/main/index.php/Matrix:Main"). Some devices may need firmware, others still need a patched kernel (M-Audio Fast Track Pro/Ultra). Firewire: any device that is supported by the [FFADO]("http://ffado.org/?q=devicesupport/list") drivers.

> **Th3Professor said:**
> Which is kind is considered "better"?Firewire. Not only because of lower latencies but also more input and output channels you can use at the same time, more possibilities with working at higher bitrates and on the hardware side, overall better pre-amps and AD/DA convertors. And like trulan said, Firewire is more stable because you simply have more bandwidth and less overhead (if I'm correct).

> **Th3Professor said:**
> What recording equipment, or "audio interface", is recommended for connecting the mics/instruments & MIDI into the computer?USB: Edirol UA-25(ex), Tascam US-122 (not the L and Mk II versions), any other class compliant USB1 device. Firewire: Focusrite Saffire Pro series, Presonus Firepod.

> **Th3Professor said:**
> If you put a list together of specific equipment to get for recording mic'd instruments and 1 or 2 MIDI instruments, what might that list look like?How many channels would you like to record at once? And what's your budget? My list would look like this:
[LIST]
[*]Edirol UA-25EX USB soundcard
[*]USB/Midi keyboard (I use M-Audio stuff)
[*]Decent microphones (Shure SM57, condenser mic; I have a Studio Projects B1, ok for vocals)
[*]Decent cables (if they have Neutrik connectors they're already pretty much ok I guess to start with)
[*]Mic stands (I use K&M, haven't run into a cheaper and comparable alternative yet)
[/LIST]

> **Th3Professor said:**
> I'm on an old version of Ubuntu Studio, I need to upgrade but first back-up things first to be safe. Also, it's 64-bit but not sure if that matters. (?)I'd advise a clean installation. Upgrading will get you into trouble, especially on the audio side of things.

Best,

Jeremy

---

### Post by trulan on 2009-12-14
> **Th3Professor said:**
> Does that sound about right?
Sounds good!  I don't know about the mackie board.  I guess if it's new there might be a chance it wouldn't be supported, but I think Mackie products have been supported by ffado for some time.  Check it out before you sink money into it, though.

Here's the UbuntuStudio wiki:
[https://help.ubuntu.com/community/UbuntuStudio](https://help.ubuntu.com/community/UbuntuStudio)

To set up firewire audio, here's a guide:
[https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)

> **Th3Professor said:**
> How would the software and recording equipment be set up to allow for playback of tracks while recording tracks simultaneously?
That should all be OK.  Basically, you need jack set to duplex.  It's set that way out of the box - it just doesn't work with some really cheap cards, like the onboard one in my laptop.  Anything decently respectable will do this automatically.

---

### Post by AutoStatic on 2009-12-14
> **Th3Professor said:**
> Thank you for the input.

I'm currently considering getting a Mackie Onyx 1220i 12-channel analog mixer with FireWire interface. I think it's a fairly new board, I believe it came out just a few months ago (around September '09).It's not listed [here]("http://ffado.org/?q=devicesupport%2Flist&filter0=mackie&filter1=&op2=OR") but like trulan says, there are other Mackie devices that are supported so chances are you'll get it to work right away or in the near future.

> **Th3Professor said:**
> I understand that it works like this:
1. mics (for live instruments and voice) go into that board.
2. The "direct outs" (1/4" jacks) on the MIDI instrument to go into the board.
(If I can hold off on MIDI-gear for right now, get that later, that'll be fine.)
3. Then the firewire from the board into the computer.
4. Load JACK & Ardour (and/or any other applications?).

Does that sound about right?Yup.

> **Th3Professor said:**
> I'm guessing I'll need to make some adjustments to the settings/options in JACK & Ardour.You probably will, but with the help of the URL's trulan pointed out and this forum you should be able to get it done.

---

### Post by Th3Professor on 2009-12-14
> **AutoStatic said:**
> USB: class compliant USB1 devices, you can check the compatibility [here]("http://www.alsa-project.org/main/index.php/Matrix:Main"). Some devices may need firmware, others still need a patched kernel (M-Audio Fast Track Pro/Ultra). Firewire: any device that is supported by the [FFADO]("http://ffado.org/?q=devicesupport/list") drivers.

Excellent.

Thank you for the links! :)

I see this:
[http://ffado.org/?q=node/85](http://ffado.org/?q=node/85)
...perhaps that's "close enough". :confused: It seems to hint at it, since the "1220i" is an "Onyx", although it doesn't specify that specific model.

> **AutoStatic said:**
> USB: Edirol UA-25(ex), Tascam US-122 (not the L and Mk II versions), any other class compliant USB1 device. Firewire: Focusrite Saffire Pro series, Presonus Firepod.

The Mackie "1220i" I'm looking at has an approximate 20 or 30 day return policy, so I suppose if it doesn't end up working with the system I can take it back and go for something like a Focusrite or Presonus, as far as firewire interfaces go.

And if the 1220i *does* work, I can always let the people know who are running those compatibility websites and they can add the "i" series Mackie Onyx boards to their lists. :D

> **AutoStatic said:**
> How many channels would you like to record at once? And what's your budget?

Ideally 8 with a little cushion room for some occasions, though at times I won't need 8. Having 12 channels and 2 buses seems to be enough for my setting.

Budget, meh, well, technically it's a little flexible but I'm going to be pretty reserved and stick to under $2k if I can, or even stick with ~$1k range for just the basic recording necessities (board+mics). I guess gear upgrades and additions can come later.

> **AutoStatic said:**
> Edirol UA-25EX USB soundcard

Hmm, right now I'm running off the motherboard's audio. It's a pretty expensive motherboard with nice audio features built-in. I'm not sure how compatible it is though. I looked up ASUS on one of the compatibility lists and it listed sound cards but nothing specific to the mobo built-in audio.

I have the Asus m3n-ht deluxe hdmi +firewire.

If it doesn't work I suppose I could get either an internal soundcard or something like that USB soundcard you mentioned. I wonder if the external option is "easier to deal with" than internal.

> **AutoStatic said:**
> I'd advise a clean installation. Upgrading will get you into trouble, especially on the audio side of things.

That sounds like a good idea. I'm going to need to do a refresher on how RAID5 & LVM work so I don't lose anything on that set-up. It has been a while since I initially set it up and I've forgotten the howto. lol

> **trulan said:**
> Sounds good! I don't know about the mackie board. I guess if it's new there might be a chance it wouldn't be supported, but I think Mackie products have been supported by ffado for some time. Check it out before you sink money into it, though.

Yeah it's looking like it might be a 50/50 thing right now.

The ffado page lists...
"Mackie Onyx Mixer FireWire Option: **Full Support**"
...and I'm looking at a Mackie Onyx Mixer FireWire Option, lol.

So maybe it's more of a 75/25 or 80/20 chance of working (considering it's new on the market).

> **trulan said:**
> Here's the UbuntuStudio wiki:
[https://help.ubuntu.com/community/UbuntuStudio](https://help.ubuntu.com/community/UbuntuStudio)

To set up firewire audio, here's a guide:
[https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)

Thank you for the links! :)

> **trulan said:**
> Basically, you need jack set to duplex. It's set that way out of the box - it just doesn't work with some really cheap cards, like the onboard one in my laptop. Anything decently respectable will do this automatically.

That makes me wonder about the ASUS motherboard-based audio. Although it's a fairly expensive board with fancy audio features (including 2 firewire ports), I have no idea if it'll work.

I guess it's just a matter of trying it out and if no luck with that I can go for a separate soundcard (internal or external).

> **AutoStatic said:**
> It's not listed [here]("http://ffado.org/?q=devicesupport%2Flist&filter0=mackie&filter1=&op2=OR") but like trulan says, there are other Mackie devices that are supported so chances are you'll get it to work right away or in the near future.

Crossing my fingers. :D

---

### Post by fedexnman on 2009-12-14
for firewire interfaces check out the   Echo audiofire stuff, i love mine i have the audiofire4, theyre inexpensive and work great with the ffado driver in jack.

---

### Post by Th3Professor on 2009-12-16
Will I need to manually add the necessary ffado driver(s) to get the Mackie to work with the computer or are the drivers already on the system?

---

### Post by AutoStatic on 2009-12-16
They are not installed by default, at least not on Ubuntu Karmic, not sure about Studio. But the driver package is called **libffado1**.

---

### Post by trulan on 2009-12-16
Firewire drivers are installed by default on any Ubuntu Studio distro, or included in the ubuntustudio-audio metapackage, should you choose to start with regular Ubuntu.

On Hardy (8.04) only the freebob drivers are included, but anything newer than that will include ffado.  And for Hardy there is a backports repository you can use to install ffado.

There have been some improvements in the ffado drivers even since Jaunty, and I would recommend going with Karmic if you want to use firewire - Unless you want to build your own software from source.

---

### Post by Th3Professor on 2009-12-18
right now i'm going to be going w/ just basic recording gear... 2 mics & a firewire mixer, then into computer to record. i'm getting some fresh cables for some electronic instruments. otherwise, all i'm getting for now consists of mics+mixer.

just the other day i got a couple mics (AT2020) plus mic cables and boom stands for each.

tomorrow (friday) i'll be getting my sound board (Mackie Onyx 1220i FireWire mixer). :D

...i'm curious if it will or won't work (currently running ubustu 8.10, haven't had a chance to upgrade yet. i won't worry about upgrading just though, gonna have to work out my raid+lvm set-up, i hear 9.10 has conflicts w/ raid.)

Anyway, soon enough i'll find out what works and doesn't work, and will hopefully be able to remedy things fairly easily if anything doesn't work. :)

---

### Post by Th3Professor on 2009-12-19
Okie dokie, I have the board, mics, basic gear... hooked up via firewire to computer.

No go on JACK. here's the message that came up:

> [COLOR=#999999]02:02:00.340 Startup script...[/COLOR]
 [COLOR=#990099]02:02:00.340 artsshell -q terminate[/COLOR]
 [COLOR=#990099][COLOR=#999999]02:02:00.751 Startup script terminated with exit status=256.[/COLOR][/COLOR]
 [COLOR=#990099][COLOR=#999999]02:02:00.751 JACK is starting...[/COLOR][/COLOR]
 [COLOR=#990099]02:02:00.751 /usr/bin/jackd -R -P70 -p128 -dfirewire -r44100 -p128 -n2[/COLOR]
 [COLOR=#990099][COLOR=#999999]02:02:00.753 JACK was started with PID=19374.[/COLOR][/COLOR]
 [COLOR=#990099]jackd: unknown driver 'firewire'[/COLOR]
 [COLOR=#990099][COLOR=#999999]02:02:00.759 JACK was stopped with exit status=1.[/COLOR][/COLOR]
 [COLOR=#990099][COLOR=#999999]02:02:00.760 Post-shutdown script...[/COLOR][/COLOR]
 [COLOR=#990099]02:02:00.760 killall jackd[/COLOR]
 [COLOR=#990099][COLOR=#ff0000]02:02:00.782 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR][/COLOR]
 [COLOR=#990099]jackd: no process killed[/COLOR]
 [COLOR=#990099][COLOR=#999999]02:02:02.751 Post-shutdown script terminated with exit status=256.[/COLOR][/COLOR]
[COLOR=#990099][COLOR=#999999]

[/COLOR][/COLOR]Any ideas? I'm not sure why it says "unknown driver 'firewire'".

I checked dev for raw1394 and found it:
> ls -al /dev/raw1394 
crw-rw---- 1 root disk 171, 0 2009-12-19 01:38 /dev/raw1394


Is it a ffado thing?

---

### Post by dawiba on 2009-12-19
Someone will correct me if I'm wrong, but you'll need to add yourself to the video group for firewire to work.
```

dawiba@ubuntustudio:~$ ls -al /dev/raw1394
crw-rw---- 1 root video 171, 0 2009-12-19 09:27 /dev/raw1394
```

---

### Post by AutoStatic on 2009-12-19
```
ls -al /dev/raw1394
crw-rw---- 1 root disk 171, 0 2009-12-19 01:38 /dev/raw1394 
```You have to make sure you're part of the 'disk' group. You're running Ubuntu Studio 9.10 right? Did you tick "enable raw 1394 access" in Ubuntu Studio Controls? System - Administration - Ubuntu Studio Controls

---

### Post by trulan on 2009-12-19
OK, a few facts first:
You are running Ubuntu Studio Hardy (8.04), correct?
What version of jackd are you running, and how did you get ffado installed in Hardy?

The above ideas are good, but you need backported versions of jack and ffado to get things working in Hardy.

---

### Post by Th3Professor on 2009-12-19
Hi all, thank you for the replies...

> **dawiba said:**
> Someone will correct me if I'm wrong, but you'll need to add yourself to the video group for firewire to work.
```

dawiba@ubuntustudio:~$ ls -al /dev/raw1394
crw-rw---- 1 root video 171, 0 2009-12-19 09:27 /dev/raw1394
```

I added myself to an audio group but not video. Is the video necessary for only doing audio? (A pre-req for firewire even if not using video?)

> **AutoStatic said:**
> ```
ls -al /dev/raw1394
crw-rw---- 1 root disk 171, 0 2009-12-19 01:38 /dev/raw1394 
```You have to make sure you're part of the 'disk' group. You're running Ubuntu Studio 9.10 right? Did you tick "enable raw 1394 access" in Ubuntu Studio Controls? System - Administration - Ubuntu Studio Controls

Disk group. That's new to me. Okay, I see "disk" is not currently listed in 'groups' for me. Hmm. I'm running 8.10 right now (I'm kinda worried about upgrading with the RAID probs in 9.10 (I'm using RAID+LVM.)) Anyway, I went ahead and added (created too) myself to a 'disk' group. No differences yet.

I enabled the features in Ubuntu Studio Controls via the "howto" page in here, enabling all 3 things, setting priority/nice level, etc.

> **trulan said:**
> OK, a few facts first:
You are running Ubuntu Studio Hardy (8.04), correct?
What version of jackd are you running, and how did you get ffado installed in Hardy?

The above ideas are good, but you need backported versions of jack and ffado to get things working in Hardy.

Okay so maybe that's the issue here? I checked synaptic package manager and didn't find "ffado" listed anywhere for install. Or does ffado come pre-installed on Ubuntu Studio 8.10?

My current JACK version- 0.3.2

Thanks!

---

### Post by dawiba on 2009-12-19
> **Th3Professor said:**
> 
I added myself to an audio group but not video. Is the video necessary for only doing audio? (A pre-req for firewire even if not using video?)

Definitely. I've never been able to use firewire without being a member of the video group as well as the audio group. It is necessary to send audio in and out through a firewire interface.

---

### Post by AutoStatic on 2009-12-19
/dev/raw1394 GID is disk. So if you're in the disk group you're allowed to use that device node. In 9.04 and 9.10 the GID of that device is root if I'm right, you could chgrp it to audio or video but best is to add a new udev rule.
But I overlooked something:
```
02:02:00.751 /usr/bin/jackd -R -P70 -p128 -dfirewire -r44100 -p128 -n2
02:02:00.753 JACK was started with PID=19374.
jackd: unknown driver 'firewire'
```
Like trulan said, libffado is not installed, you have to do that first. No idea though about the availibility of libffado for 8.10, maybe someone else could point you in the right direction. With 8.04 I used Khashayar's PPA, I think it still contains libffado, also for 8.10. All in all I'd suggest to install 9.04 or 9.10, 8.10 was not such a good release.

---

### Post by trulan on 2009-12-19
Khashayar's ppa.  Exactly.
[https://launchpad.net/~khashayar/+archive/ppa]("https://launchpad.net/%7Ekhashayar/+archive/ppa")
You'll want to upgrade Jack and install libffado from this ppa.  IIRC the version of Ardour in there is pretty good too and has support for lv2 plugins, so you could upgrade that too.  I used that stuff for a while, before Karmic was out and stable.  Add that ppa to your sources, upgrade jack, and install ffado.

The real time kernel in 8.10 was a dud.  8.04 was very good.  If you're on 8.10 it may be time to move on, but 8.04 will be okay for a while.  But I know nothing of raid or lvm issues.

---

### Post by Th3Professor on 2009-12-20
It sounds like I'll be better off with a fresh install of 9.10 (there are a few buggy issues w/ my 8.10 right now in any case). I'm going to dig a little deeper into whatever potential issues 9.10 might have with RAID before I make the fresh install, I need to make sure my data will remain safe. I wouldn't want to lose 3 TB of data. ;) Once that's good to go hopefully the fresh install will be the key remedy and take me one big step closer to recording/composing on the computer once again. :)

---

### Post by trulan on 2009-12-20
You might want to consider a parallel install in its own partition or on its own drive for Studio, especially if you have 3 Tb of data to concern yourself with.  I think I would be more comfortable having things isolated a bit.  You're gonna want to install the rt kernel for running the Mackie, and you probably will want to be able to boot the generic kernel for your other stuff.  It seems to me a fresh install of 9.10 studio in its own partition would be the way to go.

---

### Post by Th3Professor on 2009-12-20
> **trulan said:**
> You might want to consider a parallel install in its own partition or on its own drive for Studio, especially if you have 3 Tb of data to concern yourself with.  I think I would be more comfortable having things isolated a bit.  You're gonna want to install the rt kernel for running the Mackie, and you probably will want to be able to boot the generic kernel for your other stuff.  It seems to me a fresh install of 9.10 studio in its own partition would be the way to go.

good idea! :) i've been wanting to use another system to keep my variety of operating systems going. Ubustu partition only for studio, makes sense... something else for everything else.

Any ideas on how rt handles on a 64bit quad core cpu?

---

### Post by AutoStatic on 2009-12-21
> **Th3Professor said:**
> Any ideas on how rt handles on a 64bit quad core cpu?Really well. My main machine has an i7 and it's rock solid with the 2.6.31-9-rt kernel.

---

### Post by Th3Professor on 2009-12-21
Sweet. :) I heard that there were problems with it - something about 64-bit vs rt, not sure what - but that was also over a year ago. ;)

Is the 2.6.32.2 realtime kernel the most recent stable release?

I can use a previous version if it's a more solid kernel for realtime purposes.

If I end up doing multiboot w/ studio OS and normal OS, I'll probably go with the most recent generic kernel on the normal OS.

---

### Post by AutoStatic on 2009-12-21
Karmic comes with a 2.6.31-9 kernel so I'd stick with that one.
There were several issues in the past, 8.10 did not have a RT kernel at all and the RT kernel for 9.04 had issues with multiple core CPU's. But the one that comes with Karmic is pretty good if you ask me.

---

### Post by Th3Professor on 2009-12-21
Awesome! :D

I'm hoping to get my LVM & RAID set-up secured before doing a fresh install. My OS is on a separate hard drive from my raid5/lvm, so maybe it'll be easier.

---

### Post by trulan on 2009-12-21
2.6.31-9-rt is the latest realtime kernel.  There is a stable 2.6.32 generic kernel and 2.6.33 generic is in development, but as of yet there is no real time preemption patch out for anything newer than 2.6.31.  I'm playing around with Ubuntu Lucid (which is in early alpha stage) and so far it is using exactly the same rt kernel as Karmic.

---

### Post by Th3Professor on 2009-12-23
bad news... i tested a live cd of ubuntu 9.10 and it did *not* recognize my raid/lvm set-up. i have no idea what to do. :( so... no fresh ubustu 9.10 installs until that's taken care of.

on the flipside of things, i'm adding a new usb/midi keyboard to my array of instruments for recording/composing. a 49-key m-audio (axiom, i believe). a little over $200 :-/ i was hoping to just drop $100 on a new keyboard but the features on that keyboard are too juicy to just let 'em pass by.

---

### Post by AutoStatic on 2009-12-23
Did you try the alternate CD? Apparently the 9.10 liveCD doesn't have the right modules in it's initrd image, maybe with the alternate CD you have more luck. LVM should be no problem, and what kind of RAID thing is it? What kind of setup and hardware?

---

### Post by trulan on 2009-12-23
> **AutoStatic said:**
> Did you try the alternate CD? Apparently the 9.10 liveCD doesn't have the right modules in it's initrd image, maybe with the alternate CD you have more luck. LVM should be no problem, and what kind of RAID thing is it? What kind of setup and hardware?
Can you test the alternate DVD (the only way UStudio comes) without installing it?  I'm not aware that you can...

If you want a studio-capable live cd, real time kernel, firewire support and all, you could check out AVLinux:  [http://www.bandshed.net/AVLinux.html](http://www.bandshed.net/AVLinux.html)
It's not Ubuntu but it is built on Debian and contains some Ubuntu pieces.

I have no idea what it would do with RAID or LVM.

---

### Post by AutoStatic on 2009-12-23
> **trulan said:**
> Can you test the alternate DVD (the only way UStudio comes) without installing it?  I'm not aware that you can...No idea, I don't use Ubuntu Studio. I was assuming it was about a regular 9.10 CD.

---

### Post by Th3Professor on 2009-12-23
> **AutoStatic said:**
> Did you try the alternate CD? Apparently the 9.10 liveCD doesn't have the right modules in it's initrd image, maybe with the alternate CD you have more luck. LVM should be no problem, and what kind of RAID thing is it? What kind of setup and hardware?

My first try was the Ubuntu Studio 9.10 DVD. It went immediately into a non-gui type of install (no "live" running available), so I stopped that for the time being to test the raid/lvm recognition on a live cd.

My second try was the Ubuntu 9.10 (Live) CD. After loading the "live" version from the disc, it did not recognize the raid/lvm set-up. It saw several separate hard drives (of useless data without the raid/lvm).

I'm using soft raid, specifically **mdadm**. I do have onboard/mobo raid capability, which I suppose would come in handy with using the raid set-up across unlike operating systems, though that's not really a big deal for my uses.

The mdadm set-up is using RAID 5.

The lvm is LVM2, the main version of lvm that's used these days.

> **trulan said:**
> Can you test the alternate DVD (the only way UStudio comes) without installing it?  I'm not aware that you can...

If you want a studio-capable live cd, real time kernel, firewire support and all, you could check out AVLinux:  [http://www.bandshed.net/AVLinux.html](http://www.bandshed.net/AVLinux.html)
It's not Ubuntu but it is built on Debian and contains some Ubuntu pieces.

I have no idea what it would do with RAID or LVM.

Unfortunately, I don't think the Ubustu/UStudio DVD allows for testing/live runs of the system. I gave it a try but it started going through the install process, so before it could make any actual installations I forced a quit and went on to try the normal Ubuntu live CD. (All versions being 9.10.)

I'll check out AVLinux. Do you know if it's 64-bit friendly?

...on another note...

I posted a raid/lvm "please help" message over in the general forum and received a reply with basically the following steps:

1. Boot into live cd
2. Install mdadm & lvm (lvm2)
3. Enter these commands:
```
sudo mdadm --assemble
sudo vgchange -a y
```...and a warning to back-up data. I went ahead and copied important files over to a hard drive that is not part of the RAID/LVM disks, and on a separate partition from the partition that houses the operating systems. (for some reason it wouldn't let me burn a simple data cd, i ended up wasting a few nice dvds in the process.:()

---

### Post by trulan on 2009-12-24
> **Th3Professor said:**
> Unfortunately, I don't think the Ubustu/UStudio DVD allows for testing/live runs of the system. I gave it a try but it started going through the install process, so before it could make any actual installations I forced a quit and went on to try the normal Ubuntu live CD. (All versions being 9.10.)
Right.  That's what I thought.
> I'll check out AVLinux. Do you know if it's 64-bit friendly?It's 32 bit, with PAE support for systems with large amounts of ram.  It's creator seems to think that this is just as good.  I certainly wouldn't know.  Then again, my computers are all at least three years old and wouldn't benefit anyway.

---

### Post by Th3Professor on 2009-12-24
Well I've got my new baby, 49 key m-audio axiom... with all the bells and whistles on it - and *no* instruction manual came with it <o.O> I'm guessing I'll just have to wing it & use any online manuals that google or m-audio's site bring up.

I've got the mixer... mics... various instruments... ready to go... except... for the operating system. lol Gotta put Ubuntu Studio 9.10 on here first. Then to move on to starting from square one with all the programs for all of the instruments, one little step at a time. I'm betting it'll be kind of overwhelming at first. No biggy.

---

### Post by Th3Professor on 2009-12-26
Ubuntu Studio 9.10 installed fine, and even the raid/lvm set-up is working fine. :D Now to begin exploration of all of those programs. :P

---

### Post by AutoStatic on 2009-12-26
Nice!
[IMG]http://cache.hyves-static.net/images/smilies/default/smiley_piano.gif[/IMG]

---

### Post by Th3Professor on 2009-12-26
Good stuff. :)

I found this page:
[http://munix.dk/tutorials/music-recording/installing-and-recording-music-ubuntu-studio](http://munix.dk/tutorials/music-recording/installing-and-recording-music-ubuntu-studio)

...it sucks. lol It doesn't help at all. :p Well I'm sure for someone installing those versions of apps on that specific hardware.

Gonna have to refer to some other "howto" pages.

---

