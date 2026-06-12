---
title: "check what's using soundcard?"
date: 2008-10-20
forum: Ubuntu Studio
---

### Post by tacticalbread on 2008-10-20
is there a way to see what applications are using your soundcard?

whenever I start up LMMS it tells me:

```
No audio-driver working - falling back to dummy-audio-driver
You can render your songs and listen to the output files...
```

before, I would close Soundbird, it would work, but it won't work now.

---

### Post by tacticalbread on 2008-10-21
anyone?

---

### Post by tacticalbread on 2008-10-22
bump.

---

### Post by fjf on 2008-10-22
padevchooser-->volume control-->playback will tell you.

---

### Post by zenith001 on 2008-10-23
[Crusher](http://www.crusher.south.am)[Jaw Crusher](http://www.crusher.south.am/Crushing-Equipment/Crusher/Jaw-Crusher/Jaw-Crusher.html)[Cone Crusher](http://www.crusher.south.am/Crushing-Equipment/Crusher/Cone-Crusher/Cone-Crusher.html)[Cone Crusher](http://www.crusher.south.am/Crushing-Equipment/Crusher/HPC-Cone-Crusher/HPC-Cone-Crusher.html)[Impact Crusher](http://www.crusher.south.am/Crushing-Equipment/Crusher/Impact-Crusher/Impact-Crusher.html)

---

### Post by tacticalbread on 2008-10-24
thanks, I just tried that.

It told me "No streams available." so I tried LMMS again, but I still get the same error.

---

### Post by fjf on 2008-10-24
Did you set pulseaudio as sound server in system-->preferences-->sound?.  You can also test it.  Did you right click on the volume control (upperpanel, right) to see what card are you using?.  You can then double-click on it and go files-->change device and play with them.

---

### Post by Stochastic on 2008-10-24
A few questions pop into my head...

What sound server is lmms set to output to in its preferences?  Do you have Firefox open while you're trying to run lmms (quite often if firefox was used to view a flash object, it won't relinquish alsa/pulse audio control afterward, and you'll need to close the browser)?  Have you tried using jack as the sound server for lmms?

---

### Post by tacticalbread on 2008-10-24
> **Stochastic said:**
> What sound server is lmms set to output to in its preferences?

when I run LMMS through the terminal it gives me the error I previously mentioned, and when LMMS starts, it shows the Audio Preferences option, I choose a sound server, it tells me changes won't be applied until I restart LMMS, so I do that, and it happens again, everytime.

> **Stochastic said:**
> 

I've tried closing firefox, and I've tried shutting down, and rebooting, and starting LMMS straight away, and I still get the same thing.

and the only startup programs I have are:
Check for new hardware drivers
Compiz Fusion Iocn
Gmail Notifier
Network Manager
Power Manager
Update Notifier
User folders update
and Volume Manager.

[QUOTE=Stochastic;6025954]Have you tried using jack as the sound server for lmms?

I've tried all of them.

---

### Post by tacticalbread on 2008-10-27
still can't get it working.

---

### Post by luctor on 2008-10-27
Maybe you can try this :

1) shut down pulseaudio 
```
killall pulseaudio 
```
check if its still running ..
```
ps aux | grep pulseaudio
```
sometimes killall doesn't work at my box .. dunno why, could be an intrepid beta thing. If it's still running I usually kill it with the gnome-system-monitor.

2) Start qjackctl (if you don't have installed, do so, it's in the repos) and start jack
3) in LMMS, choose jack as the audio server.

the lmms in the repos is version 0.3
there's a rc 0.4 out with pulseaudio support :
[http://lmms.sourceforge.net/wiki/index.php?title=Roadmap](http://lmms.sourceforge.net/wiki/index.php?title=Roadmap)

---

### Post by thorgal on 2008-10-27
to kill pulseaudio, pulseaudio came with a command line option :

```

pulseaudio -k

```

---

### Post by luctor on 2008-10-27
> **thorgal said:**
> to kill pulseaudio, pulseaudio came with a command line option :

```

pulseaudio -k

```

thanks ! didn't know that

---

### Post by tacticalbread on 2008-10-27
> **thorgal said:**
> to kill pulseaudio, pulseaudio came with a command line option :

```

pulseaudio -k

```

didn't change anything, I still get the same error.

---

### Post by luctor on 2008-10-28
> **tacticalbread said:**
> didn't change anything, I still get the same error.

Just to clarify : Did you start the jack audio server ?
Starting qjackctl doesn't start the jackd server, you'll have to click on .. well .. start :-)

---

### Post by tacticalbread on 2008-10-30
well, that got LMMS sound working, but all samples are really choppy. I know the quality of the samples is fine, so it's a problem with LMMS, or Jack.

---

### Post by thorgal on 2008-10-30
almost sure it's your jack setting.
In qjackctl, activate the message window and my bet is that you have tons of xruns, spitted very often.

you have to tweak your jack setting for an xrun free experience.
And this depends a lot on your hardware and OS configuration.

Make a screenshot of the qjackctl setup window and post it here. Describe your hardware as well : type lspci in a terminal and post the output here as well.

---

