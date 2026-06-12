---
title: "Sound cards change device numbers every boot."
date: 2011-11-19
forum: Ubuntu Studio
---

### Post by m.lp.ql.m on 2011-11-19
I'm running Ubuntu Studio 11.10 64, with KXStudio PPAs and everything's running smoothly, save one thing:

I have 3 devices installed that the kernel identifies as a sound card: the M Audio Delta 1010LT, the built-into-the-motherboard Realtek "HDA ATI SB", and a video capture card "Conexant CX8801". On every boot, these cards will randomly switch ALSA device positions-- sometimes the 1010LT will be on HW:2, other times on HW:0, etc-- so I have to reconfigure Jack every time.

Is there a way to get them to be assigned statically?

Thanks!

---

### Post by jejeman on 2011-11-19
Here, you have everything
[http://alsa.opensrc.org/MultipleCards](http://alsa.opensrc.org/MultipleCards)

---

### Post by jeebustrain on 2011-11-22
I have a regular Delta1010, but it's the same for any card


- output your devices with:
```

$ cat /proc/asound/cards

```


Mine looks like this:
```

 0 [M1010          ]: ICE1712 - M Audio Delta 1010
                      M Audio Delta 1010 at 0xe800, irq 21
 1 [Anniv          ]: USB-Audio - MIDISPORT 4x4 Anniv
                      M-Audio MIDISPORT 4x4 Anniv at usb-0000:00:12.1-1, full speed

```

so in qjackctl, if I want to statically set my Delta1010 to be the audio card, instead of putting HW:0 in, I use HW:M1010

I imagine that the 1010LT might actually be the same value.

---

