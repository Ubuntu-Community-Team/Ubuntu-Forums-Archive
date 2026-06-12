---
title: "Can't run jack while pulseaudio is installed"
date: 2010-07-26
forum: Ubuntu Studio
---

### Post by Nidding on 2010-07-26
I'm trying to get a DAW up and running but have run into an issue. I have some trouble getting Jack to start. At first the trouble seemed to have something to do with the server, but after changing the interface to hw:1 (an usb soundcard) it seems to get past the server issue. But now it just seems to stall completely while starting up. I've gotten around this by uninstalling pulseaudio, which (amongst others I guess) disables sound from firefox. Is there any way to be able to both make music and surf without having to install and remove pulseaudio in between?

---

### Post by AutoStatic on 2010-07-27
Hello Nidding, how do you start up JACK?

---

### Post by Nidding on 2010-07-28
I open it from the applications menu. I've tried to 'sudo qjackctl', which seems to let it start, but then ardour won't open correctly (and it seems to shut down other apps as well, like firefox).

---

### Post by JC Cheloven on 2010-08-01
> **Nidding said:**
> I've gotten around this by uninstalling pulseaudio, (...)

Did you actually uninstalled pulse in lucid? Or you rather disable/enable it by "pulseaudio -k"/"pulseaudio -D"?

Assuming it's the latter: Unisntalling pulse has become tricky since karmic. I succesfully did it in karmic following [instructions here]("http://ubuntuforums.org/showthread.php?t=1313253") (posts #3 and #4), but didn't try in lucid. I tell you just in case you're actually interested in uninstalling pulse.

In my current lucid installation, which has pulse, I can't get sound from both firefox and jack (firewire driver) at the same time. If FF is running, jack won't start. If jack is running, FF won't have sound. I got used to that, and thought it was normal. To sum up, I'm unsure whether having concurrent pulse & jack would solve your problem or not (I'd say not).

---

### Post by Nidding on 2010-08-03
Actually I have just used "sudo apt-get remove pulseaudio", and thought that it uninstalled pulse. I can only start Jack up after running the command, and am only able to get sound from firefox after running "sudo apt-get install pulseaudio". Though a minor inconvenience, it would be nice to get a way around that.

[Off topic]It seems as though I will have to make a dual boot with xp anyway, as Ardour seems WAY too unstable for my needs. For instance playing/recording speeds seems to vary at random, so when I record in sync at one place in my song, and move it to another place, it's no longer in sync (at times it's grave enogh to notice during playback). I can't tell if it's due to Ardour or a hardware issue, but as I haven't experienced it before, I tend to think it's an Ardour thing. How anyone can live with this is a puzzle to me[/Off topic]

---

### Post by AutoStatic on 2010-08-03
> **Nidding said:**
> Actually I have just used "sudo apt-get remove pulseaudio", and thought that it uninstalled pulse. I can only start Jack up after running the command, and am only able to get sound from firefox after running "sudo apt-get install pulseaudio". Though a minor inconvenience, it would be nice to get a way around that.Then try creating the file */home/yourusername/.pulse/client.conf* with a single line in it:
```
autospawn = 0
```

Then open QjackCtl, select Setup and then the Options tab and replace 'artsshell -q terminate' with 'pulseaudio -k' and tick the 'Execute script on Shutdown' option and enter 'pulseaudio -D' there.

This will kill PulseAudio when you start QjackCtl and prevent PulseAudio from automatically respawning. And as soon as you quit QjackCtl PulseAudio will be started as a daemon again.

---

### Post by cchhrriiss121212 on 2010-08-03
> **Nidding said:**
> 
[Off topic]It seems as though I will have to make a dual boot with xp anyway, as Ardour seems WAY too unstable for my needs. For instance playing/recording speeds seems to vary at random, so when I record in sync at one place in my song, and move it to another place, it's no longer in sync (at times it's grave enogh to notice during playback). I can't tell if it's due to Ardour or a hardware issue, but as I haven't experienced it before, I tend to think it's an Ardour thing. How anyone can live with this is a puzzle to me[/Off topic]
I don't think anyone lives with that kind of performance ;), what kind of latency value do you have with jack?

---

### Post by JC Cheloven on 2010-08-06
> **Nidding said:**
> Actually I have just used "sudo apt-get remove pulseaudio", and thought that it uninstalled pulse. (...) ]
That was brave enough! Several things will stop working in your system if pulse is removed that way. You should replace the functionality it gives to other programs (using gstreamer...) in a way similar as I suggested in post #4. 

If pulse is getting in your way, you may consider using a distro without pulse, as xubuntu or lubuntu.

The pulseaudio -k /-D method should suffice for your case, though.

---

### Post by chaanakya_chiraag on 2010-08-23
If you install the Jack modules for pulseaudio, you can have pulse play through Jack by using ```
pactl load-module module-jack-source
pactl load-module module-jack-sink
``` and going into pavucontrol (install it if you don't have it) and setting the Jack sink and source as defaults.

---

### Post by dewdrop_world on 2010-09-24
paman rather than pavucontrol, right?

Otherwise, holy cr@p, this seems to be working! I've been looking for this for WEEKS.

Thank you!!!

---

### Post by chaanakya_chiraag on 2010-09-24
I guess...I use pavucontrol, but use whatever works for you.  No problem!  If it's solved, please mark this thread as solved by going to Thread Tools -> Mark Thread as Solved.  Thanks :)

---

