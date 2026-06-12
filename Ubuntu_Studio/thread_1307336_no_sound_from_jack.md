---
title: "no sound from jack?"
date: 2009-10-31
forum: Ubuntu Studio
---

### Post by NoxNoctis7 on 2009-10-31
I'm new to linux audio so please have patience with me.

here's the problem I'm having. Sound works fine, but then I run JACK Control, hit start, and it seems to be running. it says 'started' in yellow. But then there's no sound, from anything.

I run ardour. It gives me a warning that says:
Warning: your system has a limit for the maximum ammount of locked memory. This might cause ardour to run out of memory before your system runs out of memory. You can view the memory limit with 'ulimit -l' and it is normally controlled by '/etc/limits/control.conf'

so i click ok, import some audio, hit play. it seems to be playing. the volume meters are showing stuff. if i run Meterbridge, those needles are moving too. but no sound to my speakers. so i close ardour, stop jack, and then my sound is back(for non jack programs of course)

btw. when i run 'ulimit -l' the result i get is 64 .. is that the problem?

Any ideas what I might be doing wrong? Thanks in advance for any help

---

### Post by AutoStatic on 2009-10-31
Hello NoxNoctis7, you should check the 'Connect' and 'Messages' buttons in Qjackctl. In the 'Connect' window you can hook up audio applications to JACK and in the 'Messages' window you can check if JACK doesn't return any warnings or error messages. Did you also optimize your system for audio use? And what soundcard are you using? What are your current JACK settings, could you post a screenshot of the 'Setup' window of Qjackctl?

---

### Post by NoxNoctis7 on 2009-10-31
thanks very much for your reply.
I havn't done anything to the system yet, I just installed ubuntu studio for the first time yesterday. 

I don't know what soundcard I'm using, its built into the motherboard. if it helps, lspci says 
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)

(note: i dont expect it to sound good, i'm just playing with it while i wait for my new hardware)

When i look in the messages window of jack, these are the only things that look like warnings

 [COLOR=#999999]16:52:13.206 Startup script...[/COLOR]
 [COLOR=#990099]16:52:13.208 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]16:52:13.613 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]16:52:13.614 JACK is starting...[/COLOR]
 [COLOR=#990099]16:52:13.616 /usr/bin/jackd -R -dalsa -dhw:0 -r22050 -p1024 -n2 -S -Xraw[/COLOR]
 [COLOR=#999999]16:52:13.623 JACK was started with PID=2456.[/COLOR]
.... and then later
 JACK: unable to mlock() port buffers: Cannot allocate memory
 JACK: unable to mlock() port buffers: Cannot allocate memory
 **** alsa_pcm: [COLOR=#cc0000]xrun of at least 0.192 msecs[/COLOR]
 **** alsa_pcm: [COLOR=#cc0000]xrun of at least 0.097 msecs[/COLOR]
....(that last one repeats alot)

and finally here are some screenshots of the settings and connect windows
thanks again for any help or info

---

### Post by AutoStatic on 2009-11-01
Thanks for the info! You should use 441000 as the Sample Rate. Maybe even 48000, though I don't know what the optimal setting for AC97 chipsets is. HDA Intel prefers the latter sample rate. My old notebook (Asus A2H) has a SiS AC97 chipset but I never used it because I couldn't get it to work very well with JACK.
And what is that direct connection between the Ardour In and Out ports?

---

### Post by NoxNoctis7 on 2009-11-01
I don't know whats up with the connections, thats just how they were when i opened the window. I have changed them now, but still am having no luck. As for the setup page, it was originally at 44 and i set it to 22 hoping that would help things, but i'll set it back. 

Something I might not have made clear earlier is that when I activate jack, all of my sound stops, not just jack applications. 

Thanks much for your help so far. I'm going to keep poking at it and see if i can mess it up further :) if any ideas come to you, please let me know.

---

### Post by AutoStatic on 2009-11-02
> **NoxNoctis7 said:**
> I don't know whats up with the connections, thats just how they were when i opened the window. I have changed them now, but still am having no luck. As for the setup page, it was originally at 44 and i set it to 22 hoping that would help things, but i'll set it back.Ardour sets it up this way apparently. I don't use Ardour but I guess these initial connections are OK. And did you also try 48000 as the sample rate?

> **NoxNoctis7 said:**
> Something I might not have made clear earlier is that when I activate jack, all of my sound stops, not just jack applications.That's because JACK suspends PulseAudio, your default sound daemon. And because of the xruns JACK won't produce any sound either. Maybe you could post the output of the command **lspci | grep -i audio** in a terminal for the exact specs of your soundcard.

---

### Post by NoxNoctis7 on 2009-11-02
thanks for your patience with me and for explaining how things work.
I've tried 48000 as well, and it doesn't help.

when I run that command i get
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)

But at this point I think i'm ready to give up. My processor only runs a little faster than a gigahertz, so even if i get jack running its gonna sound terrible i'm sure. I'll just wait till I get my new system. thanks again though :)

---

### Post by AutoStatic on 2009-11-02
You're welcome! I'm going to check my own old notebook to see if I can get JACK running with the onboard SiS chipset, I think it has the same chipset.

---

### Post by trulan on 2009-11-02
Try changing the audio setting from 'duplex' to 'playback only'.  Some onboard cards just don't like to duplex with jack.

---

### Post by NoxNoctis7 on 2009-11-02
Playback only did the trick, I now have sound. Thanks much trulan. Still not quite what i was hoping for but half is better than none.

---

### Post by NoxNoctis7 on 2009-11-02
false alarm, the audio plays but at half speed.

---

