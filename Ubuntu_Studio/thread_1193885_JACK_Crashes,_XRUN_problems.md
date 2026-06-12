---
title: "JACK Crashes, XRUN problems?"
date: 2009-06-22
forum: Ubuntu Studio
---

### Post by SneakerElph on 2009-06-22
Hello everyone! I'm running xubuntu 9.04 with the realtime kernel because I'm doing audio production business. I use JACK to route all my audio. I know this is an age old question, but I'm working to reduce my XRUNs. My system is as follows:

Athlon 64 3000+
1.5GB DDR667 RAM
80 Gig Hard Drive
Soundblaster Audigy 2 ZS

I have my frames set to 1024, 44.1KHz and JACK runs in realtime. I'm getting thousands of XRUNs a minute. I notice no gap in music playback from my software (The Rivendell Radio Automation suite). I'm using Darkice to stream audio to the internet, and it seems to run okay for about an hour or so, before it crashes with a

ALSA: could not complete playback of 1024 frames

After a few hundred thousand XRUN errors, I finally get a drop in audio for a split second, with the error

**** alsa_pcm: xrun of at least 0.064 msecs

After this I get no xruns for a few minutes, before they start to come again.

Eventually Jack crashes, taking Darkice and Rivendell with it.

I would think that I could run at much lower frames/period with my soundcard. Could my processor be a bottleneck? It would seem to be plenty for audio playback onto the internet, and JACK doesn't take up more than a few percent of CPU time, so I don't think that's the problem.

Anyway, I'm sorry for being so long winded. Can anyone help me with my crashing problem? I'd like this to be a production machine that I can leave on 24/7 unattended, but if JACK crashes after about an hour, then that's not possible.

Thanks!

---

### Post by sgx on 2009-06-22
Hi, does this file 

file: /etc/security/limits.conf

have these lines added to the end of it?


@audio          -       rtprio           99
@audio          -       nice             -19
@audio          -       memlock          unlimited

and does the audio group exist, and are you a member?

If yes, is your priority in qjackctl set to 89?
This is not possible, so I am told, without the '99' value for rtprio in the text above, and is the highest figure one can set in qjackctl

So there must be an audio group on your system, of which you
are a member, with limits.conf modified as above. but  you can specify a
memlock amount, and adjust the 99 and 19. I admit seeing several values
other than 19 posted around various forums, someone who knows may offer a better number?

Also, bad luck sometimes follows my jackd, if run during or after a Mozilla or Opera browsing session. This seems more common with an RT kernel than the newest stock kernel I have, so try running  your setup from the newest stable non-rt kernel, and compare the results. Opera may be the lesser of two evils, I don't even have mozilla on my daw anymore.

More info about your system and settings would help others who have more
knowledge, but I would hunt down 4 gigs of memory, a secong hard-disk for data, and an older maudio 24/96 pci card, or other 'known to work' card also based on the same ice1712 chips, if you are in this for the long haul.
cheers:)

---

### Post by raboofje on 2009-06-23
See also [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

---

### Post by SneakerElph on 2009-06-23
> **sgx said:**
> Hi, does this file 

file: /etc/security/limits.conf

have these lines added to the end of it?


@audio          -       rtprio           99
@audio          -       nice             -19
@audio          -       memlock          unlimited

and does the audio group exist, and are you a member?

If yes, is your priority in qjackctl set to 89?
This is not possible, so I am told, without the '99' value for rtprio in the text above, and is the highest figure one can set in qjackctl

I've done all this, and setting priority to 89 helps some, but doesn't get rid of the crashing problem. I could deal with the XRUNs, since they seem to cause no noticeable problems, it's just that I suspect them to be the problem when it crashes. Hunting down 4 gigs of RAM is possible, I suppose, but that just seems to be overkill since I'm not doing any audio editing or anything like that, just playback and streaming to an icecast server that's offsite.

Using the regular kernel as the same problems, it doesn't seem to change between RT and generic kernel. I'll have to play around with it some more.

---

### Post by raboofje on 2009-06-23
> **SneakerElph said:**
> crashes with a

ALSA: could not complete playback of 1024 frames

Which version of Jack is this? And which version of the alsa modules?

This error is produced by the jack alsa driver at [http://trac.jackaudio.org/browser/trunk/jack/drivers/alsa/alsa_driver.c](http://trac.jackaudio.org/browser/trunk/jack/drivers/alsa/alsa_driver.c) . The code there suggests it should print an error number. Does it?

---

