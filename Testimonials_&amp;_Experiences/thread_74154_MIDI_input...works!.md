---
title: "MIDI input...works?!"
date: 2005-10-11
forum: Testimonials &amp; Experiences
---

### Post by philipacamaniac on 2005-10-11
I just plugged my 88-key keyboard into Breezy and played some phat beats in Hydrogen. I NEVER thought that would be possible, because my only PC MIDI input is through a MIDI-to-USB adapter made by Yamaha. Apparently the most recent ALSA drivers have picked up support for it, so now I can start my jammin again.

Well done, Breezy developers (and the Linux community at large).

Now if only I could get [Reason]("http://www.propellerheads.se") working in Wine...

---

### Post by poofyhairguy on 2005-10-11
[QUOTE=philipacamaniac]I just plugged my 88-key keyboard into Breezy and played some phat beats in Hydrogen. I NEVER thought that would be possible, because my only PC MIDI input is through a MIDI-to-USB adapter made by Yamaha. Apparently the most recent ALSA drivers have picked up support for it, so now I can start my jammin again.

Well done, Breezy developers (and the Linux community at large).

Now if only I could get [Reason]("http://www.propellerheads.se") working in Wine...[/QUOTE]

Can I ask for a link or something to the exact cable. I want this now!

How does it work with rosegarden?

[http://www.rosegardenmusic.com/](http://www.rosegardenmusic.com/)

---

### Post by philipacamaniac on 2005-10-11
[quote=poofyhairguy]Can I ask for a link or something to the exact cable. I want this now!

How does it work with rosegarden?

[http://www.rosegardenmusic.com/]("http://www.rosegardenmusic.com/")[/quote]

Cable = Yamaha UX16 USB Midi Interface.

I did start playing around with Rosegarden last night, but I went to bed before I got anything working. The problem right now is that Rosegarden wants me to load a SoundFont before it will make any noise, and I can't find my Audigy CD.

---

### Post by martin.john on 2006-02-18
[QUOTE=philipacamaniac]Cable = Yamaha UX16 USB Midi Interface.

I did start playing around with Rosegarden last night, but I went to bed before I got anything working. The problem right now is that Rosegarden wants me to load a SoundFont before it will make any noise, and I can't find my Audigy CD.[/QUOTE]

What did you have to do to get Kubuntu to recognise the USB cable?

I've managed to get /dev/sndstat to show it

```
...
Midi devices:
1: UX16
...
```

by loading uart401 and mpu401 modules. Once I've loaded those modules I also get /dev/sequencer and /dev/sequencer2. But I'm not having much luck with Rosegarden. Are there more/different modules I should be loading? I'm getting 

```
Non-fatal Error: "/dev/sequencer" : No Hardware detected
```

Which at least seems a step closer than I was getting before loading the modules, when I was getting

```
Non-fatal Error: cannot poll device "/dev/sequencer"
```

I'll have a go with Hydrogen and see if I can get anywhere with that, as that's what you've had success with.

Cheers,

Martin

---

### Post by martin.john on 2006-02-18
[QUOTE=philipacamaniac]Cable = Yamaha UX16 USB Midi Interface.

I did start playing around with Rosegarden last night, but I went to bed before I got anything working. The problem right now is that Rosegarden wants me to load a SoundFont before it will make any noise, and I can't find my Audigy CD.[/QUOTE]

For you soundfont problem - try [ubuntu studio page]("http://ubuntustudio.com/wiki/index.php/SoundFonts") which has links to soundfonts you can download

---

