---
title: "Looking for Linux native VST basics/tutorials"
date: 2010-02-27
forum: Ubuntu Studio
---

### Post by hxcobd on 2010-02-27
I've been a linux user for a long time, but have always sort of avoided audio production in it, instead dual-booting to Windows any time I wanted to do some audio work.

Well, I think it's time to blaze a trail and put my programming history to good use. I'd like to bring some native linux VSTs to the field and expand our options!

The question is: where to begin? Is there a great website that discusses the basics of native linux VSTs? Compares them to Windows VSTs? Explains the differences between linux VST/DSSI/LV2/FST?

Many thanks in advance.

---

### Post by sgx on 2010-02-28
I would get on lots of developer mailing lists like these and ask for suggestions, and if you think of something  you would use yourself, start looking through source-code of what seem to be similar or related projects.

[email]64studio-users@lists.64studio.com[/email]

[email]linuxsampler-devel@lists.sourceforge.net[/email]

usually type    join
in the subject line  of an email.

There are orphaned projects out there, Hexter DX7 clone could
use a gui, default stereo i/o, and smoothe import/management of
the huge number of sysex files on the net, perhaps even implement
features from later DX Yamaha models.

There are many under-manned projects, Bristol is an ambitious multi-gui synth, the developer is one of the nets good people, likely many features on his to-do list, I'm sure making it a true plugin would benefit lots of new users.

The great linux sample-sequencer/drum-machine Hydrogen has an orphaned windows version, taking over that project and bringing stability to it could have a great impact on musicians around the world.

The lash project also is in stalemate, getting involved bringing new apps
to it would make lots of people happy. 

New Rakarrack modules would always be appreciated, or updating Creox
and ecamegapedal, both made a good start, butt need help to move forward.

Good luck!

---

### Post by AutoStatic on 2010-02-28
> **hxcobd said:**
> Well, I think it's time to blaze a trail and put my programming history to good use. I'd like to bring some native linux VSTs to the field and expand our options!Sounds good!

> **hxcobd said:**
> The question is: where to begin? Is there a great website that discusses the basics of native linux VSTs? Compares them to Windows VSTs? Explains the differences between linux VST/DSSI/LV2/FST?
Linux VSTs: there hardly are any and if you want to port VSTs it is advised to port them to LV2.
DSSI: [http://en.wikipedia.org/wiki/DSSI](http://en.wikipedia.org/wiki/DSSI)
LADSPA: [http://en.wikipedia.org/wiki/LADSPA](http://en.wikipedia.org/wiki/LADSPA)
LV2: [http://en.wikipedia.org/wiki/LV2](http://en.wikipedia.org/wiki/LV2)
FST: [http://www.joebutton.co.uk/fst/](http://www.joebutton.co.uk/fst/)

---

### Post by transmogrifox on 2010-02-28
"VST" as I understand it is pretty much a Windows-only term...sort of reluctantly accepted into the Linux community by means of people running Windows VST's under Wine and other compatibility interfaces.

Linux plugins generally fit under (as you said), DSSI, LADSPA, LV2...quite a few standards, really.

One plugin pack that I think has really done a good job is the Calf Audio Plugin Pack.  It supports just about every Linux plugin standard out there, and has it's own standalone GUI for jack...and IMHO, the GUI is very well done.

If you wish to put your skills to use, I would imagine Calf is a really good place to start.

Hopefully you're aware that good plugins are not an exercise in programming.  You need to learn digital signal processing theory really well in order to make audio processing plugins that compete on a peer level with the commercial products with which you are familiar.  Look at swh-plugins.  Steve Harris is one developer who seems to really understand what he's doing on the DSP end.

Having good programming skills helps organizing the DSP routines into a useful interface.

---

### Post by hxcobd on 2010-02-28
> **transmogrifox said:**
> "VST" as I understand it is pretty much a Windows-only term...sort of reluctantly accepted into the Linux community by means of people running Windows VST's under Wine and other compatibility interfaces.



I don't believe this is true... Linux VSTs do exist, as far as I understand. Someone let me know if I'm wrong.

Thanks a bunch for all the tips, guys. I do have fairly extensive background in DSP (my bachelors degree is actually in this field, heh), so I'm not TOTALLY clueless; it's just the Linux plugin standards that are extremely confusing, especially considering there are so many of them!

---

### Post by sgx on 2010-02-28
> **hxcobd said:**
> I don't believe this is true... Linux VSTs do exist, as far as I understand. Someone let me know if I'm wrong.

Thanks a bunch for all the tips, guys. I do have fairly extensive background in DSP (my bachelors degree is actually in this field, heh), so I'm not TOTALLY clueless; it's just the Linux plugin standards that are extremely confusing, especially considering there are so many of them!
Amazing the info one finds putting "linux vsts" into google, lots of discussions, tips, names and places. ;)

If I were a coder, I would start a project (or modify a good dormant one) with a gui toolkit and dependencies common to all the main linux distros. It would function with jackd, and the background of the gui would be a replaceable .png, (ZebraCM is an example of this) so
wood, granite, polished metals etc could be chosen at will. Everything involved with plugin standards would be avoided like plague. And I would host the needed dependencies with the app as an archive of .debs and .rpms, to insure maximum availability.
Cheers

---

### Post by AutoStatic on 2010-03-01
> **hxcobd said:**
> I don't believe this is true... Linux VSTs do exist, as far as I understand. Someone let me know if I'm wrong.They do exist, see the 'Linux VST developers' paragraph on [http://www.linux-vst.com/](http://www.linux-vst.com/)
They're actually VSTs that have been ported to Linux. But if you take Linux DSP for example, they first offered stand-alone plugins that could be considered Linux VSTs but they're now switching to LV2.

> **hxcobd said:**
> ...it's just the Linux plugin standards that are extremely confusing, especially considering there are so many of them!There are only three, LADSPA, DSSI and LV2 of which LADSPA and DSSI are the oldest frameworks with the most limitations. LV2 is considered as their successor so it's best to focus on LV2.

---

### Post by transmogrifox on 2010-03-02
> **hxcobd said:**
> ... I do have fairly extensive background in DSP (my bachelors degree is actually in this field, heh), so I'm not TOTALLY clueless; it's just the Linux plugin standards that are extremely confusing, especially considering there are so many of them!

Good stuff.  I hope I don't come off as an elitist.  I just have a bachelors in Electrical Engineering with a focus toward analog signal processing...so I see much of DSP through the eyes of the bilinear transform :)  But I have spent enough time trying stuff to know that cookbook DSP always has its caveats, and it's good to see a programmer who understands the implications of what they're doing :-)

The disadvantage of not really knowing who you're talking to :)

Based on comments above, it still seems that "VST" is a term adopted by Linux.   From what I hear, LV2 sounds like a really good standard...maybe even better than VST. In either case, writing "VSTs" in the Windows sense for Linux is not a good idea.  Just my opinion...so please treat it as such: just another drop in the bucket :)

I agree that jack programs are the way to go for real time stuff, but there are some instances where certain plugins simply require way too much CPU time to be practical on most machines as a real-time app, and some sort of plugin  architecture can be of great benefit.

---

