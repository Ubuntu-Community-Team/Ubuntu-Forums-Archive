---
title: "Change from lowlatency to rt or realtime kernel"
date: 2015-09-27
forum: Ubuntu Studio
---

### Post by francesco.grassell on 2015-09-27
Hi, I am trying Ubuntu Studio 14.04 and it seems to work quite well. I am using LMMS as a rack for live performance, which I control with my keyboard via MIDI/USB interface. As you might guess in this case the latency is extremely important; for now, the latency is small enough to play quite seamlessly but I would like to see if I can reduce it a bit more by switching to a -rt or -realtime kernel.

I searched for some documentation but all the pages refer generically to "update to -rt or -realtime kernel" without giving details on how to exactly do it. Please can you suggest me some download link and procedures and/or whatever it may take to change the kernel?

Thank you in advance ;)

---

### Post by CrocoDuck on 2015-09-27
Hi there! rt and realtime are the same thing. A part for the lowlatency kernel UStudio does not have many relevant system optimizations for audio. I would suggest to read through [this guide]("http://wiki.linuxaudio.org/wiki/system_configuration") and try some further tweaking before to try a realtime kernel. If you decide, at the end, that you want to give a go to a realtime kernel I would advise to use [KXStudio]("http://kxstudio.linuxaudio.org/")'s one. Follow the instructions [here]("http://kxstudio.linuxaudio.org/Repositories") to add the repos. Then, install the kernel:

```
sudo apt-get install linux-meta-realtime
```

You should be able to boot into the kernel from GRUB. If not, try this:

```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

I have stopped using Ubuntu years ago, so I am not 100% sure these commands will work (they should). [This page]("http://www.linuxmusicians.com/viewtopic.php?f=19&t=9666") could contain quite good information for you. For example, it suggests an alternative way to bring a realtime kernel to your system:

```

sudo apt-get install software-properties-common wget
sudo add-apt-repository ppa:kxstudio-debian/kxstudio
sudo apt-get update
sudo apt-get install kxstudio-repos
sudo apt-get update
sudo apt-get install linux-meta-realtime

```

---

### Post by francesco.grassell on 2015-09-27
Thank you sooo much ;) just 2 things I'm not sure about:
[URL="https://help.ubuntu.com/community/UbuntuStudio/RealTimeKernel"]
this page [/URL]says -rt and -realtime are not actually the same, the first being based on Ubuntu kernel and the second on vanilla kernel. Furthermore it specifies the following:

[LIST]
[*]If the -lowlatency kernel isn't enough then you should try the -rt kernel 
[*]If the -rt kernel isn't enough stable for you then you should try the -realtime kernel
[/LIST]
Anyway, I'm following you on Soundcloud ;)

---

### Post by tgalati4 on 2015-09-27
Welcome to the forums.  There is a progression from lowlatency to rt to realtime.  It's possible that you will lose your mouse with realtime, which means no sliders, no faders, no volume control during a Live Session.  I see realtime as an embedded or recording-only, headless machine, not a live mixer or live performance monitor.  If you are trying to reduce the skew of several simultaneous channels, then you need dedicated, digital recording hardware.

Since sound travels at 1100 feet per second in standard conditions, a 2 millisecond delay results in a monitor distance of  2.2 feet (0.002 seconds * 1100 feet/sec).  A 5 millisecond delay is 5.5 feet.  You can sing or play to that distance.  If your guitar monitor is 30 feet away, then you might have an issue playing to that (27 ms delay).

So you have to ask yourself, what is acceptable for a delay?  What acoustic problem are you trying to solve? What is your typical latency with your current setup?

---

### Post by CrocoDuck on 2015-09-27
> **francesco.grassell said:**
> [this page ]("https://help.ubuntu.com/community/UbuntuStudio/RealTimeKernel")says -rt and -realtime are not actually the same, the first being based on Ubuntu kernel and the second on vanilla kernel.

:-\"Oops... Sorry about that. Well, this distinction between rt and realtime seems more of an Ubuntu thing. Like, what you do to build a realtime kernel is to take the kernel source code, add the Ingo Molnar patch, configure it and then compile it. What implements the realtime is the Ingo Molnar patch. Seems like that the difference between rt and realtime under Ubuntu is the upstream of the kernel source code: rt uses the Ubuntu source code, while realtime seems to use the [standard code]("https://www.kernel.org/") (vanilla). Every distro kernel have the vanilla as a base, with edited parameters, bug fixes, patches and so. Following [this page]("http://wiki.linuxaudio.org/wiki/system_configuration#how_do_i_build_a_real-time_audio_workstation_on_linux") to manually build the kernel would get you to something similar to the realtime edition I guess, maybe more up to date. I am used to arch Linux at the moment, that supplies [realtime kernels calling them rt]("https://aur4.archlinux.org/packages/?O=0&SeB=nd&PP=100&do_Search=Go&K=linux-rt")... that is why I was supposing it was the same here...

I never found the page you linked before! [Seems like you have a cool way to automatize the tuning now]("https://bitbucket.org/thismaechler/ubuntustudio-14.04-realtimeaudio/"). I would try it, but after reading all the docs to figure out what they do. As always, be careful and don't risk your data.


> **francesco.grassell said:**
> [COLOR=#000000]Anyway, I'm following you on Soundcloud [/COLOR]:wink:

UH \\:D/ cool!

tgalati4 made some cool point about latency. My personal rule is no more than 7 ms. I have been talking about that on [my blog]("https://thecrocoduckspond.wordpress.com/"). Have a read if you are interested. Also, if you have feedback just drop a comment!

---

### Post by tgalati4 on 2015-09-27
There was a youtube video showing a Japanese "Stop Talking" box.  Basically it was a box you wore around your neck.  It recorded the other person talking and played it back with a 200 ms delay.  The brain has trouble understanding speech delayed 200 ms and the talkative person would stop talking.  There's a chart that shows the difference between phat, reverb, chorus, echo, and longer delays.  It's simple physics, but the psycho-acoustics of audio processing are quite complicated.

If you are trying to sing acapella with 4 singers and have a 7 ms delay coming out of a floor monitor, then you might have issues trying to stay in sync--presuming you are standing closer than 7 feet.  If the monitor is 5 feet from your ears, then you have 12 feet of effective delay to deal with.

It's a useful experiment to try different delays so you can see the effect that latency has on live music sessions.  There is no correct answer, and generally lower is better, but not to the detriment of computer/recording stability.

---

### Post by CrocoDuck on 2015-09-27
> **tgalati4 said:**
> There is no correct answer, and generally lower is better, but not to the detriment of computer/recording stability.

Yep!

---

### Post by yoshii on 2015-10-05
acoustics are not the only reason for low-latency.  

MIDI overdubbing within a digital audio workstation might benefit from lower latency.  Also VST instruments in Windows programs within Wine might need all the low latency help they can get.

---

### Post by CrocoDuck on 2015-10-08
Also, another reason to prefer realtime patched kernels is audio stability. If lower latency is not always achieved the number of xruns and similar bad things is usually heavily reduced.

---

### Post by francesco.grassell on 2015-10-11
Well, I have tried both the sequences suggested, it all goes smoothly except for...

```
sudo apt-get install linux-meta-realtime
```

It says the package is impossible to find. I can't find it in Synaptic. Any suggestions? 

Anyway, the problem seems to be the crackling instead of latency, since I have been able to achieve 1.2 ms. I tried to expand the buffering size but this doesn't improve the audio quality when playing chords (single notes sound good). LMMS in the settings says this is a common problem when playing with non-realtime kernels, so I definitely have to upgrade the kernel... If only I could find it :lolflag:

> **CrocoDuck said:**
> Hi there! rt and realtime are the same thing. A part for the lowlatency kernel UStudio does not have many relevant system optimizations for audio. I would suggest to read through [this guide]("http://wiki.linuxaudio.org/wiki/system_configuration") and try some further tweaking before to try a realtime kernel. If you decide, at the end, that you want to give a go to a realtime kernel I would advise to use [KXStudio]("http://kxstudio.linuxaudio.org/")'s one. Follow the instructions [here]("http://kxstudio.linuxaudio.org/Repositories") to add the repos. Then, install the kernel:

```
sudo apt-get install linux-meta-realtime
```

You should be able to boot into the kernel from GRUB. If not, try this:

```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

I have stopped using Ubuntu years ago, so I am not 100% sure these commands will work (they should). [This page]("http://www.linuxmusicians.com/viewtopic.php?f=19&t=9666") could contain quite good information for you. For example, it suggests an alternative way to bring a realtime kernel to your system:

```

sudo apt-get install software-properties-common wget
sudo add-apt-repository ppa:kxstudio-debian/kxstudio
sudo apt-get update
sudo apt-get install kxstudio-repos
sudo apt-get update
sudo apt-get install linux-meta-realtime

```

---

### Post by tgalati4 on 2015-10-11
According to the instructions, you can either install [kxstudio]("http://kxstudio.linuxaudio.org/Repositories") by downloading and installing a *.deb package or by installing the 3rd-party repository and then following the manual apt-get instructions.  The package *linux-meta-realtime* does not exist in the standard 14.04 Ubuntu repositories.

---

### Post by francesco.grassell on 2015-10-13
At the moment, I followed the two procedures described before and installed the *.deb package, but nothing like linux-media-realtime appears when I try to install it via apt-get. The only other way I found to change the kernel in Ubuntu Studio involves manual editing of the kernel which is faaaaar beyond my reach ):P I tried with Liquorix too, no way. Are there any other repositories you can suggest me please?
Thank you again :D

> **tgalati4 said:**
> According to the instructions, you can either install [kxstudio]("http://kxstudio.linuxaudio.org/Repositories") by downloading and installing a *.deb package or by installing the 3rd-party repository and then following the manual apt-get instructions.  The package *linux-meta-realtime* does not exist in the standard 14.04 Ubuntu repositories.

---

### Post by CrocoDuck on 2015-10-14
> **francesco.grassell said:**
> At the moment, I followed the two procedures described before and installed the *.deb package, but nothing like linux-media-realtime appears when I try to install it via apt-get.

Uhm... I am looking [at the PPA]("https://launchpad.net/~kxstudio-debian/+archive/ubuntu/kxstudio/") and seems that the packages are available for Trusty, Precise, and Lucid only. Have you followed this?

[QUOTE=http://kxstudio.linuxaudio.org/Repositories]
If you're using a system **newer or equal** to **Debian Testing** or **Ubuntu 15.10** you'll need to enable GCC5 packages.
    You can do so by installing this deb file -         [kxstudio-repos-gcc5.deb]("https://launchpad.net/%7Ekxstudio-debian/+archive/kxstudio/+files/kxstudio-repos-gcc5_9.2.1%7Ekxstudio1_all.deb"),     or manually by running this:

[COLOR=#6E6E6E]# Download package file[/COLOR]
wget [https://launchpad.net/~kxstudio-debian/+archive/kxstudio/+files/kxstudio-repos-gcc5_9.2.1~kxstudio1_all.deb](https://launchpad.net/~kxstudio-debian/+archive/kxstudio/+files/kxstudio-repos-gcc5_9.2.1~kxstudio1_all.deb)

[COLOR=#6E6E6E]# Install it[/COLOR]
sudo dpkg -i kxstudio-repos-gcc5_9.2.1~kxstudio1_all.deb
 
    These packages contain: 
 
[LIST]
[*]Various sources files that activates the separate repositories 
[*]GPG keys used for package and repository signing 
[*]A post-install script that enables an extra, Ubuntu-specific repository 
[/LIST]

[/QUOTE]

There are [realtime kernels for Debian]("https://wiki.debian.org/DebianMultimedia#Realtime_kernel"), but I am not sure how good of an idea is to install them on Ubuntu... Have you tried the repo you [already found]("https://bitbucket.org/thismaechler/ubuntustudio-14.04-realtimeaudio/downloads") (accessed from [here]("https://help.ubuntu.com/community/UbuntuStudio/RealTimeKernel"))? The page seems fairly up to date...

However I know the struggle. It has been a pain to find a realtime kernel when I was using Ubuntu 11.04... I used KXStudio back then... but it was not booting (or was it 12.04... cannot even remember...)

---

### Post by CrocoDuck on 2015-10-15
> **francesco.grassell said:**
> Anyway, the problem seems to be the crackling instead of latency, since I have been able to achieve 1.2 ms. I tried to expand the buffering size but this doesn't improve the audio quality when playing chords (single notes sound good).

Sorry I didn't see this bit. This is actually very interesting. Are you sure you are not facing hardware/software distortion? Describe the crackling: does it get reported as clusters of xruns by qjackctl? If not, I guess it is distortion, like what [this guy]("http://ubuntuforums.org/showthread.php?t=2291409") is facing. From the computer point of view the computational load to process a signal is the same regardless the content of the signal (simple tone, complex tone, random, broadband, etc...) and depends mainly on the sampling variables (Sample Frequency, Periods/Buffer). So, what you play must not make a difference.

Also, keep in mind that the latency you see in qjackctl (or other setting tools) is the maths derived latency and applies only at the software level. Additional latencies are given by the converters of the sound-card, hardware controllers and other hardware related things. The only way to know the total round-trip latency for real is through [jack_iodelay]("http://manpages.ubuntu.com/manpages/precise/man1/jack_iodelay.1.html").

---

### Post by tgalati4 on 2015-10-15
Turn off computer system sounds.  You don't need those.  It's possible that you are running into stability issues with your sound hardware.  Does the distortion/crackling happen at 7 ms of latency?

---

### Post by francesco.grassell on 2015-10-25
OK just to recap... I have absolutely no idea what xruns is and how to  use qjackctl. It definitely seems to be something related to  hardware/software since I had a phone doing the same noise when it was  on overload. The best way I have to describe it is through [this]("https://www.youtube.com/watch?v=mTu45mBlXZ8") video.

I have already followed the steps proposed in the video and the  situation has improved a lot, but there remains some unpredictable noise  occurring at certain times during the playing session, with the CPU  usage having some peaks while playing through MIDI keyboard. This  doesn't happen if I play through the QWERTY keyboard, even if I play  chords, play faster and so on.

The hardware set is the following:

[LIST]
[*]MIDI controller: Korg SP250 digital piano. Notice that this  piano has automatic touch regulation which I think is the "culprit" of  all this mess, since if I play "piano" (meaning softly) all goes well,  but if I play "forte" the crackling appears. The best I could do was to  lower all the volumes (main volume and single instruments' volume) to  adjust the volume only via the analogue knob of the mixer. 
[*]CPU: Toshiba Satellite M30X (year 2005) with 1.5 GHz mono-core processor 
[*]Sound  card: I use the mixer, a Behringer Q802 USB, connected to the PC. The  sound card is obviously set as the main device in LMMS ALSA settings 
[*]USB/MIDI cable: Bespeco 
[/LIST]
Maybe  the problem could be due to some bottleneck with all these USB  connections? I was thinking to get a USB/fire-wire cable or a fire-wire  sound card but it would be the last resort. 

Notice: the problem  described with digital piano appears every time there is a volume  increase involved, so especially when I play electronic sounds like  waves and all the "whoa" stuff, in which the sample has something like a  "crescendo" already incorporated. If I recreate the same effect via the  Attack of the oscillator this doesn't happen.




> **CrocoDuck said:**
> Sorry I didn't see this bit. This is actually very interesting. Are you sure you are not facing hardware/software distortion? Describe the crackling: does it get reported as clusters of xruns by qjackctl? If not, I guess it is distortion, like what [this guy]("http://ubuntuforums.org/showthread.php?t=2291409") is facing. From the computer point of view the computational load to process a signal is the same regardless the content of the signal (simple tone, complex tone, random, broadband, etc...) and depends mainly on the sampling variables (Sample Frequency, Periods/Buffer). So, what you play must not make a difference.

Also, keep in mind that the latency you see in qjackctl (or other setting tools) is the maths derived latency and applies only at the software level. Additional latencies are given by the converters of the sound-card, hardware controllers and other hardware related things. The only way to know the total round-trip latency for real is through [jack_iodelay]("http://manpages.ubuntu.com/manpages/precise/man1/jack_iodelay.1.html").

---

### Post by francesco.grassell on 2015-10-25
Thank you, I am going to try it. How can I do? Via the system settings?

> **tgalati4 said:**
> Turn off computer system sounds.  You don't need those.  It's possible that you are running into stability issues with your sound hardware.  Does the distortion/crackling happen at 7 ms of latency?

---

### Post by tgalati4 on 2015-10-25
You need a dual-core processor to make realtime work correctly.  When you have pending instructions that interrupt sound generation, you will get xruns and glitches, which sound like distortion.  Try a stronger computer with a dual processor.

---

### Post by CrocoDuck on 2015-10-26
> **francesco.grassell said:**
> 
I have already followed the steps proposed in the video and the  situation has improved a lot, but there remains some unpredictable noise  occurring at certain times during the playing session, with the CPU  usage having some peaks while playing through MIDI keyboard. This  doesn't happen if I play through the QWERTY keyboard, even if I play  chords, play faster and so on.


Sounds like the intensity on the MIDI controller is used to synthesize/trigger signals whose amplitude exceeds the soundcard capabilities, overdriving the output preamps. Try to lower, if you can, the output signal levels both by software and hardware means. Try to launch alsamixer in the command line, you should be able to access the card software controls (if any). Alternatively, you can use [this workaround]("http://www.linuxmusicians.com/viewtopic.php?f=6&t=14764").

> **tgalati4 said:**
> You need a dual-core processor to make realtime  work correctly.  When you have pending instructions that interrupt  sound generation, you will get xruns and glitches, which sound like  distortion.  Try a stronger computer with a dual processor.

I am not sure I agree with that. In the kernel 2.X era (years ago) I have been successful with Ubuntu Studio + LXDE with a computer with a single core AMD64 + 512 Mb of ram. You may have to strip the system services and processes down though. Have a look at [this]("http://wiki.linuxaudio.org/wiki/system_configuration#disabling_problematical_services_and_other_hidden_bits"). Have a look at [this website]("http://libremusicproduction.com/") for beginner friendly introductions to jack and related tools. It should give you a view of what ALSA, jack, portaudio and pulsaudio are and how they interact. It is pretty important to understand it, Linux audio management is quirky and counter-intuitive. Also, it should explain what xruns are. In chops, they are overruns: the systems fails to write audio on software buffers, and then looses a bit of it. They produce audible cracklings, clips and pops. If you use qjackctl you will be easily able to view detailed statistics about them. For example, a [recommended reading]("http://libremusicproduction.com/articles/demystifying-jack-%E2%80%93-beginners-guide-getting-started-jack"). Usually, using a well configured jack on a well configured systems produces the best results on Linux and I would recommend to try this approach.

---

### Post by tgalati4 on 2015-10-26
CrocoDuck is quite correct.  You can get realtime performance on a single core processor, but it requires some work and a detailed understanding of linux services.  With a current linux distro, you need a lot of horsepower to get it to work out-of-the-box.  

You might need a faster computer to get better MIDI performance for your Korg keyboard.  I presume the Behringer USB mixer is on its own connection and not on a USB hub.  Most pro musicians use Firewire audio equipment as it has much higher bandwidth than USB equipment.

---

### Post by francesco.grassell on 2015-11-28
I am back, I was a bit busy these weeks :D

That's what I did today:
1 switched from ALSA to JACK in LMMS
2 installed Extra Audio Production Applications (including something called complete linux low latency kernel or something like that)

There has been a great overall improvement, the crackling doesn't appear anymore, even when playing via the MIDI keyboard, even with the damper or the variable intensity due to the finger pressure. The delay I set up is 1.5 ms. Only 1-2 sounds give problems but in general the PC seems viable for live playing. I don't know exactly what I did but it kind of worked.

I will keep you updated. In the meanwhile it would be great if you could give me some explanation of what i exactly did because I have no idea lol

Thank you ;)

---

### Post by CrocoDuck on 2015-11-28
> **francesco.grassell said:**
> 
1 switched from ALSA to JACK in LMMS


You said to LMMS to communicate with JACK instead of ALSA directly. ALSA is the soundcard driver in Linux. JACK runs on top giving an infrastructure to software to route audio between them with high CPU privileges. JACK takes care of communicating with ALSA as well.

> **francesco.grassell said:**
> 
2 installed Extra Audio Production Applications (including something  called complete linux low latency kernel or something like that)


Where did you find this package?

---

### Post by francesco.grassell on 2015-12-13
1) Thank you very much ;)
2) It's under Menu/Audio Production/Extra Audio Production Applications ;)

> **CrocoDuck said:**
> You said to LMMS to communicate with JACK instead of ALSA directly. ALSA is the soundcard driver in Linux. JACK runs on top giving an infrastructure to software to route audio between them with high CPU privileges. JACK takes care of communicating with ALSA as well.



Where did you find this package?

---

### Post by francesco.grassell on 2016-01-08
Hi, I am back... after many researches here is what I did. By the way, the noise I was talking about was actually xruns.

1) updated to Ubuntu Studio 15.10 with his new Linux kernel 4
2) switched to KX Studio
3) set up JACK accordingly to the KX Studio website's recommendations
4) set up LMMS accordingly to the new JACK settings (as regards buffer, sample rate etc.) but using ALSA inside LMMS
5) set up every single plugin or instrument I load into LMMS at 25% volume to avoid distortion, thus adjusting volume only via the knobs of the mixer I use as an audio interface
6) set up the MIDI tab in every single instrument window with Velocity at 64 and Custom base Velocity at 63 to limit the dynamic range and offset the keyboard's touch sensitivity which gave xruns

After all this, the noise and xruns disappeared, the latency is at acceptable values (5ms) and so the keyboard is playable, but I definitely think I will need a multi-core CPU to handle more complex project... one day or another ;) for many ogg, vst etc. this setup works well enough.

Thank you for your help, as regards me you can mark this thread as solved ;)

---

