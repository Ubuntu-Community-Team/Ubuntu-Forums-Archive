---
title: "mencoder how to multi thread?"
date: 2009-06-14
forum: Ubuntu Studio
---

### Post by markp1989 on 2009-06-14
i been using this command to encode some videos. but it only uses 1 core, how do i make it use both cores?
```
mencoder INPUTFILE -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=192 -srate 48000 -xvidencopts fixed_quant=4 -o OUTPUT.avi
```

Thanks Markp1989

---

### Post by lukeiamyourfather on 2009-06-15
Someone correct me if I'm wrong but the xvid encoder isn't multithreaded. If you have a lot of videos to convert you can queue them up and run two sets at a time so both cores are used. Cheers!

---

