---
title: "Cakewalk bundle files"
date: 2008-04-28
forum: Ubuntu Studio
---

### Post by onemojofilter on 2008-04-28
Hi

Can anyone tell me if there has been any headway made towards making an attempt to being able to interpret Cakewalk bundle files? I understand that it is a proprietary format, but I'm hopeful that someone has found a way via a third-party utility or some other method of getting those files interpreted in such a way so that Rosegarden or a similar app accessible in Ubuntu can read it and import the audio appropriately.

Probably wishful thinking on my part, but thought I'd ask just the same.

Thanks!

---

### Post by SynthesizersFTW on 2008-04-29
Not to my knowledge, but one thing you *can* do is bounce each audio track down to .wav's that are the duration of the song (I set start/end markers to speed things up), then set the master tempo and reassemble in Rosegarden/Ardour.  Since the files are aligned to the markers, you should have no problem lining thing up.  Labor intensive exporting individual tracks as PCM .wav, but gets the job done.  You can snip the silence back out once you get everything imported.   MIDI tracks can all go separately by saving the project as a type 1 .mid file.

Before anyone would tackle .bun, they would probably work on getting OMF support, since that's available in all the major commercial DAWs.  Anyone want to chime in on possible future OMF support in Rosegarden/Ardour... ?

---

### Post by SynthesizersFTW on 2008-04-29
Scratch that.  Apparently AAF or AAF-XML is the new way to go.  We might have to wait a while to see it implemented in Ardour, but AFAIK current versions of Sonar should be able to import older .bun files, then you just save as AAF.

Till then, .wav export/import is the way to go.  If it's quicker than re-recording, then it's worth the time IMHO.

---

### Post by Stochastic on 2008-04-29
> **SynthesizersFTW said:**
> Scratch that.  Apparently AAF or AAF-XML is the new way to go.  We might have to wait a while to see it implemented in Ardour, but AFAIK current versions of Sonar should be able to import older .bun files, then you just save as AAF.

Till then, .wav export/import is the way to go.  If it's quicker than re-recording, then it's worth the time IMHO.

Well AAF is an Open Source technology (or at least their SDK is released under an open source license) despite it being a port of Microsoft's OMF format.  So I'd imagine it would be implemented relatively soon.  I did a quick search through Ardour's dev list archives and there are people working on it, but the chatter seems to be quite sparse.  From what I could gather, turning AAF into an Ardour session is the hard part, going the other way is easy as pie (both are XML formats, which helps).

---

### Post by onemojofilter on 2008-04-30
I re-read your reply and your suggestion of bouncing each track to a wav that is equal to the duration of the entire song makes the most sense. Never occurred to me to try that. I just hate having to fire up Windows again .. ;)

---

