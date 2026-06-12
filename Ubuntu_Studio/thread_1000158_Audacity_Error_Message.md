---
title: "Audacity Error Message"
date: 2008-12-02
forum: Ubuntu Studio
---

### Post by Nickel1010 on 2008-12-02
Hello

I can't record or play sound in Audacity on Ubuntu 8.04.
Whenever I do I get the error:

"Error while opening sound device. Please check the input device settings and the project sample rate."

I know that this question has already been posted before but the other threads didn't help at all.

This problem has persisted ever since I first installed. I even reinstalled and it didn't fix it.

---

### Post by surfsunadam on 2008-12-05
Have you got everything in audacity and the ubuntu sound settings set to ALSA (default) ?

---

### Post by barisurum on 2008-12-05
If you have sound with other programs with ALSA selected as sound source then you should have with audacity too. But keep in mind that if jack is running you can't play anything in audacity as it doesn't support that server.

---

### Post by zettberlin on 2008-12-06
> **barisurum said:**
>  if jack is running you can't play anything in audacity as it doesn't support that server.

Thats not entirely correct: Audacity can play with jackd via portaudio. The latter is a halfbaked solution though and does not work always if at all...

Nevertheless you can set Audacity to use jackd as IN/OUT system.

---

### Post by barisurum on 2008-12-08
> Thats not entirely correct: Audacity can play with jackd via portaudio
Do you have to select portaudio as backend driver to jack to have audacity play through jack?

---

