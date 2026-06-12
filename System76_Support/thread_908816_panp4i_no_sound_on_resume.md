---
title: "panp4i no sound on resume"
date: 2008-09-02
forum: System76 Support
---

### Post by thebinaryblob on 2008-09-02
well, I got my new System76 Pangolin, and I really like it,
but It seems that after it resumes from suspend, the sound doesnt work!
this happens every time I close and open the lid!
Ive tried reloading some of the snd* modules, but since they are in use, I cant remove them. I really have no clue what to do next:confused:

 I have attached the results of dmesg | tail -n 20
I hope that can help

---

### Post by thomasaaron on 2008-09-03
OK, I'll have to do some testing on that one. Please file a bug report here...

[https://launchpad.net/system76](https://launchpad.net/system76)

...and let's deal with it via that venue, as it is probably something that will result in a change to the System76 driver.

---

### Post by thebinaryblob on 2008-09-03
[https://bugs.launchpad.net/system76/+bug/264516](https://bugs.launchpad.net/system76/+bug/264516)
okay, there it is, just tell me if I need to add anymore information.

---

### Post by analogian on 2008-09-03
I can confirm this issue on my new pangolin panp4i as well.  It seems that on battery power more often than not I do not have sound, and plugging it does not return the sound.  It may also be that when I close the lid to suspend the sound does not resume. I'm not on launchpad, so please keep this thread updated as you work towards a fix :)

---

### Post by thomasaaron on 2008-09-04
Contributing on launchpad is probably the best way to help with and follow this issue. Having all the info in one place makes it much less complicated.

---

