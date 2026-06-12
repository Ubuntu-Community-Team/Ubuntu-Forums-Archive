---
title: "Help please with MuseScore/ZynAddSubFX"
date: 2009-10-09
forum: Ubuntu Studio
---

### Post by Nigalius on 2009-10-09
Hi, I am fairly new to Linux in general but think I am learning fast. I have now promoted Ubuntu Studio to my number one PC, replacing XP. The download went fine and after minor hitches, all seems ok.

What I am hoping someone can help with is with MuseScore...  I can use the programme with reasonable ease but find the selection of instruments rather limited. So I went looking for other instruments and found just what I wanted in the ZynAddSubFX proggy.

 Can anyone tell me if it is possible to import the complete set of instruments from ZynAddSubFX into the sounds of MuseScore? or is there any way that I can use ZynAddSubFX with MuseScore? I dont even know if it possible. But I would like to write some music using Zyn. Perhaps this has to be done in another proggy other than MuseScore, I really dont know.

If it can be done, could anyone tell me how please.

I hope that I have explained myself good enough for you to understand.

Thank You

Nigel

---

### Post by Tahakki on 2009-12-20
Try LMMS.

---

### Post by VertexPusher on 2009-12-21
Open JACK's connection editor and connect MuseScore's MIDI output to ZynAddSubFX's MIDI input.

> **Tahakki said:**
> Try LMMS.
If all you have is a hammer, everything starts looking like a nail. Does LMMS have a notation editor? I don't think so.

---

### Post by Tahakki on 2009-12-21
Sorry. Didn't realise he needed notation. xD

---

### Post by wbm on 2009-12-21
> **VertexPusher said:**
> Open JACK's connection editor and connect MuseScore's MIDI output to ZynAddSubFX's MIDI input.


If all you have is a hammer, everything starts looking like a nail. Does LMMS have a notation editor? I don't think so.

I am learning all this too now. Do the applications that you say to connect need to be launched to show up?
Once connected, will they stay connected between e.g. reboots?
Thanks.

---

### Post by VertexPusher on 2009-12-22
> **wbm said:**
> Do the applications that you say to connect need to be launched to show up?
Yes.

> Once connected, will they stay connected between e.g. reboots?
No, every time you start up JACK, you need to reconnect all the applications. But there are at least two ways to simplify this: If you use Qtractor, your connection setup will be saved along with the Qtractor project and restored when you reload the project. The other option is to save the connection setup as a preset in JACK's control panel.

---

### Post by wbm on 2009-12-22
> **VertexPusher said:**
> Yes.


No, every time you start up JACK, you need to reconnect all the applications. But there are at least two ways to simplify this: If you use Qtractor, your connection setup will be saved along with the Qtractor project and restored when you reload the project. The other option is to save the connection setup as a preset in JACK's control panel.

Thank you. One follow up question. When I save the settings in Jack as a preset, do I then first choose the preset and then launch the respective applications, or launch the applications first and the choose the preset? It would seem the second choice would make more sense.
Thanks.

---

### Post by sgx on 2009-12-22
lash is a session management app for several linux audio softwares,
zynaddsubfx and hydrogen, among others. I'm not sure if it is still an active project, but it can probably get you at least the drums and synth loaded, maybe more

there is a link to a video about lash at this link:

[http://audioprocess.blogspot.com/](http://audioprocess.blogspot.com/)

---

