---
title: "Benefits of an rt kernel"
date: 2009-01-30
forum: Ubuntu Studio
---

### Post by Rog-Mahal on 2009-01-30
I'm just starting out with making some simple electronic music using lmms and hydrogen. I know Ubuntu Studio uses an rt kernel, but I've had some difficulty finding out exactly what kinds of benefits it gives. I'd appreciate some general information just to satisfy my own curiosity. Also, what are people's thoughts on Ubuntu Studio as an all-purpose distro? Are there any pros and cons that I should consider before putting it on as my main distro? Oh, and I'd run 64 bit.

Thanks.

---

### Post by Ng Oon-Ee on 2009-01-31
> **Rog-Mahal said:**
> I'm just starting out with making some simple electronic music using lmms and hydrogen. I know Ubuntu Studio uses an rt kernel, but I've had some difficulty finding out exactly what kinds of benefits it gives. I'd appreciate some general information just to satisfy my own curiosity. Also, what are people's thoughts on Ubuntu Studio as an all-purpose distro? Are there any pros and cons that I should consider before putting it on as my main distro? Oh, and I'd run 64 bit.

Thanks.
RT, simply put, allows you to 'force' low latency, which is especially important if you're going to want to sync a drum track from hydrogen via JACK to everything else. Its ONLY useful for Audio (IMHO), I haven't before noticed any perceptible improvement/degradation in performance for other use.

Ubuntu Studio is a good option (have not tried dynebolic and 64 Studio, myself, Ubuntu Studio has provided everything I need), basically provides everything you need to make your machine a sound production machine. I'd recommend it, of course, but please use 8.04, as 8.10 doesn't have a non-buggy RT kernel. I'd only recommend 8.10 Ubuntu Studio if you're comfortable having two kernels installed, one for audio and one for everything else. The main bugs with 8.10 RT are non-SMP (meaning you only get single core no matter what, doesn't affect non-dual/quad-core machines) and some networking stuff which is easily worked around by turning off your networking before shutting down/hibernating etc.

I myself use Ubuntu Studio 8.10 64-bit, because my audio work only happens around the end of each year (Christmas time) so at this point in time I'd rather have the latest distro. If you choose 8.04, please read up on Pulseaudio/JACK issues, they can be surmounted, there's a good guide [here]("http://ubuntuforums.org/showthread.php?t=789578") which should help you sort all those issues out. And yes, you need JACK for Ubuntu Studio, no point having an RT kernel without it.

I know this reply is messy, anything you're not sure of please feel free to ask =)

---

### Post by raboofje on 2009-01-31
> **Ng Oon-Ee said:**
> RT, simply put, allows you to 'force' low latency, which is especially important if you're going to want to sync a drum track from hydrogen via JACK to everything else.

Indeed, and for `live' playing. Basically, the trade-off is you're giving up a bit of throughput to achive better latancies - for audio, that's desirable :).

> **Ng Oon-Ee said:**
> I'd only recommend 8.10 Ubuntu Studio if you're comfortable having two kernels installed, one for audio and one for everything else.

Note that the -rt kernel in 8.10 is also unusable for USB MIDI (due to [https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/300806](https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/300806) ), but both the rt-kernel from 8.04 and the the non-rt kernel from 8.10 actually seem to perform acceptably.

---

### Post by simtaalo on 2009-01-31
i've heard that the rt kernel branch is being absorbed back into the main kernel because there's no need for it in the newer versions of the kernel? anyone know more about this?

---

### Post by Rog-Mahal on 2009-01-31
Thanks for all the replies. I'm already running Ubuntu 8.10 64-bit, so I don't think I'll downgrade. I would also be using a usb midi interface, so I suppose I'll wait and see what happens. At this point I haven't run into problems, but we shall see.

---

### Post by Ng Oon-Ee on 2009-01-31
> **simtaalo said:**
> i've heard that the rt kernel branch is being absorbed back into the main kernel because there's no need for it in the newer versions of the kernel? anyone know more about this?
Yes, I saw one post on that too, but as far as I can tell in Intrepid, its not yet true. I can't run JACK without Xruns on the latencies that I can using the (buggy) RT kernel.

---

### Post by Thomas Garman on 2010-01-26
Well, I skipped the rt part of the install and everything I have tried/used so far has worked fine, so maybe it's redundant in Karmic?

---

### Post by adzik on 2010-01-26
> **simtaalo said:**
> i've heard that the rt kernel branch is being absorbed back into the main kernel because there's no need for it in the newer versions of the kernel? anyone know more about this?

I know it is at least partly true. I don't know to what extent realtime is being implemented back, but it's certainly there.
I am currently using 2.6.31 on Debian testing, and have set up an audio workstation with jack. RT is working well there, without much issue at all. 
I can't comment on rt in ubuntu though.

---

### Post by mdrake36 on 2010-01-26
I am glad you started this thread. I started with the ubuntu gnu/linux world specifically for Hexter and Hydrogen. I started with Juanty and noticed alot of xruns with any set up < less then 10 ms i even had to switch to an oss driver on some sound cards.
My curiosity was sparked by the sounds though. they were awesome and true. so I researched th RT kernel. I have studio 9.10 karmic with RT and on my notebook all functions work and no xruns. but the more I play I notice that isn't a panacea. :popcorn:Once you get enough virtuo gear going i.e Hexter Hydro and saya virtual keyboard going you might only get one Xrun but its a doozy.

I hope to find out more about the buffers and memory allocation.

anyone know of a good article about locking down memory? Unlocking? no memory lock? blah blah vlah
 
oh AND turn off all your screen savers cause with RT it will dismount your drives.

cool thread:KS

Oh here is an easy one. In Ubuntu Studio Controls what do the check buttons like "n.i.c.e" do? 1394 firewire?  memory lock?

---

### Post by AutoStatic on 2010-01-27
> **Thomas Garman said:**
> Well, I skipped the rt part of the install and everything I have tried/used so far has worked fine, so maybe it's redundant in Karmic?No it's not. I still need it to work properly with my Firewire soundcard. The RT kernel allows me to prioritise certain processes with the help of rtirq. Without prioritising the soundcard fails to work as it should.

---

### Post by AutoStatic on 2010-01-27
> **mdrake36 said:**
> Oh here is an easy one. In Ubuntu Studio Controls what do the check buttons like "n.i.c.e" do?Nothing, setting nice values for processing audio is not necessary anymore as far as I know: [http://jackaudio.org/faq](http://jackaudio.org/faq)
It's not mentioned anymore in their FAQ. Maybe it's still useful for other processes. According to the [ALSA]("http://www.linuxsound.org/main/index.php/Low_latency_howto") site:
"nice is the minimum &#8220;nice level&#8221; a task can be run as (the willingness of a task to give up it's cpu time). These settings will get jackd, ardour and other RT capable programs running at higher priorities..."

> **mdrake36 said:**
> 1394 firewire?Necessary to enable normal users to make use of the /dev/raw1394 device node that gets created by the raw1394 kernel module. A lot of Firewire devices need this kernel module.

> **mdrake36 said:**
> memory lock?From the [ALSA]("http://www.linuxsound.org/main/index.php/Low_latency_howto") site:
"The memlock setting is the maximum amount of memory that a member of the audio group can lock with a realtime task. This should be less than the maximum physical amount of memory, some recommend it to be half."
I set it too 'memlock unlimited' though because there are programs that prefer that, like Hydrogen and LMMS.

More info here: [http://wiki.linuxmusicians.com/doku.php?id=system_configuration#limits.conf](http://wiki.linuxmusicians.com/doku.php?id=system_configuration#limits.conf)

---

### Post by mdrake36 on 2010-02-01
> **AutoStatic said:**
>  
From the [ALSA]("http://www.linuxsound.org/main/index.php/Low_latency_howto") site:
"The memlock setting is the maximum amount of memory that a member of the audio group can lock with a realtime task. This should be less than the maximum physical amount of memory, some recommend it to be half."
I set it too 'memlock unlimited' though because there are programs that prefer that, like Hydrogen and LMMS.
 
More info here: [http://wiki.linuxmusicians.com/doku.php?id=system_configuration#limits.conf](http://wiki.linuxmusicians.com/doku.php?id=system_configuration#limits.conf)
 
 
Very helpful! :P

---

### Post by raboofje on 2010-02-02
> **AutoStatic said:**
> Nothing, setting nice values for processing audio is not necessary anymore as far as I know. Maybe it's still useful for other processes. 

rtprio and nice are 2 ways of telling the scheduler to give some processes priority over others.

rtprio is (by far) the strongest of the 2, so if you have your rtprio's set up correctly, there's no need for nice anymore.

---

### Post by mdrake36 on 2010-02-02
Ok guys and gals I have finally locked down Memory. but here is the kicker:frown:
I had to uninstall PulseAudio. I tried everything to avoid it but pulse doesn't seem to want to let ALSA do its thing.
So I had to re-install it cuz after removing it I am un able to get through preferences/sound/alsa and esound doesn't take over for Karmic 9.10 after removing Pulseaudio
I tried all the RTprio junk to no avail. it all led back to PulseAudio
 
Where all my audio geeks at? we can do this.
I guess I could regress back to Jaunty? oh dear.

---

### Post by AutoStatic on 2010-02-02
> **mdrake36 said:**
> Ok guys and gals I have finally locked down Memory. but here is the kicker:frown:
I had to uninstall PulseAudio. I tried everything to avoid it but pulse doesn't seem to want to let ALSA do its thing.
So I had to re-install it cuz after removing it I am un able to get through preferences/sound/alsa and esound doesn't take over for Karmic 9.10 after removing Pulseaudio
I tried all the RTprio junk to no avail. it all led back to PulseAudio

Audio production: JACK
Anything else: PulseAudio

So my audio production account uses JACK and my day to day account uses PulseAudio. There really isn't more to it. No need to uninstall PulseAudio, just a client.conf file in the ~/.pulse directory with *autospawn = no* in it and a **pulseaudio -k** as a startup application for the audio production account and you're done :)

---

### Post by bluesscream on 2010-02-04
I press my thumbs for hope they really bring jack back into main. These new kernels 2.6.31.xxx, 2.6.32.xxx, 2.6.33.xxx all give fine low latencies for audio. Most important is fixing  cpu scaling at highest values and deactivate all save energy options as long as you are doing audio work.

---

### Post by AutoStatic on 2010-02-05
> **raboofje said:**
> rtprio and nice are 2 ways of telling the scheduler to give some processes priority over others.

rtprio is (by far) the strongest of the 2, so if you have your rtprio's set up correctly, there's no need for nice anymore.Didn't know that, thanks for the info!

---

### Post by trulan on 2010-02-05
I had noticed that:
1. Ubuntu Studio Controls doesn't write the nice settings in Karmic like it did in Jaunty, and,
2. Manually entering the audio nice settings didn't seem to do anything at all.

I've been suspeting that NICE has been pretty much deprecated in Karmic, but had never seen any confirmation of that before this.  Well, that's one less thing to worry about I guess...

---

### Post by niffcreature on 2010-02-06
i have yet to fully read over this thread, but i just wanted to mention that even if you have a half decent external audio usb or firewire interface, its a silly idea to try and use realtime unless you have a specific reason. the sound quality just isnt as good.

---

### Post by trulan on 2010-02-06
> **niffcreature said:**
> i have yet to fully read over this thread, but i just wanted to mention that even if you have a half decent external audio usb or firewire interface, its a silly idea to try and use realtime unless you have a specific reason. the sound quality just isnt as good.
Could you elaborate?  If you are experiencing a decrease in audio quality, something is definitely very wrong.  Do you mean the realtime kernel or the realtime setting in Jack?  What programs are you using for audio?

---

### Post by niffcreature on 2010-02-06
i believe it is a known fact, though i could be wrong. i was under the impression that audio quality is occasionally sacrificed for realtime especially while the system is under heavy load. even with a realtime kernel.

---

### Post by cooper77z on 2010-02-06
I bet you my 2k real sound is better than your 8g rendered media. Just kidding. I sware people are scared to create because the kilobytes don'w mathcgh up that's wiers, id don make too much ds sense you truing to dpe spreaad a messasf fme em message or to die on the cap cap] carpet. d d d trying to die on the c a r p e t . just for fun.

====    iT IS JUST SILLY. AOA THE small amuint o f life said nevermind their bullsjiet because nevermind

it said don't listen to them, so id didn'rt,  jt dkls lsa dkl lskd kdk f **** with them... hdhdh haha

---

### Post by AutoStatic on 2010-02-07
> **niffcreature said:**
> i believe it is a known fact, though i could be wrong. i was under the impression that audio quality is occasionally sacrificed for realtime especially while the system is under heavy load. even with a realtime kernel.Yes, that's right, those sacrifices are called xruns. That's where the real benefit of a RT kernel lies: it helps minimising the chance of getting xruns. Not only with the kernel itself but also with the possibility that comes with RT kernels to prioritise processes.

---

### Post by niffcreature on 2010-02-07
im aware of xruns, i guess i was thinking the soundcard had some automatic downsampling function or something. guess im probably wrong, i didnt hear it from a reliable source come to think of it

---

### Post by niffcreature on 2010-02-07
> **cooper77z said:**
> I bet you my 2k real sound is better than your 8g rendered media. Just kidding. I sware people are scared to create because the kilobytes don'w mathcgh up that's wiers, id don make too much ds sense you truing to dpe spreaad a messasf fme em message or to die on the cap cap] carpet. d d d trying to die on the c a r p e t . just for fun.

====    iT IS JUST SILLY. AOA THE small amuint o f life said nevermind their bullsjiet because nevermind

it said don't listen to them, so id didn'rt,  jt dkls lsa dkl lskd kdk f **** with them... hdhdh haha

hey, cooper, youre probably right but you know the carpet is pretty hairy. life viewed and spoken is the denial that it is bigger than the creation. its just a little mean, u kno its ok for us to be afraid of the kilobytes, balances the carpet speakers from saying things too us...

---

### Post by markbuntu on 2010-02-12
FYI, some of the rt kernel patches are in the .33 kernel but that does not mean the kernel packagers will not kludge their functionality by using less than optimum parameters for the scheduler, disabling rtprio, and other things that can drag down rt performance.

Nevertheless, if you want your machine to do a lot of stuff in real time you need a lot of cpu power and ram. Even a I7 can choke trying to keep up with your 52 ardour tracks along with 24 tracks from rosegarden/zynaddsubfx and 16 from hydrogen with a bunch of live midi and other instruments and vocals all with pre and post effects. 

There are some people who make dedicated consoles for this type of stuff, they use linux and a ton of dedicated hardware and the consoles cost $100,000+ so don't expect that your little pc can do it all.

Something to keep in mind as you build you edifice of sound.....

---

