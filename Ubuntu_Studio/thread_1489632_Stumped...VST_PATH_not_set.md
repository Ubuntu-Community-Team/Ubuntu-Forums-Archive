---
title: "Stumped...VST_PATH not set"
date: 2010-05-21
forum: Ubuntu Studio
---

### Post by mango42 on 2010-05-21
I just came across this strange* error in **Qtractor** when attempting to use a **LADSPA** plugin, the "Analog Style 16 Step Sequencer"

```
VST_PATH not set, defaulting to /home/xxxxxxxx/vst:/usr/local/lib/vst:/usr/lib/vst
```

and although there's a vst entry under usr/lib/dssi there isn't one in /usr/lib/ladspa or the directories tried by the program

* Strange because why would a LADSPA plugin need to have anything to do with commercial plugins anyway? Perhaps it's a wrapper thing, as I float way out of my depth ;-)

---

### Post by sgx on 2010-05-21
> **mango42 said:**
> I just came across this strange* error in **Qtractor** when attempting to use a **LADSPA** plugin, the "Analog Style 16 Step Sequencer"

```
VST_PATH not set, defaulting to /home/xxxxxxxx/vst:/usr/local/lib/vst:/usr/lib/vst
```

and although there's a vst entry under usr/lib/dssi there isn't one in /usr/lib/ladspa or the directories tried by the program

* Strange because why would a LADSPA plugin need to have anything to do with commercial plugins anyway? Perhaps it's a wrapper thing, as I float way out of my depth ;-)

You are lucky, I usually sink to my depth :)

So welcome to the arcane world of
'environment variables', but click the link, scroll down to the
Troubleshooting section, and all will become clear, just a simple textfile
and edit.

[http://neurotix.com/music/renoise_for_linux_howto.html](http://neurotix.com/music/renoise_for_linux_howto.html)

---

### Post by mango42 on 2010-05-22
Light bones - LOL

Thanks for that interesting link - certainly sheds more light on the morass.

Yeah, I'm aware of ENVironment variables but haven't yet looked deeply enough into LADSPA to figure out whether these plugins are for general use or specifically for building synths.

The main query still stands, though - why's Qtractor looking for a **VST** path for a **LADSPA** plugin?

Oh well, back to the Doepfer MAQ - there's nothing quite like physical controls to grab hold of, IMO.

---

### Post by sgx on 2010-05-22
Hi, there are several plugin unstandards to grapple with,
dssi, ladspa, and linux vst,  which is not 'windows-commercial-vst'
as most people would perceive it. Because linux devs are mostly unpaid, and free to reinvent the wheel without getting fired, they often do,
so strange implementations show up trying to bridge the gaps between standards, traversing the bit divide, squeezing code into distro regulations, and meeting new kernel requirements. I'm sure
most of them have a favorite, bridge, or rooftop, just in case ;)

[http://www.mail-archive.com/64studio-users@lists.64studio.com/msg00834.html](http://www.mail-archive.com/64studio-users@lists.64studio.com/msg00834.html)

[http://www.linuxjournal.com/node/1000192](http://www.linuxjournal.com/node/1000192)

[http://www.linux-vst.com/](http://www.linux-vst.com/) 

Cheers

---

### Post by mango42 on 2010-05-23
> **"sgx"]plugin unstandards[/QUOTE]

Love it!  said:**
> Because there is no Linux VST, Qtractor couldn't find a Linux VST, but there was a Windows VST and this wasn't included too.

...it's usually at this point in any such thread that my eyes start glazing over and my mind turns towards just making music the old fashioned way ;-)

And 'spinymouse' ?? - hmm, more dastardly genetic modification courtesy of Monsatan Inc, perhaps? :)

From that LinuxJournal link:-

> ...as more Windows users contemplate a change of operating system, the musicians among them will want the option to use VST plugins under Linux.

Why? Only because they paid through the nose for them, when they could have easily spent the same amount on some halway-decent hardware that only requires compatability with a few audio XLR or jack plugs! [/rant]

I really appreciate your assistance, **sgx** - one day I might just finally get up to speed on all these variegated virtual nuts and bolts... Meanwhile, I am dusting off me old Revox B :guitar:

---

### Post by sgx on 2010-05-23
[img]http://gifgif.net/wp-content/uploads/2010/04/kiss_of_death.gif[/img]

I've overheard a couple of those 'high-level developer meetings'

---

### Post by mango42 on 2010-05-24
LOL! And not a pizza in sight ;-)

---

