---
title: "How can i connect JACK and PulseAudio without messing around with packages?"
date: 2011-05-26
forum: Ubuntu Studio
---

### Post by FQ`9 on 2011-05-26
Hi, i want to connect JACK and PulseAudio together, to prevent QjackCtl muting PulseAudio

How can i do this, without messing with packages?

---

### Post by Pablo_F on 2011-05-26
[https://help.ubuntu.com/community/UbuntuStudioPreparation#PulseAudio%20and%20Jack](https://help.ubuntu.com/community/UbuntuStudioPreparation#PulseAudio%20and%20Jack)

---

### Post by FQ`9 on 2011-05-27
The Solution isn't working

---

### Post by Pablo_F on 2011-05-27
Can you elaborate? What did you exactly do and please describe a test case.  

Or join the IRC channel at: 

[http://webchat.freenode.net/?channels=ubuntustudio](http://webchat.freenode.net/?channels=ubuntustudio)

---

### Post by PelleK on 2011-05-30
cadence in kxstudio has a pulse-jack bridge that gives you a 'pulse audio jack sink' audio output in qjackctl. it works very well.

---

### Post by FQ`9 on 2011-08-22
> **PelleK said:**
> cadence in kxstudio has a pulse-jack bridge that gives you a 'pulse audio jack sink' audio output in qjackctl. it works very well.

^ that was not what i needed

---

### Post by madeinfamous on 2011-08-22
allo FQ`9!

Pablo_F has given you the answer!

```
sudo apt-get install pulseaudio-module-jack
```

then... after installing pulseaudio-module-jack, instead of opening a terminal...

do this in jack:

[https://sites.google.com/site/nueusx/jack-pulse.png](https://sites.google.com/site/nueusx/jack-pulse.png)

script after start:

```
pacmd load-module module-jack-source channels=2; pacmd load-module module-jack-sink channels=2;
```

You can change if necessary the number of audio channels by changing the number "2".

script after closing jack (to restart pulseaudio):

```
pulseaudio -k
```

cheer's

have a nice week!

:)


edit: oh... I almost forgot...

you also need to go in sound preference to select jack source...

[https://sites.google.com/site/nueusx/jacksource.png](https://sites.google.com/site/nueusx/jacksource.png)

;)

---

### Post by FQ`9 on 2011-08-22
can it work with non ubuntu distros?

---

### Post by madeinfamous on 2011-08-22
allo FQ`9!

why not!?! :)

you need to give more info!?! if I can't answer someone will do!

there's also another way to do it after installing pulseaudio-module-jack,

you need to edit:  etc/pulse/default.pa

and write this in it:

```
load-module module-jack-sink
load-module module-jack-source
```

just like this:

```
### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-udev-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink
load-module module-jack-sink
load-module module-jack-source
```

that way, jack start automatically with pulseaudio, @ login

but I don't like it, I don't see my hardware!

:)

---

### Post by linkx on 2012-11-29
@madeinfamous: 

Thank you so much! I have wanted this for a long time, your suggestion worked perfectly and was really straightforward. 

Cheers, 

Link

---

### Post by overdrank on 2012-11-29
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

