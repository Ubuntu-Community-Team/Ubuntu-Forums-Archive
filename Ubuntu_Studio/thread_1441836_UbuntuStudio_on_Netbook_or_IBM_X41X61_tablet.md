---
title: "UbuntuStudio on Netbook or IBM X41/X61 tablet?"
date: 2010-03-29
forum: Ubuntu Studio
---

### Post by wtc on 2010-03-29
Hello,

I am looking to buy a laptop, install UbuntuStudio and use it mainly for recording/editing (Jack+Ardour+Hydrogen mostly, up to ~20 tracks) in home studio, with external USB sound interface.

Is Netbook with Atom processor enough for that task? Which configuration should I buy? They have different processors - N270, N280, N450 - can you share your experience? Is 1GB RAM enough for audio production actually?

Alternative would be also small and light Lenovo X41 or X61 tablet (they have Centrino processor - how is it comparable to Atom?)

Thanks!

---

### Post by snowpine on 2010-03-29
Hi WTC, I use my netbook (Dell Mini 9, Atom 270 with 1gb ram) with Audacity as a portable 2-track recorder, for taping band practices and the like. I then copy the files for editing on my more powerful desktop computer.

I also tried Hydrogen briefly and it worked fine. I have not tested Jack. 

Atom 270 performance is somewhere between a Pentium 3 and Pentium 4. I have never used a Centrino. Hope that is helpful information... :)

---

### Post by wtc on 2010-03-29
thanks snowpine for comment, that's helpfull indeed! 

any other practices, anybody?

---

### Post by AutoStatic on 2010-03-29
Hello wtc, I have a netbook with an AMD L110 CPU (1.2 Ghz) and I can record fine with it (Qtractor). I would advise though NOT to use Gnome as your desktop environment, I've tried for like 15 minutes and it just doesn't work. So I switched to a lighter DE (in my case IceWM).
Not that it could help you much decide (AMD L110 is not an Intel Atom), but it might be useful info anyway. I would not get anything like a pad or a slate at the moment. I would wait until the iPad really hits the market and other vendors start issuing cheaper models.

---

### Post by wtc on 2010-03-29
Hello AutoStatic,

Thanks for a note! Could you detalize a bit - are you using Jack, and if yes how big is the latency? Are you using any midi samples via sw syntheser (qsynth etc) and how large? Or using live recording, or predefined loops? How big are your projects - i.e. number of tracks / size MB in qtractor? Nave you noticed if RAM is enough (1GB right?)

Your idea about the pads hits the point, thanks:)

---

### Post by cchhrriiss121212 on 2010-03-29
I think you should prioritise quality cpu over RAM as it has a much greater effect on performance. RAM is also easy and cheap to upgrade in a laptop. 2GB should be enough for your projects, and you could switch to a lighter environment like Autostatic says if things get sluggish.

If you are going to use this as your main recording setup, then I would think you need something more substantial than netbooks/pads currently offer.

---

### Post by wtc on 2010-03-29
Hello Cris,
Thanks for comment. I was really looking for something easy to carry but still capable of doing general recording tasks, vs a high-performance studio - I have a PC for editing as well. Rather, mobility is my main concern now. With regards to performance, I'm bit confused what to expect on which hardware - couple of years ago it was right to make quality recordings using Pentium4 machine, now dealers offer me at least Intel I5 processor plus 4GB RAM for the same tasks, so I really want to know what is --enough-- on current hardware (as said, jack+ardour+hydrogen is mostly why I need it for).

---

### Post by AutoStatic on 2010-03-30
> **wtc said:**
> With regards to performance, I'm bit confused what to expect on which hardware - couple of years ago it was right to make quality recordings using Pentium4 machine, now dealers offer me at least Intel I5 processor plus 4GB RAM for the same tasks, so I really want to know what is --enough-- on current hardware (as said, jack+ardour+hydrogen is mostly why I need it for).I don't use Ardour so no idea if that would run well on a netbook for example. On my netbook Qtractor does really well, I have some 20+ tracks projects that play flawlessly. Don't know about sizes, looking at some drumtracks now and then we're talking hundreds of Mb's already. Recording is a different thing as you will probably end up with a notebook/netbook without Firewire so you'll be forced to use USB. And with a decent USB soundcard you can record 2 channels at once max. Unless you find a supported USB2 device, I haven't come across one yet that works properly.
But I dare to say that a core I5 with 4Gb of RAM is really over the top. Like I said, I can record and play around fine with my 1.2 Ghz [Gateway]("http://www.netbooktech.com/2009/07/10/gateway-lt3103u-review/") notebook with 2Gb RAM (sold in Europe as a [Packard Bell]("http://packardbell.nl/showroom/netbooks/dot-m%2fa/dot-m%2fa.nl%2f202-LU.BCC0Y.027-1849.html"))

My current JACK settings on the netbook:
Frames/Period: 64
Sample rate: 48000
Periods/Buffer: 3
Latency: 4ms

This is with a Edirol UA-25 and I also use the rtirq script to prioritise processes. When recording or working with audio I disable practically everything (Wifi, ethernet, webcam etc) and I use a lightweight Desktop Environment (IceWM with Rox). The overall latency is approx. 10ms (tested with jdelay and with a recorded sine in Audacity).

---

### Post by wtc on 2010-03-30
Hi AutoStatic,

Thanks for info! Yep, the only netb with Firewire option that i know is Lenovo S10 1st edition, it's not produced any more. 
I just came across some Netbook models having dual-core Atom 330 (like Asus 1201N etc), let's see what they have to offer..

---

### Post by AutoStatic on 2010-03-30
> **wtc said:**
> Yep, the only netb with Firewire option that i know is Lenovo S10 1st edition, it's not produced any more.Yeah, I spotted those when I was in Hong Kong.
Dell now offers a 12" Latitude with Firewire afaik, but then you're talking > $1000,-

---

### Post by wtc on 2010-04-01
.. just found interesting link - 
[http://createdigitalmusic.com/2009/05/05/the-mobile-music-netbook-linux-powered-indamixx-os-laptop-looking-slicker/](http://createdigitalmusic.com/2009/05/05/the-mobile-music-netbook-linux-powered-indamixx-os-laptop-looking-slicker/)

.. and that are apps they have inside:
[http://www.indamixx.com/applications/audio-applications.html](http://www.indamixx.com/applications/audio-applications.html)

So basically overclocked Netbook with 2GB RAM and customized Ubuntu called Transmission OS :)  Of course these guys had a good time tuning VST's and other stuff, respect:)  Seems the Software pack they sell also separately.

Looks like a reality to get Ardour, jamming on the small&light Netbook...

---

