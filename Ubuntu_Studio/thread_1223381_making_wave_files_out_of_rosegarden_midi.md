---
title: "making wave files out of rosegarden midi?????????"
date: 2009-07-26
forum: Ubuntu Studio
---

### Post by shantiq on 2009-07-26
[B][COLOR=Blue]ok[SIZE=3] so [SIZE=2]just started with rosegarden and managed to make a nice piece of midi music which i want to export as a wave file

but looking around the handbook and the program itself i cannot see how to do that


can someone help this neophyte PLEASE

i am sure it is simple but i just cannot see it




thank you    shan:D
[/SIZE][/SIZE][/COLOR][/B]

---

### Post by shantiq on 2010-04-26
and the answer was export as midi file

then convert midi file to wave using soundkonverter or any other converter



**or** Timidity best from command line


> timidity --output-24bit -A120 filename.mid -Ow -o filename.wav


or same  >  timidity  -A120 filename.mid -Ow2 -o filename.wav   
they could tell you it would save a lot of time

---

### Post by sgx on 2010-04-27
> **shantiq said:**
> [B][COLOR="Blue"]and the answer was export as midi file

then convert midi file to wave using soundkonverter or any other converter


they could tell you it would save a lot of time[/COLOR][/B]
Could you post the size of both those files, please?

---

