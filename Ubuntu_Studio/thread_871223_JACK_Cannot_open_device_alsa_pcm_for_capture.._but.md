---
title: "JACK Cannot open device alsa_pcm for capture.. but audacity can?"
date: 2008-07-26
forum: Ubuntu Studio
---

### Post by thomasjw on 2008-07-26
Hey helpful forum folks.  I just made the switch to Ubuntu Studio from winxp and have spent many many hours reading, learning, and trying new and confusing things in the past 3 days.  I was immediately delighted, during my first launch of Studio, when I opened up Audacity and found that my M-Audio Fast Track Pro was automatically detected (by name!) and I could actually record through it with no glitches.  Couldn't ever do that under xp, now for the first time my usb1.1 audio interface is actually useful and not an expensive paperweight.  so far so good, so then I try starting qjackctl so I can start messing with Ardour etc.  

Here my troubles began.  A lot of things I've already fixed thanks to reading other threads, setting memlock to unlimited and soforth, but there remains one problem I can't solve or find comprehensible advice on.  No matter what combination of options I try, I always get this error from Jack:
> ALSA: Cannot open PCM device alsa_pcm for capture. Falling back to playback-only mode
which confuses me because it's the ALSA driver I was using in Audacity, where it worked perfectly.  
I have read lots of different threads about Jack problems that discuss similar error messages but none that seem like the same problem.  Also when I try switching from duplex to capture-only, Jack won't start at all, the whole operation fails.  

Hopefully this is something simple to fix??  I found a thread back in the archives from someone using an m-audio fast track and he never seems to have had this problem... [http://ubuntuforums.org/archive/index.php/t-447744.html](http://ubuntuforums.org/archive/index.php/t-447744.html)

...help please?

---

### Post by asuastrophysics on 2009-04-05
i have the exact same issue :(

---

### Post by markbuntu on 2009-04-05
It sound like some other application has taken hold of the capture so jack can't grab it. Skype will do that.

---

### Post by asuastrophysics on 2009-04-07
that is not the case. i have closed every other program running and it still won't start.

i have been working on this for 4 hours now...

---

### Post by schef on 2011-02-01
Hej..
The problem is that FastTrack Pro has 2 sound cards in one..
So main output is on my pc like hw:2,0 and another output and capture are on hw:2,1..

Becouse of that you have to use .asoundrc to combine the two sound cards as one.

```
#asound.rc
pcm.mt4 {
     type multi
     slaves.a.pcm "hw:2,0";
     slaves.a.channels 2;
     slaves.b.pcm "hw:2,1";
     slaves.b.channels 2;

     bindings.0.slave a;
     bindings.0.channel 0;
     bindings.1.slave a;
     bindings.1.channel 1;
     bindings.2.slave b;
     bindings.2.channel 0;
     bindings.3.slave b;
     bindings.3.channel 1;
}

ctl.mt4 {
     type hw
     card 0
}

pcm.multi4 {
     type route;
     slave.pcm "mt4";
     ttable.0.0 1;
     ttable.1.1 1;
     ttable.2.2 1;
     ttable.3.3 1;
}

ctl.multi4 {
     type hw;
     card 0;
}
```

So now you start jack as:


```
jackd -d alsa -C hw:2,1 -P mt4 -r 44100
```

and now it works..:)
now i have 4 output channels and 2 input channels..:)
Thanks to [http://www.linuxmusicians.com/viewtopic.php?f=6&t=2622]("http://www.linuxmusicians.com/viewtopic.php?f=6&t=2622")

---

