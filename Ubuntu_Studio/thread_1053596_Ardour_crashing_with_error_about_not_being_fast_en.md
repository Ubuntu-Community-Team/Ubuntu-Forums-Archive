---
title: "Ardour crashing with error about not being fast enough."
date: 2009-01-28
forum: Ubuntu Studio
---

### Post by binger on 2009-01-28
I have a project that I was working on in 2.3 and I started getting this error.

    JACK has either been shutdown or it
    disconnected Ardour because Ardour
    was not fast enough. Try to restart
    JACK, reconnect and save the session.

It got the point where I couldn’t work on the project anymore. I could open the project and playback my song, but as soon as I stopped playback that message would pop up and JACK would get Xruns. My session isn’t extroidinary, it has 7 drum tracks that I recorded from Hydrogen, 2 guitar tracks and a bus. It has 7 effects running which doesn’t seem like a lot since I have run more effects in Abelton Live and Adobe Audition before.
I investigated and tried to make sure my system was tweaked correctly. I am running Ubuntu Studio Hardy with real time kernel 2.26.24. I have my audio group setup in the limits file with unlimited memlock. My system has a 1.8GHz Core Duo and 2GB of ram. I don’t have any hefty daemons/processes running. I am using a Edirol UA-4fx USB audio interface. I have jack setup with 128 frames and 3 periods. I got the same results when I turned the frames up to 1024. Ardour plays/records fine in a new session with just a few tracks. Other audio apps work fine with Jack. I built .116 jack and 2.7 Ardour from source with optimize flags and still get the same result. My hard drive is running in udma6 mode and gets 900MB/sec cached read and 40MB/sec buffered disk read. I have run the realTimeConfigQuickScan.pl from [http://wiki.linuxmusicians.com](http://wiki.linuxmusicians.com) and all checks are good. I am out of ideas and just want to make music, any help is greatly appreciated.

Thanks.

---

### Post by binger on 2009-01-30
Okay, so after continuing my search for a solution I can across someone with a similar problem that ended up being cause by a bug in a effects plugin(freeverb).  I had about 10 plugins in my project and I narrowed it down to the one causing the problem!  TAP Equalizer.  I don't know what the actually problem is, but it causes ardour/jack to fall apart.  Upon checking out the website for TAP it looks like development has been dead since 2004 so I don't know if it will be fixed. 

Ardour Rocks.  Case closed.

---

