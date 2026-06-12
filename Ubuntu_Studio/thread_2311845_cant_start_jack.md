---
title: "cant start jack"
date: 2016-01-30
forum: Ubuntu Studio
---

### Post by guarnieri-philippe on 2016-01-30
Hi,

 i have an issue with a DAC; my previous DAC was a HRT MICROSTEAMER  all was working fine but for my final installation i bought a UD503 and  with this one impossible to start JACK
msg ERROR: ALSA: cannot set hardware parameter for play
        ERROR: ALSA connot configure playback channel.
        ERROR: Cannot initialize driver
        ERROR: JackServer::Open failed with -1
        ERROR: Falied to open server

I don't know where to search to find a solution if one exist.

A little help will be appreciated

Thanks

---

### Post by jejeman on 2016-01-30
Is sound card supported by ALSA?

---

### Post by guarnieri-philippe on 2016-01-31
I don't know .; how to get this information ?

---

### Post by jejeman on 2016-02-01
Do you have any sound thru it?
give
```
aplay -l
```

---

