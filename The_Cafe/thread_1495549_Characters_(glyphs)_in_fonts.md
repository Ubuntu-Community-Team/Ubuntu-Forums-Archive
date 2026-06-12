---
title: "Characters (glyphs) in fonts"
date: 2010-05-28
forum: The Cafe
---

### Post by pompa on 2010-05-28
Hi everyone.
I'm searching for a tool to verify what's inside a font.
It often happened to install a font which I'd love to discover only later that some charater was missing (as for example omacron &#332; or similar). So I was wondering if there is not in ubuntu, or for linux in general, any tool that permits doing some checks in this sense.

PS: The charmap does not what i want to do, because also selecting a font from the list the smart program fetches automatically the missing characters for the other font. So I need something more stupid!

Thank you, and some informations about terminology will be appreciated (font is the container, and character is a single glyph?)

---

### Post by Sam on 2010-05-28
```
sudo apt-get install gnome-specimen
gnone-specimen
```

---

### Post by pompa on 2010-05-28
> **Sam said:**
> ```
sudo apt-get install gnome-specimen
gnome-specimen
```
 
Nice software, but it will not solve my problem. Because of the fact that, as the charmap does, it fetches the missing characters from the other font in the same family, and so on.
In addition to it what I am searching for is something that should show me which characters are missing.
And if possible, how many glyphs are there in the font (that is useful to compare chinese/japanese fonts in which the number of characters is relevant and is not possible to test kanjis one by one).

---

