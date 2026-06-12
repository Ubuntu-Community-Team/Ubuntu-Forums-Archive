---
title: "USB Audio Devices for use as primary sound"
date: 2009-06-10
forum: Ubuntu Studio
---

### Post by bcschmerker on 2009-06-10
I am currently researching workarounds for a defective Realtek ALC-882 on my Everex' [Gigabyte MA78GM-S2HP](http://www.gigabyte.com.tw/) micro-ATX 'board running Ubuntu 8.04-LTS (LinUX Kernel 2.6.24-24-generic); replacing the chip is considerately more expensinve than bypassing it due to the need for specialized tools to deal with surface-mounted integrated circuits.  GStreamer Properties, GNOME Sound Properties, ASoundConf-GTK, etc. all recognize a Dynex microphone that I used for proof of concept, so any of a range of USB Audio devices may work as my interim primary sound device.

As of 9 June 2009, the Sing And Record Engine at [SingSnap](http://www.singsnap.com/) does not detect non-default audio devices on LinUX systems, so an offboard sound card (e.g., Creative Labs X-Fi Go!) or mixer (e.g., Behringer Xenyx 1202FX, Mackie ProFX12) will be needed.  Having a [Nady DKW-3 VHF wireless handheld mic system](http://www.nady.com/), I am leaning toward a mixer.  What has the community experience been with USB mixers and soundcards by make and model?  Details will help me narrow down candidates for my new sound device.

---

### Post by jukingeo on 2009-06-29
I have the same version of Ubuntu Studio on my machine and I have been exploring the idea of USB sound for a long while now.  Thusfar my findings have not been good.

I have an M-Audio Delta44 sound card that does work right out of the box with Ubuntu, but the thing is that the card is 4 1/4" plugs in and 4 1/4" plugs out.  Not exactly convenient to hook up speakers too as I need an amp.

There are limitations to USB recording, for one, I think you are strapped in to 96k.  I have not seen a single USB device that breaks this barrier.  There may be speed and latency issues as well.

The more promising avenue seems to be Firewire.  FFADO is a new system that supposed to support firewire devices running through Jack.  The problem was that Jack didn't come with it and it was a pain to set it up.

Now I have been out of the loop for a while and I am wondering f the new version of Ubuntu Studio, Jaunty (9.04) will offer fully FFADO support.  While firewire devices are more expensive than their USB counterparts, they generally offer better performance.

One thing I do know if that you are going to go the USB route, you must physically disable your on-board sound.  Setting up one sound device is bad enough in Ubuntu, but if it sees two cards (even though the on-board one isn't working), you could be in a world of trouble trying to set it up.

Also when looking on the ALSA site for supported devices, be careful.  Not everything there that is listed as 'supported' will work.  I have had mucho trouble with the Echo line of products which are labeled as 'supported' under ALSA.  The developer of the Alsa driver for the Echo line couldn't even help me.  In fact he barely answered my emails.  So the support is only as good as how far the developer is able to help you.

Needless to say, I sold the Echo sound device and took the forum's advice and bought the M-Audio Delta44.  This card was truly plug-n-play.  But it is more or less a pro-card and it doesn't have connectors on it to hood it up to computer speakers, which is why I was looking into alternatives as well.

Anyway, keep us posted if you find anything worthwhile that works.

---

### Post by markbuntu on 2009-06-30
You can change the default alsa device fairly easily so a pci card is not out of the question, just stay away from anything X-fi, pci or usb. You can also disable the on-board in bios so anything you plug in will become default. If you are lucky this will happen automatically. If not it is fairly easy and painless to fix.

You should look around in this forum before deciding on hardware. It will also give you a good idea on how to get it working properly.

---

### Post by jukingeo on 2009-07-03
> **markbuntu said:**
> You can change the default alsa device fairly easily so a pci card is not out of the question, just stay away from anything X-fi, pci or usb. You can also disable the on-board in bios so anything you plug in will become default. If you are lucky this will happen automatically. If not it is fairly easy and painless to fix.

You should look around in this forum before deciding on hardware. It will also give you a good idea on how to get it working properly.

Hello Mark, seen you around in the past a lot and have quick semi related question for you.

Ok, so it seems like usb audio is still a problem, but how is firewire faring?  Last I heard they were working on a change over from FreeBob to FFADO.  I am still on Ubuntu Studio Hardy (8.04).  Apparently they didn't have an Ubuntu Studio Intrepid (8.10), but I DID notice that they have an Ubuntu Studio for 9.04.  I was hoping that this version of US comes with the updated version of Jack which supports FFADO natively.  I know that you can manually add FFADO, but it is a huge pain in the neck.

So I am wondering if you heard something down the Firewire pike about any improvements there.  If so, then Firewire might be a better choice than USB.  For certain, it is faster than USB.  

Thanx,

Geo

---

### Post by trulan on 2009-07-04
Ubuntu Studio 9.04 does indeed come with ffado natively installed, and it works quite well.  It's a bit of a pain setting up permissions for raw firewire (1394) access (and they say it's a security risk) but it's doable.

I have however had mixed success with Jaunty.  It works great on my desktop (AMD64) but I had to wipe it and put Hardy on my laptop (Dell Inspiron 1505) because the Jaunty real time kernel kept freezing on that machine.  But I was able to get ffado working on it under Hardy as well.  Not a huge pain in the neck, just a moderate one.

---

### Post by sgx on 2009-07-04
> **jukingeo said:**
> 
snip

I have an M-Audio Delta44 sound card that does work right out of the box with Ubuntu, but the thing is that the card is 4 1/4" plugs in and 4 1/4" plugs out.  Not exactly convenient to hook up speakers too as I need an amp.
 Hi, adaptors for your cabling needs are plentiful and cheap. Do you live in an area retailers of these are far away?

---

### Post by jukingeo on 2009-07-05
> **trulan said:**
> Ubuntu Studio 9.04 does indeed come with ffado natively installed, and it works quite well.  It's a bit of a pain setting up permissions for raw firewire (1394) access (and they say it's a security risk) but it's doable.

That is good to know that FFADO does come set up with Jack, but I am surprised that it is still a pain to set it up.  My issue with Hardy was getting FFADO to work...many times I messed up Jack and had to reinstall it.  I never got it to work.

> I have however had mixed success with Jaunty.  It works great on my desktop (AMD64) but I had to wipe it and put Hardy on my laptop (Dell Inspiron 1505) because the Jaunty real time kernel kept freezing on that machine.  But I was able to get ffado working on it under Hardy as well.  Not a huge pain in the neck, just a moderate one.

For some reason, I been noticing this to be a pattern with Ubuntu.  The newly released version is very unstable and has problems.  It usually takes about 4 months or so of patches before it finally becomes stable.  Then they release a new unstable version.  I heard this story when I first started with Ubuntu.  I had version 6.04 when I started and was told it was too old, so I upgraded to Hardy which was then current.  I went with the Ubuntu Studio version since I want to do audio and video editing.  I had nothing but problems getting the hardware to work properly.  There were other issues too with Hardy and I was looking into other Linux distributions.  What I found out was much worse than what I was dealing with under Hardy!!  I tried Studio 64, OpenSUSE, and Dyne-Bolic and my problems with all three were worse than with Ubuntu.   The absolute most stable and fastest distribution I have is Puppy Linux.  I absolutely LOVE it...BUT there are issues with getting a stable real time kernel to work with it.  Also there are not many supported programs that work with it.   I still use Puppy though.

So anyway, I ended up getting the M-Audio Delta 44 sound card and this device cured most of my audio problems considering I bought it and was told it was Plug-N-Play with Linux and low and behold that is what it was.

Now the unfortunate thing is that the Delta 44 is pretty limited.  It has 4 1/4" line ins and 4 1/4" line outs.  There are no mic pre-amps and there is no midi.  I had to use a seprate box for that.

So SGX if you are reading along, this is why adapters will not help in my case.

Overall The Focusrite Saffire LE will handle just about all my needs.  BUT it is a Firewire device.  That is why I was inquiring about how FFADO was working with the new version of Ubuntu (Jaunty).

Geo

---

### Post by dawiba on 2009-07-05
If it helps, I'm running UbuntuStudio 9.04 on a Dell Latitude D505 with a Focusrite Saffire LE and it's working just fine now.

Here's what I've done.

I had similar freezing and crashing problems as others when running the rt kernel, so I downloaded the generic kernel and all the associated packages using Synaptic:

linux-generic, linux-headers-2.6.28-13, linux-headers-2.6.28-13-generic, linux-headers-generic, linux-image-2.6.28-13-generic, linux-image-generic, linux-libc-dev, linux-restricted-modules-2.6.28-13-generic, linux-restricted-modules-common, linux-restricted-modules-generic.

I then created a video and audio group and made myself a member of each. Then, in Ubuntu Studio Controls, I enabled memlock and set it to 90%, I enabled raw1394 access and I enabled nice and it's set to -10.

After rebooting, 

```
uname -a
```

confirmed I was using the generic kernel. I then opened Jack Control and selected Firewire from the dropdown menu, saved, clicked start and everything worked straight away and according to Jack, I'm running in realtime. I can now have Jack running, open Ardour and everything can be running quite happily for hours at a time with no x-runs or other problems. I can also have other audio and non audio programs open at the same time without any problems.

I access the internet through a router that has a firewall and I installed GUFW and enabled the firewall on the computer as well. I don't want to talk about security as the last time I did on a thread in here, it got moved to security and disappeared without trace without any answers to my question. I guess you just need to be careful as it appears to me you can't run Firewire devices without root access of some sort.

---

### Post by bcschmerker on 2009-07-07
Thank you, all Posters this Thread, for the heads up on emerging capabilities concerning IEEE 1394, a subsystem, I have not yet tested on my Gigabyte 'board under Kernel 2.6.24-24.  At this stage, it is beginning to look as though the mixer option will still be Mackie, in this case Onyx 1620 + Onyx FireWire in for ProFX12.  I'll investigate other audio devices for IEEE 1394 for proof of concept; what I still do not know at present is whether the Sing And Record Engine at SingSnap will detect IEEE 1394 audio devices via the Setup Wizard, running through Mozilla Firefox 3-up and ALSA (it only picked up the default device, viz., the bad Realtek chip, on my system under Ubuntu but does pick up all accessible audio devices in Microsoft Windows XP, Vista and presumably 7 Beta).

I may still be forced to wait until Autumn 2009 for Ubuntu 10beta1 Limber to be released for testing as an OS upgrade, as the ALSA Snd-CTXFi driver (which I would need to run the Creative Laboratories Sound Blaster X-Fi Titanium Fatal1ty Professional, currently the best-shielded sound card within my anticipated budget restrictions) is planned for Kernel 2.6.31 and 9.1beta7 Karmic still packs 2.6.30.  Creative Laboratories seems to be pulling the plug on support for not only the Audigy series, but the E-mu 0404 and 1010; none of these E-mu 10K2-based cards are as well-shielded as I'd like for my system.

---

### Post by jukingeo on 2009-07-08
> **dawiba said:**
> If it helps, I'm running UbuntuStudio 9.04 on a Dell Latitude D505 with a Focusrite Saffire LE and it's working just fine now.

Here's what I've done.

I had similar freezing and crashing problems as others when running the rt kernel, so I downloaded the generic kernel and all the associated packages using Synaptic:

linux-generic, linux-headers-2.6.28-13, linux-headers-2.6.28-13-generic, linux-headers-generic, linux-image-2.6.28-13-generic, linux-image-generic, linux-libc-dev, linux-restricted-modules-2.6.28-13-generic, linux-restricted-modules-common, linux-restricted-modules-generic.

I then created a video and audio group and made myself a member of each. Then, in Ubuntu Studio Controls, I enabled memlock and set it to 90%, I enabled raw1394 access and I enabled nice and it's set to -10.

After rebooting, 

```
uname -a
```

confirmed I was using the generic kernel. I then opened Jack Control and selected Firewire from the dropdown menu, saved, clicked start and everything worked straight away and according to Jack, I'm running in realtime. I can now have Jack running, open Ardour and everything can be running quite happily for hours at a time with no x-runs or other problems. I can also have other audio and non audio programs open at the same time without any problems.


So did you install Ubuntu Studio first and then installed the generic kernel or did you install it afterwards?

Is FFADO now a part of Jack in 9.04?

> **bcschmerker said:**
> 

I may still be forced to wait until Autumn 2009 for Ubuntu 10beta1 Limber to be released for testing as an OS upgrade, as the ALSA Snd-CTXFi driver (which I would need to run the Creative Laboratories Sound Blaster X-Fi Titanium Fatal1ty Professional, currently the best-shielded sound card within my anticipated budget restrictions) is planned for Kernel 2.6.31 and 9.1beta7 Karmic still packs 2.6.30.  Creative Laboratories seems to be pulling the plug on support for not only the Audigy series, but the E-mu 0404 and 1010; none of these E-mu 10K2-based cards are as well-shielded as I'd like for my system.

Oh, so they are working on the problem with getting the Creative Labs X-Fi to work?  I remember that I did get the X-Fi to work in 8.04.  I had to use a custom kernel build...BUT the problem was that it wasn't real time.  Another issue was that I switched video cards and I have an ATI card now.  So the custom kernel build didn't like that too much either.  I ended up pulling the X-Fi in favor of the Delta 44 which was automatically recognized by Linux.

But right now I would like to get firewire to work with Jack as I need something with more features than the M-Audio Delta 44 provides.

Geo

---

### Post by dawiba on 2009-07-08
> **jukingeo said:**
> So did you install Ubuntu Studio first and then installed the generic kernel or did you install it afterwards?

Is FFADO now a part of Jack in 9.04?

I did a clean install of Ubuntu Studio, let it update through Update Manager and then the first thing I did was to install and reboot into the generic kernel. I then went on to add more software as I needed. If I used the rt kernel instead, then freezes and hangs would follow.

FFADO is definitely one of the options in Jack using 9.04 although it's listed as 'firewire' in the dropdown menu. The FFADO drivers are preinstalled, so if you want, you can just use Ubuntu Studio Controls to set things up the way that I've done.

I've attached a screenshot of Jack to show my settings.

---

### Post by jukingeo on 2009-07-08
> **dawiba said:**
> I did a clean install of Ubuntu Studio, let it update through Update Manager and then the first thing I did was to install and reboot into the generic kernel. I then went on to add more software as I needed. If I used the rt kernel instead, then freezes and hangs would follow.

FFADO is definitely one of the options in Jack using 9.04 although it's listed as 'firewire' in the dropdown menu. The FFADO drivers are preinstalled, so if you want, you can just use Ubuntu Studio Controls to set things up the way that I've done.

I've attached a screenshot of Jack to show my settings.

Wow that is interesting.  Nice to know that FFADO is working great with the Saffire LE.  I see you were able to check off the realtime option.  So then the generic kernel supports R-T?  That was one of the problems when I first tried a generic kernel with the Creative X-Fi, it wouldn't go into RT.  

This new info MIGHT prompt me to go with the upgrade...however, I never did a full upgrade of Ubuntu Studio before.  I am on a triple boot system using Grub bootloader to boot into Ubuntu, Puppy Linux, or Windows XP.  Naturally I don't want to mess my machine up.  I might wait a bit though because I heard Jaunty is a little "jumpy"...if you know what I mean.

Thanx,

Geo

---

### Post by trulan on 2009-07-08
It is possible to use ffado without upgrading to Jaunty - it actually works better in my experience.  Using the info here:
[http://ardour.org/node/2660](http://ardour.org/node/2660)
You'll want to upgrade Jack, Ardour, and install ffado.  The ppa used by this how-to says it is being taken down, but it looks like it is still up.

So if you'd like to hang on to Hardy a bit longer (don't blame you), that's another option.

---

### Post by dawiba on 2009-07-08
> **jukingeo said:**
> Wow that is interesting. Nice to know that FFADO is working great with the Saffire LE. I see you were able to check off the realtime option. So then the generic kernel supports R-T? That was one of the problems when I first tried a generic kernel with the Creative X-Fi, it wouldn't go into RT.

When you say 'check off' realtime, I take it you mean that it's enabled?

I've attached another screenshot. I don't know if you can see it all, but in the picture I'm running;

Evolution, Firefox, Jack Control (which shows 'RT' in the panel), Terminal (showing the regular kernel), Ardour, Aqualung and Ubuntu One is connected as well. There's no way I could do this using the rt kernel.

I don't pretend to understand why or how, but it works :D

---

### Post by jukingeo on 2009-07-08
> **dawiba said:**
> When you say 'check off' realtime, I take it you mean that it's enabled?

Yes

> 

I've attached another screenshot. I don't know if you can see it all, but in the picture I'm running;

Evolution, Firefox, Jack Control (which shows 'RT' in the panel), Terminal (showing the regular kernel), Ardour, Aqualung and Ubuntu One is connected as well. There's no way I could do this using the rt kernel.

I don't pretend to understand why or how, but it works :D

Yes, I do see RT in the panel, but it is dimmed.  However, you also have Jack in the 'stopped' mode.  Does it come up fully bright "RT" when you are running?

Geo

---

### Post by dawiba on 2009-07-09
> **jukingeo said:**
> Yes, I do see RT in the panel, but it is dimmed. However, you also have Jack in the 'stopped' mode. Does it come up fully bright "RT" when you are running?

Geo

The 'RT' is dimmed because that just happened to be the moment I took the screenshot. Normally, it 'flashes' for want of a better way of putting it. If I timed it better, I could get a picture of it 'bright' :)

The 'Stopped' just means that Jack transport isn't running. I could have started Ardour from Jack and then it would say 'Rolling', but I prefer running things from Ardour.

I've attached another screenshot which is probably what you want to see.

---

### Post by jukingeo on 2009-07-09
> **dawiba said:**
> The 'RT' is dimmed because that just happened to be the moment I took the screenshot. Normally, it 'flashes' for want of a better way of putting it. If I timed it better, I could get a picture of it 'bright' :)

The 'Stopped' just means that Jack transport isn't running. I could have started Ardour from Jack and then it would say 'Rolling', but I prefer running things from Ardour.

I've attached another screenshot which is probably what you want to see.

Yes, I remember that it was flashing and not steady on when in RT mode.  I guess that proves that it IS working. 

I probably will look into it once I found out all the issues with Jaunty.  I have not delved into the exact issues yet, just that I heard it is buggy.

---

### Post by bcschmerker on 2009-07-11
> **jukingeo said:**
> That is good to know that FFADO does come set up with Jack, but I am surprised that it is still a pain to set it up.  My issue with Hardy was getting FFADO to work...many times I messed up Jack and had to reinstall it.  I never got it to work....

So anyway, I ended up getting the M-Audio Delta 44 sound card and this device cured most of my audio problems considering I bought it and was told it was Plug-N-Play with Linux and low and behold that is what it was.

Now the unfortunate thing is that the Delta 44 is pretty limited.  It has 4 1/4" line ins and 4 1/4" line outs.  There are no mic pre-amps and there is no midi.  I had to use a seprate box for that....

Overall The Focusrite Saffire LE will handle just about all my needs.  BUT it is a Firewire device.  That is why I was inquiring about how FFADO was working with the new version of Ubuntu (Jaunty).

GeoMy own tests with the Everex have proved USB Audio fully workable within a 96 kHz maximum sample rate; unfortunately, the MIDI trend is toward separate USB devices from the audio rigging.  I'll probably be stuck with Ubuntu 8.04-LTS Hardy until 10beta1 Limber becomes available for testing Autumn 2009, as 10.04 is the next release to be long-term-supported; 10beta1 is almost certain to pack FFADO support, as does 9.04 Jaunty and will 9.10 Karmic.

Unlike the [M-Audio Delta 44](http://www.m-audio.com/products/en_us/Delta44.html), the [Mackie ProFX12](http://www.mackie.com/products/profxseries/) is a full-on live sound mixer with one high-Z and six mic preamps, plus 32-bit DSP, in addition to integrated USB I/O; the Onyx Series, which includes an optional [FireWire adapter module](http://www.mackie.com/products/onyxfirewire/index.html) is the equivalent for IEEE 1394.

---

### Post by jukingeo on 2009-07-27
> **bcschmerker said:**
> 
Unlike the [M-Audio Delta 44](http://www.m-audio.com/products/en_us/Delta44.html), the [Mackie ProFX12](http://www.mackie.com/products/profxseries/) is a full-on live sound mixer with one high-Z and six mic preamps, plus 32-bit DSP, in addition to integrated USB I/O; the Onyx Series, which includes an optional [FireWire adapter module](http://www.mackie.com/products/onyxfirewire/index.html) is the equivalent for IEEE 1394.

...AND you have tested this Mackie unit have have proved it to work?

---

### Post by sgx on 2009-07-27
Hi, maybe consider an affordable yet excellent external pre-amp from ART, and a 2x2 midi interface from m-audio (there is a firmware package for those.) I would not scrap the stable, quality Delta recording ability, in hopes of some miracle-x-fi event in a distant future!
Cheers

---

### Post by bcschmerker on 2009-07-28
> **sgx said:**
> Hi, maybe consider an affordable yet excellent external pre-amp from ART, and a 2x2 midi interface from m-audio (there is a firmware package for those.) I would not scrap the stable, quality Delta recording ability, in hopes of some miracle-x-fi event in a distant future!
CheersThe wait to test Ubuntu Lucid Lynx is as much for FFADO in a long-term-supported distribution as for ALSA and Kernel support for the E-mu 20k1/20k2; as I understand things, several have tried to put FFADO on 8.04-LTS, without success.

Judging from the consistent performance of a [SIIG USB SoundWave 7.1 Pro](http://www.siig.com/) that I've been testing as an alternate for a bum [Realtek ALC889](http://www.realtek.com.tw/), the [Mackie ProFX12](http://www.mackie.com/) should work well enough for my requirements.  According to Mackie's [Pro-FX User Manual, Appendix D](http://www.mackie.com/products/profxseries/pdf/profx-qs.pdf), the USB Interface has Thru selectable to enable or disable USB audio send (from the computer) mixback into the USB audio return (to the computer).  The Onyx 1640 route requires FFADO, which was first available in Ubuntu 9.04, if memory serves me correctly.

---

### Post by trulan on 2009-07-28
I'll say it again:  I have 8.04 Studio LTS **with FFADO** running on my laptop, and it is working excellently.  It most certainly can be done, and was not difficult at all.

FFADO is not available in the Hardy repositories, and it will not work with the version of Jack that is in the Hardy repositories.  So you either need to build these yourself or find somewhere to get them (such as the ppa I linked in my previous post.)  I don't know how to build stuff myself yet so I used the ppa.

---

### Post by bcschmerker on 2009-07-28
> **trulan said:**
> I'll say it again:  I have 8.04 Studio LTS **with FFADO** running on my laptop, and it is working excellently.  It most certainly can be done, and was not difficult at all.

FFADO is not available in the Hardy repositories, and it will not work with the version of Jack that is in the Hardy repositories.  So you either need to build these yourself or find somewhere to get them (such as the ppa I linked in my previous post.)  I don't know how to build stuff myself yet so I used the ppa.Which explains some of the difficulties that I encountered attempting to get the package from FFADO.org.  Thanks for the heads up; I'll see about landing BZip2's of source for both JACK and FFADO in this case.

---

### Post by wenko on 2009-09-11
I am in the process of building a home recording studio for pod-cast style recording. The breadth of the recording will be spoken voice (voice tracking for multimedia apps). Regardless the mixer we have purchased is the Mackie ProFX12 and I want to confirm that that unit will work under Either Ubuntu or Ubuntu studio. For me the best situation would be for the mackie to appear as a sound card. 

Anyone experienced with this unit in Nix? I want to avoid Windows like the plauge and really do not want to resort to purchasing a seperate A-to-D.

Thanks

---

### Post by bcschmerker on 2009-09-12
Judging from my experience with a [SIIG® USB SoundWave 7.1 Pro](http://www.siig.com/), the [Mackie® ProFX12](http://www.mackie.com/) should in fact be detected as a USB audio device, with both alsa_output.usb_device and alsa_input.usb_device entries in the PulseAudio Manager.  With ASoundConf-GTK, the ProFX12 can be selected as Default sound device.

---

### Post by jukingeo on 2009-09-12
> **trulan said:**
> I'll say it again:  I have 8.04 Studio LTS **with FFADO** running on my laptop, and it is working excellently.  It most certainly can be done, and was not difficult at all.

FFADO is not available in the Hardy repositories, and it will not work with the version of Jack that is in the Hardy repositories.  So you either need to build these yourself or find somewhere to get them (such as the ppa I linked in my previous post.)  I don't know how to build stuff myself yet so I used the ppa.

The link you mentioned links to the ppa you suggested and instructs how to install FFADO.  However, I don't see where to get the correct version of Jack.  Where do you get that?  Do you have to uninstall the old Jack first?

Thanx,

Geo

---

### Post by trulan on 2009-09-13
> **jukingeo said:**
> The link you mentioned links to the ppa you suggested and instructs how to install FFADO.  However, I don't see where to get the correct version of Jack.  Where do you get that?  Do you have to uninstall the old Jack first?

Thanx,

Geo
I didn't uninstall Jack, just added the ppa to my sources.  Then, in synaptic, I upgraded Jack, upgraded Adrour, and installed ffado.  I think that's all you should need to do, unless you have already installed Jack from a source other than the Hardy repository.  (or maybe they have upgraded Jack in the main repos - I haven't checked.)

Alternately, I guess you could download the debs from the ppa and install them that way.

The version of Jack in that ppa is 0.116.1-3.

---

### Post by jukingeo on 2009-09-13
> **trulan said:**
> I didn't uninstall Jack, just added the ppa to my sources.  Then, in synaptic, I upgraded Jack, upgraded Adrour, and installed ffado.  I think that's all you should need to do, unless you have already installed Jack from a source other than the Hardy repository.  (or maybe they have upgraded Jack in the main repos - I haven't checked.)

Ok, I did go into synaptic and checked my current installations for Ardour and Jack...indeed they were older versions.  Right clicking on them did show the upgrade tab.  So I did that.

Just to give you a heads up, my Ubuntu install was made fresh from an Ubuntu Studio Hardy install disk.  So the version of Jack I have was included with that bundle

> 
The version of Jack in that ppa is 0.116.1-3.

Ok, that seems like you have an older version that I do.   The version I just upgraded to is 0.3.4. Is that good or not?   Supposedly the current build was from Feb, 2009 which is prior to your first post in this thread.

Oh!  outside of Jack & Ardour, do any other programs need to be updated to take advantage of firewire or no?

Thanx,

Geo

---

### Post by trulan on 2009-09-13
> **jukingeo said:**
>  Ok, that seems like you have an older version that I do.   The version I just upgraded to is 0.3.4. Is that good or not? That would be the version of qjackctl, or Jack Control.  Your version of jackd will now be at 0.116.1-3. > **jukingeo said:**
> Oh!  outside of Jack & Ardour, do any other programs need to be updated to take advantage of firewire or no? A lot of the stuff in kashayar's ppa is experimental.  I would let everything else go (you did get Ffado, right? you need that.)  Apologies for this thread wandering off track.

---

### Post by jukingeo on 2009-09-13
> **trulan said:**
> That would be the version of qjackctl, or Jack Control.  Your version of jackd will now be at 0.116.1-3.  A lot of the stuff in kashayar's ppa is experimental.  I would let everything else go (you did get Ffado, right? you need that.)  Apologies for this thread wandering off track.

Oh, that was jackd you were referring to.  Generally when someone just says "Jack" it is referring to qjackctl.  That clears up a bunch right there!  Yes, I did check via Synaptic and I do have the correct version on my system now.

Yes, ffado was the first thing that I put on after I got set up for ppa.   Prior to that I was still on FreeBob. 

When I go into Jack now, it still says "Firewire" for the choice selection under 'sound device'.  Will it use ffado now?  Unfortunately I have no way to test it as I never did buy a firewire audio device.  But now I am prompted to do so since you mentioned you got it working with the Saffire LE, right?

Thanx,

Geo

---

### Post by trulan on 2009-09-14
Select 'Firewire' to use ffado as your audio driver, yes.

I'm running a Presonus Firepod.  The Saffire LE is listed on ffado's site as being fully supported, but I have no personal experience with it.

---

### Post by jukingeo on 2009-09-14
> **trulan said:**
> Select 'Firewire' to use ffado as your audio driver, yes.

I'm running a Presonus Firepod.  The Saffire LE is listed on ffado's site as being fully supported, but I have no personal experience with it.

Oh, Ok, the the only reason I mentioned it is because Jack does still have the Freebob dependencies loaded.  Should I remove those because Freebob is obsolete?  I don't want it to interfere with ffado.   Or is it ok to leave it as is?

Thanx,

Geo

---

### Post by trulan on 2009-09-15
Freebob won't interfere, just let it there.  Any Ubuntu Studio install (including the current Alpha version) will have both freebob and ffado.  The only other hitch you will probably run into is getting your permissions set correctly.  Using real time mode requires some permissions, and using a raw1394 (firewire) device requires an additional set of permissions.  I'd tell you how, but it's been a while since I did it on on Hardy, Jaunty is a bit different, and Karmic is different still - I'm afraid I would get it confused.  IIRC it's not very hard in Hardy, and there are some good how-to's out there.

---

### Post by jukingeo on 2009-09-15
> **trulan said:**
> Freebob won't interfere, just let it there.  Any Ubuntu Studio install (including the current Alpha version) will have both freebob and ffado.  The only other hitch you will probably run into is getting your permissions set correctly.  Using real time mode requires some permissions, and using a raw1394 (firewire) device requires an additional set of permissions.  I'd tell you how, but it's been a while since I did it on on Hardy, Jaunty is a bit different, and Karmic is different still - I'm afraid I would get it confused.  IIRC it's not very hard in Hardy, and there are some good how-to's out there.

Yeah, I am familiar with those settings.  There was a permissions file in a security folder and I think you have to set one of the settings to 'unlimited' and another buffer setting to "94" or something like that.  I would have to refresh my memory, but I think I do already have the correct settings.

Yes, I have heard that the newer versions of Ubuntu do have certain differences and that more then likely all your settings have to be redone.  I said to heck with that.  Ubuntu 8.04 happens to be an LTS version and will be supported for a while, so I am going to stick with it.

Once I have a good complete working version 8.04, I would like to 'can' the whole system on a disc and then I could always do a complete install on another machine with everything in place.  It just takes a long long time to get everything configured properly in Linux.   

When 8.04 first came out, it gave me nothing but problems, but with updates it did get better.  Also making changes and mods along the way has given me a pretty stable Linux machine as of now.  So that is another reason I want to stay with 8.04.

So now the only thing left for me to do is get a firewire device and test it out.

Thanx,

Geo

---

