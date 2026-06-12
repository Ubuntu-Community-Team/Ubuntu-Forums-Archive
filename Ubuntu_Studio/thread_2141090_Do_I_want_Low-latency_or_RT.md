---
title: "Do I want Low-latency or RT?"
date: 2013-05-01
forum: Ubuntu Studio
---

### Post by forkenbrock on 2013-05-01
I'm trying to figure out whether I need the Low-latency or RT kernel?  I'm looking for the one that will deliver the best performance (in theory) when it comes solely to playback of audio files.

I downloaded Ubuntu about 6 weeks ago.  The link said it was 12.10, but when I installed it the version says 12.04.  Anyway, I've been under the impression all along that I need to patch the kernel and I should go with RT, but some of the YouTube videos I've seen suggested all I need to do to get RT performance is adjust the Config file (which I did) and I do see the RT flashing in my JACK setup.  However, from what I've read my understanding is that my system is not doing RT at this point.

The last post about updating the kernel seemed to have some good info and I found the post below with instructions to patch the kernel (shown in the first answer), which I'm under the assumption is relatively accurate.

Any feedback you can offer is appreciated.  Should I follow the instructions below and update with the RT patch?


[http://askubuntu.com/questions/72964/how-can-i-install-a-realtime-kernel](http://askubuntu.com/questions/72964/how-can-i-install-a-realtime-kernel)

---

### Post by matt_symes on 2013-05-01
Hi

This is a pretty good read. Read the section on *kernel* and then plough on through the rest of it.

[http://wiki.linuxmusicians.com/doku.php?id=system_configuration&DokuWiki](http://wiki.linuxmusicians.com/doku.php?id=system_configuration&DokuWiki)

Kind regards

---

### Post by zequence on 2013-05-01
> **forkenbrock said:**
> I'm trying to figure out whether I need the Low-latency or RT kernel?  I'm looking for the one that will deliver the best performance (in theory) when it comes solely to playback of audio files.


Kernels don't improve audio quality, so you should probably just stick with the generic kernel. Nothing in your computer really does, except for the audio card you use. And, the difference between those is so small nowadays, that probably few human ears would notice the difference on a consumer system setup.

The only benefit you get with either of those kernels is you can get lower latency without audio dropouts, which is only important if you're doing something live, like playing midi keyboard and using soft synth sounds, or monitoring what you are recording live.

A realtime kernel may give you sligthly better performance, but this is not always true. The biggest benefit in using linux-lowlatency is that it's in harmony with linux-generic. It has the same source, just with a different configuration. And, it's getting continuous security updates.

Hope that answers your question.

---

### Post by cub on 2013-05-01
> **zequence said:**
> The only benefit you get with either of those kernels is you can get lower latency without audio dropouts, which is only important if you're doing something live, like playing midi keyboard and using soft synth sounds, or monitoring what you are recording live.
I would say that is the most important part for using Ubuntu Studio if you are going to record any music.

But for just playing audio files there's no need for a special kernel.

---

### Post by zequence on 2013-05-01
> **cub said:**
> I would say that is the most important part for using Ubuntu Studio if you are going to record any music.

But for just playing audio files there's no need for a special kernel.

It's not important for recording either. You can have a very large latency setting for recording. Low latency is only important if you are doing something live. Such as live monitoring of recording sources - but it is always preferable to do monitoring outside of the computer.

---

### Post by forkenbrock on 2013-05-02
> **zequence said:**
> Kernels don't improve audio quality, so you should probably just stick with the generic kernel. Nothing in your computer really does, except for the audio card you use. And, the difference between those is so small nowadays, that probably few human ears would notice the difference on a consumer system setup.

The reason I'm delving into Linux is I have a company that sells audio equipment and I'm trying to develop a new server with a Linux OS (in addition to Windows).  We're not talking about sound cards and typical consumer electronics, these are state-of-the-art digital converters.  I've been building Windows servers for a few years and lowering latency, through the hardware and OS, certainly improves sound quality on gear that precise enough to take advantage of it.  I don't know whether a kernel patch can be heard with playback, but that's what I intend to find out.  Unfortunately, if it does, DAC manufacturers don't develop proprietary USB drivers for Linux.

Thanks for pointing out the Wiki.  I'll read that.

---

### Post by cub on 2013-05-02
> **zequence said:**
> It's not important for recording either. You can have a very large latency setting for recording. Low latency is only important if you are doing something live. Such as live monitoring of recording sources - but it is always preferable to do monitoring outside of the computer.
I think we sort of agree. I'm not talking about live performance though or recording everything in one take. When you are doing multitrack recording and adding a new instrument or track you need to be able to hear what's already been recorded (which is then played back by Ubuntu Studio) as well as what you are playing that very instant. If the latency is too big the music will not sound tight (depending on the musician of course).

---

### Post by zequence on 2013-05-02
> **forkenbrock said:**
> I've been building Windows servers for a few years and lowering latency, through the hardware and OS, certainly improves sound quality on gear that precise enough to take advantage of it.  I don't know whether a kernel patch can be heard with playback, but that's what I intend to find out. 

The reason why there is no difference in sound quality between one kernel compared to another is that audio is represented by a long series of zeros and ones - and the order in which the bits end up (bits are zeros or ones), or the timing in which they are played through the sound card is no different between the kernels. It's exactly the same, no matter if it's a generic, lowlatency or a rt kernel.

The only difference you get with a low latency capable kernel is that you can use a smaller buffer without there being audio dropouts. Meaning, you can use a smaller latency. Usually with linux-lowlatency, you'll be able to use less than 10ms, while not on linux-generic. There's some information on audio latency here [http://en.wikipedia.org/wiki/Latency_%28audio%29](http://en.wikipedia.org/wiki/Latency_%28audio%29)
What latency in this context generally means is the time it takes for audio to pass through the computer, from the audio input to the audio output.

---

### Post by zequence on 2013-05-02
> **cub said:**
> I think we sort of agree. I'm not talking about live performance though or recording everything in one take. When you are doing multitrack recording and adding a new instrument or track you need to be able to hear what's already been recorded (which is then played back by Ubuntu Studio) as well as what you are playing that very instant. If the latency is too big the music will not sound tight (depending on the musician of course).

First of all, live monitoring is not the same as recording a live session. 

I'm specifically saying that the only reason you need low latency is when you need to do live monitoring, which is what you now describe (and didn't before), or you any other kind of live processing, such as using the PC as a controllable synth, sampler, or a guitar FX box.

There will always be a small amount of latency when using the computer to monitor your recording though, which is why it is always preferred to use an external mixer, as you get zero latency with a hardware monitoring system.
The latency will not affect the actual recording, but it will affect how you as a musician hear yourself in context with the background music being played from the computer, so how you do monitoring is only interesting from a musicians point of view.

The application makes up for the latency, since it's aware of the exact latency you use. So, if you use a very large latency, and use external equiptment for monitoring your input sound, this will not affect the timing of the recording at all, and it will give you zero monitoring latency, which is great from the musicians point of view.

---

### Post by forkenbrock on 2013-05-03
> **zequence said:**
> The reason why there is no difference in sound quality between one kernel compared to another is that audio is represented by a long series of zeros and ones - and the order in which the bits end up (bits are zeros or ones), or the timing in which they are played through the sound card is no different between the kernels. It's exactly the same, no matter if it's a generic, lowlatency or a rt kernel.

There would be no difference if we're just talking about changing the size of the buffer, but RT has to do with interruptions of the clock schedule...the precision of the buffer.  The computer and DAC clocks are supposed to be synced, but they're never perfect.  Each time the computer sends a payload of data, a sample, the DAC has to take a snap shot and read it in real time.  Think of a roller coaster that takes a picture of the car as it comes out of the tunnel; take the picture too soon and the back is still in the tunnel or too late and the front is passed the camera.  This difference in expected timing is called jitter, which is measured in pico seconds (billionths of a second).  Lower jitter rates result in better sound quality with gear that's capable of taking advantage of it.  Lower latency results in better sound quality only in the sense that it seems to coincide with a lower rate of jitter.

---

### Post by zequence on 2013-05-03
> **forkenbrock said:**
> There would be no difference if we're just talking about changing the size of the buffer, but RT has to do with interruptions of the clock schedule...the precision of the buffer.  The computer and DAC clocks are supposed to be synced, but they're never perfect.  Each time the computer sends a payload of data, a sample, the DAC has to take a snap shot and read it in real time.  Think of a roller coaster that takes a picture of the car as it comes out of the tunnel; take the picture too soon and the back is still in the tunnel or too late and the front is passed the camera.  This difference in expected timing is called jitter, which is measured in pico seconds (billionths of a second).  Lower jitter rates result in better sound quality with gear that's capable of taking advantage of it.  Lower latency results in better sound quality only in the sense that it seems to coincide with a lower rate of jitter.

And you can measure this jitter, how?

If you want hard realtime, you need a realtime kernel. 
If you need higher resolution for your kernel timer, read this [http://kerneltrap.org/node/6750](http://kerneltrap.org/node/6750)

linux-lowlatency is configured like a realtime kernel, but lacks the -rt patch, which would give it hard realtime preempt capability.

I can't say I know the details of what the variables are in the system, concerning the reliability of the sync between CPU clock, RAM, and various peripherals, but I'm not at all sure that realtime will improve sync on that level.
If you believe this to be true, could you point me to some documentation on that?

From my understanding, the only jitter that realtime reduces, is the jitter in how accurately processes are scheduled.

---

### Post by forkenbrock on 2013-05-03
This is all just theory about how to lower jitter and something I want to try.  There is a jitter measurement test with XP over on the Cicsmemory site.  Lowering latency with Windows can produce worthwhile improvements in sound, but with Linux it's easier for me to just try it and see if I like the results.  There probably isn't any jitter measurements or documentation out there.

---

