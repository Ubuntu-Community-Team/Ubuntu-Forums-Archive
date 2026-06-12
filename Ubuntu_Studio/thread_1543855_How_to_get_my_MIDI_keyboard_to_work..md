---
title: "How to get my MIDI keyboard to work."
date: 2010-08-01
forum: Ubuntu Studio
---

### Post by timtincher on 2010-08-01
I have Ubuntu Lucid Lynx. Not, Ubuntu Studio Lucid Lynx. But, I went into the terminal, and downloaded all the audio programs via \```
aptitude install ubuntustudio-audio
```. So I have JACK, etc. [http://wikipedia.org/Ubuntu_Studio](http://wikipedia.org/Ubuntu_Studio) I have everything on the Audio list on this link.

But, I need to figure out how to detect my keyboard to the system. It is a YAMAHA PSR-293 it has a USB port that a printer would use. I have it connected to the computer, now I just need to figure out how to get this to work. Any ideas? 

:popcorn::o

---

### Post by JC Cheloven on 2010-08-01
I don't know about this particular keyboard, but every USB midi keyboard I've used (3 different models so far) have been just recognised at plug in.

I used them with MuseScore, to speed up my note input. As I said I had to do nothing special.

JC

---

### Post by cchhrriiss121212 on 2010-08-02
If you are new to jack then you should know that any available MIDI connections will show up in the connections window under the tab called ALSA (this is because ALSA is the default MIDI driver).

---

### Post by mango42 on 2010-08-02
> **cchhrriiss121212 said:**
> If you are new to jack then you should know that any available MIDI connections will show up in the connections window under the tab called ALSA (this is because ALSA is the default MIDI driver).

Before that check QJackCtl's setup dialog to set MIDI to 'seq', that is ALSA, rather than 'raw', that is Jack MIDI (bottom left hand corner of dialog). To combine use of both internal and external hardware synths flexibly, it is also necessary to get JACK to fire up **a2jmidid** - there's an option to do this in the QJackCtl setup, something like ```
a2jmidid -e &
```

---

### Post by AutoStatic on 2010-08-02
> **timtincher said:**
> But, I need to figure out how to detect my keyboard to the system. It is a YAMAHA PSR-293 it has a USB port that a printer would use. I have it connected to the computer, now I just need to figure out how to get this to work. Any ideas? [http://www.youtube.com/watch?v=kBEzMC35gt8](http://www.youtube.com/watch?v=kBEzMC35gt8)

The Yamaha PSR293 needs no USB drivers to work so it probably just works in Ubuntu like the M-Audio Oxygen 8 v2 in my Youtube tutorial.

---

