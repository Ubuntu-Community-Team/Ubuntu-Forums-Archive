---
title: "Can I do this in Linux?"
date: 2015-11-07
forum: Ubuntu Studio
---

### Post by O)9(yo&amp;# on 2015-11-07
I have been using Sonar in Windows for years. But I hope to transition to Linux by the time Windows 7 is EOL (2020). I already use Linux for 90% of things, but music is the one thing I still need Windows for. Here is my setup: Sonar 8.5, with Garritan Personal Orchestra, East West Symphonic Orchestra Gold, plus some synths that come with Sonar (Dimension Pro, TTS-1). My computer specs: Intel I-7 CPU, Gigabyte mobo with 16 GB ram (can go to 32); two 1TB WD Black hard drives (not solid state but 7200rpm); and speakers with subwoofer (M-Audio/Mackie). I have never used any Linux audio programs, but have been investigating them. I should point out that I compose classical music, so midi is important, and I use notation, not PRV. (Sonar has decent enough notation to use while composing, and I then export it to Notion to produce a true score). The two problems I see are 1) Finding a DAW that has notation, and 2) finding a DAW that I can use my sample libraries with (see above). Which condenses into 3) finding a DAW with notation that allows me to use my libraries. From what I can see, this does not exist. There is Rosegarden, but I don't think I can use my libraries with it. There is Ardour, but it doesn't have notation. There is Bitwig, but again, no notation. My only hope at this point is Reaper, which apparently can run in Wine, and which is working on notation capability. I'm confident that by 2020 it will be an option, and probably much sooner, like next year. Unless there is another option, which is why I'm asking the question. As I said, my knowledge of Linux Audio is very scant, so maybe/hopefully I'm wrong.

---

### Post by CrocoDuck on 2015-11-07
Hi there. To use notation with a DAW you could write your scores with [Lilypond]("http://lilypond.org/"). I am not used to work that way and I never used Lilypond, but It should be able to export to midi. So you can import the midi track into the DAW. Not sure how well and comfortable, but worth to look into. I think there are ways to use your samples on Linux, either by try to convert them to some kind of other format (not always possible) or resorting to wine. I have been able to use bandstand from NI years ago, for example. I cannot assist much though since I not only stopped to try to use win software, but I even stopped to like the majority of commercial audio software. [Renoise]("http://www.renoise.com/") is actually the only one I like, have you checked if it supports notation?

---

### Post by yoshii on 2015-11-08
You'll want to check to find out if your soundcard / audio interface has drivers available in linux (either officially or non-officially) OR if the hardware is USB Class Compliant (which means it doesn't require drivers for any OS--you just plug it in).

---

### Post by O)9(yo&amp;# on 2015-11-08
> **CrocoDuck said:**
> Hi there. To use notation with a DAW you could write your scores with [Lilypond]("http://lilypond.org/"). I am not used to work that way and I never used Lilypond, but It should be able to export to midi. So you can import the midi track into the DAW. Not sure how well and comfortable, but worth to look into. I think there are ways to use your samples on Linux, either by try to convert them to some kind of other format (not always possible) or resorting to wine. I have been able to use bandstand from NI years ago, for example. I cannot assist much though since I not only stopped to try to use win software, but I even stopped to like the majority of commercial audio software. [Renoise]("http://www.renoise.com/") is actually the only one I like, have you checked if it supports notation?

Thanks Crocoduck for the tips. I have heard that Lily Pond is hard to use. also, I need the notation to be fully integrated into the DAW, as it is how I compose and edit. Not into rewiring. I finish the work in Sonar, and then export to Notion in order to fix up the notation.

---

### Post by O)9(yo&amp;# on 2015-11-08
> **yoshi2 said:**
> You'll want to check to find out if your soundcard / audio interface has drivers available in linux (either officially or non-officially) OR if the hardware is USB Class Compliant (which means it doesn't require drivers for any OS--you just plug it in).

No problem there, my UR-22 works fine in Linux out of the box.

---

### Post by jejeman on 2015-11-09
Do you do only MIDI + Samplers, or you need Audio tracks also?

---

### Post by O)9(yo&amp;# on 2015-11-09
> **jejeman said:**
> Do you do only MIDI + Samplers, or you need Audio tracks also?  I only do midi, but it's conceivable at some point I might do audio on rare occasions.

---

