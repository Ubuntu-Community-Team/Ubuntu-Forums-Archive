---
title: "Multi camera live production?"
date: 2010-06-09
forum: Ubuntu Studio
---

### Post by mccord42 on 2010-06-09
I am wondering if anyone knows of any way to do multiple camera live editing with capabilities like transitions and green screen using just Linux software and firewire cameras?

I'm looking to set up a basement studio for some live podcasts and I thought it would be great if I could set it up using Linux but I've had very little luck finding any live video production software for linux.

Thanks for any help or suggestions.

---

### Post by sgx on 2010-06-09
It might be worth checking out multi-camera security solutions,
and see what can be gleaned, and cross reference the various
hardware with v4l devices, and then look for video codecs and
streaming solutions within linux apps. 

ffmpeg can perhaps be a useful go-between, using groups
of command options to your adavantage.
Cheers

---

### Post by FakeOutdoorsman on 2010-06-11
I once VJ'ed a dance party for a local radio station with a Linux program called [EffecTV](http://effectv.sourceforge.net/).  Workflow was: miniDV camcorder > composite video output > video switch > Canopus AVDC110 Analog/Digital converter > Firewire input to computer.  I did it this way because I didn't have any long firewire cables and the two camcorders and the wireless camera were at least 20' away.

Possibly a little different than what you may be looking for but it worked well for me.

---

