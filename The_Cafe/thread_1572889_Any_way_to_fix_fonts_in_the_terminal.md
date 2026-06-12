---
title: "Any way to fix fonts in the terminal?"
date: 2010-09-11
forum: The Cafe
---

### Post by Legendary_Bibo on 2010-09-11
Or just have a font that doesn't look messed up in the terminal besides any form of monospace? Basically the letters always seem to overlap for me.

---

### Post by alexan on 2010-09-12
apt-get moo
wouldn't be the same


Anyway... try with other fonts?

[http://www.dafont.com](http://www.dafont.com)
[http://www.blambot.com/](http://www.blambot.com/)

---

### Post by TNT1 on 2010-09-12
> **Legendary_Bibo said:**
> Or just have a font that doesn't look messed up in the terminal besides any form of monospace? Basically the letters always seem to overlap for me.


Thank heavens. I thought I was the only one... Funny, before my last format and re-install, I had it looking good, any now I don't remember what I did ...

---

### Post by juancarlospaco on 2010-09-12
OMG ComicSans*-like* fonts WTF

---

### Post by Legendary_Bibo on 2010-09-12
> **juancarlospaco said:**
> OMG ComicSans*-like* fonts WTF

I just did this as an example, and it's called "I hate comic sans" actually.

---

### Post by Legendary_Bibo on 2010-09-12
> **TNT1 said:**
> Thank heavens. I thought I was the only one... Funny, before my last format and re-install, I had it looking good, any now I don't remember what I did ...

Yeah I have some fonts that look okay, but they still have the overlapping issue.

---

### Post by Spice Weasel on 2010-09-12
Monospace is the default for a reason. It all goes down to xterm or something, but I'm positive you can't use fonts whose characters aren't all equal length.

---

### Post by ice60 on 2010-09-12
i like 'Lucida Console Bold' and/or 'Bitstream Vera Sans Bold' 


i just remembered this too - try running this in a term and see if you like the look of it!

```
xterm -bg black -fg white -ls -j -s -sl 10000 -sb -fa DejaVu-Sans-11 -fs 11
```

---

### Post by ice60 on 2010-09-12
here's the xterm one - 



please forgive the accidental red lines, they're from very old screencapture software i hadn't bothered updating :( lol

---

### Post by Legendary_Bibo on 2010-09-12
Ah, so it has to do with the font hinting. I guess the terminal doesn't support that. I did find a nice italicized font, but I guess I won't be able to have any cleaner fonts. I'm using Tlwg Typo Bold Oblique.

---

### Post by sgosnell on 2010-09-12
Most fonts have italic.  I sort of like Bitstream Vera Sans Mono Oblique.  You do need a mono in the terminal, but all the monospace fonts I've seen also have an italic variation.

---

