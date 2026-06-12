---
title: "USB Audio Interfaces"
date: 2011-04-03
forum: Ubuntu Studio
---

### Post by timbolex on 2011-04-03
I am looking to buy a USB audio interface to use in Ubuntu Studio.  All the devices that have been suggested in previous forum posts or are listed on Linus/ALSA websites are no longer available at online retail sites.

What device should I buy from an online retail store that works with Ubuntu Studio?  I am looking for an entry level device (less that $200) with maybe 2 inputs.

TYIA

---

### Post by cfhowlett on 2011-04-05
I have had the Presonus 1Box (AudioBox) for about a month now and I'm quite pleased with it.  

Please see [http://ubuntuforums.org/showthread.php?t=1702228&highlight=presonus+1box]("http://ubuntuforums.org/showthread.php?t=1702228&highlight=presonus+1box") or [http://www.youtube.com/watch?v=XDL6fMQXIoE]("http://www.youtube.com/watch?v=XDL6fMQXIoE")

---

### Post by AutoStatic on 2011-04-06
Basically all class compliant USB1.1 audio devices should work. If you find a card of your liking, check the on-line manual for these terms (most manufacturers have manuals on-line).
I've heard the Cakewalk by Roland UA-25EX might have been taken out of production recently but if you could your hands on one of those you're sure you have a top notch audio card that works flawlessly with Ubuntu.

Best,

Jeremy

---

### Post by Pablo_F on 2011-04-06
> ...a top notch audio card that works flawlessly with Ubuntu.

Yes, but before buying anything USB, check your USB controller.

lspci |grep -i usb


If you find this:

USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller

You are very unlucky... Ths sad fact is that lots of computers have this chipset. :(

---

### Post by MBybee on 2011-04-07
> **Pablo_F said:**
> Yes, but before buying anything USB, check your USB controller.

lspci |grep -i usb


If you find this:

USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller

You are very unlucky... Ths sad fact is that lots of computers have this chipset. :(

Ok - as a person who has this... what specific issues should I be looking for? I'm in the market for something like the [M-Audio Fast Track Ultra]("http://www.m-audio.com/products/en_us/FastTrackUltra.html"). Are you saying you've had huge issues with the USB stuff on these chipsets?

---

### Post by AutoStatic on 2011-04-07
Yes. At work we have several machines with that chipset. Full Duplex (playback & capture at once) just doesn't work with USB soundcards, you'll get a 'broken pipe' ALSA error.

Best,

Jeremy

---

### Post by MBybee on 2011-04-07
> **AutoStatic said:**
> Yes. At work we have several machines with that chipset. Full Duplex (playback & capture at once) just doesn't work with USB soundcards, you'll get a 'broken pipe' ALSA error.

Best,

Jeremy

So this shouldn't impact a device with realtime monitoring in hardware, I would think. It sounds like it would cause a serious issue for the 'monitor while recording' in software though.

---

### Post by Pablo_F on 2011-04-07
> So this shouldn't impact a device with realtime monitoring in hardware, I would think. It sounds like it would cause a serious issue for the 'monitor while recording' in software though. 

Well, yes, you can set jack in capture only mode and do hardware monitoring.

(You might need jackd2. In my experience jackd1 does not even work in capture only with this chipset)

You can also do software monitoring with another card, for example, the onboard. For this you need alsa_out ("man alsa_out"). You could do, for example, "alsa_out -dhw:Intel". This is an example, check the name of your cards in the output of "cat /proc/asound/cards", between square brackets. 

However, not being able to use the card in duplex mode is a real chore because you need to restart jack if you want to use the card for playback, not only for software monitoring, but also for mixing, etc. You need jack to work in ardour, qtractor, even when you are not capturing. 

If you playback through the onboard with alsa_out, at least you don't have to restart jack when you change tasks in your workflow. This is very unfortunate anyway. I hope some day some one will solve the issue... 

Cheers, Pablo

---

### Post by MBybee on 2011-04-07
Not sure about other people, but issues like this have really discouraged me from spending a lot of time pursuing Linux for pro-audio.

Is there anyone who makes a 'turnkey/ready to run' system package for pro-audio? There's plenty for non-Linux, but it seems like a nice niche for someone on the Linux side.

---

### Post by AutoStatic on 2011-04-07
> **MBybee said:**
> Not sure about other people, but issues like this have really discouraged me from spending a lot of time pursuing Linux for pro-audio.This is an Intel bug, not a Linux one.

> **MBybee said:**
> Is there anyone who makes a 'turnkey/ready to run' system package for pro-audio?Yes, there are like 5 or 6 specialized distributions for this and there are also some specialized repositories.

Best,

Jeremy

---

### Post by MBybee on 2011-04-07
I know what you mean, but unless the same issue occurs with Win 7, it's still limited to Linux. I would love to test this, but I use firewire audio right now and can't even get that working at all under linux... hence buying a USB one :)


Someone really does need to work with System 76 or somebody to develop an Ubuntu Studio build. I would happily buy one, I'm planning to use them for my next rig anyhow.

---

### Post by MBybee on 2011-04-07
> **AutoStatic said:**
> This is an Intel bug, not a Linux one.

Yes, there are like 5 or 6 specialized distributions for this and there are also some specialized repositories.

Best,

Jeremy

Sorry - didn't see your response before I posted. Could you elaborate on these? I was under the impression that Ubuntu Studio was currently the best specialized distribution for doing pro-audio.

/edit Also - apologize for threadjacking a USB-on-Ubuntu Studio thread... :)

---

### Post by AutoStatic on 2011-04-07
> **MBybee said:**
> I know what you mean, but unless the same issue occurs with Win 7, it's still limited to Linux.Haven't tested with Win 7 but if I would've to believe the Intel documents on this Win 7 should have these issues too. Unless there are drivers available that work around these issues. I don't use Windows so I really wouldn't know.

> **MBybee said:**
> I would love to test this, but I use firewire audio right now and can't even get that working at all under linux... hence buying a USB one :)What kind of FireWire device do you have currently?

Specialized distro's:
[list][*][Tango Studio]("http://tangostudio.tuxfamily.org/en/tangostudio")
[*][AV Linux]("http://www.bandshed.net/AVLinux.html")
[*]Dream Studio
[*]KX Studio
[*]PureDyne
[*]Dyne:Bolic
[*]Musix
[*]ArtistX
[*]GnuGuitarix[/list]

Best,

Jeremy

---

### Post by MBybee on 2011-04-07
Currently an M-Audio FW 410.

---

### Post by AutoStatic on 2011-04-07
[http://ffado.org/?q=node/24](http://ffado.org/?q=node/24)

So it's not supported unfortunately :(

Best,

Jeremy

---

### Post by pedrogent on 2011-04-19
I've been wanting to make the switch completely now for [over three years]("http://brainstorm.ubuntu.com/idea/2800/").

Actually I want to move to Debian Squeeze, but that's beside the point. The lack of sound card support is the only thing that has stopped me switching from Windows, and later OS X, over these past three years.

Does anyone know a sound card (USB or FireWire) that definitely works in a plug & play fashion in a Debian/Ubuntu environment? This is for **playback only**. I don't wish to record. It's purely to act as an interface for my powered monitors.

Note, my motherboard has:

```
$ lspci | grep -i usb
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
```

I really wanna go Linux only. I'm sure there are many many others in my situation where sound is the only thing holding them back.

Cheers.

---

### Post by sgx on 2011-04-21
I recently purchased an maudio
Fast Track usb on closeout, and it appeared and functioned in linux without needing special configuration, though I have not tested it in a wide variety of linux versions.

I have my motherboard soundchip blacklisted, by entering its kernel module in the textfile /etc/modprobe.d/blacklist
The entry is simple, mine is 

blacklist snd_intel8x0

The lsmod command will list your modules, all the audio modules are
grouped together, yours may be different. maudio modules usually include ice1712 or ice1724 in the naming.

They make other usb models aimed more at listening, that are widely
available.
Cheers

---

### Post by pedrogent on 2011-04-21
> **sgx said:**
> I recently purchased an maudio Fast Track usb on closeout, and it appeared and functioned in linux without needing special configuration, though I have not tested it in a wide variety of linux versions.

I have my motherboard soundchip blacklisted, by entering its kernel module in the textfile /etc/modprobe.d/blacklist The entry is simple, mine is 

blacklist snd_intel8x0

The lsmod command will list your modules, all the audio modules are grouped together, yours may be different. maudio modules usually include ice1712 or ice1724 in the naming.

They make other usb models aimed more at listening, that are widely available.
Cheers

Hey sgx, thanks for your reply. When you say 'closeout' do you mean these aren't made any more? Would be a shame, altho' I think my cousin has one I could buy off him, or perhaps swap for my FireWire Solo.

So you just plugged it in and it worked (i.e. you could playback music)? If this is the case my 3+ year quest has come to its conclusion.

Blacklisting modules is no problem for me.

Out of interest, what does the following print for you?

```
lspci | grep -i usb
```

I've recently been told that USB audio plays up with the particular Intel USB controller I have (as seen in my post above).

Thanks for your help.

---

### Post by AutoStatic on 2011-04-21
> **pedrogent said:**
> Does anyone know a sound card (USB or FireWire) that definitely works in a plug & play fashion in a Debian/Ubuntu environment?USB1.1: Basically all class compliant audio devices
USB2: [http://ubuntuforums.org/showpost.php?p=10659800&postcount=4](http://ubuntuforums.org/showpost.php?p=10659800&postcount=4)
FireWire: All fully supported devices on the FFADO site: [http://ffado.org/?q=devicesupport%2Flist&filter0=&filter1=&op2=OR&filter2[]=perfect](http://ffado.org/?q=devicesupport%2Flist&filter0=&filter1=&op2=OR&filter2[]=perfect)

> **pedrogent said:**
> Note, my motherboard has:```
$ lspci | grep -i usb
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
```This probably rules out full duplex usage of USB audio cards. But since you're only interested in playback this is not a problem.

Best,

Jeremy

---

### Post by pedrogent on 2011-04-21
Hey Jeremy, thanks for the reply. The trick here is working out which USB devices are:

[LIST]
[*]Class-compliant
[*]The ones included in the group you describe as 'basically all'
[/LIST]

It'd be disappointing to buy a USB sound card only to find that it wasn't class-compliant, or not in the above mentioned group, or both.

Class-compliance is an interesting topic. My FireWire Solo is and it isn't. Let me explain a little. When the device was released it was class-compliant. This was many years ago. Then M-Audio saw fit to break its class-compliance via driver updates. Some of these driver updates also packed a nasty bit of firmware (undocumented) that broke the class-compliance of the device.

So this was a bum move by M-Audio with no apparent reason behind it. Nonetheless it'd be forgivable if there were a tool available to easily revert the device back to its original, advertised, sane, class-compliant state.

There is a workaround. (Buy and) Install Windows XP pre-SP2. Install deprecated drivers that are hidden away on M-Audio's site (the older the better) and reflash the firmware back to its class-compliant state. I've done this and it has many advantages. For one, I can run the device 'driverless' in OS X. I suspect the fact that many people own a non-class-compliant FireWire Solo is the reason some report success and others don't when working with Linux. It's a needless added hidden problem that doesn't help things at all.

Now on to ffado.org. I'm a huge fan of the work they're doing and they should be congratulated for that. There is, however, some fairly liberal usage of the term 'Full Support'. For example: [http://www.ffado.org/?q=node/12](http://www.ffado.org/?q=node/12). Perhaps I'm being harsh.

For what it's worth, the FireWire Solo is listed as 'Reported to work' on ffado.org. This can be read as 'Don't get your hopes up pal'.

I suppose the reason for this mini-rant is to forewarn potential external sound card/Linux users that class-compliance is a dynamic thing and that M-Audio in particular play fast & loose in this area.

/rant

---

### Post by sgx on 2011-04-21
> **pedrogent said:**
> Hey sgx, thanks for your reply. When you say 'closeout' do you mean these aren't made any more? Would be a shame, altho' I think my cousin has one I could buy off him, or perhaps swap for my FireWire Solo.

So you just plugged it in and it worked (i.e. you could playback music)? If this is the case my 3+ year quest has come to its conclusion.

Blacklisting modules is no problem for me.

Out of interest, what does the following print for you?

```
lspci | grep -i usb
```

I've recently been told that USB audio plays up with the particular Intel USB controller I have (as seen in my post above).

Thanks for your help.lspci | grep -i usb output:
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
This is on a pclinuxos with E17, and I use qjackctl to connect
the aqualung player to the Fast Track, and also vlc and xine have jackd addons. xine starts using jackd with this:

xine -A jack

vlc has the option in its audio preferences. Just tested both, all is
working.

I have not tested with youtube or streaming net music.
The other models may be a better choice, for general listening, but this one has mic, and button switchable line/guitar input, rca outputs for speakers, and a headphone output. Its very lightweight, and the knobs have a nice pro feel to them.
It is sometimes part of a bundle with Pro-Tools Essential, a limited
edition DAW (windows vintage) package, I paid $50.

There may be a way to set up vlc as the firefox plugin, perhaps someone here has done this?


Cheers

---

### Post by AutoStatic on 2011-04-21
> **pedrogent said:**
> Class-compliance is an interesting topic. My FireWire Solo is and it isn't. Let me explain a little. When the device was released it was class-compliant.Hello pedrogent, there are no class-compliant FireWire devices afaik. But luckily most of them use generic chipsets like DICE or BeBoB and that's why FFADO drivers, which are basically generic FireWire drivers, work for so many devices. When people talk about class-compliant audio devices it is mostly about USB1.1 devices, afaik USB1.1 is the only protocol for which an audio class has ever been agreed on. But I could be wrong, not an expert on this matter :)

> **pedrogent said:**
> Now on to ffado.org. I'm a huge fan of the work they're doing and they should be congratulated for that. There is, however, some fairly liberal usage of the term 'Full Support'. For example: [http://www.ffado.org/?q=node/12](http://www.ffado.org/?q=node/12). Perhaps I'm being harsh.The FA-66 is fully supported. Devices only get the term full support when the devs have the necessary specs, documentation and a testing device. For the FA-66 this was the case so if it doesn't work, don't blame FFADO.

Best,

Jeremy

---

### Post by AutoStatic on 2011-04-21
> **pedrogent said:**
> Hey Jeremy, thanks for the reply. The trick here is working out which USB devices are:

[LIST]
[*]Class-compliant
[*]The ones included in the group you describe as 'basically all'
[/LIST]Most manufacturers publish the manuals for their devices on their websites. So if you see a nice USB1.1 device you're interested in, check the manual and if it states the device is class-compliant and doesn't need drivers in order to run on Mac or Windows you can be sure it will work with Linux.

Best,

Jeremy

---

### Post by pedrogent on 2011-04-21
Thanks Jeremy. That's what I understand class-compliance to be. You don't need to install drivers to get the device to work. You plug it in and away you go.

That's what I can do with my FireWire Solo in OS X... now that I've flashed the firmware back to its original (c. 2005) state using 6 year-old-drivers in a version of a decade-old OS that you can't even buy any longer (i.e. pre-SP2 XP).

I can assure you that I had to install drivers prior to doing this in order for the device to work. This is how I justify my statement to the effect that M-Audio changed the device's firmware from class-compliant to non-class-compliant with a very shady set of drivers.

Perhaps there are some semantic issues here but if we take 'class-compliant' to mean 'plug & play "driverless" usage' then such semantic issues are avoided. (M-Audio explain class-compliance in this way [here]("http://www.m-audio.com/index.php?do=support&tab=driver").)

Here's the concern. I'm wary of manufacturers stating that a device they sell is 'class-compliant' only to change the truth of that assertion through shady software practices somewhere down the track.

I also feel that many users that have things up and working as they should perhaps lose sight of the fact that a great many users are frustrated and baffled as to why such a simple task as plugging in a sound card and having it work should become a black art in Linux, so completely obfuscated and complex. It's not for want of effort either. I've been at this on and off for three years now.

@**sgx**: Thanks for your input here. I really appreciate your time and effort to check those things. I fear that given the fact you're using a non-Debian based OS and our USB controllers are different (and that I allegedly have the problematic ones) my quest to interface Linux and some powered speakers will continue for now.

Perhaps ThunderBolt will change are this? We can hope.

---

### Post by AutoStatic on 2011-04-21
If you really want a device that fully works: [http://www.roland.com/products/en/UA-25EX/index.html](http://www.roland.com/products/en/UA-25EX/index.html)

I've got its predecessor, the UA-25, and it works like a charm on all my machines that all have different USB controllers. I also tested it with the same controller you are having and it worked, but not full duplex, so only capture or playback.

Best,

Jeremy

---

### Post by pedrogent on 2011-04-21
Yeh I've been spying that one for a little while now. Good to know it works without a hitch. Lack of full-duplex isn't an issue for me. Do you know why it changed from 'Edirol' to 'Cakewalk' branding by any chance? Is it the same unit?

Here's a hypothetical situation:

I buy this sound card, attach my KRK VXT6 speakers to it, turn them on, plug the sound card into Ubuntu 10.10 with VLC installed, attempt to play a .mp3 file. Will the speakers output sound? Or would I need to muck around with jack, ardour, et al. first?

---

### Post by AutoStatic on 2011-04-21
> **pedrogent said:**
> Do you know why it changed from 'Edirol' to 'Cakewalk' branding by any chance?That's because Roland is rebranding its stuff: [http://www.rolandsystemsgroup.com/articles/100126](http://www.rolandsystemsgroup.com/articles/100126)

> **pedrogent said:**
> Is it the same unit?Yes, but with an added ground lift and compressor/limiter option.

> **pedrogent said:**
> I buy this sound card, attach my KRK VXT6 speakers to it, turn them on, plug the sound card into Ubuntu 10.10 with VLC installed, attempt to play a .mp3 file. Will the speakers output sound?No, but it probably won't do so on any platform. Every platform needs to know at least which soundcard it has to address as the default one.

> **pedrogent said:**
> Or would I need to muck around with jack, ardour, et al. first?It depends what you want to do with it. If you want to use your KRK's for watching movies, YouTube videos and listening to some mp3's then you need to look at Ubuntu's Sound Preferences. If you want to use your KRK's for their intentional purpose then you will need JACK and probably also a DAW like Ardour.

Best,

Jeremy

---

### Post by pedrogent on 2011-04-21
Yes, that's right, I'd like to watch lolcatz on youtube. Here's an ever so slightly different hypothetical situation:

I buy this sound card, attach my KRK VXT6 speakers to it, turn them on, plug the sound card into Ubuntu 10.10 with VLC installed, navigate to Ubuntu's Sound Preferences and "address" the Cakewalk sound card as the default one and attempt to play a .mp3 file. Will the speakers output sound? Or would I need to muck around with jack, ardour, et al. first?

Now for the minutiae: let's assume, Jeremy, that the city has a working power grid, the speakers are functional, some elite hacker hasn't pwned my machine and rendered VLC useless by removing some key libs, and also that the .mp3 file in question isn't corrupted. Let's also assume I'm of sane mind and I have the faculties to press the 'play' button on VLC.

Seriously dude, why the attitude? Does it 'empower' you? A simple answer is easier to provide than a simple answer that throws in a 'for their intensional [sic] purpose' jibe for good measure. You have zero idea what it is I do. You also apparently have zero idea what the 'intensional [sic] purpose' of a set of speakers is. I assume that you're bundling me in with the 'hobbyist' rabble - not elevating me to the status of 'pro' user. You know, the type that has daisy-chained sound cards and expensive microphones, etc.

If you don't want to answer my questions I won't hold it against you. In fact, I never would have known of you. I'm just trying to get the straight dope on GNU/Linux + sound after more than three years of trying on & off to get the two to gel. Regrettably I've frequently run into folks like you all along that winding path. It's a curiosity.

Incidentally OS X realizes that I wish to "address" my FireWire Solo as the default sound card as soon as it's plugged in. Perhaps a 'pro' user such as yourself could write some code and get the same thing to happen in GNU/Linux.

---

### Post by Pablo_F on 2011-04-21
I think this is a misunderstanding. Autostatic is not being arrogant or anything. On the contrary, he is kindly trying to help you. He insists on things that you may consider obvious but they are very important because in Linux you don't have one only audio system.
 
Basically, you have two "sound servers", pulseaudio and jack. Both use the alsa drivers but they behave differently and have different graphical front-ends for configuration and making connections between their clients (=audio card and applications).

For example, if you use jack, the settings in the Sound Preferences (pulseaudio front-end) are completely irrelevant. This seems counter-intuitive. If you just want to play VLC, you don't want jack at all.

---

### Post by pedrogent on 2011-04-21
Hey Pablo_F. I'd like to think this was a misunderstanding, but frankly, it's not. I lurk here quite a bit, trying to glean info, and I've noted on more than one occasion this chap proclaiming from on high. It rubs people the wrong way and it's a pity that people, particularly newcomers, who are genuinely seeking quality information get 'spoken at' in this way.

Why must there be this curt discourse?

Thanks for your input here mind you. I do have some understanding of how jack works, having used it three years ago. I actually got my FireWire Solo working, albeit very briefly and intermittently. Jack wasn't my idea of fun back then but to be fair it may have improved a lot since.

Anyway, I guess I'm more or less where I always was. GNU/Linux + audio isn't ready for prime time just yet. By prime time I mean for users who want to plug stuff in and get going. I can't complain - I haven't paid a cent, and I've only submitted a few bug reports along the way. :)

I'll check back in a year or so. In the meantime I'll continue to happily use Linux for the stuff I can make it do.

---

### Post by MBybee on 2011-04-21
Not sure what the beef here is, but I have definitely had issues where JACK didn't like my card and PulseAudio was happy with it.

If you're using linux for Pro Audio, you've got to deal with both sound systems, and that's not being high and mighty, that's just reality. OSX has CoreAudio that does it all. Windows you pick ASIO vs DirectSound, etc. Linux it's JACK vs Pulse (and a handful of other possibilities). Some apps will require JACK, and so the same setup that works for general OS sound might bomb when you try to go low-latency.

This, BTW, is my issue too, and why I had to move back to Win 7 (tweaked all to heck for low latency) for my performances.

---

### Post by sgx on 2011-04-21
> **pedrogent said:**
> Hey Pablo_F. I'd like to think this was a misunderstanding, but frankly, it's not. I lurk here quite a bit, trying to glean info, and I've noted on more than one occasion this chap proclaiming from on high. It rubs people the wrong way and it's a pity that people, particularly newcomers, who are genuinely seeking quality information get 'spoken at' in this way.

Why must there be this curt discourse?

Thanks for your input here mind you. I do have some understanding of how jack works, having used it three years ago. I actually got my FireWire Solo working, albeit very briefly and intermittently. Jack wasn't my idea of fun back then but to be fair it may have improved a lot since.

Anyway, I guess I'm more or less where I always was. GNU/Linux + audio isn't ready for prime time just yet. By prime time I mean for users who want to plug stuff in and get going. I can't complain - I haven't paid a cent, and I've only submitted a few bug reports along the way. :)

I'll check back in a year or so. In the meantime I'll continue to happily use Linux for the stuff I can make it do.

People often give thorough answers, since many people will read this
forum in 2012 and beyond for the same issues, or similar ones. I can guarantee that Autostatic was being concise, not condescending. You
may want to reconsider departure from a forum that has a wealth of knowledge on offer. Many here also are bi-lingual, yet with grammar
superior to those with english as the native tongue. Lots of knowledge
can be gained, or passed by, in a year :)
Cheers

---

### Post by sgx on 2011-04-21
> **MBybee said:**
> Not sure what the beef here is, but I have definitely had issues where JACK didn't like my card and PulseAudio was happy with it.

If you're using linux for Pro Audio, you've got to deal with both sound systems, and that's not being high and mighty, that's just reality. OSX has CoreAudio that does it all. Windows you pick ASIO vs DirectSound, etc. Linux it's JACK vs Pulse (and a handful of other possibilities). Some apps will require JACK, and so the same setup that works for general OS sound might bomb when you try to go low-latency.

This, BTW, is my issue too, and why I had to move back to Win 7 (tweaked all to heck for low latency) for my performances.
Pulse audio can be pulled in as a dependency, but not by apps
that are the basis of 'pro audio', which is an interesting term in
itself. For me, that would include jackd, qjackctl, patchage, Hydrogen, Rakarrack, Guitarix, Yoshimi, Phasex, Linuxsampler, Audacity, Ardour, Qtractor, wineasio, and a full Ladspa fx collection. Probably others have differing defines for 'pro'. Remastering a custom system based loosely on these
apps should leave libpulse on the sidelines, and can be the
basis of effective audio production. Add a few vst favorites,
and it's time for the record button :)
Cheers

---

### Post by MBybee on 2011-04-21
> **sgx said:**
> Pulse audio can be pulled in as a dependency, but not by apps
that are the basis of 'pro audio', which is an interesting term in
itself. For me, that would include jackd, qjackctl, patchage, Hydrogen, Rakarrack, Guitarix, Yoshimi, Phasex, Linuxsampler, Audacity, Ardour, Qtractor, wineasio, and a full Ladspa fx collection. Probably others have differing defines for 'pro'. Remastering a custom system based loosely on these
apps should leave libpulse on the sidelines, and can be the
basis of effective audio production. Add a few vst favorites,
and it's time for the record button :)
Cheers

I agree entirely :)
I am one of the unfortunates with a combination of Firewire devices that are unsupported combined with lousy chipsets. Fortunately, Win7 has great support for my Firewire device, so I can make do with Ableton Live and Serato Itch

---

### Post by sgx on 2011-04-23
This place could use a little DJ'n from time to time :)

---

