---
title: "Gutsy? New Soundcard? or Pulse Audio removal..."
date: 2008-05-19
forum: Ubuntu Studio
---

### Post by wadelewis4 on 2008-05-19
I am determined to get a multimedia studio up and running out of my favorite distro - ubuntu (duh). I mean seriously, I will find a way to get this done (hopefully through this thread). 

Problem? 

I hate Pulse Audio. I have had nothing but problems with it - it's a flaky mess. Besides the fact that it is making recording impossible, I can't even play a song in Rhythmbox and watch a flash video on youtube at the same time - it's like two attention-starved apps are fighting over my audio hardware. This did not happen when I was using Gutsy. I could simultaneously enjoy audio from multiple applications without hiccup. So what's the deal now? 

Someone out there must be having similar issues - it can't just be me. 

I want to record in a multitrack setting (Ardour, Rosegarden, Jokosher, etc). I want to be able to use multiple entertainment application and get audio from all of them. So, What exactly should I do? 

1) Install Gutsy and wait until Hardy is ready.
2) Somehow blame it on my audio hardware and just buy some new stuff?

OR

3) Find a way to remove Pulse Audio?

Which, if any of those, would you suggest? Would you have any other options in mind?

Please, let me know. 

Thanks

---

### Post by thorgal on 2008-05-19
not a ubuntu user myself (debian sid)but I have been fiddling around PA a while ago. I don't know which version is shipped with hardy but it was not mature at the time I was trying it.

But anyways, you have to be aware of one thing that will never change :

ardour, rosegarden and others (pro music prod apps) are using and will continue using jackd as the audio server. Pulseaudio is more for desktop usage, an all in one environment for generic purposes. It can be tuned so that jack or alsa apps can use it but it requires some tweaking. I could have PA work with jack for example but in my case, using netjack ends up doing what I wanted (LAN client-server operations for audio data).

Conerning your issues, I cannot really help you, just wanted to mention the jackd side of things because you mentioned ardour and rosegarden. From what I hear since 8.04 was released is that it's been the least smooth ubuntu release on this side of the galaxy ... of course, some ppl may have more positive experiences. I cannot say, I am just here to help from time to time since I am a music producer working with a linux based studio. It's my feedback to the community. Sorry I could not be of more help.


by the way, how about turning off PA ? in a terminal, just type : pulseaudio -k
it will kill any PA daemon. I guess your audio will fall back to the lower level which is ALSA (default in previous ubuntu versions).

---

### Post by Stochastic on 2008-05-19
Have you looked at this thread: [http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)

It seems to have fixed a number of pulse audio issues for people.

---

