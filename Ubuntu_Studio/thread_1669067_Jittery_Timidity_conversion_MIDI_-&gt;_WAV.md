---
title: "Jittery Timidity conversion MIDI -&gt; WAV"
date: 2011-01-17
forum: Ubuntu Studio
---

### Post by Pencilpen on 2011-01-17
Greetings Community!

I have a problem which I feel ill equipped to solve, perhaps someone has encountered similar and can help me, I have searched for help but come up with none so far.

So! I have a midi file which I converted to a wav file with the command:
timidity -Ow "salvum-fac-(11.10.11.10.d)-0-satb.mid"

The result was decidedly ordinary (jittery I think may be the term but perhaps staccato or even jerky), I have attached the mid file and an mp3 of the wav (wav file is tooooo big to attach). To check that the actual conversion wasn't the problem I sent the file to my sound card with the command:
timidity -Os "salvum-fac-(11.10.11.10.d)-0-satb.mid" and the result was exactly the same.

Timidity has such an array of possible settings to tweak in the conversion I thought I'd ask here before trying randomly to apply settings in an effort to get a better result.

I am sure the midi file itself is fine because playing it through Audacious results in a beautifully smooth sounding output.

I have converted several other midis to wav and had pretty good results overall, with the same default settings as used above. I have had some other less than beautiful results but this one is the worst.

Any help/advice gratefully received.

TIA,
Karl

---

### Post by hgernhardt on 2011-01-18
Karl—

I think your problem lies in the configuration of the instrument you're using.  In listening to your .mp3, I heard a patch setup which had a rather slow attack for the tempo you were using.

Although I wasn't able to play your .mid using instrument 53, I did remap it to a string section in Rosegarden.  I would say that your patch setup needs a quicker attack, and reasonable decay on the staccato stops.

Good luck,

Henry

---

