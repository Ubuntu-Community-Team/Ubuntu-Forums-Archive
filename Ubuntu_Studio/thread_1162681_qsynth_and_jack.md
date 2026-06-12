---
title: "qsynth and jack"
date: 2009-05-17
forum: Ubuntu Studio
---

### Post by markgobbin on 2009-05-17
in ubuntu jaunty, qsynth says "failed to create the audio driver (jack)".

I have started jack before starting qsynth, also tried the other way around. doesn't work. other synths work. why?

thanks

---

### Post by markgobbin on 2009-05-18
i figured out that if you untick "auto connect jack outputs" this will solve it for some reason

however i have a different question, in ubuntu studio controls under "system > administration" what does "nice" mean?? can't find any reference to this at all!

---

### Post by raboofje on 2009-05-18
> **markgobbin said:**
> however i have a different question, in ubuntu studio controls under "system > administration" what does "nice" mean?? can't find any reference to this at all!

Each process has a 'nice' value, which determines how 'nice' this program is to other programs. 'being nice' here means taking priority when being scheduled: when 2 programs are both competing for CPU time, the scheduler will give the program with the lowest 'nice' value precedence.

Hence, it's often a good idea to give audio-related applications a low (or even negative!) 'nice' value.

You can assign nice values with the 'renice' command. You can view current 'nice' values in the 'NI' column of top and ps (e.g. "ps -eo pid,rtprio,ni,comm"). 

By default, 'normal' users cannot assign negative nice values. You can give the 'audio' group this right by setting up your /etc/security/limits.conf as described at [http://wiki.linuxmusicians.com/doku.php?id=system_configuration#limits.conf](http://wiki.linuxmusicians.com/doku.php?id=system_configuration#limits.conf)

---

### Post by markgobbin on 2009-05-18
hee, that makes sense.

thanks

---

