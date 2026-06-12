---
title: "Is it low latency?"
date: 2011-04-15
forum: Ubuntu Studio
---

### Post by rusty377 on 2011-04-15
I installed 10.10 a week or so ago and have it playing nicely with Reaper DAW via wine and using Jack and wineasio v .75. My question is- how do you tell if the kernel you are running is set for lowlatency- and if not , how do you set that option?

Another question:

What numbers do you go by to verify latency times? Is it the latency calculation displayed in jack setup screen? Or is there a way to actually measure the latency? My jack is currently showing 11 ms using external X-fi USB sound and recording using Blue Snowflake mic.

---

### Post by Pablo_F on 2011-04-15
Hi, 

There is a tool to measure real round-trip latency called jdelay (it is in the ubuntu repos). You need a physical cable between input and output of your card and make jack connections from jdelay output to system playback and from system capture to jdelay input. You will see the latency measured in frames. 

If you can work with those jack settings, then why worry if it is low enough latency. You are using a generic kernel I suppose (check *uname -a*). There are other types of kernels with a special configuration. Take a look at this:

 [https://help.ubuntu.com/community/UbuntuStudio/RealTimeKernel](https://help.ubuntu.com/community/UbuntuStudio/RealTimeKernel)

---

### Post by rusty377 on 2011-04-15
Pablo,

Thanks again for the reply!

I am using the generic kernel- but I have heard that the lowlatency is not available for 10.10. I thought maybe there was some run-time "command-line" mods that approached a lowlatency compile- maybe not? When I downloaded the Ubuntu Studio package I just thought it would most likely already be lowlatency since it seemed geared towards audio recording.

I cannot use a true latency software comparison as my microphone of choice (1 track at a time overlay recording) is the Blue Snowflake condenser mic that is USB self contained. Does the latency display in the jack control setup give a reasonable estimation of latency? I think the latency while using is better than in xp when overlay recording.

Does the blinking RT in the Jack display indicate realtime? Guess it couldn't if kernel is generic

---

### Post by Pablo_F on 2011-04-15
> I thought maybe there was some run-time "command-line" mods that approached a lowlatency compile- maybe not?

No. 

> When I downloaded the Ubuntu Studio package I just thought it would most likely already be lowlatency since it seemed geared towards audio recording.
Previous versions of US included a rt kernel. But not maverick. 

Some people have installed a low-latency kernel from alternative repos. Search the forum.

> Does the latency display in the jack control setup give a reasonable estimation of latency?
Yes. But note that if you are running jackd in asynchronous mode, there is one more period size of latency and qjackctl does not report it. 

For example, if you run with 256 frames/period, 2 periods/buffer at 48000 Hz, the calculated round trip latency in synchronous mode is 512 frames (512 / 48000 = 10,6 ms) but in async mode is 768 frames (16 ms).

You need to know your jack version. (*jackd -V* in a terminal). 1.9.x is jack2 or jackmp, 0.xxx.x is the original jack or jack1. Jack2 is asynchronous by default. You have to append "-S" to the server path field to run jackd2 in sync mode. 

More info: [http://trac.jackaudio.org/wiki/Q_differenc_jack1_jack2](http://trac.jackaudio.org/wiki/Q_differenc_jack1_jack2)

> Does the blinking RT in the Jack display indicate realtime? 
Yes, it indicates that Jack is running in realtime mode but this has nothing to do with the kernel. See Jack faq: [http://jackaudio.org/realtime_vs_realtime_kernel](http://jackaudio.org/realtime_vs_realtime_kernel)

Cheers! Pablo

---

### Post by rusty377 on 2011-04-15
Thanks- I added the -S and will test next week. I think I can live with the 11 ms delay. Again thanks and cheers

---

### Post by trulan on 2011-04-16
I find, using jdelay to measure, that my souncard (I'm using firewire) adds about 4 ms round trip latency in its own hardware.  So if I want <10ms latency, Jack Control needs to be showing <6 ms.  Your hardware is probably a bit different, I really don't know.  But the hardware usually adds a little latency, that's why the only way to properly measure it is with something like jdelay.  I'm not sure how you would do that with your setup though.

A lowlatency or realtime kernel won't exactly lower your latency, but it **might** let you run better with lower buffering settings.  It might make things worse for you, it really depends on your hardware.

Keep in mind that latency is often over-rated.  Also, the 'other' OS's usually don't take into account everything that actually causes latency when making their <10ms claims.  Finally, every 10ms latency is equivalent to moving about 9 feet/3 meters away from your speakers.

---

### Post by Pablo_F on 2011-04-17
My m-audio 2496 PCI adds some 60 frames. At 48000 Hz, 1,2 ms. A friend of mine's FA 66 adds about 4 ms, too, IIRC.

---

### Post by barisurum on 2011-04-21
UbuntuStudio 11.04 + 2.6.38-lowlatency kernel works great!

[https://launchpad.net/~abogani/+archive/ppa](https://launchpad.net/~abogani/+archive/ppa)

---

### Post by lboorse2 on 2011-04-22
This just threw me for a loop (pun intended).  I'm planning on setting up a PC with Studio once I figure out which PC will work best for me from my few already owned choices.  I'm going to use it for some simple audio recording with Audacity or maybe even Ardour.  

I was thinking the low latency kernel was really what made Ubuntu Studio special (aside from the available programs already packaged with it).  I've tried recording on a Windows XP PC with Audacity in the past and the latency really killed any chance of recording multiple tracks, one at a time, with simultaneous playback and record.  

Is Ubuntu Studio still better able to handle that than say, an regular flavor Ubuntu install with just the few apps I'll probably use?  (Audacity and maybe Ardour).  I'm debating if I even need Jack for what I want to do, or is Jack what's going to help me accomplish the simultaneous playback and record with little delay?

What am I missing?

---

