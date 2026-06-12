---
title: "piano tuner"
date: 2011-03-18
forum: Ubuntu Studio
---

### Post by bluesscream on 2011-03-18
My old piano is awfully out of tune :eek: So I'm looking for some assistant software to adjust it in a circulated temperament.  Any hints are welcome.
Best regards bluesscream

---

### Post by Pablo_F on 2011-03-20
I use *tuneit* to tune my guitar. It is a command line tool. 

Example (the output in bold letters):

$ tuneit -jf
**Note G ( 195.998Hz): +16 cents ( 197.836Hz)**  

I don't know if the reference notes are in a circulated temperament, but you monitor the input frecuency all the time.

[http://delysid.org/tuneit.html](http://delysid.org/tuneit.html)

Cheers, Pablo

---

### Post by bluesscream on 2011-03-26
Tx Pablo, I'll give it a try. The more I dive into this matter the more I recognize: piano tuning is high sophisticated arts. I. e. for concerts pianos are tempered in specially tailored manners exactly for certain compositions, heavily depending on the tuner's ears, who must be an artist as well as the interpreter. So I decided to give a local craftsman a chance...
But theoretically this might be an interesting topic for experienced coders.
best regards
bluesscream

---

### Post by wilee-nilee on 2011-03-26
You can't tune a piano yourself it is a specialised skill, and fairly cheap in my area, without repairs.

A piano has 3 strings per key, 2 root and a 5th I think you have to deaden them individually. I believe not all registers have 3 strings though.

---

### Post by kevinamadeus2 on 2011-03-29
If you just want your old piano to be more in tune, rather than tuned into a professional performance level, it is certainly fun to try that.

What software are you seeking, the one that tells you how much it is shape or flat when you input the piano sound, or simply playing the note and you will use your ear to adjust?

If it is the second case you just need some MIDI to give you the note.

The following is not really about Ubuntu but in case if you don't know...
Every note has 3 strings. Use soft materials (like rubber wedges) to damp the outer strings of a note and tune the middle string to the right frequency (with reference to tuning fork, tuners, or any apps that you can find). Make sure only the middle string is sounding otherwise your ears will get really confused.

Do this to the notes of the middle octave. Then tune the outer strings to match the middle one by ears. Then just repeat this to other octaves by matching the sound (octaves apart) to the middle ones (again by ears).

---

### Post by ebasa on 2011-03-29
Some things are best left to professionals.

---

### Post by Enigmapond on 2011-03-29
> **wilee-nilee said:**
> You can't tune a piano yourself it is a specialised skill, and fairly cheap in my area, without repairs.

A piano has 3 strings per key, 2 root and a 5th I think you have to deaden them individually. I believe not all registers have 3 strings though.

Just an FYI - 
You CAN tune a piano yourself with the proper equipment...I know as I do it...you need a tuning wrench, oscilloscope, (if you don't have perfect pitch), and a length of felt. Also the three strings are in the mid and upper registers and are all tuned to the tonic. There is no fifth involved.

Cheers! :)

---

