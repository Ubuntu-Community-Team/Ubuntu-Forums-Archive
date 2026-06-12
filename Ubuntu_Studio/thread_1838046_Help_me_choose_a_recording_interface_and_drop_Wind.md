---
title: "Help me choose a recording interface and drop Windows forever"
date: 2011-09-02
forum: Ubuntu Studio
---

### Post by eqyiel on 2011-09-02
*****Summary: **

These are all devices that have been reported to work by the helpful community members you see below.

[http://www.focusrite.com/products/audio_interfaces/saffire_pro_24/](http://www.focusrite.com/products/audio_interfaces/saffire_pro_24/)
[http://www.focusrite.com/products/audio_interfaces/saffire_pro_40/](http://www.focusrite.com/products/audio_interfaces/saffire_pro_40/)
[http://www.roland.com/products/en/FA-66/](http://www.roland.com/products/en/FA-66/)
[http://www.m-audio.com/products/en_us/Delta1010LT.html](http://www.m-audio.com/products/en_us/Delta1010LT.html)
[http://www.m-audio.com/products/en_us/Audiophile2496.html](http://www.m-audio.com/products/en_us/Audiophile2496.html)
[http://www.lexiconpro.com/product.php?id=7](http://www.lexiconpro.com/product.php?id=7)
[http://www.sweetwater.com/store/detail/SaffireLE/](http://www.sweetwater.com/store/detail/SaffireLE/) *no longer in production, but you might be able to get it secondhand
[http://www.musiciansfriend.com/guitars/fender-mustang-i-20w-1x8-guitar-combo-amp/h61791000001000](http://www.musiciansfriend.com/guitars/fender-mustang-i-20w-1x8-guitar-combo-amp/h61791000001000) * depending on your particular needs this may not qualify, but it looks great if you just want to track some guitars!
[B]
***Original post:[/B]

This is not a specific question about Ubuntu Studio, but it has everything to do with recording in Linux, so I hope it's okay to post here.

I started using Lucid around the start of this year.  It took some time, but slowly I found far better open source alternatives to everything I needed to use back in XP, and learned how to do some exciting things I'd never even tried before (setting up a headless scan/print/web server, etc.) and generally been very happy in Ubuntuland.  I really want to make the change forever but there's something missing which is really important to me...

Recording audio has been the only area I haven't been successful in.

As far as DAWs go, been suitably impressed with Ardour, but I've been pulling out my hair trying to find a suitable recording device.  I've had enough experience trying to get this going that I've come to not expect things to work out of the box.  I'm not scared of reading guides all over the internet and spending a few days trying to set it up if necessary.  I just need something that is more functional than I've experienced so far!

Here's what I used to use:
[MOTU 828mkII]("http://www.motu.com/products/motuaudio/copy2_of_828")
[Behringer ADA8000]("http://www.behringer.com/EN/Products/ADA8000.aspx")
Combined the two for a total of 10 mic inputs, used XP and Reaper.  It was pretty good for recording bands live, just enough for a drum kit and a couple of instruments.  I was pretty happy with this setup.

After reading around a bit, I heard that the 828mkII had pretty dismal support in Linux.  Of course, at first I resisted believing that and tried to get it working myself (in Lucid).  Got as far as being able to record one track in Ardour and play it back, however... if there was more than one instrument plugged in, it would all be routed through the same track (for instance, if you had 10 mics plugged in recording onto 10 tracks, each one of them would end up being the exact same .wav file despite being configured to different inputs).  Not quite the recording dream I had in mind!

I also own a [Digidesign Mbox2 Mini]("http://www.amazon.com/Digidesign-Portable-USB-Powered-Tools-Workstation/dp/B000KW4TZK") (for recording on the go and mucking around at home).  I heard similar depressing stories about this device in Linux, until I found [ZamAudio's]("http://www.zamaudio.com/?p=97") driver.  After following that guide I was able to get the Mbox to record into Audacity, but not Ardour (had to select it from the pulseaudio menu though).  This could be kind of cool for making field recordings or something but again, not quite the multi-tracking dream I had in mind.

***Thanks for reading this far!***

A couple of weeks ago, I sold the 828mkII and purchased a Presonus Firepod 2nd hand after hearing some success stories.  It arrived earlier this week, and sadly it appears to be a dud unit, having this [well-documented problem]("http://forums.presonus.com/posts/list/3082.page").  I spent a whole day messing around trying to get it to work, but after I couldn't even use it with Windows, I knew something was up.  So now I'm going through the annoying process of sending it back to the guy (all the way back to Texas from Australia).

My question to you all is, please, help me choose a suitable recording device.  Firewire, USB, PCI, I don't care, as long as it can work with Linux.  All I want to do is some recording!

Should I try again with another Presonus Firepod/FP10?  They seem kind of hard to come by in my part of the world.  I've been burned but I will persist with them for the sake of recording in Linux if anyone here can tell me it's the best option.  Other names I've heard thrown around are Edirol FA-101, Lexicon Omega Studio, Echo Audiofire 8/12... thinking more about compatibility than price range or specific number of ins/outs at this point.

I've been poring over the pages at [ffado.org]("http://www.ffado.org/?q=devicesupport/list"), [linuxstudiopro.com]("http://linuxstudiopro.com/#") and [alsa-project.org]("http://www.alsa-project.org/main/index.php/Matrix:Main"), but some of the stories there are kind of dated, it seems like a lot of devices that have worked well for people in the past aren't being manufactured anymore.  Kind people of ubuntuforums... I'd love to hear your success stories.  Please tell me what has worked for you!

:tongue:

---

### Post by pepun on 2011-09-03
Hey eqyiel!

Don't know if this is any help for you... but I'm pretty happy with a Focusrite Saffire Pro 24!
It might not be the best option for live recording since it has only two mic inputs. But it works pretty well with Jack and ffado. You just need some time to get used to the ffado-mixer interface, though.

Plus... if you need more inputs... people reported the Saffire Pro 40 to work well with ffado, too.

Soo... perhaps it helps...!
Let me know if you need any more infos about this interface.

---

### Post by jejeman on 2011-09-03
I have Edirol FA-66 and it works without any problems (so far) in Lucid (and puppy studio 3.3) on my computer. I didn't really stressed the setup, but I don't think there will be problems when I do.
The card has only 4 analog inputs, so it's not so suitable for band recording.

---

### Post by eqyiel on 2011-09-03
Wow, thanks for your replies!

> **pepun said:**
> Don't know if this is any help for you... but I'm pretty happy with a Focusrite Saffire Pro 24!
It might not be the best option for live recording since it has only two mic inputs. But it works pretty well with Jack and ffado. You just need some time to get used to the ffado-mixer interface, though.

Plus... if you need more inputs... people reported the Saffire Pro 40 to work well with ffado, too.


This looks great!  Initially while I was browsing through the supported FFADO device list, I skimmed over these two because they were marked as "Experimental", but after you told me that I found [this thread.]("http://www.ffado.org/?q=node/863") Unheard of!  That's so exciting that Focusrite is actively pushing driver development for their interfaces.

> **jejeman said:**
> I have Edirol FA-66 and it works without any  problems (so far) in Lucid (and puppy studio 3.3) on my computer. I  didn't really stressed the setup, but I don't think there will be  problems when I do.
The card has only 4 analog inputs, so it's not so suitable for band recording.

This looks like it would be a perfect replacement for the Mbox!  I notice though that they are now marketed as "Cakewalk FA-66," do you know if this is just an exercise in re-branding or whether the device is actually the same?
For comparison, [Edirol,]("http://www.production-room.com/gfx/products/large/edirol-fa66---2.jpg") [Cakewalk.]("http://cdn.head-fi.org/1/19/19fdc59e_CAKEWALK20FA-6620EN20MULTISON.jpg")

I think I'm dribbling a bit now.

---

### Post by jejeman on 2011-09-03
I don't know if they are the same. I have Edirol edition. They look absolutly same.

---

### Post by sgx on 2011-09-05
Probably just rebranding, I think Roland owns the works. Sometimes a new model is released after the techies make one with a reduced number of components. And pass the savings on to the boss.

Another solid option is the delta series of pci cards,
a few people sync two mAudio Delta 1010LT pci cards in one computer
for 16 analog ins and 4 mic ins

[http://www.m-audio.com/products/en_us/Delta1010LT.html](http://www.m-audio.com/products/en_us/Delta1010LT.html)

sync two 1010s:

[http://www.jrigg.co.uk/linuxaudio/ice1712multi.html](http://www.jrigg.co.uk/linuxaudio/ice1712multi.html)

Cheers
I use an maudio24/96 pci revision2 for years without problems,
analog, midi and digital i/o, used price around $40 or so.

---

### Post by eqyiel on 2011-09-12
Hi everyone, I have decided to go with the Focusrite Saffire Pro 40, because it seems out of all of these to be the most similar to my original setup.  When I get it, I'll hopefully be able post here the steps I took to get it working!

---

### Post by oscarivera9 on 2011-09-13
This is a bit small compared with the Focusrite but it might something you might want to look into for some quick setup work.  It works great:  the Lexicon Alpha.  It's under $80 US dollars.

---

### Post by eqyiel on 2011-09-21
It's been a while!  Thanks for your input everyone!  I hope this thread helps someone else to select an interface in the future.  The Focusrite arrived a day or two ago, for the sake of future users here's how I managed to get it recording in Ardour on [vanilla Maverick]("http://releases.ubuntu.com/10.10/").

Why Maverick?

Because in Natty the legacy stack has been removed, and the new stack currently only supports recording (not playback).  I can only assume that the FFADO developers are working on this... In Lucid, the FFADO drivers available in the repositories (libffado2.0.0) are do not work with the Saffire Pro 40.  Maverick alone satisfies both criteria of having the old stack as well as libffado 2.0.1 in its repositories.  I was alerted to this fact [here.]("http://www.ffado.org/?q=node/862#comment-11198")

It may be that it will work on other Ubuntus if you compile FFADO yourself, but I was unable to get it working using the steps over at [http://subversion.ffado.org/wiki/Dependencies/Ubuntu](http://subversion.ffado.org/wiki/Dependencies/Ubuntu).

My device was brand new, so initially I had trouble setting up ffado-mixer correctly.  Following the advice [here]("http://ubuntuforums.org/showpost.php?p=9490115&postcount=12"), I used Windows XP with a firewire card to install the Focusrite drivers from the CD (without connecting to the internet -otherwise it tries to update the installer and perhaps the firmware - I have come to be very suspicious of this making things not work properly and what not!!). From the newly installed Saffire MixControl,  File > Restore Factory Defaults > Save To Hardware. Thankfully, that's all I had to do using Windows, which is more than I can say for my Ipod Classic...

Now, from Maverick.  In a terminal, type:

```
sudo apt-get update && sudo apt-get install ubuntustudio-controls ardour libffado2 ffado-dbus-server ffado-tools ffado-mixer-qt4
```Select yes when jack asks for access to realtime priority.  After that is finished, go System > Administration > Users and groups > Advanced Settings > User Privileges.  Check "use audio devices" and "use video devices" (video devices may not be necessary, but that's what I did).

Next, go System > Administration > Ubuntu Studio Controls.  Check all three boxes.  I don't know yet if these settings are optimal, but I chose 70% memlock, -3 nice.  If someone knows a more elegant way to do this, i.e. from the terminal rather than installing the ubuntustudio-controls package, please let me know. 

Next, in a terminal type:
```

sudo nano /etc/modprobe.d/blacklist-firewire.conf
```Make it look like this:

```
#blacklist ohci1394
#blacklist sbp2
#blacklist dv1394
#blacklist raw1394
#blacklist video1394

blacklist firewire-ohci
blacklist firewire-sbp2
```Rebuild initramfs.  Don't skip this if you want these settings to be permanent.
```

sudo update-initramfs -k all -u
```add dv1394 and raw1394 to /etc/modules
```
sudo nano /etc/modules
```Now you can reboot, pray, start the Saffire Pro 40 and start ffado-mixer.  If everything's okay it will ask you to register your device with FFADO to prove that linux users do exist or somesuch.  Hooray!

Start Jack Control, choose firewire, start Jack server, start Ardour.  That's it!  I haven't tested this in a recording environment yet, but I'm able to get sound from every input which is leagues ahead of anything else I have experienced in Linux so far.  I'll give updates in a week or so and mark as solved if everything's still okay.  Thanks for reading, hopefully this will encourage you guys to post the steps you took to get your hardware working and we can get some great reference material around here!

PS.  8ms latency without even installing the lowlatency kernel!

Notes:

[LIST]
[*]I'm a newbie, if there's a better way to do any of this please let me know.
[*]Tested using Ricoh Co Ltd R5C832 IEEE 1394 Controller on a Dell Inspiron 9400.
[*]I'm not very knowledgeable about security, but I heard that having  a firewire card poses a security risk.  To counter this, I think you  can just blacklist everything here and sudo modprobe the drivers as  needed.  SECURITY EXPERTS!  Please tell me if this reasoning is sound.   I'm only a little bit paranoid.
[*]essential reading: [https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)
[/LIST]

---

### Post by GhostofJohnToad on 2011-09-29
Thanks, eqyiel.  I am looking at getting a Focusrite so this was very informative and encouraging!  I interested on how it will perform in a live situation with everything going on at once.

---

### Post by dawiba on 2011-09-29
I'm currently using a Saffire LE in regular Natty. Dell Studio with built in VIA firewire. Easiest setup I've had yet in Ubuntu.

Open Software Centre
Download Qjacktl
Download FFADO and Qtractor
Enable Realtime Priority in Jack when asked
Add myself to the audio group
Open Qjacktl and setup. Settings are as follows...
Server Path /usr/bin/jackd --sync
Driver firewire
Priority 60
Frames/Period 256. It will run as low as 64, but 256 makes it easy for the computer. I don't use any of the available softsynths either, so latency is not an issue.
Sample Rate 44100
Periods/Buffer 3
Start Jack and I'm good to go.

I also use Mixbus and Linuxdsp plugins and record my synth as midi through Qtractor and the audio into Mixbus. I hardly ever get xruns and overall, everything works really well. No need for RT or lowlatency kernels here :)

However, the Saffire is showing signs of it's age (all the jack sockets on the back have broken and I've had to do some running repairs to keep it working), so I'm looking at the M Audio 2496 (read only good stuff about this in Linux/Ubuntu) and a small mixer

---

### Post by eqyiel on 2011-10-04
> **dawiba said:**
> 
I also use Mixbus and Linuxdsp plugins and record my synth as midi through Qtractor and the audio into Mixbus. I hardly ever get xruns and overall, everything works really well. No need for RT or lowlatency kernels here :)


Awesome, if it ain't broke, don't fix it, huh?  Keep the linux pro audio success stories coming!!

> **GhostofJohnToad said:**
> Thanks, eqyiel.  I am looking at getting  a Focusrite so this was very informative and encouraging!  I interested  on how it will perform in a live situation with everything going on at  once.

This warms my heart.  I'm glad to hear it.

I've been having a hell of a time these last couple of weeks learning  about compiling custom kernels while kernel.org has been down!  My  missions since last time I posted have been to patch and compile a  realtime kernel, and then to do set everything up like I have it here in  Arch Linux (where I plan to migrate eventually).

What will be of interest for you about this is that I can now confirm  that it is possible to compile a custom kernel with the legacy firewire  stack if the new one doesn't play nice with FFADO and your device, like  the Saffire Pro 40.  I couldn't find any answers for this before I tried  it myself.  Seeing as the old stack is removed from the newer Ubuntu  kernels and both the current and lts Arch kernels, it looks like this is  just something that we'll have to do until FFADO catches up.

The realtime kernel is great!  I was noticing a few xruns in the plain  Maverick setup that I posted before, but with the realtime patch I can  set the frames/period as low as 64 with 4ms latency and no xruns at  all!!

For those of you who are interested, [this is the resource]("http://www.anticore.org/ratgentoo/index.php?page=004") that helped me  the most while I was unable to access the official realtime-patch  documentation.

When you run make localmodconfig, pay special attention to these queries:

```
FireWire driver stack (FIREWIRE) [N/m/y/?] n
Legacy alternative FireWire driver stack (IEEE1394) [N/m/y/?] (NEW) y
  OHCI-1394 controllers (IEEE1394_OHCI1394) [N/m/y/?] (NEW) y
  PCILynx controller (IEEE1394_PCILYNX) [N/m/y/?] (NEW) n
  Storage devices (SBP-2 protocol) (IEEE1394_SBP2) [N/m/y/?] (NEW) n
  IP networking over 1394 (experimental) (IEEE1394_ETH1394) [N/m/y/?] (NEW) n
  raw1394 userspace interface (IEEE1394_RAWIO) [N/m/y/?] (NEW) y
  video1394 userspace interface (IEEE1394_VIDEO1394) [N/m/y/?] (NEW) y
  dv1394 userspace interface (deprecated) (IEEE1394_DV1394) [N/m/y/?] (NEW) y
  Excessive debugging output (IEEE1394_VERBOSEDEBUG) [N/y/?] (NEW) n
```Obviously, if you need the legacy modules for the PCILynx controller  (whatever that is), sbp2 or IP networking, you need to select yes for  those ones too.

```
Preemption Mode
  1. No Forced Preemption (Server) (PREEMPT_NONE)
  2. Voluntary Kernel Preemption (Desktop) (PREEMPT_VOLUNTARY)
  3. Preemptible Kernel (Low-Latency Desktop) (PREEMPT_DESKTOP) (NEW)
  > 4. Complete Preemption (Real-Time) (PREEMPT_RT) (NEW)
```You want to select number 4.

I'm pretty sure you can compile the new stack as well if you need that  for other devices if you pay attention to which stack is currently  modprobed. I still haven't had a chance to test everything in a live  environment with the pressure on, just been recording a bit of guitar by  myself.  I'll be sure to tell you ASAP!

---

### Post by sgx on 2011-10-04
Fender Mustang 1 usb amp should be great for hassle free live linux setups. No kernel magic needed, it just shows up, ready for action.

[http://www.musiciansfriend.com/guitars/fender-mustang-i-20w-1x8-guitar-combo-amp/h61791000001000](http://www.musiciansfriend.com/guitars/fender-mustang-i-20w-1x8-guitar-combo-amp/h61791000001000)

linux Mustang patch editor reaches V1.0!

[http://piorekf.org/plug/](http://piorekf.org/plug/)

This has most of the funtions of the mac/windoze Fuse software.
Make fx chains, pre and post, choose from 12 Fender Amps, choose
the speaker cabinet, bias and sag on some models. Save 24 presets
available on the amps dial. Process further in Rakarrack, Calf, Guitarix, LV2 rack, as desired.

---

### Post by dawiba on 2011-10-04
[QUOTE=eqyiel]Awesome, if it ain't broke, don't fix it, huh?[/QUOTE]

Umm..I wasn't bragging or anything, I was just replying to this sentence of yours in post #9

[QUOTE=eqyiel]Thanks for reading, hopefully this will encourage you guys to post the steps you took to get your hardware working and we can get some great reference material around here![/QUOTE]

I guess I've been pretty lucky with my set up in comparison to some others. It pretty much 'just worked'. Sorry if you took my post the wrong way.

---

### Post by eqyiel on 2011-10-04
> **dawiba said:**
> Umm..I wasn't bragging or anything, I was just replying to this sentence of yours in post #9



I guess I've been pretty lucky with my set up in comparison to some others. It pretty much 'just worked'. Sorry if you took my post the wrong way.

Sorry for making you worry!  I wasn't trying to be sarcastic or clever or anything.  Honestly, I'm happy that it works so well for you!!

> **sgx said:**
> This has most of the funtions of the mac/windoze Fuse software.
Make fx chains, pre and post, choose from 12 Fender Amps, choose
the speaker cabinet, bias and sag on some models. Save 24 presets
available on the amps dial. Process further in Rakarrack, Calf, Guitarix, LV2 rack, as desired.

Thanks for bringing this to my attention.  At first it was so alien to me, I've never heard of Fuse until now or seen anything like this amp before!  Crazy how many pies Fender has their fingers in these days, you would think that after so long of making guitars and amps that they wouldn't need to start developing software...

---

