---
title: "Ladi Session - No Midi"
date: 2013-07-17
forum: Ubuntu Studio
---

### Post by DanielDiersant on 2013-07-17
Hi everyone,

I felt in love with UbuntuStudio 13.04, so I'm still a noob on this one. I have an issue I don't find a solution online, or maybe I didn't get it right. 

In a Ladi Session, I can't seem to have my MIDI peripheral and input/outpu, as I can have in Patchage. I took some screenshots. Is it normal ? If so, how do you work with this ? Do you use QjackCtrl to set-up your MIDI connections, then everything else in the Ladi Screen ?

Thanks !!

Daniel

[IMG]http://iceimg.com/i/14/ca/288a790efb.jpg[/IMG]


[IMG]http://iceimg.com/i/08/9a/d4523f456c.jpg[/IMG]

---

### Post by jejeman on 2013-07-17
I don't use LADISH, but it seams like no ALSA MIDI in it. Maybe you need to enable it?
You can "export" ALSA MIDI to JACK MIDI eather by a2jmidid  or selecting MIDI driver "Seq" in Qjacktl.

---

### Post by DanielDiersant on 2013-07-19
> **jejeman said:**
> I don't use LADISH, but it seams like no ALSA MIDI in it. Maybe you need to enable it?
You can "export" ALSA MIDI to JACK MIDI eather by a2jmidid  or selecting MIDI driver "Seq" in Qjacktl.

I'll try that as soon as possible, thanks !

---

