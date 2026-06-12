---
title: "jack and qsynth"
date: 2015-04-14
forum: Ubuntu Studio
---

### Post by msaether on 2015-04-14
I've succsessfully installed jack and qsynth. Realtime function is even working. But I just can't find qsynth in the jack tabs. I guess I've missed something in the setup tabs but I'm tired of trying myself.  I think I've done all here 

[http://www.rosegardenmusic.com/tutorials/qsynth-rosegarden/ConfiguringJackAndQsynth.html](http://www.rosegardenmusic.com/tutorials/qsynth-rosegarden/ConfiguringJackAndQsynth.html)

still I don't get qsynth in jack. What should the input and output devices be in the jack settings?
Error message in jack: zombified - calling shutdown handlerfluidsynth: error: Help! Lost the connection to the JACK server

Can someone help me?

---

### Post by pepsifx357 on 2015-04-23
I would highly recommend using patchage to hook up software to Jack.  I never liked doing things in Jack.  it was too clunky.  Patchage gives you a nice overview of what's running to where.  It also will make it easier to troubleshoot.

```
sudo apt-get install patchage
```

---

