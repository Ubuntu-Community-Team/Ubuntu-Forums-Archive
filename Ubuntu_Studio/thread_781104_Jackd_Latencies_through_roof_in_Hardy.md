---
title: "Jackd Latencies through roof in Hardy"
date: 2008-05-04
forum: Ubuntu Studio
---

### Post by gorkon on 2008-05-04
I have been trying since upgrading to Hardy to get Jackd and Ardour setup for recording.  Ever since clean installing hardy and setting up the realtime kernel I haven't been able to get back to where I was when I ran Gutsy with the same sound hardware.  I have a Behringer U-Control UCA-202 on the way and we'll see.  The only thing I have not done was compile my own kernel to see if I can solve this issue.  I use the following to start jackd:

/usr/bin/jackd -v -R -P89 -p128 -t5000 -dalsa -dhw:1 -r44100 -p2048 -n5 -D -Phw:1,0 -i2 -o2

This is with a Griffin iMic Currently.  Am I EVER going to get back to 10 ms latencies (which isn't great, but MUCH better than this) and no xruns??  Possibly?  Anyone got ANY idea??

Saw the following on the ALSA Wiki:

Tuning USB devices for minimal latencies

On linux-audio-user Christoph Eckert brought up the question about how to get better latencies out of USB audio devices, and USB guru Clemens Ladisch had a very good tip: The snd-usb-audio module accepts a module option called "nrpacks", which according to modinfo, sets the: Max. number of packets per URB. (int). Setting this to "nrpacks=1" should allow latencies in the area of 4-6 msecs.

Unfortunatly on some systems/kernels nrpacks=1 conflicts with a feature called "USB bandwidth allocation" in the kernel. Here's the way out:

    * In the kernel config ensure that both options (taken from a 2.6.10) are disabled:: 

:[   ] Enforce USB bandwidth allocation (EXPERIMENTAL)
:[   ] Dynamic USB minor allocation (EXPERIMENTAL)

    * Ensure to loTuning USB devices for minimal latencies

On linux-audio-user Christoph Eckert brought up the question about how to get better latencies out of USB audio devices, and USB guru Clemens Ladisch had a very good tip: The snd-usb-audio module accepts a module option called "nrpacks", which according to modinfo, sets the: Max. number of packets per URB. (int). Setting this to "nrpacks=1" should allow latencies in the area of 4-6 msecs.

Unfortunatly on some systems/kernels nrpacks=1 conflicts with a feature called "USB bandwidth allocation" in the kernel. Here's the way out:

    * In the kernel config ensure that both options (taken from a 2.6.10) are disabled:: 

:[   ] Enforce USB bandwidth allocation (EXPERIMENTAL)
:[   ] Dynamic USB minor allocation (EXPERIMENTAL)

    * Ensure to load the snd-usb-audio module with the parameter "nrpacks=1", maybe including it into one of the boot scripts:: 

modprobe snd-usb-audio nrpacks=1

    * Or use the module configuration line (e.g. in /etc/modprobe.conf): 

options snd-usb-audio nrpacks=1

    * Now invoke JACK with the following command (or entering the corresponding values into Qjackctl): 

jackd -R -P89 -dalsa -dhw:2 -r48000 -p256 -n3 -S

You can omit the "-S" if your card supports 24bit or 32bit access as well and you want to use that.

Request: could somebody please provide info on what needs to be done to set IRQs properly? ad the snd-usb-audio module with the parameter "nrpacks=1", maybe including it into one of the boot scripts:: 

modprobe snd-usb-audio nrpacks=1

    * Or use the module configuration line (e.g. in /etc/modprobe.conf): 

options snd-usb-audio nrpacks=1

    * Now invoke JACK with the following command (or entering the corresponding values into Qjackctl): 

jackd -R -P89 -dalsa -dhw:2 -r48000 -p256 -n3 -S

You can omit the "-S" if your card supports 24bit or 32bit access as well and you want to use that.

Request: could somebody please provide info on what needs to be done to set IRQs properly? 

Are these options disabled in the default realtime kernel on Hardy??  Seems kind of stupid to have Experimental options on in a LTS.

---

### Post by gorkon on 2008-05-04
More investigation.  I found that no matter what I did in /etc/security/limits.conf I was unable to get the nice level up of jackd.  At least that's what I thought happened unless System Monitor is lying to me! :D

Pulse Audio is running at -11 nice level.  

Also, I noticed the standard audio group seems to be missing in Hardy.  I try adding it by hand and was unable to add it.  I assign rtprio to my own signon in /etc/security/limits.conf as well as the memlock and other line.

Right now, I am about ready to revert back to gutsy and just deal with some of the issues I had on gutsy that I don't have in Hardy (namely, suspend doesn't work on Gutsy on my Lenovo T60).

I have a hunch that Pulse is the culprit here possibly.  Things have just NOT worked as well on Hardy for audio production as it did on Gutsy.  :P

---

### Post by friderman on 2008-05-04
Seems like linux-rt in hardy has serious troubles keeping low latencies.
Running cyclictest from rt.wiki.kernel.org gives latencies up to 1800 us in my system. 
Don't know how to fix it. I tried to compile the latest rt patch (2.6.24.4) in a vanilla kernel but it doesn't get any better.
I'm rolling back to gutsy by now. 
Maybe when the rt patch comes out for 2.6.25...

If anyone has a solution, please share!

Regards

---

### Post by gorkon on 2008-05-04
> **friderman said:**
> Seems like linux-rt in hardy has serious troubles keeping low latencies.

So it's NOT JUST ME???  WOO! :D  

I am looking at downloading JackLab or something else until I see something different.

It's a shame because the rest of Hardy is friggin outstanding!

---

### Post by thorgal on 2008-05-04
go 64studio, it's debian under, the father of ubuntu so it won't be too foreign (jacklab is suse, the admin is sorta different than on debian systems)

---

### Post by prismatic7 on 2008-05-05
> **gorkon said:**
> So it's NOT JUST ME???  WOO! :D  

I am looking at downloading JackLab or something else until I see something different.

It's a shame because the rest of Hardy is friggin outstanding!

It's not just you... It's not pulseaudio either - I've tried out my usual workflow after 'killall pulseaudio' and realtime performance is still appalling. I've gained some improvements by stopping compiz in favour of metacity, but even so, my UCA202 (the device you're buying) is running at some 69ms latency (opposed to the 11ms or lower I used to get)'

If compiz is interfering with realtime performance, that's going to be really irritating. After all, OSX has a composited, 3D accelerated GUI *and* a low-latency audio server...

Ah well, bug report time...

---

### Post by prismatic7 on 2008-05-05
I've [reported a bug](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/226872). Please add as much detail as possible, guys.

---

### Post by gorkon on 2008-05-08
> **prismatic7 said:**
> I've [reported a bug](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/226872). Please add as much detail as possible, guys.

Thanks for doing the bug report.  I concur...still have the issue with my Behringer too.

At the rate I am going, Gutsy may be going back on this machine.  I have a old athlon box with Gutsy on it now, but the fan in it is so damn noisy recording on it would SUCK!

---

### Post by gorkon on 2008-05-08
> **prismatic7 said:**
> I've [reported a bug](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/226872). Please add as much detail as possible, guys.

I read your bug report and I don't think it has anything to do with compiz, perse.  I think it's a kernel issue.  specifically, those 2 experimental USB items I posted earlier in the thread.  

Either that or something in the configuration is munged between gutsy and hardy.  

Incidentally, I also tried this on Ubuntu Studio and while having less configuration to do (it seems the linux-rt package should setup the security limits....it doesn't), it still is xrunning like crazy even after disabling Compiz.

---

### Post by MetalMusicAddict on 2008-05-08
Are running actual Studio or Ubuntu with -rt kernel?

---

### Post by gorkon on 2008-05-08
> **MetalMusicAddict said:**
> Are running actual Studio or Ubuntu with -rt kernel?

I've tried both.  To no avail.  Lots of xruns....

---

### Post by robeast on 2008-05-09
I've been using Hardy with the rt kernel 2.6.24-16-rt and my audio performance is also worse than it was with Gutsy, but not by nearly as much as you all are experiencing! I have an AMD Athlon64 3000+, 1.5gb RAM and a Presonus Firepod. It definitely seems like compiz-fusion is taking more of a toll on my processing power, because in Gutsy I had full-on everything and occasionally the video would get choppy. In Hardy the video remains fast and the audio gets choppy if some crazy compiz effects are running! I think most of my problems are coming from my Hardy hd being a slave to the Gutsy hd at the moment.

---

### Post by nalmeth on 2008-05-09
I don't know what your problem is, but I'm reporting excellent latencies here. My Firepod has never worked better than under hardy (Ubuntu with linux-rt). 2.9 ms with no xruns or clipping in the audio.

I'm pretty sure that in limits.conf, if you're just setting the variables for AUDIO, you have to make sure you are in a group called AUDIO. 
This may already be the case if you're using UbuntuStudio, but I think that in default hardy there is no such group AUDIO. That could explain why editing limits.conf has had no effect.

---

### Post by gorkon on 2008-05-11
> **nalmeth said:**
> I don't know what your problem is, but I'm reporting excellent latencies here. My Firepod has never worked better than under hardy (Ubuntu with linux-rt). 2.9 ms with no xruns or clipping in the audio.

I'm pretty sure that in limits.conf, if you're just setting the variables for AUDIO, you have to make sure you are in a group called AUDIO. 
This may already be the case if you're using UbuntuStudio, but I think that in default hardy there is no such group AUDIO. That could explain why editing limits.conf has had no effect.

I have tried with Ubuntu Studio and Hardy to create a audio group and it does not stick in the graphical utility.  I am using the manager from the Administration menu.  Should I just do it via the files (/etc/group and so on...)??

Also, I might add, this is on USB devices where we're seeing this.  I don't have a Firepod.  I have had a Griffin iMic and a Behringer UCA-202 working with 11 ms latencies and NO xruns on Gutsy and I also tried a Studio 64 Live CD and it worked great there too even on the live CD.  

When I went to Hardy in either straight Ubuntu or Ubuntu Studio, latencies are garbage.  

I am not expecting to do multitrack recording....just two tracks.  One for my vocal and one for the music (recording a Podcast).

Both USB sound devices worked great on Gutsy,

I also saw Audacity having issues too.  

I even tried installing the proposed updates to hardy (which include a new kernel too) and they didn't help either.

---

### Post by enaoutan on 2008-05-12
Hi!

As for myself, I also did the upgrade from Gutsy to Hardy and jack is always crashing : it's too annoying!!! Before, with Gutsy it was not really stable but it usually worked. Now with Hardy tears are going to rust my edirol FA101 (firewire) 'cause I (almost) cannot play anything (Hydrogen, Ardour, Rosegarden, Zynaddsufx, and even Qarecord!!!) with jack before it crashes (after 5s, 1mn, 30s, ... it's total random).
Therefore  I'd like to go back to Gutsy : how can I do without uninstalling everything? Does "downgrading" exist on Ubuntu studio???
Thanks for reading and ideas (if ever...)

---

### Post by nlz on 2008-05-12
It doesn't seem to be recognized as a real problem, but the real bad performance of JACK in hardy drives me crazy, and downgrading just isn't possible.
If no-one can tell me when this problem is going to be solved, i think i'm going to reinstall gutsy..

Maybe it's an good idea to post our hardware specs, jack settings and limits.conf to see if there is something similar or a solution.

A huge lot of xruns and:

Sony Vaio VGN-FZ31M
Intel Core 2 Duo Processor T7250
2 GB ddr2 RAM
nVIDIA Geforce 8400M GT
HDA intel

priorty 89
Frames/Period 64
Sample rate 44100
Periods/Buffer 15
Port Maximum 256

```

@audio - rtprio 99
@audio - nice -10
@audio - memlock 1031014

```

---

### Post by nalmeth on 2008-05-12
> **gorkon said:**
> I have tried with Ubuntu Studio and Hardy to create a audio group and it does not stick in the graphical utility.  I am using the manager from the Administration menu.  Should I just do it via the files (/etc/group and so on...)??

Also, I might add, this is on USB devices where we're seeing this.  I don't have a Firepod.  I have had a Griffin iMic and a Behringer UCA-202 working with 11 ms latencies and NO xruns on Gutsy and I also tried a Studio 64 Live CD and it worked great there too even on the live CD.  

When I went to Hardy in either straight Ubuntu or Ubuntu Studio, latencies are garbage.  

I am not expecting to do multitrack recording....just two tracks.  One for my vocal and one for the music (recording a Podcast).

Both USB sound devices worked great on Gutsy,

I also saw Audacity having issues too.  

I even tried installing the proposed updates to hardy (which include a new kernel too) and they didn't help either.
You should be able to do this with the GUI, when a user is highlighted you should be able to hit 'Manage Groups', add the audio group, then highlight it and make sure your username is checked. 

If all this is done and latencies are not better, then maybe you should go to Studio 64. Its a great studio distro, and if its working better there, I wouldn't fight to get things going on Ubuntu.

---

### Post by nlz on 2008-05-12
> **nalmeth said:**
> You should be able to do this with the GUI, when a user is highlighted you should be able to hit 'Manage Groups', add the audio group, then highlight it and make sure your username is checked. 

If all this is done and latencies are not better, then maybe you should go to Studio 64. Its a great studio distro, and if its working better there, I wouldn't fight to get things going on Ubuntu.

off-topic: I just downloaded this 64studio and it is really nice (on my dektop)! But the xserver won't work on my laptop with the livecd and i couldn't get it working. Is this a common problem for 64studio? I couldn't find a workaround through google of their site.

---

### Post by thorgal on 2008-05-12
what's your graphics chip ?

---

### Post by MetalMusicAddict on 2008-05-12
Can someone try adding **nohz=off** to their grub line for the -rt kernel only?

Example:

Terminal: sudo nano /boot/grub/menu.lst
```
[SIZE="1"]title           Ubuntu 8.04, kernel 2.6.24-16-rt
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.24-16-rt root=UUID=d01c8f74-2cb0-4f2e-940e-8428084b03f3 ro quiet splash **[COLOR="Red"]nohz=off[/COLOR]**
initrd          /boot/initrd.img-2.6.24-16-rt
quiet[/SIZE]
```

---

### Post by tgalati4 on 2008-05-12
Give Dynebolic a spin (dynebolic.org).  It's a live CD geared toward audio recording.  You can save a "nest" of your configuration files and save your data files to your existing Projects directory.

I'd be curious to know what your USB device latencies are running jackd under Dynebolic.

---

### Post by prismatic7 on 2008-05-13
OK. After a week or so of investigation - hosing my laptop and installing 64Studio, then hosing again and installing straight UbuntuStudio, I'm convinced I was wrong about Compiz. Very wrong. With Compiz enabled on 64Studio (painful. Very painful. I recommend not.) I was still getting rock-solid 11ms or lower latencies from my UCA202. Back on UbuntuStudio now, I'm getting 46ms or greater, with audible crackles and XRUNs beyond 130ms. 

This is really, really annoying. I'm already stuck using the broken Nvidia beta driver because *certain* Nvidia cards don't work with the -rt kernel, so I can't take my laptop mobile because it doesn't suspend or resume reliably. Furthermore, I can't use my laptop off the power supply because the beta driver plays badly with power management and Compiz. I realise that the workaround here is not to use compiz, but it's pretty hard in the Mac-dominated sound world to try to show off how good the Linux platform is when IT DOESN'T WORK.

GAH!

Sorry. Whinging

---

### Post by thorgal on 2008-05-13
may I ask why, if you get a decent performance with 64studio, you need compiz on top of that ? and why do you switch back to ubuntu if you only get worse perf ? unless your box is not dedicated entirely to music prod, I don't see the need. I am just curious, not really advising anything.

---

### Post by prismatic7 on 2008-05-13
> **thorgal said:**
> may I ask why, if you get a decent performance with 64studio, you need compiz on top of that ? and why do you switch back to ubuntu if you only get worse perf ? unless your box is not dedicated entirely to music prod, I don't see the need. I am just curious, not really advising anything.

I use a number of functions in compiz for my personal productivity - I find things like the Scale and Expo plugins really useful, and I also use live taskbar window previews for quickly monitoring my Ardour sessions (mixer on one workspace, arrangement on another, for example - try it, I recommend it!)

64Studio gave me good audio performance, but I couldn't make suspend, hibernate, bluetooth, my wireless card or even my mousewheel work. Have you tried NOT having a mousewheel at any stage in the last 10 years?! Madness. 64Studio was better than configuring Debian back in the pre-Ubuntu days when I last used that distro, but I don't have time or energy to spend tweaking much anymore! So, back to Ubuntu, which at least recognises all my hardware and lets me use it without (too many) issues.

As for a solely production-oriented machine, well... This is my laptop, dig? I use it for everything - uni (sound design), business (sound design for theatre), web, etc. Everything except games! Compiz - while not as well-integrated as the visual effects in OS X - is pretty good in terms of memory and CPU these days, and as I said earlier I use it in my workflow.

As I said in my earlier post, I tried Compiz on 64Studio and jackd performance remained pretty solid. Therefore I'm inclined to believe that my earlier insistence that XRUNs and bad audio were Compiz' fault was probably all in the mind!

In any case, my desktop is *prettttyyyyyy*!

---

### Post by thorgal on 2008-05-13
your hardware issues with 64studio don't sound good ... could not have mousewheel ??? wow, that's lame ...
I did not have any of these issues. It must depend on hardware vendors ... but I see your point about compiz. I had it working on my laptop at the time it forked out to beryl. It was nice but too distracting to my taste. Anyway, good luck with your xrun hunt :)

---

### Post by nalmeth on 2008-05-13
In my experience, compiz is just _not usable_ with a low-latency setup.

There is a consistent crackling that occurs with compiz enabled, and as much as I love the features I can't deal with that kind of crackling, especially during recording. And at all other times it is more annoying than the features are useful.

I hope you can get a sane setup going with compiz, but I tell you, I doubt it can happen without some impressive 'ing hardware.

---

### Post by gorkon on 2008-05-13
> **thorgal said:**
> what's your graphics chip ?

ATI Mobility Radeon X1400 

Never had an issue on Gutsy.

---

### Post by gorkon on 2008-05-13
> **MetalMusicAddict said:**
> Can someone try adding **nohz=off** to their grub line?

Example:

Terminal: sudo nano /boot/grub/menu.lst
```
[SIZE="1"]title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=d01c8f74-2cb0-4f2e-940e-8428084b03f3 ro quiet splash **[COLOR="Red"]nohz=off[/COLOR]**
initrd          /boot/initrd.img-2.6.24-16-generic
quiet[/SIZE]
```

THAT GOT IT!  WOO HOO!  5.8 msec latency and only 1 XRUN when I connected Audacious mid stream(normal).  Used this to start:

/usr/bin/jackd -R -P89 -p128 -t1000 -dalsa -r44100 -p128 -n2 -D -Chw:1,0 -Phw:1,0 -i2 -o2

This is with a Behrunger UCA-202.  I am LIKING this now!  W00t!

To the others....we don't want to switch from Ubuntu.  We want to make Ubuntu better.  If we don't share the issues we're having, noone will ever see the fix!  

Now someone get this into a patch!  Or at the very least some documentation somewhere.  Thanks MetalMusicAddict!

---

### Post by gorkon on 2008-05-14
> **nalmeth said:**
> In my experience, compiz is just _not usable_ with a low-latency setup.

There is a consistent crackling that occurs with compiz enabled, and as much as I love the features I can't deal with that kind of crackling, especially during recording. And at all other times it is more annoying than the features are useful.

I hope you can get a sane setup going with compiz, but I tell you, I doubt it can happen without some impressive 'ing hardware.

With the nohz=off line in the grub menu as suggested, I am now seeing 5.8 msec latency and no xruns with compiz active on a a Lenovo T60 laptop with my Behringer UCA-202 interface.  Try that if your having issues.

---

### Post by Stochastic on 2008-05-14
> **MetalMusicAddict said:**
> Can someone try adding **nohz=off** to their grub line?

Example:

Terminal: sudo nano /boot/grub/menu.lst
```
[SIZE="1"]title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=d01c8f74-2cb0-4f2e-940e-8428084b03f3 ro quiet splash **[COLOR="Red"]nohz=off[/COLOR]**
initrd          /boot/initrd.img-2.6.24-16-generic
quiet[/SIZE]
```

What does that flag do?  Would it be useful/safe for the average user?

---

### Post by nlz on 2008-05-14
> **thorgal said:**
> what's your graphics chip ?

nVIDIA Geforce 8400M GT

---

### Post by thorgal on 2008-05-14
> **Stochastic said:**
> What does that flag do?  Would it be useful/safe for the average user?

it turns off the recently introduced kernel tickless mode. When I compile my own kernel, I always go for a frequency of 1000Hz but recently, there's a possibility to run the kernel tickless. But it seems like it breaks a few things. I am no expert in these matters but you can certainly google some info around.

About the graphics chip :
I don't know about you guys but when it comes to graphics, I only use my intel mobo's integrated chip and disabled a lot of fancy things in my xorg.conf (3D acc, even 2D acc because intel's GPUs are using PCI access for this). I get a rock solid desktop (using openbox tweaked to look like KDE), maybe a bit more sluggish than h/w accelerated ones but with NO collision with the audio processing whatsoever.

ATI and nVidia GPUs tend to "belive" (if things can believe :) ) that they are the most important part of your machine so many default setup will allow them to bulldoze anything on the PCI bus or CPU access path if they want to. So be aware that there is a lot of "internal politics" going on between your different devices regarding who should do what first and prioritarily (am I making a new word ? :lol: )

---

### Post by prismatic7 on 2008-05-14
> **MetalMusicAddict said:**
> Can someone try adding **nohz=off** to their grub line?

Example:

Terminal: sudo nano /boot/grub/menu.lst
```
[SIZE="1"]title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=d01c8f74-2cb0-4f2e-940e-8428084b03f3 ro quiet splash **[COLOR="Red"]nohz=off[/COLOR]**
initrd          /boot/initrd.img-2.6.24-16-generic
quiet[/SIZE]
```

Oh. Oh wow... That REALLY doesn't work with my setup. I get the same compiz behaviour I do from powersaving modes - 100%+ CPU usage, lockups, whitescreening... I think (given it's the source of so much else that's terrible in my life right now) that the Nvidia beta driver I have to use causing the problem.

Interestingly, could it be the tickless kernel that causes the regular, Ubuntu-packaged driver to fall over with -rt flavours? After this show goes up (next week) I'll spend a day or so testing...

---

### Post by MetalMusicAddict on 2008-05-14
Crap. I accidentally added an example that showed -generic when it should have only been for -rt. *Example corrected.

Let it also be noted that this was a [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229499"), and the bug has received a [SRU approval]("https://lists.ubuntu.com/archives/kernel-team/2008-May/002466.html"). So it will at the very least make the 8.04.1 updates.

---

### Post by eric71 on 2008-05-14
Thanks for this quick fix. I've hardly had a chance to do any recording since I installed Hardy, but I had noticed things weren't running too well when I set it all up. This is a great thing about the Ubuntu community. Things like this are found, there's always someone who can help, and the developers get things fixed. I'm running out of excuses for my out of control distro hopping.

---

### Post by prismatic7 on 2008-05-14
> **MetalMusicAddict said:**
> Crap. I accidentally added an example that showed -generic when it should have only been for -rt. *Example corrected.

Let it also be noted that this was a [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229499"), and the bug has received a [SRU approval]("https://lists.ubuntu.com/archives/kernel-team/2008-May/002466.html"). So it will at the very least make the 8.04.1 updates.

Yeah, I figured you meant -rt, so that was where I put it... With shattering results...

---

### Post by MetalMusicAddict on 2008-05-14
> **prismatic7 said:**
> Yeah, I figured you meant -rt, so that was where I put it... With shattering results...

Sorry you're havin' bad luck. Between posts here and the mailing list this looks to be helping most people.

---

### Post by prismatic7 on 2008-05-15
> **MetalMusicAddict said:**
> Sorry you're havin' bad luck. Between posts here and the mailing list this looks to be helping most people.

Not me, unfortunately. The key here is really that damn Nvidia driver...

And I've just had my Saffire LE delivered, and I can't get that to work either... but that's another matter entirely.

---

### Post by cb951303 on 2008-05-15
I got an onboard sound card (a realtek I think?)
I installed jackd + qjackctl and here is how my setup looks (I didn't change anything else)

it says 17.4 ms for latency but I played my guitar trough 3 jack-rack +1 ardour with 2 buses with a total of 10 ladspa plugins enabled, and I didn't notice any latency so I'm thinking it's less than 10ms in real.

EDIT: BTW I don't use -rt kernel, should I use it to apply realtime effects to my guitar?

---

### Post by nlz on 2008-05-15
> **prismatic7 said:**
> Not me, unfortunately. The key here is really that damn Nvidia driver...

And I've just had my Saffire LE delivered, and I can't get that to work either... but that's another matter entirely.

I also have the Nvidia driver, and after i used MetalMusicAddicts hack for the kernel i have no problem at all.

I have a Nvidia Geforce 8400 M GT

---

### Post by robeast on 2008-05-15
> **cb951303 said:**
> 
it says 17.4 ms for latency but I played my guitar trough 3 jack-rack +1 ardour with 2 buses with a total of 10 ladspa plugins enabled, and I didn't notice any latency so I'm thinking it's less than 10ms in real.

Humans start to notice delays a between 20-50ms. If you are monitoring a mix of your input and output you would definitely hear your latency as a chorus effect, but if you are only monitoring your wet signal you might not even notice a delay of 17ms.

> **cb951303 said:**
> 
EDIT: BTW I don't use -rt kernel, should I use it to apply realtime effects to my guitar?

You can use everything with your present kernel, however you should get increased performance with an -rt kernel.

---

### Post by prismatic7 on 2008-05-15
> **nlz said:**
> I also have the Nvidia driver, and after i used MetalMusicAddicts hack for the kernel i have no problem at all.

I have a Nvidia Geforce 8400 M GT

Are you using the stock Ubuntu-packaged driver or the Beta? I can't use the Ubuntu-packaged driver because it causes my system to lock up - as reported in February ([Bug #197130](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/197130))

---

### Post by nlz on 2008-05-16
> **prismatic7 said:**
> Are you using the stock Ubuntu-packaged driver or the Beta? I can't use the Ubuntu-packaged driver because it causes my system to lock up - as reported in February ([Bug #197130](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/197130))

I'm amazed, because i'm using all the standard modules and i am expriencing no problems whatsoever. Only Ubuntu Studio Controls is quite instable.

---

### Post by MetalMusicAddict on 2008-05-16
> **nlz said:**
> Only Ubuntu Studio Controls is quite instable.
What does that have to do with the current chat?

---

### Post by nlz on 2008-05-16
> **MetalMusicAddict said:**
> What does that have to do with the current chat?

absolutely nothing. I was only pointing out the only troubles i have with Ubuntu Studio and the -rt config.

---

### Post by jwmislan on 2008-05-20
> **MetalMusicAddict said:**
> What does that have to do with the current chat?


Ububtu Studio 8.04 
Has realtime capabilities built-in now - no more (realtime.lsm) module necessary.
There was unfortunately no Ubuntu Studio 8.04 release notes detailed about this.

May be my posts in this, (Ubuntu Studio Sound) thread, Referring to setting of the new -  System - Administration - (Ubuntu Studio Controls) option in Ubuntu's 8.04 
  can help a few here.

[http://www.backports.ubuntuforums.org/showthread.php?t=775501](http://www.backports.ubuntuforums.org/showthread.php?t=775501)

It's short, - a two page thread.

JWM

---

### Post by gorkon on 2008-06-04
Guys, just so you know, it's fixed.  Check out:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229499](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229499)

The kernel update I downloaded today has the nohz line in it.  So you can go back to a standard menu.lst.  Yippeee!

---

### Post by kramthegram on 2008-06-05
The nohz=off line seems to have helped quite a bit but there is still some slowdown. When I first moved my audio rig to Hardy it was terrible, so I did some research and found that the audio group was not set up properly. Eventually I did a complete reinstall and added the audio group with rt priority and memlock. When I did this I got blazing speeds(rare xruns at 64B frames). However, once I let the system update run I began having terrible xruns at even 1024. I cam here and found the nohz-off setting was helping other, I tried it and have improved to only a few xruns at 1024. Has anyone else seen a difference between a brand new install with proper audio group settings without the nohz=off flag and a fully updated hardy with the aforementioned flag? I'm wondering if reinstalling and going with a non updated system would be the better choice for speed as I can't seem to get it back down since updating.

---

### Post by faust99 on 2008-06-06
I've tried the kernel fix mentioned above but have noticed no change in the massive latency. Being a noob, I am only plugging in though the microphone input on my laptop rather than either firewire or usb. Could this be a source of lag as well?

---

### Post by nlz on 2008-06-08
> **faust99 said:**
> I've tried the kernel fix mentioned above but have noticed no change in the massive latency. Being a noob, I am only plugging in though the microphone input on my laptop rather than either firewire or usb. Could this be a source of lag as well?

no, that shouldn't be the problem. Have you tried tinkering with the setting of JACK (frames, sample rate and periods)?

You can do a lot with that line in, and if you use only one line in and don't want to do massive professional multitrack production, one input is fine for the time being.

Do you have the -rt kernel installed? And did you enable the memlock in system>administration/studio settings?

---

### Post by faust99 on 2008-06-08
> **nlz said:**
> no, that shouldn't be the problem. Have you tried tinkering with the setting of JACK (frames, sample rate and periods)?

You can do a lot with that line in, and if you use only one line in and don't want to do massive professional multitrack production, one input is fine for the time being.

Do you have the -rt kernel installed? And did you enable the memlock in system>administration/studio settings?

Yes I've started to play around with those jack settings and have gotten a smaller latency. The signal gets interrupted sometimes when I adjust those settings for a lower latency. I do have the rt kernel installed, although I'm using straight ubuntu. I couldn't get studio to run properly-i couldn't use wireless as it wouldn't recognise my card.

---

### Post by geoff123 on 2008-06-17
Yes the new kernel is much better.

---

### Post by eyecolor on 2008-08-16
> **cb951303 said:**
> I got an onboard sound card (a realtek I think?)
I installed jackd + qjackctl and here is how my setup looks (I didn't change anything else)


thanks for posting the image - that helped me making it work
:)

---

