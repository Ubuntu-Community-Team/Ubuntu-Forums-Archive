---
title: "Rosegarden quantize"
date: 2010-09-28
forum: Ubuntu Studio
---

### Post by maaark38 on 2010-09-28
Hi.  I haven't had much luck trying to search the rosegarden-user archive, so here is my question.

I know Rosegarden can do iterative quantize, but that is not exactly what I want.  I am looking for a Humanize function.  First I quantize everything to a hard 16th note, then I would like to apply the Humanize setting, that makes the time vary a little.

Can Rosegarden do this or should I look at another sequencer ?  Hydrogen drum machine can do this, but I am not sure how it would work as a general sequencer.

FWIW I compiled the latest trunk of Rosegarden.

Thanks.

---

### Post by maaark38 on 2010-10-02
So I quess Rosegarden thinks I will be manually entering my drum patterns with a keyboard, so there will be timing errors, and iterative quantize makes sense.  However, I enter my notes with the matrix (piano roll) editor with 1/16th grid, so all of the notes are spot on, and I need to make them be off a little.

I guess I could move the notes around a little by hand.  But I decided to take the midirouter MIDI code sample and change a couple of lines to make it add a random amount of delay before each NOTE ON.  I specify a number of milliseconds N , then the program generates a random delay between 0 and N milliseconds for each note.  I use Jack to route the output of Rosegarden into the midirouter program, then into Hydrogen.

Here are the results.  Three 4 bar drum samples, the first with zero delay, the second with up to 20ms, and the third with up to 40ms (too much).

[http://www.think600.com/quant.ogg](http://www.think600.com/quant.ogg)

I really need to get a girlfriend.

---

