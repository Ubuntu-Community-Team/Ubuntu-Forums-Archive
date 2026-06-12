---
title: "advice\suggestions needed - midi controller and playing the piano!"
date: 2009-02-13
forum: Ubuntu Studio
---

### Post by angelsneverdie on 2009-02-13
Hello everyone.

So i wanted to learn how to play the piano and I found a midi controller keyboard that I like (m-audio keystation 88es) that is affordable.

but i am completely new to all this,  i've never messed around with audio on the computer.  All i really want to do is be able to hook up the keyboard to the computer and play it like a piano.  is there good reliable software out there that will allow me to do this?  

is it user friendly enough that a noob like me could set it up?  I want to make sure that this will work before i buy the keyboard!

thanks for any suggestions you may have.

---

### Post by dox_drum on 2009-02-13
Have to try to look up a package in Synaptic?

---

### Post by angelsneverdie on 2009-02-13
i'm so new to this i wouldn't even know what to look for.

---

### Post by dox_drum on 2009-02-13
> **angelsneverdie said:**
> i'm so new to this i wouldn't even know what to look for.

Go to System --> Administration --> Synaptic Package Manager 
Use the Administrator password (if you are the only user of the computer, should be your own)

Use the search bar for looking up for packages... 

I just type **piano** and a package called **rosegarden** appears. It is not a canonical package, so you should add the community repository.

[INDENT]For the sake of completeness: (Adding extra repositories)

Go to System --> Administration --> Software Sources

In the Ubuntu Software Tab, check all the possibilities (or those you please)

In the Update Tab, check all possibilities but Pre-released updates (that my personal choice)

If you have added another repository (using either this or another method), it should appear in the Third-Party Software Tab, you may just chack they are enable.

Make sure of update your repositories when the windows is closing.

Finally you should open a konsole (or favourite terminal) and do

```
sudo apt-get update
sudo apt-get install rosegarden
``` 

The second line will install the rosegarden program. [COLOR="Red"]**NOTE** that I've never used the program (don't know either if it works for your will), but is an example of the possible package you could find[/COLOR][/INDENT]

[CENTER]Enjoy![/CENTER]

---

### Post by angelsneverdie on 2009-02-13
> **dox_drum said:**
> Go to System --> Administration --> Synaptic Package Manager 
Use the Administrator password (if you are the only user of the computer, should be your own)

Use the search bar for looking up for packages... 

I just type **piano** and a package called **rosegarden** appears. It is not a canonical package, so you should add the community repository.

[INDENT]For the sake of completeness: (Adding extra repositories)

Go to System --> Administration --> Software Sources

In the Ubuntu Software Tab, check all the possibilities (or those you please)

In the Update Tab, check all possibilities but Pre-released updates (that my personal choice)

If you have added another repository (using either this or another method), it should appear in the Third-Party Software Tab, you may just chack they are enable.

Make sure of update your repositories when the windows is closing.

Finally you should open a konsole (or favourite terminal) and do

```
sudo apt-get update
sudo apt-get install rosegarden
``` 

The second line will install the rosegarden program. [COLOR="Red"]**NOTE** that I've never used the program (don't know either if it works for your will), but is an example of the possible package you could find[/COLOR][/INDENT]

[CENTER]Enjoy![/CENTER]

Thanks for the response (and the completeness of the response, i appreciate it).  I'll try that out when I get home.  Does anyone know of any programs that are really simple?  i really don't need to be able to do anything other than press a key and have it make the appropriate sound.

---

### Post by dox_drum on 2009-02-13
> **angelsneverdie said:**
> Thanks for the response (and the completeness of the response, i appreciate it).  I'll try that out when I get home.  Does anyone know of any programs that are really simple?  i really don't need to be able to do anything other than press a key and have it make the appropriate sound.

You are welcome!

I encourage you to try several items... just looking around synaptic.

---

### Post by thorgal on 2009-02-13
you need a so-called softsynth. Rosegarden is different, it's a sequencer, where you can record your MIDI input (from the keyboard), and connect the MIDI playback to a softsynth which will be triggered to produce the appropriate sound, according to the MIDI note being played back. 

Rosegarden works with the audio server jack for playback transport and its audio handling. But it uses ALSA by default for its MIDI interface. It can be a little bit hard to set this all up. But some softsynth apps may not use jack for the audio output so we can do without all this first. 

In fact, I would say that if all you want is to have a sound triggered as you strike a key, you don't need rosegarden at all. You need a softsynth that can play some piano sounds or more weird sounds if that's what you're after. There are many softsynths, some good some bad. Something like 'fluidsynth' might be more appropriate in your case, with its GUI called qsynth. You can load sound fonts (sf2 format) and I read here and there that you can find some decent piano sf2 fonts (look in [http://www.hammersound.net/hs_soundfonts.html#Melodic_instruments](http://www.hammersound.net/hs_soundfonts.html#Melodic_instruments) for sound fonts).

Let's get started:
install qsynth (from the terminal):
```

sudo apt-get install qsynth

```
say yes to extra packages to be downloaded.

Now fire up qsynth from the terminal:

```

qsynth -a alsa

```

the '-a alsa' is to tell qsynth to use ALSA as the audio driver (to use the jack audio server instead, use '-a jack' but that's a more complicated setup).

Now go to hammersound.com, get a piano sound font (sf2 file), download it to some directory of your choice. Now, in qsynth, click on 'Setup...' and check the sound font tab. Click on 'Open' and navigate to where you downloaded your soundfont. Select it and click 'OK'.

Now, install qjackctl:
```

sudo apt-get install qjackctl

```
say yes to extra packages (jack and stuff).

Fire up qjackctl from the terminal
```

qjackctl

```

don't attempt to start the audio server jack. That's for a more advanced time ...

Click on the 'Connect' button.
You have a window showing up. You will see a tab called ALSA. If your keyboard is driven by ALSA, you will see it in the connection window to the left. In the right hand side window, you will see Fluidsynth. What you want then is to connect the keyboard (left connection window) to qsynth (right window connection). For that, highlight both of them by clicking on them once, then click on the Connect button.

Play on your keyboard, you should hear something.


Here is a snapshot (I don't have a keyboard connected to my laptop, so I used the MIDI through client as a substitute for the sake of explanation, but I can also start a software keyboard like vkeybd and use it instead by pressing my laptop keys) :

[IMG]http://img6.imageshack.us/img6/4515/midiconnect1gy5.jpg[/IMG]

You can tweak the audio setting in qsynth : click on 'Setup ...' and go to the audio tab. You can increase the buffer size if you notice some glitches (audio card not coping with the small buffer size). But the bigger the buffer, the higher the latency (time between your key action and the sound heard from your speakers).

I have a more comprehensive pic here (careful, imageshack sucks with stupid popups):

[[IMG]http://img525.imageshack.us/img525/9262/midiconnectkb2.th.jpg[/IMG]](http://img525.imageshack.us/my.php?image=midiconnectkb2.jpg)

---

### Post by angelsneverdie on 2009-02-13
Wow - thanks for the help, i can't wait to try it out!  I should be getting my keyboard in the mail next week.

---

### Post by angelsneverdie on 2009-02-13
> **thorgal said:**
> you need a so-called softsynth. Rosegarden is different, it's a sequencer, where you can record your MIDI input (from the keyboard), and connect the MIDI playback to a softsynth which will be triggered to produce the appropriate sound, according to the MIDI note being played back. 

Rosegarden works with the audio server jack for playback transport and its audio handling. But it uses ALSA by default for its MIDI interface. It can be a little bit hard to set this all up. But some softsynth apps may not use jack for the audio output so we can do without all this first. 

In fact, I would say that if all you want is to have a sound triggered as you strike a key, you don't need rosegarden at all. You need a softsynth that can play some piano sounds or more weird sounds if that's what you're after. There are many softsynths, some good some bad. Something like 'fluidsynth' might be more appropriate in your case, with its GUI called qsynth. You can load sound fonts (sf2 format) and I read here and there that you can find some decent piano sf2 fonts (look in [http://www.hammersound.net/hs_soundfonts.html#Melodic_instruments](http://www.hammersound.net/hs_soundfonts.html#Melodic_instruments) for sound fonts).

Let's get started:
install qsynth (from the terminal):
```

sudo apt-get install qsynth

```
say yes to extra packages to be downloaded.

Now fire up qsynth from the terminal:

```

qsynth -a alsa

```

the '-a alsa' is to tell qsynth to use ALSA as the audio driver (to use the jack audio server instead, use '-a jack' but that's a more complicated setup).

Now go to hammersound.com, get a piano sound font (sf2 file), download it to some directory of your choice. Now, in qsynth, click on 'Setup...' and check the sound font tab. Click on 'Open' and navigate to where you downloaded your soundfont. Select it and click 'OK'.

Now, install qjackctl:
```

sudo apt-get install qjackctl

```
say yes to extra packages (jack and stuff).

Fire up qjackctl from the terminal
```

qjackctl

```

don't attempt to start the audio server jack. That's for a more advanced time ...

Click on the 'Connect' button.
You have a window showing up. You will see a tab called ALSA. If your keyboard is driven by ALSA, you will see it in the connection window to the left. In the right hand side window, you will see Fluidsynth. What you want then is to connect the keyboard (left connection window) to qsynth (right window connection). For that, highlight both of them by clicking on them once, then click on the Connect button.

Play on your keyboard, you should hear something.


Here is a snapshot (I don't have a keyboard connected to my laptop, so I used the MIDI through client as a substitute for the sake of explanation, but I can also start a software keyboard like vkeybd and use it instead by pressing my laptop keys) :

[IMG]http://img6.imageshack.us/img6/4515/midiconnect1gy5.jpg[/IMG]

You can tweak the audio setting in qsynth : click on 'Setup ...' and go to the audio tab. You can increase the buffer size if you notice some glitches (audio card not coping with the small buffer size). But the bigger the buffer, the higher the latency (time between your key action and the sound heard from your speakers).

I have a more comprehensive pic here (careful, imageshack sucks with stupid popups):

[[IMG]http://img525.imageshack.us/img525/9262/midiconnectkb2.th.jpg[/IMG]](http://img525.imageshack.us/my.php?image=midiconnectkb2.jpg)

the jack control thing doesn't really open - i  mean it opens, but then it is just there and does nothing, I have to force quit.  here's the output:
> mitchell@mitchell-laptop:~$ qjackctl
Warning: no locale found: /usr/share/locale/qjackctl_en_US.qm

and when i run qsynth:
> mitchell@mitchell-laptop:~$ qsynth -a alsa
Warning: no locale found: /usr/share/locale/qsynth_en_US.UTF-8.qm


qsynth seems to work fine until i select the soundfont to use, it says it needs to restart the engine, and when i say okay, it crashes.

any idea what i'm doing wrong?

---

### Post by angelsneverdie on 2009-02-16
So i just tried following all of the instructions on my desktop and i got it to work using a virtual keyboard - even though i get the same output in the terminal as i do on my laptop.

any idea why my laptop would be having trouble?

thanks in advance!

---

### Post by angelsneverdie on 2009-02-17
So i just completely wiped my laptop and installed ubuntu studio.

Now everything seems to work fine, BUT i've tried two different piano soundfonts and they both come out sounding just the same - like footsteps on wet cement stairs echoing through the stairwell with a little bit of distortion . . .

i feel like i'm close . . . can anyone get me through this?

---

### Post by esemns on 2009-02-27
I think you have to go to the setup in qsynth and set a bigger bufer size...

On the other hadn, does anyone knows how to record what I hear in qsynth into audacity or ardour?

---

### Post by thorgal on 2009-02-28
to record in ardour, you'll have to use the audio part of jackd. In my quick and dirty howto above, I told angelsneverdie to not use jackd's audio before he feels comfortable with some basic stuff. 

If you feel comfortable with jackd and qjackctl, then you need to start the jackd audio server in the main qjackctl window. I won't tell you which setting you must apply, it depends on your h/w and OS configuration. Google around to know more.  

OK, once you have jackd running, you will have to start qsynth with the jack driver instead of ALSA (see my previous posts in this thread).

once you get sound out of qsynth, you're in good shape. You then open ardour, create a new session if you want, and just create a stereo track. Click on the input button of the track mixer strip, disconnect whatever was connected by default (system:capture_x by default). Browse the track connection window and select the qsynth jack output ports. Close the track connection window. Arm the track for recording, press the big record button and start the transport. Play from your keyboard or MIDI sequencer. The qsynth audio will be recorded in the ardour track. If you had ardour in the "software monitoring" mode, you may hear qsynth sound twice because qsynth was probably directly connected to your system: playback_x jack ports. To avoid that, either disconnect qsynth's output ports from system: playback_x or switch the ardour monitoring mode to "hardware provides monitoring".

The key here is to get jackd up and running for audio. This is a little tricky the first time as you have to get familiar with the setting parameters (that will determine the latency, sample rate, etc).

---

