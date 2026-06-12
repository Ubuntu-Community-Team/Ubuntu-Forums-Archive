---
title: "midi to wav, mp3, etc. with timidity help"
date: 2008-10-10
forum: Ubuntu Studio
---

### Post by zizzdude on 2008-10-10
Hey, I heard you can convert midi to different sound files with timidity. What are the commands to do that?

---

### Post by paulmerchant on 2008-10-10
Go to the terminal and type:

timidity [midifile.mid] -M [wavefile.wav]

For all of your options, type:

timidity --help

---

### Post by zizzdude on 2008-10-19
it doesnt make a wav file though. Is there such a way to do so?

---

### Post by Dufangoer on 2008-10-19
bump up   then lurkcheap wow power leveling --------------------------------**buy [eq2 plat](http://www.epaxx.com),  [eq2 gold](http://www.epaxx.com), [everquest platinum](http://www.epaxx.com), [rs gold](http://www.favgames.com/rs-gold/), [silkroad gold](http://www.favgames.com/silkroad-gold/),**

---

### Post by WestCoastSuccess on 2008-10-31
Try using:

timidity /path/to/midi/file/.mid -Ow -o /path/to/output/file/.wav

---

