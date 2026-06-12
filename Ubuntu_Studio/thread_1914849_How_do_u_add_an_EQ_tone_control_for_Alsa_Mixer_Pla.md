---
title: "How do u add an EQ /tone control for Alsa Mixer Playback?"
date: 2012-01-25
forum: Ubuntu Studio
---

### Post by nazaroo2 on 2012-01-25
While I have to put up with playback through the onboard soundcard
on my DELL Optiplex 330, is there any way I can install an (software) EQ or tone control?
The harshness of the computer playback is driving me nuts. :o

:guitar:

---

### Post by sanderd17 on 2012-01-25
You could use alsaequal I guess: [https://launchpad.net/ubuntu/+source/alsaequal](https://launchpad.net/ubuntu/+source/alsaequal)

it's in the repos.

---

### Post by nazaroo2 on 2012-01-25
> **sanderd17 said:**
> You could use alsaequal I guess: [https://launchpad.net/ubuntu/+source/alsaequal](https://launchpad.net/ubuntu/+source/alsaequal)

it's in the repos.

Hi thanks.
I ran the .deb pkg and it says its already installed!@

But I can't find an EQ on the pulldown menus anywhere.
What am I missing? 
Do I need to put it in the bootup or something?
Where would the controls show up?

---

### Post by sanderd17 on 2012-01-25
I'm not really into sound configuration, so maybe this can help you: [http://www.thedigitalmachine.net/alsaequal.html](http://www.thedigitalmachine.net/alsaequal.html)

Check out the "usage" section, and the extra links below.

---

### Post by nazaroo2 on 2012-01-25
> **sanderd17 said:**
> I'm not really into sound configuration, so maybe this can help you: [http://www.thedigitalmachine.net/alsaequal.html](http://www.thedigitalmachine.net/alsaequal.html)

Check out the "usage" section, and the extra links below.

I'm still clueless here.

I've got Gnome Alsamixer appearing,
and I managed to get "Alsamixer v1." to appear.
They look totally different, and neither shows any EQ options.

...I'm afraid to just run random terminal commands. 
When I started one of those, I got an error message.
I know "Equal" is already installed, but it doesn't show up on the menus anywhere,
and when I run the command in a terminal nothing happens.

---

### Post by sanderd17 on 2012-01-25
I'm using pulseaudio now, so I can't really test it. But if you use
```

alsamixer

```

don't you get an equalizer?

---

### Post by nazaroo2 on 2012-01-25
> **sanderd17 said:**
> I'm using pulseaudio now, so I can't really test it. But if you use
```

alsamixer

```don't you get an equalizer?

Thanks for replying.

I can open a terminal, and run alsamixer. 
Then a small window opens, and it looks like this:

[IMG]http://4.bp.blogspot.com/-_dcXZha5WNM/TyC85Ya3pyI/AAAAAAAAAvs/f1ZFeEUxuhg/s640/alsamixer1.png[/IMG]

But I cannot see any equalizer that I recognize.  
Maybe I'm missing something, but these all look like various volume controls,
the same as the Gnome Mixer has.

Any ideas?

---

### Post by sanderd17 on 2012-01-26
[https://bbs.archlinux.org/viewtopic.php?id=53139](https://bbs.archlinux.org/viewtopic.php?id=53139)

it should be possible, look at the screenshot. But I don't have hints for you.

---

### Post by jejeman on 2012-01-26
On the screenshot one can see that the display is changed to "Eq" card. Press F6 and change card to Eq.

---

### Post by nazaroo2 on 2012-01-26
okay now we are getting somewhere:

I got F6: Select sound card on upper right.

I press it and get a popup window navigatable with arrow keys.
It was on (default),  I moved it to 0 HDA Intel.
This made no difference.

I tried typing in "Equal" <Enter>
and got 'Cannot open mixer device 'Equal'. No such file or directory [new box]
Makes no difference if I capitalize "equal".  (also tried "Eq" and "Eq." as you typed literally)

what next?

---

### Post by nazaroo2 on 2012-01-26
On the other hand, I may be going about this wrong:
Is there any other EQ system I could use, that might go in easier?
For instance, even a good software stereo parametric EQ would be more than adequate.

---

### Post by jejeman on 2012-01-26
Probably you didn't setup alsaequal right. I don't use this so I can't help.
I don't know what do you want to achive, but audio players have their builtin eq. For example Audacious. You can use that.

---

### Post by nazaroo2 on 2012-01-26
> **jejeman said:**
> Probably you didn't setup alsaequal right. I don't use this so I can't help.
I don't know what do you want to achive, but audio players have their builtin eq. For example Audacious. You can use that.

hmmm. okay.
Well, what I wanted was to record some stuff, 
using Ardour, and play it back through my computer audio out.
But then EQ the sound better just before it went out.
Maybe there is an EQ system I can use in the LMMS...

---

### Post by jejeman on 2012-01-26
Play it from Ardour, or export and then play it?

For first, why you just don't do eq in ardour? You can e.g. route all track to single bus and apply eq to it.

For second use player with eq.

---

### Post by nazaroo2 on 2012-01-26
> **jejeman said:**
> Play it from Ardour, or export and then play it?

For first, why you just don't do eq in ardour? You can e.g. route all track to single bus and apply eq to it.

For second use player with eq.

First, now Ardour doesn't work... see my other thread...

Second, I don't want to have to keep setting it up and turning it on, 
and I want it to always be on, even when I'm not running JACK or Linux Studio.

That is, it should be in the chain when I boot up, and the EQ should be set to where I last left it when I play an mp3 or watch youtube.

---

### Post by jejeman on 2012-01-26
Well, than, you can when using pulseaudio (mp3, youtube all audio without jack) setup a pulseaudio eq.
[http://exploreubuntu.wordpress.com/2010/04/18/equalizer-for-pulse-audio/](http://exploreubuntu.wordpress.com/2010/04/18/equalizer-for-pulse-audio/)

When using jack, you need to add eq to the audio chain, or manage alsaequal to work. If you do that, I belive that you don't even need pulseaudio eq.

This is just me thinking outloud, i don't use any eq on my system.

---

### Post by nazaroo2 on 2012-01-27
Looks like I might have to give up on the idea of a system playback EQ in software.
I think I just might as well take the outputs from computer to an external EQ,
which will probably sound a whole lot better IMHO...

---

