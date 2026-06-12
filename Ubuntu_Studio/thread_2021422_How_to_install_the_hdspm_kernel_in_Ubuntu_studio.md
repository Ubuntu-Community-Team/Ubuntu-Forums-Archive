---
title: "How to install the hdspm kernel in Ubuntu studio"
date: 2012-07-09
forum: Ubuntu Studio
---

### Post by Gusss on 2012-07-09
When I type : echo `uname -r` into terminal I get this result :
3.2.0-26-generic
But I need the hdspm kernel module to run my RME raydat 32ch soundcard. I am quite new to linux - where can I find the hdspm kernel module and how do I install it ?
I am currently running ubuntu studio will the hdspm kernel module work with this distro or do I need a different distro ?
cheers,
Gus

---

### Post by Sylos on 2012-07-10
Hello there.

Just had a quick google around and I think it should be included in the existing kernel.

Could you try entering 

```
sudo modinfo snd-hdspm
```

in a terminal and see if the module shows up. If it does then could you elaborate on whether your card is being detected and what usability (if any) you currently have.

Cheers


EDIT: Appears there was trouble in the past with snd-hdspm not working propoerly. Would have thought it would be fixed by now but might not be. I think installing the snapshot of alsa should fix it. read here:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/905650](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/905650)

---

