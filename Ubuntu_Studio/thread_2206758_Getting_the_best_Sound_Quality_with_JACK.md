---
title: "Getting the best Sound Quality with JACK?"
date: 2014-02-20
forum: Ubuntu Studio
---

### Post by forkenbrock on 2014-02-20
After years of using highly modified Win 7 OS for file playback with external DACs on high-end stereo systems I set out to see if I could build an Ubuntu system that could beat it.

I've been using a Wyred4Sound DAC2 with a Juli@ sound card (the digital portion), attached to a I2S to HDMI interface.  I plan to eventually upgrade to the new PS Audio Perfectwave DAC (when it's released).

So far my effort to beat Windows have not been successful.  My Windows setup still sounds a bit better than Linux.  I was wondering if anyone has some suggestions.

In my Ubuntu setup I've installed Realtime and Low-latency kernels.  I'm using JACK with Gstreamer and Rhythmbox.  I've searched everywhere and as far as I can tell, Gstreamer is the only way to connect Rhythmbox to JACK (not sure if Gstreamer could degrade the sound quality).  I've been working on getting a JACK / MPD / Ario setup going, to see if that's any better, but haven't been able to get it going so far.

---

### Post by tgalati4 on 2014-02-20
Because of the psychoacoustics involved (and your hearing) better can be subjective.  If you have a high-end sound card, and only have Windows drivers, then that will probably sound better.  If you have a decent sound card with both Windows and Linux support, I doubt there would be a difference.  I use an oscilloscope to test such differences because the waveforms will show ripples before your ability to hear them.  A pure sine wave should be a pure sound wave throughout the entire system, but you would be surprised at what it looks like after going through several processing/amplification levels.

If your gain stages are not set properly, you can clip signals internally and that you will hear.  Sometimes such clippling can give the impression that one system is better than another, but simply changing the gains can fix that.

Rhythmbox catalogs your files, Gsteamer is a framework that decodes the files.  JACK provides the signal routing from input to output in real-time (for low-latency applications such as monitoring your instrument playing).  If you are only playing back music, then real-time/low-latency is really not a factor since you are not monitoring your live instrument playing.

As far as better, you will have to perform A-B tests.  Using your ears and different kinds of music may reveal differences, but I use an oscope to see those differences with simple sine waves at various frequencies.

I don't have any of your hardware so I can't comment on your setup, but in general the transducers (speakers and headphones) make a big difference.  Everything after the microphone and before the speaker is in the digital realm, so it's pretty darn linear.

---

### Post by CrocoDuck on 2014-02-21
You may want to use a player that directly connects to jack. I use this one: [http://aqualung.factorial.hu/](http://aqualung.factorial.hu/) . This distro is designed to offer the highest playback quality: [http://www.ap-linux.com/](http://www.ap-linux.com/) , maybe you could give it a try or dig into the documentation and/or configuration to find good suggestions. As tgalati4 said, low latency is not required to hi-fi playback. However, you should benefit from a RealTime kernel, since a realtime kernel is basically a kernel that manage processes in way that avoid buffering delays. For more details: [https://en.wikipedia.org/wiki/Real-time_operating_system](https://en.wikipedia.org/wiki/Real-time_operating_system) . Applied to audio processing, this means a reduced ammount of jitter and distortion due to sheduling, and not just a lower latency.
 				 					[ 						 							]("http://ubuntuforums.org/member.php?u=241895")

---

