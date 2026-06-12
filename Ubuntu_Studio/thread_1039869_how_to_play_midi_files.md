---
title: "how to play midi files"
date: 2009-01-15
forum: Ubuntu Studio
---

### Post by oboedad55 on 2009-01-15
Can someone steer me the right direction so I can get midi files to play?

Thanks!

---

### Post by Cresho on 2009-01-15
timidity

---

### Post by Jormeliini on 2009-01-15
I like Fluidsynth. You'll need a Soundfont with it. There are plenty of Soundfonts available here [http://www.hammersound.net/](http://www.hammersound.net/). I have been using a Soundfont called Chorium. It is basically a General Midi set but there is something extra as well. You can find it in Hammersound.net / Sounds / Soundfont Library / Collections.

Playing a MIDI file with fluidsynt is simple.

```
fluidsynth -ni your_soundfont your_midi_file
```

Option n means "Don’t create a midi driver to read MIDI input events" and i "Don’t read commands from the shell". The purpose is just to play the file and not start a server.

---

### Post by oboedad55 on 2009-01-24
> **Jormeliini said:**
> I like Fluidsynth. You'll need a Soundfont with it. There are plenty of Soundfonts available here [http://www.hammersound.net/](http://www.hammersound.net/). I have been using a Soundfont called Chorium. It is basically a General Midi set but there is something extra as well. You can find it in Hammersound.net / Sounds / Soundfont Library / Collections.

Playing a MIDI file with fluidsynt is simple.

```
fluidsynth -ni your_soundfont your_midi_file
```

Option n means "Don&#8217;t create a midi driver to read MIDI input events" and i "Don&#8217;t read commands from the shell". The purpose is just to play the file and not start a server.

Sorry to be so dense. I've tried Qsynth and get an error "Failed to create the audio driver (jack). Cannot continue without it.
fluidsynth: error: Jack server not running?"
Also, the hammersound page is a porn site now.
Help!

Thanks,

---

### Post by Jormeliini on 2009-01-25
> **oboedad55 said:**
> Sorry to be so dense. I've tried Qsynth and get an error "Failed to create the audio driver (jack). Cannot continue without it.
fluidsynth: error: Jack server not running?"
Also, the hammersound page is a porn site now.
Help!
Thanks,

You're probably not running JACK server. Try starting QJackCtl and then starting Qsynth. An easier way is to run Qsynth with ALSA audio driver. You can select ALSA driver in Settings -> Audio tab. JACK is very handy when running multiple music applications at once since it lets you connect the inputs and outputs pretty much any way you want to. If your goal is just to play a MIDI file then you most likely don't need JACK.

Qsynth is just a graphical front-end to Fluidsynth. You'll need a soundfont to get any sound out of it.

I may be stupid but I can't figure out how to play a MIDI file with Qsynth. I've used Qsynth with Rosegarden and it works fine that way. I connect the MIDI output of the channels in Rosegarden to Qsynth and then play the MIDI file with Rosegarden. That's why I find way more simple to play a MIDI file with Fluidsynth using the Terminal. I use Rosegarden and Qsynth only when writing music.

Hammersound.net seems to be fine on my connection. Here's the link to collection soundfonts [http://www.hammersound.com/cgi-bin/soundlink.pl?action=view_category&category=Collections&ListStart=0&ListLength=15]("http://www.hammersound.com/cgi-bin/soundlink.pl?action=view_category&category=Collections&ListStart=0&ListLength=15").

---

