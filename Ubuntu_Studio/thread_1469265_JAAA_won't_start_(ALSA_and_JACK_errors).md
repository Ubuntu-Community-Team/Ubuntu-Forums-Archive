---
title: "JAAA won't start (ALSA and JACK errors)"
date: 2010-05-02
forum: Ubuntu Studio
---

### Post by ojc123 on 2010-05-02
I've searched but can't find anything helpful. I can't get anywhere with JAAA.

owen@Compaq:~$ jaaa -A
Alsa_driver: the playback interface doesn't support mmap-based access.
Can't connect to ALSA

or

owen@Compaq:~$ jaaa -J
Can't connect to JACK

I'm using 10.04 on a Compaq CQ60 305EA laptop. As far as I can see all the jack and alsa stuff seems to be installed.  Sound works ok.  Audacity etc. work fine.

Any help gratefully received.

Thanks in advance.

---

### Post by ojc123 on 2010-05-02
Sorted.  After hours of messing I post, then I see the problem. I had not started Jack Control before I started JAAA. Obvious when you see it.

---

