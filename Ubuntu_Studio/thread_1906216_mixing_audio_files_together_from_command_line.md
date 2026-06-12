---
title: "mixing audio files together from command line"
date: 2012-01-08
forum: Ubuntu Studio
---

### Post by ashyashy on 2012-01-08
hey,
i'm trying to put a few short audio files ('wav' for now, but i can convert them if needs) into one big audio file ('wav' also).
that means - I have one big audio file (lets call him A) and a few small audio files (B,C,D,....)
I want to create a new file that while playing it, most of the time you will hear A but in some decided seconds you will hear (A+B) or (A+C) or ...
and i'm want to do so in command line because its all going to a python script.
any idea?
thanks

---

### Post by marsanyi on 2012-01-17
I built a tool for SoftSynth, Inc that does this by specifying a control file in XML.  The "dialect" of XML is dubbed MiXML (bad choice, there's a slew of other XML tools out there with that name), and it'll let you specify multiple input files in parallel and serial with varying level and pan information, and ways to crossfade, duck, and so on with the levels.  There's a command-line mixer in Java.

You might get in touch with SoftSynth ([www.softsynth.com](www.softsynth.com)) and see what the status of the tool is.

--rbt

---

