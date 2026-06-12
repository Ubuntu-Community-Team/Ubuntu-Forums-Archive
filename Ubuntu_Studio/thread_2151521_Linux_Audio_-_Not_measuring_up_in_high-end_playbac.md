---
title: "Linux Audio - Not measuring up in high-end playback."
date: 2013-06-04
forum: Ubuntu Studio
---

### Post by forkenbrock on 2013-06-04
I’ve built a Linux audio system for playback of audio files that uses the low-latency kernel (there’s also a Realtime kernel installed), JACK, ggStreamer and rhythmbox.  I’ve also used the Realtime Quick Config Scan tool to make sure my settings were optimized for performance (all categories are positive). 
 
My system consists of a First Watt F5 amp, a modwright 36.5 preamp, a Wyred 4 Sound DAC2 w/ Juli@ soundcard and HDMI I2S interface, and Zu Audio Druid Mk5 speakers.  The First Watt amp has .001% THD and is very resolving; if there’s a difference you’ll hear it.
 
The idea was to build a great sounding OS for Audio playback as a free download on my website for audiophiles, to create a Live DVD.  However, it’s not performing as well as I had expected, sound-wise. 
 
Using the Wyred DAC I can set the JACK latency to its lowest, at .72ns and it plays fine.  Out of my highly tweaked Win 7 OS, with music playing, the DPC Latency Checker tool usually reads between 8-14ns.  I was anticipating that getting near realtime performance in the kernel would produce a notable improvement in the sound quality.  Big reductions in latency with Win 7 have yielded dramatic improvements in sound.  However, I have to admit that after all this work Win 7 (using the ASIO4All driver) still wins on clarity.  Low-latency Linux still beats stock Windows and probably Mac, but I’m disappointed it didn’t perform as I was hoping.
 
BTW, I tried the array of drivers in JACK (OSS, Freebob, Coreaudio, etc) and didn't note much change or improvement.  I wonder if there’s anything I can do to try to get better results, such as use something other than ggStreamer?

---

### Post by zequence on 2013-06-04
Latency will not affect audio quality. Less latency just gives the computer less time to complete its computation of the audio process. 
So, for audio playback, large latency is preferred over low, as low latency is only useful for live processing, where the musician needs the input to be outputted as fast as possible.

---

### Post by forkenbrock on 2013-06-04
That's not entirely true.  Latency by itself does not affect audio quality.  However, variances in latency result in jitter.  Reducing the latency to near zero should reduce the potential for variance.  We don't know whether there is much variance that translates to jitter in my Win 7 setup (I don't have the tools to measure jitter, just my ears).  I'm just trying to figure out if there's anything I've overlooked or if this is the best I can do with Linux.

---

### Post by zequence on 2013-06-05
I don't believe this to be true. Show me some proof.

What is involved is CPU clock, drivers, etc. Not latency. Low latency just means there's a bigger chance the process might not finish in time. Timing is unaffected.

---

### Post by forkenbrock on 2013-06-05
Low-latency and Realtime kernels as I understand it are designed to prioritize transmission of audio data above interruptions from other non-critical processes.  These interruptions could lead to timing errors (jitter) when the data reaches the DAC...we are talking about timing in billionths of a second.  The only reason I'm exploring Linux is to see if limiting those interruptions at the kernel level improves sound.

At any rate, it's not important whether we agree.  The point of my post is to find out if I've already done everything that can be done to get the best sound performance out of Linux audio.

---

### Post by zequence on 2013-06-05
No, realtime kernels are designed to make sure processes are completed in time. Or, that realtime process are completed in time. Which means, other processes will have to wait.

The throughput of a realtime kernel, or a lowlatency kernel is reduced because of this, which makes them unsuitable for server machines, but quite suitable for live audio processing.
If you're only doing playback, a generic kernel will be just as fine as any other.

If you want audio quality, you really only need fairly good audio card, cables and speakers. And, a generic kernel for audio playback.

---

### Post by CrocoDuck on 2013-06-05
Hi. An interesting page about linux, audio performances and latency (not finished yet): [http://apps.linuxaudio.org/wiki/jack_latency_tests](http://apps.linuxaudio.org/wiki/jack_latency_tests) . A lot of programs useful for measures (also for playing:D): [http://kokkinizita.linuxaudio.org/linuxaudio/](http://kokkinizita.linuxaudio.org/linuxaudio/) . Maybe some of those programs can help you to quantify the issue.

---

### Post by forkenbrock on 2013-06-05
Thank you CrocoDuck.  Certainly an interesting page.  I think the word  Latency has gotten us off track, probably from the way I phrased my  initial post.  

I'm not concerned with high or low latency.  My  reason for using the LL and RT kernels was for their preemption  capabilities.  I wanted to experiment with keeping interruptions at the  kernel level from interfering with near-perfect transmission of audio  samples.  Comparing Linux to Win 7, it would seem the JACK drivers are  not yielding the results I'm looking for (up against ASIO 4 All) and if  the more advanced preemption is helping anything it's not enough.

We've  had a debate on theories.  Now, is there anyone else out there who's  experienced with these tools and has a suggestion to produce better  audio quality for a high-end system, using JACK or other approaches?   Are there any other tools (please don't say PulseAudio or MPD)?

---

### Post by jejeman on 2013-06-05
Did you check this?
[http://www.ap-linux.com/](http://www.ap-linux.com/)

---

### Post by CrocoDuck on 2013-06-05
> **jejeman said:**
> Did you check this?
[http://www.ap-linux.com/](http://www.ap-linux.com/)

Uh! Interesting!

forkenbrock, maybe the "cgroup thing" could help a little the prioritizing, but its effectiveness is controversial. You may try to adapt this guide for gentoo [http://proaudio.tuxfamily.org/wiki/index.php?title=DAW_Digital_Audio_Workstation#Instructions_for_3.x_Kernels](http://proaudio.tuxfamily.org/wiki/index.php?title=DAW_Digital_Audio_Workstation#Instructions_for_3.x_Kernels) . I've tryed it with Archbang. I'm not sure if really effective, but I feel like it had improved stability.

---

### Post by forkenbrock on 2013-06-05
Thanks Jejeman.  This is interesting.  It looks like the same  approach...RT + JACK.  They use a different player and MINT, which  wouldn't affect the sound.  It doesn't appear that they were able to  come up with any other options either.  thanks

---

### Post by CraigPid on 2013-06-11
Sound to me like you're causing this "jitter" by trying to get near zero latency. In effect you're throttling the pipeline and the audio signal is getting choked off resulting in dropouts.What you need to do is raise the latency for smooth playback. Here is a good article to read so that you could understand what latency is in terms of digital audio.
[http://apps.linuxaudio.org/wiki/jack_latency_tests](http://apps.linuxaudio.org/wiki/jack_latency_tests)

---

### Post by magyar666 on 2013-06-15
There is a quite informative article on the variables affecting digital audio quality at the Analog Devices site also.  It raises issues not mentioned here.
[http://www.analog.com/en/processors-dsp/sharc/products/technical-articles/relationship_data_word_size_dynamic_range/resources/fca.html](http://www.analog.com/en/processors-dsp/sharc/products/technical-articles/relationship_data_word_size_dynamic_range/resources/fca.html)

---

