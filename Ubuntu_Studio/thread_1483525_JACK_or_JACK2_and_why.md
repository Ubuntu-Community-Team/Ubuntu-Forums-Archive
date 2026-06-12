---
title: "JACK or JACK2 and why?"
date: 2010-05-14
forum: Ubuntu Studio
---

### Post by hxcobd on 2010-05-14
Seeing as to the end-user, they function basically identically, what exactly should be one's basis for choosing one or the other?

Am I going to run into weird dependency problems if I install one and not the other? I've heard you're not supposed to have both installed on one system at one time (doing this very thing on my previous install and having JACK display extremely strange output seems to verify this).

---

### Post by thorgal on 2010-05-15
jack2: multicore CPUs, glitch-free connection to the graph, other (more experimental) features to boost process callback execution of clients

jack1: single core CPU, more mature

jack2 is an attempt to overcome jack1's shortcomings. I've been using it for 1.5 year and it is quite nice. I've experienced solid performance against the vanilla kernel (using 2.6.32 ATM) and practically no xrun (only due to client crashes or poorly coded process callback functions).
the glitch-free graph modification is really a big +! you can add or remove jack clients and not hear a single glitch while other clients are playing.

my experience with jack1 is not as good so I don't try to use it. YMMV.

---

### Post by hxcobd on 2010-05-15
Thanks for the reply, thor.

I ended up installing JACK2 simply because it seems to get the most updates as of late. Looks to be running fine for me (and you're right, the number of xruns looks to be drastically reduced), so I suppose I made the right call!

One thing I did notice is that in JACK2's settings, its default priority is set VERY low, to a value of 10. I seem to recall JACK1 being set to "auto" or something to that effect.

You can of course manually increase this priority (to a max of 89, strangely?), but it'd be nice if it had the same "auto" option JACK1 did.

---

### Post by trulan on 2010-06-07
I've always wondered why so many people seemed to prefer Jack2.  I have always seen noticeably worse performance with Jack2 than with Jack1 (Presonus Firepod, via Ffado drivers).  Today that changed.  I found thorgal's post here:

In short, I added```
-S
``` to the command line in QjackCtl.  It puts jack in synchronous mode (apparently as opposed to asynchronous mode, which if I understand correctly is a new feature of Jack2.)
```
/usr/bin/jackd -S
```For the first time ever I can say Jack2 actually works better than Jack1.
:):):)

:guitar:

---

### Post by thorgal on 2010-06-08
hi trulan,

you should probably check that the jack transport mode works as you expect it. I recall Pablo Fernandez reporting issues with this transport mode.

I hardly use it myself (only when programming drum lines in rosegarden while ardour plays the audio tracks) so I never really had any deep feel of the quality of jack2's transport mode.

---

### Post by gaz514 on 2010-06-08
I use Jack1 because Jack2 just doesn't appear to be at all compatible with my card (Echo Audiofire 6).

---

### Post by trulan on 2010-06-08
> **thorgal said:**
> hi trulan,

you should probably check that the jack transport mode works as you expect it. I recall Pablo Fernandez reporting issues with this transport mode.

I hardly use it myself (only when programming drum lines in rosegarden while ardour plays the audio tracks) so I never really had any deep feel of the quality of jack2's transport mode.
Sorry, I'm not a good one to test Jack Transport.  I work almost exclusively with acoustic instruments and vocals, and I've never used Jack Transport even once.

I revisited this because Debian Testing has moved to that, and a lot of upgrades over there were dependent on Jack2.  So far it's noticeably more stable than Jack1 had been.

---

### Post by thorgal on 2010-06-08
> **gaz514 said:**
> I use Jack1 because Jack2 just doesn't appear to be at all compatible with my card (Echo Audiofire 6).

that would be very weird, jack (1 or 2) knows close to nothing about the h/w. Jack1 and Jack2 should provide the same functionality to the user.

@trulan: it is quite the same for me, I am an "old school" instrumentist, i.e. I play real instruments for real :lol: except for the drumming, which I need to sequence. But there, my use of the jack transport is very limited so I did not see any real issue.

And yes, jack1 has been very unstable on my system. Everytime a client triggers a blip, the whole graph becomes unusable and the sound heavily distorted (when jack survives, that is). jack2 does not exhibit these issues, I have no xrun at all latencies, and the glitch-free graph changes are really cool. Only ardour does something unusual when I create or delete a track, as I hear a little "bzzz" while I do that.

I tried the more experimental jack2 branch but they did not fulfill their promise to perform better than the main trunk. Maybe I misused the experimental options ... but I do not need them. 

Since I use a2jmidid for MIDI, MIDI ports have real names as well :) I do not use the jackd -dalsa -X option anymore. Jack2 provides a poor naming for MIDI ports. I think a2jmidid should be made into an in-process client that one could trigger with a jackd option. I will ask the jack audio dev mailing list.

---

### Post by Pablo_F on 2010-06-08
Hi!

> you should probably check that the jack transport mode works as you expect it. I recall Pablo Fernandez reporting issues with this transport mode.

The jack2 transport issue is very old, I just bumped it in the LAU mailing list because it has not been solved yet ](*,)

Here it is:
[http://tracker.ardour.org/view.php?id=2856](http://tracker.ardour.org/view.php?id=2856)

I think this is the same issue, with a much more technical explanation:

[http://tracker.ardour.org/view.php?id=2569](http://tracker.ardour.org/view.php?id=2569)

So they are working on it...

This bug is what makes me stick to jack1, even if the workaround is not a big hassle. My user case is ardour with tempo changes and I want hydrogen to follow them. I need ardour as master for this. 

What I really like about jack2 is that netjack is sooo easy to setup. "Netjack2 or how to expand your studio" by thorgal at Linuxmusicians explains it very well :-({|=

Cheers! Pablo

---

### Post by Peter7K on 2010-09-21
I currently would like to revert back from Jack2 down to Jack1.  I'm not sure how to do this without uninstalling all of my audio plugins.  

I currently use [http://ubuntuforums.org/showthread.php?t=1350304]("http://ubuntuforums.org/showthread.php?t=1350304") FalkTx PPA, so here is the package: [https://launchpad.net/~falk-t-j/+archive/lucid/+build/1959154](https://launchpad.net/~falk-t-j/+archive/lucid/+build/1959154)

Is there a way to downgrade without uninstalling everything?  I don't even see a Jackd regular package.

The jack2 package appears to reinstall itself whenever I reinstall ubuntustudio-audio.

---

### Post by mango42 on 2010-09-21
+1 Peter7K

I'd love to know how to do that successfully as well, as I've hit a brick wall trying to get Jack to route my firewire i/f on 64bit Lucid Studio.

Synaptic tells me I am using **jackd & jackd-firewire version 0.118+svn3796** but issuing **jackd -v** from the commandline returns version **0.119**. Hmm - I only have AutoStatic's PPA enabled and hardly ever put that machine online anyway.

Well at least I can *see* the connections in QJackCtl now - they just don't do anything but put a spurious (and strangely inaudible) -3dB signal across channels 5-8.

I know this will work eventually, all thanks to the tenacity of the programmers involved. :)

---

### Post by AutoStatic on 2010-09-21
> **Peter7K said:**
> Is there a way to downgrade without uninstalling everything?  I don't even see a Jackd regular package.That is because you have FalkTX's PPA enabled. Disable it, uninstall Jack2 and reinstall Jack1 from the official repositories.

> **Peter7K said:**
> The jack2 package appears to reinstall itself whenever I reinstall ubuntustudio-audio.That's probably because a lot of packages in FalkTX's PPA depend on Jack2.

---

### Post by AutoStatic on 2010-09-21
> **mango42 said:**
> Synaptic tells me I am using **jackd & jackd-firewire version 0.118+svn3796** but issuing **jackd -v** from the commandline returns version **0.119**. Hmm - I only have AutoStatic's PPA enabled and hardly ever put that machine online anyway.0.119 is not the same as Jack2. 0.119 is the latest Jack1 version available. You probably compiled and installed it yourself. And it's better not to enable my PPA, only download the packages you need.

---

### Post by mango42 on 2010-09-21
> You probably compiled and installed it yourself

No, I don't even know how to! ;-)

The reason I'm trying to return to 0.118 is because you said it works for you with a Saffire interface.

What I'm getting in Jack 1 (0.119) is connections recognised but clock not - at least it doesn't show clock frequency in QJackCtl front panel. Looking at system monitor | processes, it seems Jack is waiting for a clock signal - anyway it just freezes.

---

### Post by AutoStatic on 2010-09-22
> **mango42 said:**
> No, I don't even know how to! ;-):oops: sorry! Then you must've got it from a PPA. Lucid comes with 0.118.0 so you must've upgraded it somewhere along the road.

> **mango42 said:**
> The reason I'm trying to return to 0.118 is because you said it works for you with a Saffire interface.It works with 0.119 too.

> **mango42 said:**
> What I'm getting in Jack 1 (0.119) is connections recognised but clock not - at least it doesn't show clock frequency in QJackCtl front panel. Looking at system monitor | processes, it seems Jack is waiting for a clock signal - anyway it just freezes.You probably mean sample rate.

But we're going offtopic and you're hijacking someone else's thread ;)

---

### Post by mango42 on 2010-09-22
> But we're going offtopic and you're hijacking someone else's thread

True, but have you counted how many 'Jack' threads there are already? ;-)

Thanks for the confirmation that Jack1, 0.119 works for you.

---

### Post by sgx on 2010-09-22
Hi Mangot, find the inconspicuous 'package details'
button on a PPA page, and it will expand the view, and show
the available files to download, for manual installs or compiling.

I would do a fresh install of plain ubuntu, use synaptic to uninstall
any jackd things if present, and then manually install the jackd of choice, and only install/update the apps you use, and the kernel that meets your needs. 
Cheers

---

### Post by mango42 on 2010-09-23
Hi **sgx** - words of wisdom indeed but I've already done so much tweaking to this UbuntuStudio 10.04, I am really loath to start over yet again - it feels so very close to success - ever the optimist ;)

I'm going to do *just one more* run through with that brilliant [realTimeConfigQuickScan.pl]("http://wiki.linuxmusicians.com/doku.php?id=system_configuration&DokuWiki=e6f509f44b88d29f6f9361b8b3066507#quickscan") script... if that doesn't pinpoint my cluelessness, I'm *really* gonna dust off my old Revox B ;)

---

### Post by sgx on 2010-09-23
I&#7743; using this linux lately

[http://www.murga-linux.com/puppy/viewtopic.php?t=57447&sid=41ffb6aa10357928d239555734572ccb](http://www.murga-linux.com/puppy/viewtopic.php?t=57447&sid=41ffb6aa10357928d239555734572ccb)

Its RT, jackd, and wine enabled, even has the Reaper demo installed. All the main audio apps have desktop icons, and it works, and works fast. It runs from ram after loading from the live cd.
At first shutdown, you are asked  about the save options, to set up a hard-disk file to use in future sessions. So you can keep your current linux.The iso is 458 meg.

The download link is below the many pics of the available apps, and has
a username and password to use in the download.
Cheers

---

### Post by mango42 on 2010-09-23
Great suggestion, **sgx** but, being stuck with nVidia SLI graphics, I don't get past setting up X in Puppy (lupu-510.sfs); the screen just freezes blank black - great shame 'cos it looks to be a really good distro.

---

### Post by sgx on 2010-09-23
It seems like I read there are boot arguments you can use for alternate video, if you press the magic key, I'll see what I can dig up :)

---

### Post by sgx on 2010-09-23
Ok, puppy nvidia sli workaround?

Press F2 to get boot arguments prompt, at the prompt type

puppy pfix=nox,ram

This loads the whole shootin match in ram and lands you at a root prompt.

Type    startx

and you will have the option to choose VESA or normal X, so try VESA first.
Hope it works. Isn´t my garden path pretty this time of year? ;)

---

### Post by mango42 on 2010-09-24
[QUOTE="sgx"]Isn´t my garden path pretty this time of year? [/QUOTE]

LOL. Now the thread is totally hijacked - call in the DHS and TSA!! :)

Thanks very much for that - I'll give it another try on *the beast* later. Kinda frustrating because Puppy works flawlessly on this T43 Clunkpad, which however, refuses to do expresscard firewire...

Porro et deorsum

:guitar:

---

### Post by mango42 on 2010-09-24
At the risk of moderator wrath ;-)

[QUOTE="sgx"]Press F2 to get boot arguments prompt, at the prompt type

puppy pfix=nox,ram[/QUOTE]

At what point should F2 work? I'm booting from a USB stick, everything loads into ram and up pops a video probe page - that's where it all comes to a halt, whatever resolution I choose...

---

### Post by sgx on 2010-09-24
Hi, I'm booting from the puppy studio CD, and press F2 right away, I think the screen says you have 5 seconds to choose boot options.:guitar:
Cheers

---

