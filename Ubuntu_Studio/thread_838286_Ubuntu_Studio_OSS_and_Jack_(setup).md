---
title: "Ubuntu Studio OSS and Jack (setup)"
date: 2008-06-23
forum: Ubuntu Studio
---

### Post by jukingeo on 2008-06-23
Hello all,

I am pretty new to Linux and I been running Ubuntu for only a month now.  I been a Windows user for over 15 years now.  For the most part I managed to find similar applications to Windows that can handle my everyday tasks (Firefox (internet, Open Office (MS Office), Evolution (Email), etc).   But I do work with audio a lot and I upgraded my standard Ubuntu installation to Ubuntu Studio.  Now the trouble is that most of the Ubuntu applications either do not have sound or crash the system. 

What I learned is that just about everything in Ubuntu Studio is setup to use a connection server called Jack.  Unfortunately, I don't know jack about Jack (pun intended).  The Jack website didn't help much in terms of documentation either.

I believe what my issue lies is that I am using a Sound Blaster X-Fi audio card and this card will not work right with ALSA, which is what Ubuntu Studio is set up for.  My audio card works with OSS.

I did a bit of reading and while most applications are configured via ALSA, it did appear that Jack could also be set up to use OSS on the hind end.

This is what I am after, because if I can get Jack to communicate through OSS to my audio card, I should be able to get everything else going using Jack.

Now for the kicker.  I don't know how to reconfigure Jack so it works with OSS and my sound card and this is where I am going to need help.

So any help to get my Ubuntu Studio operational would be much appreciated.

While I would like to get all of the Ubuntu Studio programs operational, my major concerns are:

Audio:

Audacity
Ardour
Rosegarden
Hydrogen

Video:

Open Movie Editor
Cinelerra
Kino

I would appreciate any assistance.

Thank You,

Geo

---

### Post by thorgal on 2008-06-23
try this in a terminal (never mind messages concerning something called xruns, if you get that far, it's a good start and can tune it later on) : 

jackd -doss -r48000 -p1024 -n2

assuming that your soundcard is 48kHz capable (I am almost sure it is).
If the server does not shutdown by itself after you executethis command, you can have high hopes :)

---

### Post by jukingeo on 2008-06-23
> **thorgal said:**
> try this in a terminal (never mind messages concerning something called xruns, if you get that far, it's a good start and can tune it later on) : 

jackd -doss -r48000 -p1024 -n2

assuming that your soundcard is 48kHz capable (I am almost sure it is).
If the server does not shutdown by itself after you executethis command, you can have high hopes :)


Hello, 

This is what I got when I ran that code in Terminal.  I tried both with and without Sudo:

geo@geo-desktop:~$ jackd -doss -r48000 -p1024 -n2
could not open driver .so '/usr/lib/jack/jack_alsa.so': /usr/lib/libasound.so.2: undefined symbol: midiparser_input_buf

could not open driver .so '/usr/lib/jack/jack_freebob.so': /usr/lib/libasound.so.2: undefined symbol: midiparser_input_buf

jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
OSS: failed to open device /dev/dsp: oss_driver.c@549, errno=16
cannot start driver
Segmentation fault
geo@geo-desktop:~$ sudo jackd -doss -r48000 -p1024 -n2
[sudo] password for geo: 
could not open driver .so '/usr/lib/jack/jack_alsa.so': /usr/lib/libasound.so.2: undefined symbol: midiparser_input_buf

could not open driver .so '/usr/lib/jack/jack_freebob.so': /usr/lib/libasound.so.2: undefined symbol: midiparser_input_buf

jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
OSS: failed to open device /dev/dsp: oss_driver.c@549, errno=16
cannot start driver
Segmentation fault
geo@geo-desktop:~$ 


I don't see anything with xruns.  I take this that this is NOT a good thing.

Any ideas of what to do next?

Thanx,

Geo

---

### Post by deadgobby on 2008-06-23
OK to get JackD to run is to install the GUI window called jack control. That program can be found in synaptic. Next you must need to link. Like in the old days of analogs of CV/Gate. You must link to the program. 
Look at the screen shot. 
Gobby

---

### Post by thorgal on 2008-06-24
OK, looks like you don't have jackd compiled for OSS. To be sure (because looking at the jackd messages, I don't see why jackd tries to use freebob or alsa when you explicitely specify OSS), could you post what you have in the directory /usr/lib/jack (just copy/paste the output of the terminal command 'ls /usr/lib/jack'). If you don't see something called jack_oss.so, then you will need to recompile jack with oss enabled.

The alternative explanation is that something is blocking your /dev/dsp, e.g. if you have firefox already opened and have played some flash videos, it could be that jack cannot get a handle on /dev/dsp because the flash plugin keeps it for itself (selfish bast..rd! :lolflag:) 

But honestly, isn't it a bit strange that your soundcard is OSS compatible but not ALSA ?

About Qjackctl (previous post), it's only a GUI frontend to jackd. If the basic command I gave you does not work, qjackctl will also fail since it will execute that command behind the stage.

About sudo : you need not run jack as root. When you get to the point where you can run the simple command I mentioned, we'll take it from there.

---

### Post by jukingeo on 2008-06-24
> **thorgal said:**
> OK, looks like you don't have jackd compiled for OSS. To be sure (because looking at the jackd messages, I don't see why jackd tries to use freebob or alsa when you explicitely specify OSS), could you post what you have in the directory /usr/lib/jack (just copy/paste the output of the terminal command 'ls /usr/lib/jack'). If you don't see something called jack_oss.so, then you will need to recompile jack with oss enabled.

The alternative explanation is that something is blocking your /dev/dsp, e.g. if you have firefox already opened and have played some flash videos, it could be that jack cannot get a handle on /dev/dsp because the flash plugin keeps it for itself (selfish bast..rd! :lolflag:) 

But honestly, isn't it a bit strange that your soundcard is OSS compatible but not ALSA ?

About Qjackctl (previous post), it's only a GUI frontend to jackd. If the basic command I gave you does not work, qjackctl will also fail since it will execute that command behind the stage.

About sudo : you need not run jack as root. When you get to the point where you can run the simple command I mentioned, we'll take it from there.

I am not at my machine at home right now but I can fill you in on a couple of things.  As of now I have not done anything with Jack.  I don't know anything about it so I didn't touch anything or try to configure anything with it.  Thusfar the documentation on Jack is not very extensive (or perhaps I just am not looking in the right place).

The Sound Blaster X-Fi DOES have ALSA drivers, however, the drivers as provided by Creative are only in the Beta state and obviously since Linux is an Open Source (free) system, they are not really rushing to get suitable drivers going for the X-Fi under Linux.  So I guess open source developers just worked with what they had.  Since OSS is an older system than ALSA it appeared that they had a working Linux driver in place way before an ALSA driver was created.  As it is, the ALSA driver is very buggy, causes many problems and is just unpleasant to work with.  The OSS driver, on the other hand, is practically painless to set up.  However, with the newer versions of Ubuntu more and more supporting ALSA, interfacing with OSS is creating issues, which seem to rear their ugly head more with the "Hardy" version of Ubuntu than with previous versions.

In a nutshell, since I am a newbie and I do have sound, I just need to find a way to get everything talking together properly so this way I can check out all those cool Ubuntu Studio applications.

So apparently the 

jackd -doss -r48000 -p1024 -n2

line didn't seem to work, correct?

If so, then what do I do now?

Thanx,

Geo

---

### Post by thorgal on 2008-06-24
we need to understand why this simple jack command does not work before anything else because if it continues to not work, you're stuck and the only thing for you would be to switch to a soundcard that is fully supported by ALSA or freebob (FFADO).

---

### Post by jukingeo on 2008-06-24
> **thorgal said:**
> we need to understand why this simple jack command does not work before anything else because if it continues to not work, you're stuck and the only thing for you would be to switch to a soundcard that is fully supported by ALSA or freebob (FFADO).

Could it be that Jack is defaulting to ALSA?  I thought Jack could be configured to also use OSS on the hind end...At least that is what I read. 

As for sound cards.  I really do not want to switch out my Soundblaster X-Fi because:

A) It was fairly expensive
b) It works great with my windows applications
c) In windows it has 7.1 channel surround sound.

Also it wasn't an easy card for me to set up...even in Windows.  But now that it is working great, it is pretty stable.  So I really don't want to muck with it.

Now could I have two audio cards in my machine.  Physically yes, but I don't know what that will do with my Windows set up.

However, I do have a Firewire audio interface that caused no problems at all with my SB X-Fi set up (in Windows).   So I would be willing to use either a USB or Firewire external sound card.

Would anyone know if these would work?

[http://cgi.ebay.com/Creative-Sound-Blaster-Extigy-External-USB-Card_W0QQitemZ330246072212QQcmdZViewItem?hash=item330246072212&_trkparms=72%3A392%7C39%3A1%7C65%3A12&_trksid=p3286.c0.m14](http://cgi.ebay.com/Creative-Sound-Blaster-Extigy-External-USB-Card_W0QQitemZ330246072212QQcmdZViewItem?hash=item330246072212&_trkparms=72%3A392%7C39%3A1%7C65%3A12&_trksid=p3286.c0.m14)

[http://cgi.ebay.com/Creative-Sound-Blaster-Audigy-2-NX-External-USB-Card_W0QQitemZ330246285780QQcmdZViewItem?hash=item330246285780&_trkparms=72%3A392%7C39%3A1%7C65%3A12&_trksid=p3286.c0.m14](http://cgi.ebay.com/Creative-Sound-Blaster-Audigy-2-NX-External-USB-Card_W0QQitemZ330246285780QQcmdZViewItem?hash=item330246285780&_trkparms=72%3A392%7C39%3A1%7C65%3A12&_trksid=p3286.c0.m14)

[http://cgi.ebay.com/Creative-Sound-Blaster-USB-24-Bit-External-brand-new_W0QQitemZ370061654963QQcmdZViewItem?hash=item370061654963&_trkparms=72%3A392%7C39%3A1%7C65%3A12&_trksid=p3286.c0.m14](http://cgi.ebay.com/Creative-Sound-Blaster-USB-24-Bit-External-brand-new_W0QQitemZ370061654963QQcmdZViewItem?hash=item370061654963&_trkparms=72%3A392%7C39%3A1%7C65%3A12&_trksid=p3286.c0.m14)

(the links look the same...but they are not).

I guess once I free up some resources and can put together a dedicated Linux machine then I would be in a better position to choose hardware that I know would work with Linux.  But for now that is not convenient.  For now, I prefer trying out Linux on one machine that I can dual boot to.  I don't have the room to set up another full machine.

Where can I see how Jack is set up?  A configuration file?  I am curious to know what it is set up for.  More then likely it is probably trying to use ALSA to communicate with my card and that I can see can cause quite a few problems.

EDIT:

Ok, I did a bit more playing around on the Jack site.  I found this:

[http://jackaudio.org/files/JACK-Diagram.png](http://jackaudio.org/files/JACK-Diagram.png)

Ok, now it seems the only thing I would need to do is either set Jack to use OSS ONLY to communicate with my soundcard through OSS.  By right everything else could stay ALSA.   Last night someone told me about an ALSA-OSS "Wrapper".  Supposedly this is a program that should bridge the use of an ALSA program with an OSS device.  However, as with Jack,  I don't know how it works or if it could present a danger of disrupting things and making matters worse then they are already.

So as they say, it seems so close, but yet so far.

Geo

---

### Post by Stochastic on 2008-06-24
jackd (aka jack) is a sound server that is started with the command jackd [options].  By executing the jackd -doss -r48000 -p1024 -n2, you were trying to start jackd withe the options of (in order) OSS as the device, 48000hz as the sample rate, 1024 samples per buffer period, and 2 periods in the buffer.  So yes, jack is trying to use oss when you run this command.

OSS is considered by most to be a depreciated sound driver (there are those who still prefer it), and as such not too many use it (also because alsa is ubuntu's default).  Have you made sure that OSS is up and running properly on your system (should do this before worrying about getting jackd to piggyback off oss), if not, take a read through this thread: [http://ubuntuforums.org/showthread.php?t=780961](http://ubuntuforums.org/showthread.php?t=780961) This is a major change to the underlying audio structure in Ubuntu, so you should proceed with caution, and do your research to make sure your card will work afterward.

From what I've read the X-Fi is not a linux friendly card, but I haven't researched the oss side of things.  You might find it more useful (and less of a headache) to purchase a fully supported card.  But it's understandable why you'd be less inclined to do so.  Just think of it as buying an entire recording studio worth of software with just the simple (and relatively cheap) purchase of a linux compliant card.

If you do have OSS up and running (i.e. you can play an mp3 on your card), then jack is probably behaving weird.  Try running qjackctl (it's in the repos), going into the setting window, and changing the driver option to be OSS, then change the Input Device and Output Device options to point directly to your card (also, while you're in there, turn verbose messages on).  Click OK, then try to start jack.  Post back all the output in the messages window.

---

### Post by thorgal on 2008-06-24
in a terminal, execute

lspci

you will see if you have 2 sound chips

then, as Stochastic said, you have to know at least 2 things :

which h/w is using OSS (I guess the X-Fi)
if more than 1 sound card, you need to explicitely choose the right h/w when invoking jackd. At least, this would be the case if both sound cards were driven by ALSA. I don't how this goes with OSS. I don't even know if you can have one card driven by oss and the other by alsa, at the same time. Conceptually, I would think it works but in practice, I have no clue. If it is so, then it seems obvious that jackd is trying to get to the alsa driven card. BUt all this is just speculation because your h/w picture is not clear from your posts.

---

### Post by jukingeo on 2008-06-24
> **Stochastic said:**
> jackd (aka jack) is a sound server that is started with the command jackd [options].  By executing the jackd -doss -r48000 -p1024 -n2, you were trying to start jackd withe the options of (in order) OSS as the device, 48000hz as the sample rate, 1024 samples per buffer period, and 2 periods in the buffer.  So yes, jack is trying to use oss when you run this command.

OSS is considered by most to be a depreciated sound driver (there are those who still prefer it), and as such not too many use it (also because alsa is ubuntu's default).  Have you made sure that OSS is up and running properly on your system (should do this before worrying about getting jackd to piggyback off oss), if not, take a read through this thread: [http://ubuntuforums.org/showthread.php?t=780961](http://ubuntuforums.org/showthread.php?t=780961)


Hello Stochastic,

I don't know if followed along from the entire thread or my past posts in other threads, but to get you up to speed, I have the Sound Blaster X-Fi sound card in my machine and right away I had problems with it.  I was told that getting ALSA to work with it is a pain because the drivers are only Beta and there are issues with Creative Labs in regards to getting everything fully operational on this card.   I was then introduced to this thread here:

[http://ubuntuforums.org/showthread.php?t=571656](http://ubuntuforums.org/showthread.php?t=571656)

As you can see the thread is still very much active and you can see me posting my problems there as well.  I followed the guide to install OSS in the hopes that this driver would work.  Low and behold it did work.  I do HAVE sound.  However, not everything is working correctly.

What I have sound with right now as we speak are as follows:

1) Ubuntu System Sounds
2) Totem Movie Player
3) Most of my games (with the exception of GFCE NES Emulator.  I have other Emulators including Stella, GENS, and DosBox and they work with sound.  Sound isn't always clear with games, but I have sound nevertheless).

The biggies that are out is just about the entire Ubuntu Studio application line-up.  The video programs such as Open Movie Editor and Cinelerra also do not work.  Streaming internet is also not working.  The video on streaming internet DOES work, but no sound.

The link you posted is very similar to the discussion that I am involved with in the link I posted.  In fact I do recognize quite a few names in that thread.   Both Nullhead and Temüjin have been helping me out there.

>  This is a major change to the underlying audio structure in Ubuntu, so you should proceed with caution, and do your research to make sure your card will work afterward.

Yes, I only began to realize this.  Apparently ALSA seems to be fairly new and OSS is old and is being replaced by ALSA.  However, at this state of the game, I don't care what is old or what is new, but rather what will work.

As far as I know I have heard (read) about more nightmares with ALSA than OSS.  So that was a determining factor in what driver I ended up choosing.

However, a big problem I face now is that Ubuntu Studio is mostly ALSA based.  But my hope lied in the fact that Ubuntu Studio tied everything together through Jack and if I could get Jack to talk to my sound card, then if I needed an overlay or "wrapper" to tie Jack into OSS, then by right I should get those applications to work.  Should, though.  Again I am speculating because I am really new to Ubuntu and don't know what is really going on.

> From what I've read the X-Fi is not a linux friendly card, but I haven't researched the oss side of things.

That is what I found out was really weird considering that this card is the next most popular card to the Sound Blaster Live.  Yet that card is fully supported.  After learning that, I was under the impression that Ubuntu (or Linux in general) is really chasing Window's tail...always playing catch up.  Yet, I did some more digging and found out that it is really Creative that is at fault because they never really fully released a working open source driver that works with the X-Fi.  But apparently it seems that OSS beat ALSA to the punch and released a somewhat working driver for the X-Fi.

 >  You might find it more useful (and less of a headache) to purchase a fully supported card.  But it's understandable why you'd be less inclined to do so.  Just think of it as buying an entire recording studio worth of software with just the simple (and relatively cheap) purchase of a linux compliant card.

Oh I would do that on a dedicated Linux system.  No problem.  But not this system.  This is my main computer.  The X-Fi is my primary sound card for Windows XP, and I am certainly not going to muck things up there by installing another PCI card next to it and let Windows do it's thing with it. (Remember Windows Plug and Pray?).  As of now Linux is really on a "trial basis" on this machine.  I just want to try out the audio applications and see how Linux performs as a Audio/Video editing tool.  

For this system I would then rather use a Linux supported EXTERNAL sound device; one that I can plug into the USB port or Firewire port; one that I can yank the plug out when I go into Windows.

Do you have any suggestions to external sound cards that have full Linux support?  I do prefer something that is multi-channels and has XLR connectors so I can test the audio programs in Linux.

> If you do have OSS up and running (i.e. you can play an mp3 on your card), then jack is probably behaving weird.

Yes, I can play an MP3 and I even have sound on most of my games as I said earlier.


>   Try running qjackctl (it's in the repos), going into the setting window, and changing the driver option to be OSS, then change the Input Device and Output Device options to point directly to your card (also, while you're in there, turn verbose messages on).  Click OK, then try to start jack.  Post back all the output in the messages window.

I did try opening up Jack Control (qjackctl is already installed on my system) tonight and I DID see a setting for OSS under Sound Devices.  I set it for that and then tried to open up Ardour.  Ardour crashed.  

I also get this error message when opening up Jack Control:

"Could Not Open ALSA sequencer as a Client. ALSA Midi Patchbay will not be available"

GREAT!  Now I know I have another problem...NO Midi!  This just keeps getting better and better. (Yes I am being sarcastic).

Jack Control also crashes in that I have to do a force quit as well.  It will not let me get back into the Sound Devices tab.

Jack also crashes.

I am taking it that I have a major problem here.  I hope there is a solution.

So what do I do now?

Thanx,

Geo

---

### Post by jukingeo on 2008-06-24
> **thorgal said:**
> in a terminal, execute

lspci

you will see if you have 2 sound chips

Ok, this is what I got in my Terminal when I invoked the command above.

geo@geo-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
02:02.0 Multimedia audio controller: Creative Labs SB X-Fi
02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
geo@geo-desktop:~$ 


I don't know what to make of all this, but if I were to take a stab at it, this is all my hardware on my system.  I do see the Creative SB X-Fi card next to last entry.

As of now I only have one card on my system.  I was making the comment above on what if I were to go with a Linux/ALSA supported card that was external.  This way I don't have to worry about it messing things up when I go back into Windows (I simply can just "pull the plug". Can't do that with an internal card).


>  as Stochastic said, you have to know at least 2 things :

which h/w is using OSS (I guess the X-Fi)
if more than 1 sound card

That is a given as I do have sound with some applications using the X-Fi through OSS.  It is fixing the stuff that isn't working that is the problem right now.

> , you need to explicitely choose the right h/w when invoking jackd. At least, this would be the case if both sound cards were driven by ALSA. I don't how this goes with OSS. I don't even know if you can have one card driven by oss and the other by alsa, at the same time. Conceptually, I would think it works but in practice, I have no clue. If it is so, then it seems obvious that jackd is trying to get to the alsa driven card. BUt all this is just speculation because your h/w picture is not clear from your posts.

As of now Jack is doing something very weird.  I went into the Jack Control, as I explained above in my reponse to Stochastic, and set it to OSS. Now it and Jack itself crashes.

So I don't know what is going on.  Maybe something has to be changed in a configuration file...via the Terminal?


I will say one more thing though that may shed some light on the situation.  When I put OSS on my system, I DID have streaming audio on the internet for a short time.  But then I fired up Audacity and that didn't work.  I followed that up with Ardour and it crashed.  I rebooted right after that and since then my streaming internet hasn't been working.

So something got blown out of whack.

I will say that at this point, I would entertain the fact that if I could get a USB or Firewire audio device that is fully Linux/ALSA compliant, I would make the investment.  But my X-Fi works beautifully in Windows XP and I am certainly not going to part with it.  I bought the X-Fi when it first came out and it cost me $279 back then.

Here feast your eyes on this:

[http://en.wikipedia.org/wiki/Sound_Blaster_X-Fi](http://en.wikipedia.org/wiki/Sound_Blaster_X-Fi)

It is amazing what this thing can do...in Windows that is.  It is your perverbial "kitchen sink" card.

In Windows this thing has surround sound and expanded sound fields.  Absolutely fantastic when you play games. FPS games like Quake?  Oh Boy...ear candy.

In short it is a pretty high end sound card.  It is a commercial card, but it does have quite a few pro-like features.  So naw...I am not going to give it up so long as I am using Windows.

I do hope that eventually it will be fully supported in Linux.

Anyway...I am hoping to fix this problem.  As of now I am not shooting for the full capabilities of the X-Fi.  I would be happy just getting sound to and from it on two channels.

As I said, the goal is to try out the Ubuntu Studio programs.

I have to run, 

Hopefully there is a solution to this dilema.

Thanx,

Geo

---

### Post by Stochastic on 2008-06-24
> **jukingeo said:**
> I did try opening up Jack Control (qjackctl is already installed on my system) tonight and I DID see a setting for OSS under Sound Devices.  I set it for that and then tried to open up Ardour.  Ardour crashed.  

I also get this error message when opening up Jack Control:

"Could Not Open ALSA sequencer as a Client. ALSA Midi Patchbay will not be available"

So what was the output of qjackctl's message window when you tried to start jack?  Please make the distinction between opening qjackctl and starting jack with qjackctl - I am assuming no error message popped up when you opened qjackctl, but rather when you started jack.

---

### Post by jukingeo on 2008-06-24
> **Stochastic said:**
> So what was the output of qjackctl's message window when you tried to start jack?  Please make the distinction between opening qjackctl and starting jack with qjackctl - I am assuming no error message popped up when you opened qjackctl, but rather when you started jack.


Actually it is vice versa. That error message came up within Jack Control.   Opening up just Jack Rack itself results in a crash.  Jack Control crashes too, but at least that message does come up.  There is a message window that comes up, but because of the crash I cannot copy the details...it won't let me.  Jack Rack comes up with the "Jack Rack" logo in the middle of the screen and there it sits looking pretty.  Nothing else happens and I have to force quit it.

---

### Post by thorgal on 2008-06-25
OK, according to lspci, you have only one soundcard, which is a bit surprising (no onboard sound) but it looks like your intel mobo is an old model (i865). Anyways, when you boot and log in (KDE or gnome ?), is there any sound daemon running on top of OSS ? (artsd, esd, pulseaudio)

you can check processes from a terminal :

ps xa | grep arts
ps xa | grep esd
ps xa | grep pulse

if nothing is returned, I guess not.

After that, check if you have any alsa stuff going on (alsa has an OSS emulation layer) :

lsmod | grep snd

if nothing is returned then it most likely means that alsa is not running at all and you truly use old OSS.


last thing : as I mentioned in my 1st or 2nd post, list the content of /usr/lib/jack

ls /usr/lib/jack


then we'll see.

---

### Post by jukingeo on 2008-06-25
> **thorgal said:**
> OK, according to lspci, you have only one soundcard, which is a bit surprising (no onboard sound) but it looks like your intel mobo is an old model (i865). Anyways, when you boot and log in (KDE or gnome ?), is there any sound daemon running on top of OSS ? (artsd, esd, pulseaudio)

you can check processes from a terminal :

ps xa | grep arts
ps xa | grep esd
ps xa | grep pulse

if nothing is returned, I guess not.

After that, check if you have any alsa stuff going on (alsa has an OSS emulation layer) :

lsmod | grep snd

if nothing is returned then it most likely means that alsa is not running at all and you truly use old OSS.


last thing : as I mentioned in my 1st or 2nd post, list the content of /usr/lib/jack

ls /usr/lib/jack


then we'll see.

Hello,

I'm at work again, so I will not be able to check out those things until later.  As far as I know I don't have any overlays running.  I did try Pulse at one time, but took it off because it caused a problem.  As it turned out, the OSS driver for X-Fi was updated and I didn't need Pulse anymore.  I did instruct Synaptic to fully remove Pulse.  So I am not sure if something was left behind because of that.  But I did take the old OSS driver off & removed Pulse before I put on the updated driver of OSS.

As for the age of my system.  Well, it is only three years old, but I guess that is enough.  With computers if anything is more than 4 months old it is considered "Old".  The computer doesn't have a mobo sound system because I specifically told Dell I wanted a mobo without it.  So they put a Sound Blaster Live on instead.  Now before you say, "Put the Live card back in because it is ALSA supported".  Keeping in mind that my machine is a Dell.  Dell was putting in what I called "Fake" SB Live cards and my machine had one.  I didn't have anywhere near the features that the REAL SB Live people had.  So I pulled the card in favor of the X-Fi.

For the record, I did check if the Dell "FAKE" SB Live card is supported in Linux, it isn't.

I will check those things you mentioned when I get home, but I don't believe I have anything running on top of OSS as of now.

Thanx,

Geo

---

### Post by jukingeo on 2008-06-25
> **thorgal said:**
> OK, according to lspci, you have only one soundcard, which is a bit surprising (no onboard sound) but it looks like your intel mobo is an old model (i865). Anyways, when you boot and log in (KDE or gnome ?), is there any sound daemon running on top of OSS ? (artsd, esd, pulseaudio)

you can check processes from a terminal :

ps xa | grep arts
ps xa | grep esd
ps xa | grep pulse

if nothing is returned, I guess not.

After that, check if you have any alsa stuff going on (alsa has an OSS emulation layer) :

lsmod | grep snd

if nothing is returned then it most likely means that alsa is not running at all and you truly use old OSS.


last thing : as I mentioned in my 1st or 2nd post, list the content of /usr/lib/jack

ls /usr/lib/jack


then we'll see.

Hello again,

I am back.  I did as you asked above and this is what I got in my Terminal:

geo@geo-desktop:~$ ps xa | grep arts
 6546 pts/0    R+     0:00 grep arts
geo@geo-desktop:~$ ps xa | grep esd
 6292 ?        S      0:00 esd -nobeeps
 6548 pts/0    R+     0:00 grep esd
geo@geo-desktop:~$ ps xa | grep pulse
 6550 pts/0    R+     0:00 grep pulse
geo@geo-desktop:~$ lsmod | grep snd
geo@geo-desktop:~$ lsmod | grep snd
geo@geo-desktop:~$ ls /usr/lib/jack
inprocess.so  jack_alsa.so   jack_freebob.so
intime.so     jack_dummy.so  jack_oss.so
geo@geo-desktop:~$ 


Please let me know if this is good :), bad :(, or ugly ](*,)

Thanx,

Geo

---

### Post by thorgal on 2008-06-26
this is good :)

there you have it : you have the sound daemon 'esd' running and probably having a firm grip on your soundcard ;)
so I would kill it. I assume you use GNOME since esd is the gnome sound server. There is a way to kill it from some gnome GUI but I don't know gnome, I use KDE so let's apply the brute force. From the terminal, type :

killall -9 esd

then try jack again as I told you very early in this discussion (you have the jackd oss backend according to your listing)

jackd -doss -r48000 -p1024 -n2


PS: by killing esd, you may lose some functionality in standard gnome sound apps (like system sounds, or even flash plugin, skype, whatever was communicating to esd). Honestly, I don't know because I never ever used these sound daemons. If jackd works for you after that, you enter a completely different world, be warned. Jackd has never meant to be a generic sound server for desktop environments. It is possible to use as such but it requires some tweakings and very stable setup (h/w and s/w). Jackd is designed for professional work requiring very precise operations and low latency, not for playing mp3's in the background while surfing on youtube (but it is of course possible ;) )

Another thing, I had a look at the wikipedia link you provided. I have a couple of comments :

1- I remember now that I already had one myself because I also bought a Dell desktop (Dimension something) for my girlfriend a few years ago (2005 I think). I did not know that the mobo had a soundchip but it did (intel's sigmatel). So I almost immediately sold the extra PCI card which happened to be an X-Fi. The onboard chip was more than enough for my girlfriend :)

2- having read the details, I find it sort of unsuitable for professional audio work. It is not a good idea to transform the sound "behind your back" because of a builtin h/w EQ (or compressor). On the other hand, if you can turn if off easily through software, that's not an issue but it becomes a useless feature (again, in the context of audio / music production).

---

### Post by jukingeo on 2008-06-26
> **thorgal said:**
> this is good :)

there you have it : you have the sound daemon 'esd' running and probably having a firm grip on your soundcard ;)
so I would kill it.

Oh, THAT doesn't sound good!  :lolflag:


> I assume you use GNOME since esd is the gnome sound server. There is a way to kill it from some gnome GUI but I don't know gnome, I use KDE so let's apply the brute force. From the terminal, type :

killall -9 esd

Kill it?  Wouldn't that take out what little sound I have working?  

> then try jack again as I told you very early in this discussion (you have the jackd oss backend according to your listing)

jackd -doss -r48000 -p1024 -n2


PS: by killing esd, you may lose some functionality in standard gnome sound apps (like system sounds, or even flash plugin, skype, whatever was communicating to esd). Honestly, I don't know because I never ever used these sound daemons. If jackd works for you after that, you enter a completely different world, be warned. Jackd has never meant to be a generic sound server for desktop environments. It is possible to use as such but it requires some tweakings and very stable setup (h/w and s/w). Jackd is designed for professional work requiring very precise operations and low latency, not for playing mp3's in the background while surfing on youtube (but it is of course possible ;) )

So essentially that command is going to kill the audio that I have now?  If I kill it and it doesn't work, can I easily turn it back on?  That is something I need to know before I try anything.

> Another thing, I had a look at the wikipedia link you provided. I have a couple of comments :

1- I remember now that I already had one myself because I also bought a Dell desktop (Dimension something) for my girlfriend a few years ago (2005 I think). I did not know that the mobo had a soundchip but it did (intel's sigmatel). So I almost immediately sold the extra PCI card which happened to be an X-Fi. The onboard chip was more than enough for my girlfriend :)

2- having read the details, I find it sort of unsuitable for professional audio work. It is not a good idea to transform the sound "behind your back" because of a builtin h/w EQ (or compressor). On the other hand, if you can turn if off easily through software, that's not an issue but it becomes a useless feature (again, in the context of audio / music production).

Oh, I would be the first one to tell you that the X-Fi is NOT a pro card.  Yet, it does get close...certainly much more so than the Sound Blaster Live.  So being that it is IN my system, the supposed easy and least costly way is to try to get it to work in Linux.

At any rate, I DO have a professional sound device, an Alesis IO-16.  But that unit has NO Linux support.

At this point in time I am probably not going to do professional work in Linux until I know everything is 100%.  What I DO want to do is get some kind of audio out of my machine and into it so I can try out those Linux recording and editing applications.  I simply want to see how they compare to their Windows counterparts.  If I find I can do what I want within Linux, then I can save myself $1000's on software.  On the other hand if I find that the applications don't do what I need them to do, I am probably not going to use Linux for audio applications and stick with Windows XP for that.  BUT, I have to know one way or the other.

Anyway, I will wait for your response in regards to the above questions.  In the meantime I am at work and can't do anything right now anyway.

Thanx,

Geo

---

### Post by thorgal on 2008-06-26
go ahead, kill the beast :D

you can always resurrect it, either from the command line 

esd -nobeeps&

(note the & at the end)

or by loging out and in again.

---

### Post by jukingeo on 2008-06-26
> **thorgal said:**
> go ahead, kill the beast :D

you can always resurrect it, either from the command line 

esd -nobeeps&

(note the & at the end)

or by loging out and in again.

Ok here goes nothing (or everything):

I did as you said and this is what I got in the Terminal:

geo@geo-desktop:~$ killall -9 esd
geo@geo-desktop:~$ killall -9 esd
esd: no process killed
geo@geo-desktop:~$ jackd -doss -r48000 -p1024 -n2
could not open driver .so '/usr/lib/jack/jack_alsa.so': /usr/lib/libasound.so.2: undefined symbol: midiparser_input_buf

could not open driver .so '/usr/lib/jack/jack_freebob.so': /usr/lib/libasound.so.2: undefined symbol: midiparser_input_buf

jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
OSS: failed to enable full duplex for /dev/dsp: oss_driver.c@565, errno=95
oss_driver: /dev/dsp : 0x10/2/48000 (4096)
oss_driver: indevbuf 4096 B, outdevbuf 4096 B
oss_driver: using barrier mode, (dual thread)
OSS: read() failed: oss_driver.c@968, count=-1/4096, errno=13
jack main caught signal 2

I see lots of errors. 

Anyway, I lost my sound completely.

Jack and Jack Control are still crashing.

I will be back, I am going to try the above command to see if I can get my sound back.

EDIT:

OK, I am back.  I had to reboot my system.  Good thing is that my sound is back to where it was.

I did some reading earlier and someone recommended that because Hardy is a bit buggy, to go back to Ubuntu Studio version 7.10 and try and install the ALSA drivers for the X-Fi.  They claimed to have Ubuntu working fine, but it wasn't easy to do.  Yet, when they upgraded to Hardy...it blew everything out of whack and still he didn't get the problem fixed.

While in one way I am open to that idea, it is kind of taking a step back.  So am not sure if I should do that or just wait until Hardy gets fixed.

Still I also have been kicking around the idea to try out something else besides Ubuntu Studio such as Open SuSE's JackLab.  It supposed to be something similar to Ubuntu Studio.  But then another question arises if it is easier or harder to set up than Ubuntu.  I will not know unless I do come across someone that has used both and can give me an opinion on each.

I will say too that if I know for sure that I can do the same things with the Linux applications as I can do with Ableton's Live, Sonar, Reason and Soundforge then I probably would sell off both my Alesis unit and my X-Fi card and buy a Hammerfall card.  But that is the trick isn't it?  Pulling the X-Fi out of my computer is really the point of no return.  Which is why I want to make sure the Linux applications WILL be a suitable replacement for my Window's apps.

For one...I believe that Audacity is a replacement for Soundforge.  The combination of Ardour and Rosegarden MIGHT replace Sonar and Live.  So the last thing is if there is a replacement for Reason.

Optimally I do want to check out these programs FIRST before I do anything rash.  But this is frustrating that I cannot get any of the Ubuntu Studio applications to work.  Some crash, some don't even start up.  It's a mess in there, that is all I know.

Geo

---

### Post by thorgal on 2008-06-27
Things don't look too good with this oss driver.
1- you could kill the esd sound daemon (killall does not output anything when it succeeds)
2- jackd tries by default to use the soundcard in full duplex mode but it looks like it is not possible here. So you could start jack in playback or capture only mode but I don't know if the jack oss backend can be configured like that. I know the alsa backend can be.

About the few options you mention, I would say this: if the very end goal is to get some piece of h/w by RME (which I fully recommend, I own one myself and it works beautifully!) but want to make sure beforehand that the linux apps are good enough for you to switch from windows, you don't need to spend that much time trying to get jack working with the X-Fi. If you have a spare card that is alsa compatible, it will be more than enough to get a taste of the jack world. About the OS, I personally use Debian Sid. Ubuntu Studio has proven unstable for me, even though it is much more user friendly. I sacrificed userfriendliness for stability.

---

### Post by jukingeo on 2008-06-27
> **thorgal said:**
> Things don't look too good with this oss driver.
1- you could kill the esd sound daemon (killall does not output anything when it succeeds)
2- jackd tries by default to use the soundcard in full duplex mode but it looks like it is not possible here. So you could start jack in playback or capture only mode but I don't know if the jack oss backend can be configured like that. I know the alsa backend can be.

I heard that Jack can be configured to OSS as a backend and by right that should be able to communicate with my sound card.

Now as far as ESD goes, I did kill it and right away I had no sound.  So obviously I tried to go back into Jack Control and like before, I got that same error message (about MIDI) and it crashes.

I set ESD back on and at first I didn't have sound, but I rebooted the machine and I had my sound back.  You said too that if I turned ESD off and rebooted my machine, my sound would come back.  What did get to thinking is that perhaps we could set ESD not to comeback on reboot and thus the reboot should clear everything out.  Maybe then I can get into Jack?

How about a configuration file in Jack.  Since I can't change settings now because Jack crashes, is there something we can do in a configuration file via Terminal?

While the idea of reverting back to the older version of Ubuntu (7.10) sounds promising, it would mean a lot of fixes and compiling work to get the ALSA drivers to work, correct?   Even if it does work, my qualm is that is moving a step backward and eventually I do have to upgrade Ubuntu. BUT it would at least allow me to try out the Ubuntu Studio applications.  

> About the few options you mention, I would say this: if the very end goal is to get some piece of h/w by RME (which I fully recommend, I own one myself and it works beautifully!) but want to make sure beforehand that the linux apps are good enough for you to switch from windows, you don't need to spend that much time trying to get jack working with the X-Fi. If you have a spare card that is alsa compatible, it will be more than enough to get a taste of the jack world. About the OS, I personally use Debian Sid. Ubuntu Studio has proven unstable for me, even though it is much more user friendly. I sacrificed userfriendliness for stability.

Ok, are you a musician or recording engineer yourself?  I hope so.  This way you know what it is with the situation I am facing.

The Hammerfall cards are excruciatingly expensive.  Being in a tight money situation I am not, I cannot afford to create a new machine. I could sell off both my X-Fi and My Alesis unit and that certainly would get me more than halfway there for a decent Hammerfall card, BUT will it really work 100% in both operating systems?

But it does boil down to the applications in Linux.  If I don't like what I see, then I am probably going to stick with what I have and don't need to invest a dime.  But since I can't see (or hear) anything I DON'T know what the applications can do.

Now in terms of supported hardware.  I DO have an old Sound Blaster Live that was in my old computer.  However, I did already try to use that card in my machine when I found out Dell's Sound Blaster Live is a FAKE.  However, that card wouldn't install properly on my Dell machine.  So I know I can't use it.  That is what prompted me to splurge for the X-Fi in the first place.

As it is for an "experiment" with a compatible sound device in Linux, I would say that really my only option is to go with a USB or Firewire device.   I KNOW that there are some that are compatible and Jack DOES allow you to select "USB SOUND" (I saw the option).  There are many posts here about those that have laptop computers in which the onboard sound is incompatible with Linux and they have been putting external USB sound devices into use (with varying degrees of success, mind you).

So to me getting an external USB (or firewire) sound device would be probably the only solution.  I could get an external Sound Blaster Live or Audigy for less than $100.  So that is inexpensive enough for me.  At least it is a good price to pay to be able to check out the Ubuntu applications.

Now, you mentioned that you are using a different distro.  I was thinking about doing the same.  Obviously if I don't have to buy anything new, and if changing the distro, I can get the sound to work, then I am good.  However, I am going to assume that the driver situation with the X-Fi applies to Linux across the board, correct?  If so, then I really don't know what my chances are with trying to get the X-Fi to work.

You said you are using Debian Sid.  Is that an audio editing based OS?  I been looking into Open SuSE and Musix myself.  However, Musix is still very new, like Ubuntu Studio.  So I am wondering if I am in the same boat.

Now getting back to Ubuntu Studio...thus far I have not met a single person here in the Ubuntu forums that managed to get Ubuntu Studio fully working even WITH a compatible card.  So that does support your claim that Ubuntu Studio is unstable.  In my case I can't get ANYTHING to work.  At least before I upgraded to Ubuntu Studio, I did get Audacity to work and Cinelerra.  Now neither is working.

Now since this IS all about the apps I am going to assume that all these cool programs in Ubuntu Studio are also compatible with other distros, correct?

So with Ubuntu Studio and Musix being very new and possible riddled with problems, I would like to perhaps investigate something that is more stable.

Outside of my audio requirements, I would like the distro to be able to let me play my emulated console games (and Linux games) and handle every day work such as emails, the internet (yes with sound too), and of course be able to use Open Office.

So I was ready to give Open SuSE's Jacklab a try...but as I recall I think that is a Red Hat based distro and I am not sure about any major differences between Red Hat and a Debian based distro.  However Ubuntu is Debian based and you say you are using Debian Sid.  How is that?

Anyway thanx again for your help, I have to run.

EDIT:

Ok, I am back.  I did some more research in regards to USB external cards.  These tend to be a double edged sword in Linux.  While they do have ALSA support, the drivers work slower than their Window's counterparts and as such the USB cards develope latency issues.  This is true with both Creative and M-Audio products.

So far it seems that one of the best supported "cheap" cards is the M-Audio Delta series.

While I am not fond of M-Audio products, the cards do offer TRS balanced 1/4" inputs & outputs and are fully supported in applications such as Ardour and Rosegarden.

The card is cheap at a cost of around $130 (cheaper on Ebay).

The bad thing is that I would have to go into my machine and dig out the X-Fi card and I am worried that I may run into problems.

But if there is absolutely nothing that I can do with the OSS driver on the X-Fi card in Ubuntu, then it leaves me without many options.

As a safeguard for my Windows applications, I am going to see if I can switch over my Windows audio to the Alesis IO-26...because if I can then I am less likely to wipe out my sound in Windows.  That is something I am going to check into now.

I am also going to sign up to the OpenSUSE forum and see how they are fairing with sound on the X-Fi over there.  If people are having the same issues then perhaps it is a problem that is across the board and maybe I have to say Bye Bye to my beloved X-fi card.

RE-Edit:

Ok, I'm back

The Alesis IO-26 is a full go with Windows.  Get this...it is fully 7.1 channel supported just like my X-Fi.  I am going to test it some more tonight, but so far it looks good.  System sounds, streaming video and my games I routed all to the Alesis IO-26.

So I can basically all I have to do now is disable the X-Fi completely and if everything is good with the Alesis IO-26, then I can quietly unload the drivers for the X-Fi and uninstall the card without disturbing the Alesis IO-26 setup.

Ok, OKAY.  So this is a really really really good thing.  Because now I don't have to fear blowing out my sound for Windows. 

The selection I have made for a replacement for the X-Fi is the M-Audio Delta-44.  It is a PCI card like the X-Fi, but it has a 4 in and a 4 out breakout box.  No digital recording capability, but at a $100 to $140 price range, it is worth a shot.  Supposedly this card has one of the higher successes with set up on Ubuntu in that it should be "Plug & Play".

I am hoping so.

I am going to venture over to the Open SuSE forum now and see how they are fairing with sound and the X-Fi before I do anything rash.  But if the results are the same over there, it would be safe to say that I would have problems with any Linux distro. 

Ok, so now I have a plan of attack.  Time to start researching and getting busy.


Geo

---

### Post by thorgal on 2008-06-29
hello! lots of stuff to think about ;)

the M-Audio is pretty much plug'n'play. I used to own a Delta1010 and it was so. The M-Audio PCI cards are usually quite good. I had limitations with hardware monitoring since only 2 channels could be monitored at that level. But in the end, I sold it and got the RME HDSP + Multiface II, which is more versatile. The drawback is that I needed external preamps for my mics, so I bought the RME Quadmic (4 IOs, mic and line level + phantom power, lo cut and phase reversal). The RME does work on both windows and linux. The linux driver is quite good for the HDSP. I don't know about other RME gears like the Digiface or the MADI but windows is officially supported by RME, no doubt.

By the way, I am a "self-made" music producer so I don't compromise in my studio. I go for quality and full support. Being an old unix/linux user, I make sure before I buy anything that it will work as expected on my system. The RME HDSP definitely fell into this category.

OpenSuse: it is redhat based or used to. It uses different system configuration scripts, etc. I was used to redhat until I switched to debian many years ago, which introduced me to new admin ways but it was not that difficult.

---

### Post by jukingeo on 2008-06-29
> **thorgal said:**
> hello! lots of stuff to think about ;)

the M-Audio is pretty much plug'n'play. I used to own a Delta1010 and it was so. The M-Audio PCI cards are usually quite good. I had limitations with hardware monitoring since only 2 channels could be monitored at that level. But in the end, I sold it and got the RME HDSP + Multiface II, which is more versatile. The drawback is that I needed external preamps for my mics, so I bought the RME Quadmic (4 IOs, mic and line level + phantom power, lo cut and phase reversal). The RME does work on both windows and linux. The linux driver is quite good for the HDSP. I don't know about other RME gears like the Digiface or the MADI but windows is officially supported by RME, no doubt.

I been doing quite a bit of research on three companies now.  In terms of a cheap choice, M-Audio seems to be doing well with the Delta series of cards.  They do have breakout boxes which is cool for their price range.  Being an audio technician, I do know that M-Audio's stuff doesn't hold up very well. Now I don't know how their computer cards are, but I see their keyboards and controller in the shop VERY often.  Also if you look on Musician's Friend clearance web page, they have quite a few M-Audio products listed.  So I am thinking quite a few returns and/or B stock resale items.  BUT I would say that in terms of experimenting in Linux...the audio cards seem to be a good buy. Sadly, no 192khz support.

Next in line are the RME cards, but they are VERY expensive.  While this is where I probably want to end up on a dedicated unit on a pro-audio level, it is not in the cards (pun intended) now.  I would probably have to sell off my Alesis IO-26 to purchase one of these.  However, from closely examining pictures of the RME cards...they sure do look very pro to me.

Echo. These seem like a good middle of the road card.  I would say slightly less endowed than my Alesis unit, but WAY better than M-Audio.  What I like about Echo is that they ARE supported and their firewire series DOES go to 192khz.  However, Linux firewire support is mostly FreeBob based and that worries me.  I think I want to play it safe and stick to ALSA.   So that does make the M-Audio Delta series the best bet to play with for now.


> By the way, I am a "self-made" music producer so I don't compromise in my studio. I go for quality and full support. Being an old unix/linux user, I make sure before I buy anything that it will work as expected on my system. The RME HDSP definitely fell into this category.

Well, by education I am an audio engineer, by trade I am an audio technician.  I have had a hardware based studio in my parents home for a while (prior to getting married).  I was first analog and then went digital.  I didn't like digital and I had a tough time recouping my costs on the equipment.   The reason I didn't like digital was because of the sampling rate at that time, which was 48k.  I could never get rid of the artificial grainy sound (zipper, or stepping distortion).  I didn't have enough money to repurchase analog gear, so I closed up shop for a while. But I kept an eye on digital and knew it would be only a matter of time before the technology improved.  And improve it did.  96k came along I started to play with digital sound again.  But I felt it still wasn't there.  NOW with 192k and some tube processing...I'M BACK!!

But this time I am going all computer.  But being married and two extra mouths to feed...money is a bit short now.  So that is one of the reasons why I am here.

> OpenSuse: it is redhat based or used to. It uses different system configuration scripts, etc. I was used to redhat until I switched to debian many years ago, which introduced me to new admin ways but it was not that difficult.

As of now I am not fully sure if I should stay with Ubuntu or switch to JackLab.  I had a funny feeling that OpenSuSE was totally different, but since you used it before, I am curious as to what changes I would be facing in comparison to Ubuntu (or Debian based) distros.

Also, I am pretty much sure that at this point in time OSS is not going to work out for me and I do have to bite into the ALSA sour apple.

I do still want to get my X-Fi card to work, but it seems like that I may either have to revert back to Ubuntu version 7.10 as that is the only operating system that is proven to have the X-Fi Beta ALSA drivers work on.

I do believe that the X-Fi issue will also present itself over at JackLab too.  I have seen a few X-Fi problem posts in the JackLab forum and I did feel a bit uneasy that those posts really didn't have conclusive answers to the X-fi owner's problems.   So I am going to take a good guess that the problem with ALSA drivers and X-Fi are across the Linux board.

I guess really the only reason for switching would be that if truly JackLab is better than Ubuntu Studio.  I would say it is probably better than the current version of Ubuntu because version 8.04 is littered with problems.  But as far as I hear, version 7.10 is a really good stable version of Ubuntu. 

So as of today I still don't know what to do.  Should I:

1) Revert to Ubuntu (Studio) 7.10 and install the ALSA drivers for my card?
2) Should I buy a new audio card i.e. M-Audio Delta series.

3) Should I still switch distros?

But I do know one thing is for sure.  My struggles with OSS are over.  I am going to dump it one way or another.  Jack doesn't work with it and nor does the internet.  So that is half a Linux setup and it is unacceptable.

Thanx,

Geo

---

### Post by rlameiro on 2008-06-30
well, in my Dell D600 laptop, the onboard chips works nicely with all the ubuntustudio programs setup. I recently buyed a edirol UA4FX and I think that now there is some work beeing done to put it to work, it is not a pro interface but it has phantom power etc. I cannot tell you if the card is fully supported in the advance mode (midi ports plus the 48khz and 92khz) I am learning to programm now and dont have a lot of time to work arround the audio setup, but I will some day :) I am happy to ear that you think to dump the xfi. Creative should support they products to opensource community also.

---

### Post by jukingeo on 2008-06-30
> **rlameiro said:**
> well, in my Dell D600 laptop, the onboard chips works nicely with all the ubuntustudio programs setup. I recently buyed a edirol UA4FX and I think that now there is some work beeing done to put it to work, it is not a pro interface but it has phantom power etc. I cannot tell you if the card is fully supported in the advance mode (midi ports plus the 48khz and 92khz) I am learning to programm now and dont have a lot of time to work arround the audio setup, but I will some day :) I am happy to ear that you think to dump the xfi. Creative should support they products to opensource community also.


Nice looking sound device you have there.  Anyway, I did look it up on the ALSA supported devices list and it isn't listed.  The UA-3FX is though.  I wouldn't say that isn't pro, as it does have basic pro features.  Semi-Pro yes...I would say that it is that for sure.

I have a fairly large unit, it is an Alesis IO-26 and it is 8in by 8 out with a phono input, digital ins/outs...phantom power, 24/192khz interface, VU meter bridge.  It is definitely a pro unit...but it isn't going to do me any good in Linux because it isn't supported.

The shame is that I only had the piece for one year and I didn't think far enough in the future that I would be playing around with Linux already.  But there are many changes going on in my life and I do have to watch my spending now.  So a Linux based rig is definitely going to save me a ton of money on software purchases.

I am going to hold on to my Alesis unit for now because in the event that Alesis does hop on the Linux bandwagon I still will have the unit.  But yeah, after a long few nights of wracking my brain out.  I did come to the conclusion that as long as I can use the Alesis unit for sound in Windows (and it is working fine), then I can pull the X-Fi card out and sell it.

I have been looking at a few different supported cards, but because I need to watch my spending, and I am pretty much just experimenting with Linux right now, I am going to go for one of the M-Audio cards.  I know M-Audio isn't the greatest, but they do give you a big bang for the buck.  I settled on the Delta series.  Which one, I really don't know...probably the Delta 44 or 66.  But the whole Delta line is supported in Linux, so it doesn't matter which Delta I would get, it will work.

At any rate it is worth saying that I am trying one more last ditch effort to get the X-Fi to work in Hardy (via ALSA).  There is a guy who managed to do it and I am in discussion with him right now. I will come back here and post the results if we are successful.   If not then I am going to continue with my plan to yank the card.

EDIT:

I have since discovered a way to us the ALSA drivers for the X-Fi, by following this guide here:

[http://ubuntuforums.org/showpost.php?p=4823915&postcount=675](http://ubuntuforums.org/showpost.php?p=4823915&postcount=675)

The correspondence for this procedure starts here:

[http://ubuntuforums.org/showthread.php?t=571656&page=102](http://ubuntuforums.org/showthread.php?t=571656&page=102)

Ignore the fact that the posted thread above is in the AMD64 forum.  The procedure works on Intel & 32 bit machines as well.

Thank You,

Geo

Geo

---

