---
title: "Ubuntu audio production - still problems"
date: 2009-12-29
forum: Ubuntu Studio
---

### Post by arielon on 2009-12-29
Setup: 
. sound card - Presouns FIREBOX [firewire - works great with ffado, better than in Windows with RT+jackd]
. keyb - KORG K61P
. OS - Ubuntu 64 bits (using RT and non RT, doesn't make much difference here :confused:)

Setup:
. qjackctl (ffado)
. **wineasio**
. alsa + jack pcm plugin

Soft:
. Rosegarden (master)
. Propellerheads Reason (slave)

I want to achieve:
. plausible - Rosegarden (or any other linux native seq, including Ardour[albeit no midi yet]) sending midi to Reason (wine) while playing other samples from within sequencer.
. best - Live or Cubase [Rewire or Jack Transport] to Reason (using wine)

So far:
. winecfg / ALSA+jack pcm = lots of Xruns [which means sound stops in Reason]; midi works! [from Rosegarden seq and K61P midi keyboard]
. winecfg / JACK = No midi in Reason. Great timing, though, almost no xruns [best config so far] (RT)
. winecfg / ALSA / **wineasio** = xruns (seems wineasio introduces further lag) The worst problem is that the connection graph is lost there (i.e.: no more ASIO_reason connection in jack) and app hangs until I shut down the jack server and I get an error in Reason.
 

---
. Why Reason? - Why not? It works completely stable with Jack audio in winecfg, only problem is no MIDI (I haven't find the way yet)
. Why Live? - [www.ableton.com]("http://www.ableton.com/") (download demo and you'll see)

---

### Post by wentzr on 2009-12-30
> **arielon said:**
>  

. OS - Ubuntu 64 bits (using RT and non RT, doesn't make much difference here :confused:)


exactly which version of "Ubuntu 64 bits" are you running? That info would certainly be good to know. Have you tried running  ArtistX, 64Studio or AVLinux? I'd recommend highly the latter. Learn from what each does differently, how it fits your needs and customize whichever if you like to bring it all working beautifully under one kernel. 

I seriously don't get why you're using reason on linux. just run it in windows. Why put yourself in a Tesla Roadster so you can have the dash of your ford escape?!?! to each their own..

---

### Post by arielon on 2009-12-30
**Ubuntu version: **The version you can download at [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) (64 bits).

I've installed the RT kernel (linux-rt package), but as said doesn't really make a difference, also because I can't get now my ATI 3200 HD working with it.

This is my first "serious" Ubuntu after being tinkering around. If I can get an stable studio I'll go into a clean install (after some trying here and there). After seeing that the installs you talk about would simply add some of the changes I'm already doing, I'm now considering now whether, as you say, I can "customize to bring it all working beautifully under one kernel".

. **Why Reason? **- Why not? It works completely stable with Jack audio in winecfg, only problem is no MIDI (I haven't find the way yet)


If only Jack (firewire-FFADO) could get some midi and WINE could get to do some Jack Transport...

Tesla & Ford, in my view, should get together for a while then & rock:guitar:.

---

### Post by AutoStatic on 2009-12-30
> **wentzr said:**
> I seriously don't get why you're using reason on linux. just run it in windows. Why put yourself in a Tesla Roadster so you can have the dash of your ford escape?!?! to each their own.. I second that. [Linux is not windows]("http://linux.oneandoneis2.org/LNW.htm").

---

### Post by JC Cheloven on 2009-12-30
@arielON:

Me, as many people here, had a long previous run in windows, specially regarding audio/music applications. 
At the beginning, everyone wants to keep using under ngu-linux the familiar apps they're used to in windoze. As time passes, one realizes that it's a nonsense. 

If you have a real interest in foss, you should look for free replacements for the apps you need. They may not be as fancy as proprietary ones, but they will (hopefully) prove to be functional for your needs, and as I always say "they will improve if we use them". 

If your bet is for proprietary software, you'd better to stick with win2 or mac. Either way, best of luck, and happy new year !!

---

### Post by chkneater on 2010-04-01
> **arielon said:**
> **Ubuntu version: **
Tesla & Ford, in my view, should get together for a while then & rock:guitar:.

Should I point out the irony that Edison and Ford were good friends while Tesla and Edison hated each other?  Or that without Edison having invented the phonograph, Les Paul would never have created The Log?  Off topic, I know, sorry.

---

### Post by sgx on 2010-04-02
> **arielon said:**
> **Ubuntu version: **The version you can download at [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) (64 bits).

I've installed the RT kernel (linux-rt package), but as said doesn't really make a difference, also because I can't get now my ATI 3200 HD working with it.

This is my first "serious" Ubuntu after being tinkering around. If I can get an stable studio I'll go into a clean install (after some trying here and there). After seeing that the installs you talk about would simply add some of the changes I'm already doing, I'm now considering now whether, as you say, I can "customize to bring it all working beautifully under one kernel".

. **Why Reason? **- Why not? It works completely stable with Jack audio in winecfg, only problem is no MIDI (I haven't find the way yet)


If only Jack (firewire-FFADO) could get some midi and WINE could get to do some Jack Transport...

Tesla & Ford, in my view, should get together for a while then & rock:guitar:.

Hi, you must consider that Reason is made to be an efficient standalone Windows based audio system, whose users often struggle with, and debate various options when trying to integrate Reason in other audio systems.

Install Reaper and rewire, which hold the keys. Reaper is by far your best option to use windows vsts in wine, and with rewire, well watch the video, in Reaper, select wineasio in Reaper prefs, as your asio driver

[http://www.youtube.com/watch?v=EAHjQAtfKGY](http://www.youtube.com/watch?v=EAHjQAtfKGY)

 and don't give up! In the long run, you'll want an nvidia 2D graphics solution, everything else will hinder audio production eventually.
Cheers

---

