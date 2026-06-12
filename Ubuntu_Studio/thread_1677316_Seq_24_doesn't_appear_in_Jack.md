---
title: "Seq 24 doesn't appear in Jack"
date: 2011-01-28
forum: Ubuntu Studio
---

### Post by The Jinty on 2011-01-28
Hello I'm a complete beginer on this whole thing. 

I was following the guide "how to make a song in seq24 when I came to a complete stop WHen trying to make connections in jack seq 24 isn't appearing *ZynAddSubFX, Hydrogen *and *Virtual Keyboard *Are appearing as is Midi Through but thats it. 

There also appears to be sound problems I'm able to get sound in *Hydrogen* but not with[I] ZynAddSubFX. 

Jack[/I] Appears to be working just fine the meters light up in *ZynAddSubFX *When I click on the keys in *Virtual Keyboard* And Hydrogen starts playing When I click play on Jack

My guess here is that their is something blatantly obvious staring at me in the face but I haven't got the first clue where to look

---

### Post by AutoStatic on 2011-01-28
Hello, seq24 doesn't create (ALSA) MIDI ports by default. You have to set so-called MIDI buses for each pattern in the top right field of the pattern editor window.
It is possible though to have seq24 create ALSA MIDI ports that are visible in QjackCtl, but that requires some editing of a configuration file.

Best,

Jeremy

---

### Post by The Jinty on 2011-01-30
[FONT=Arial]Cheers for that. Will be shure to try[/FONT]

---

