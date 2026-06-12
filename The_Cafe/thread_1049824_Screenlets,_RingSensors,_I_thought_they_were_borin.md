---
title: "Screenlets, RingSensors, I thought they were boring, so I hacked them"
date: 2009-01-25
forum: The Cafe
---

### Post by DoctorMO on 2009-01-25
If anyone's ever used screenlets, they're cairo based widgets which sit on your desktop and do things. based in python.

Well I was enjoying watching the ringlets pump up and down in response to the cpu when I though: hey wouldn't it be cool if they were in colour.

[http://imagebin.ca/view/oa38Qire.html](http://imagebin.ca/view/oa38Qire.html)

Well, there they are, had to refactor the entire options code to get the new multi colour option control. But the damn thing will go from any colour to any other colour depending on the value.

Thoughts?

Oh code is in launchpad if anyone wants to try it.

---

### Post by Chokkan on 2009-01-25
Nice :D

---

### Post by Islington on 2009-01-25
Awesome job!

---

### Post by Martje_001 on 2009-01-25
```
Oh code is in launchpad if anyone wants to try it.
```
Where? :)

---

### Post by DoctorMO on 2009-01-25
Here you go:

[https://code.launchpad.net/~doctormo/screenlets/options-rework](https://code.launchpad.net/~doctormo/screenlets/options-rework)

I added some other options too, took out the big bars checkbox and put in a number field where you can specify the number of bars from 10 to 80. The colour changes now have two styles, Fan (sets the entire colour from the last position) and Grad (rainbow like effect)

I used 'Fan' so my battery ring will fade out to transparent between 95% and 100% so long at my laptop is plugged in, it's invisible.

---

