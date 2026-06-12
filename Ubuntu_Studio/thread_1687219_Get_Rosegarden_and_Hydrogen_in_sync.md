---
title: "Get Rosegarden and Hydrogen in sync"
date: 2011-02-13
forum: Ubuntu Studio
---

### Post by _oscar_ on 2011-02-13
Hi all,
I'm working with UbuntuStudio Maverick, trying to get Rosegarden and Hydrogen in sync. I've got it all connected and use Jack transport, so start/stop works smoothly.
The problem comes up with tempo changes; esp. accelerando and ritenuto. When I set a tempo change in Rosegarden that ramps to the next tempo, I'm lost.
I can set the same beat in Hydrogen, but don't know to make those acc. and rit. there.

Best would be if Hydrogen get's the beat from Rosegarden I suppose, any suggestions how to achieve that, or any other hint that can help me out here?

Thanx in advance!

---

### Post by Pablo_F on 2011-02-13
Hi, 

Hydrogen won't follow rosegarden tempo maps but there is a workaround. 

You can use a versatile metronome called klick. You write down a tempomap file in text mode and let klick read it as a jack transport master. 

This way, hydrogen will follow the text tempo map but rosegarden will follow its own one. You have them synchronized if you set the same tempomap in rosegarden as in the text file. 

Take a look at this: 

[http://www.linuxmusicians.com/viewtopic.php?f=19&t=2290](http://www.linuxmusicians.com/viewtopic.php?f=19&t=2290)

Skip the ardour part.

I think that klick is in the maverick official repos. Search for gtklick in the software center and you will have both.

Cheers, Pablo

---

### Post by Pablo_F on 2011-02-13
Another workaround, maybe simpler.

Don't use hydrogen as a sequencer but only as a drum synth:

You can create a midi track in rosegarden and assign it to hydrogen midi input in Studio -> Manage midi devices. You write the drums in RG but hear the drumkit loaded in H2. You have to figure out the note pitch to instrument mapping, but this is not a big deal. 

Cheers again, Pablo

---

### Post by _oscar_ on 2011-02-14
Thanks Pablo ;)
Your article you refer to didn't show up in my Google searches, but it gives me what I wanted.
I prefer programming the drum patches in Hydrogen (when all done I merge Hydrogens midi export in Rosegarden to trigger an external drum machine), but with klick it works great.

I have to fake the time signatures to make tempo changes halfway a measure and simulate fermatas (e.g 3x4/4 = 3x7/8 + 2/8 + 1/8 ) and that seems to confuse Hydrogen, but I think I can work that out.

---

### Post by Pablo_F on 2011-02-14
Hi, 

I am glad I helped you. If you have further questions I will be of little help, I am afraid. But you can always ask Dominic. He developed klick, wrote an excellent manual and he is a very nice person. 

[http://das.nasophon.de/klick/](http://das.nasophon.de/klick/)

Cheers, Pablo

---

