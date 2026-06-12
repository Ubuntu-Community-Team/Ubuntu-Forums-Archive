---
title: "Ardour is now incompatible with ALL Ubuntu sound software?"
date: 2012-01-07
forum: Ubuntu Studio
---

### Post by teledyn on 2012-01-07
Sorry for the alarmist headline, but that is what I was just told by the IRC forum for ardour support: the reason I cannot play any files exported by the ardour current now with Ubuntu 11.10 is because the exported files are fine, but ALL the software in Ubuntu is "broken".

Here's the issue: no matter how I export, 32 bit, 16 bit, the file I get plays as if it was an unsigned file, in audacity the file will appear as a half-wav with the base at -1.0; the file will play with sndfile-jackplay, but it comes out as blurps and scratches that you'd expect if this was a half-wave file.  Ardour support tells me to buy the $45 version or go away.

so now what?  I am running Ubuntu 11.10 on an intel x86 platform, and ardour did work fine on this machine under Ubuntu 10.x -- does no one else have this issue?  Could this be somehow a hardware issue?? 

I have attached a screen capture that gives the ardour, jackd and audacity screens -- I have tried all the options on ardour export and I still get the identical half-wave display on audacity.  I'm stuck, stymied and more than a little frustrated as I have all these tracks to render to any kind of shareable format and all of a sudden nothing works :(

---

### Post by teledyn on 2012-01-07
here's another clue: I selected only two tracks of the recording, and on exporting those two tracks the exported file shows that the channels are now OFFSET from zero, down towards the bottom; adding more tracks offsets farther toward the bottom.

and just to make things interesting, I re-opened a previous recording made with ardour and ubuntu back about one year ago (it was the night of the Super Moon actually) and lo, re-exporting that recording, the export WAV file is just fine, it plays perfectly, same number of tracks, same settings, same computer :(

Here's my guess: my son recorded this newer piece and he may have recorded the samples in 32 bit 48k sound whereas the other was 16 bit 44.1k.  Could that explain these results?  It still looks to me like Ardour, despite their ardent assurances, are producing buggy export wav files.

---

### Post by Don-F on 2012-01-13
> **teledyn said:**
> Sorry for the alarmist headline, but that is what I was just told by the IRC forum for ardour support: the reason I cannot play any files exported by the ardour current now with Ubuntu 11.10 is because the exported files are fine, but ALL the software in Ubuntu is "broken".I'm not sure what you were told, but I think either you were told wrong, or you misunderstood.
 
Standard distro builds of Ardour are sometimes "broken" by the packagers' insistence of using the SYSLIBS=1 option when building Ardour. I suppose they do this because it makes the package smaller. Unfortunately it also prevents Ardour's specialized versions of some libraries (e.g. libsndfile) from being built and included in the package.
 
The problem I see in your screenshots does indeed look like there may be an incompatibility between Ardour and whatever version of libsndfile you have on your system. But that's just a guess on my part.
 
> **teledyn said:**
> It still looks to me like Ardour, despite their ardent assurances, are producing buggy export wav files.This is consistent with my "incompatible libsndfile" theory.
 
> **teledyn said:**
> Ardour support tells me to buy the $45 version or go away.Again, I think you are mistaken. Ardour is free software, in both senses of the word "free". Ardour's download page ([http://ardour.org/download](http://ardour.org/download)) says "You can edit the amount in the box below to **any** amount you wish."
 
"Any amount" includes zero.
 
Down below, it does say "Linux users: if you choose to pay nothing for a ready-to-run version, you will get the normal version but should not expect support from our IRC channels or mailing list." You should not *expect* support, but the reality is that I've never heard of anyone being asked how much they donated when they asked a question either on the IRC channel or on the mailing list. It's just a big, happy family.
 
If you enter zero in the amount field, you are taken to a "pretty please" page, but you still have the option to pay nothing.
 
So, my recommendation is that you go ahead and download the package from ardour.org, install that, and see whether it changes anything. If you find that it does, please consider making a donation to help keep the project going.
 
Regards,
Don

---

### Post by teledyn on 2012-01-13
Thanks Don, that's much more encouraging.

I was told that the WAV headers in ALL other Linux software were wrong and that was the reason why I was unable to play any exported files from Ardour regardless what software I tried to use.  I tried to explain that all of these other projects breaking their formats independently and simultaneous to an Ardour update was simply not logical, but the insistence was that Ardour was right and Linux was broken nonetheless.

What I have since discovered is that the 32-bit WAV produced is incompatible, but when I trashed that recording and redid the project in 16 bit samples, everything was fine, it worked just as it had before, and while yes, 32-bit samples would be better, I don't have a very elaborate studio and so it is perfectly acceptable for my purposes.

As for the fee, that may have been my bad, I was already quite upset at the illogic of their response and when I went to the official download page it appeared to require a $45 payment, which is cheap ... when the software works ;) However I didn't yet have that assurance, so I was a bit put off by that and sought my support elsewhere, which is back here at the usually very friendly Ubuntu forums.

If the libs are out of sync, then it likely is a Ubuntu issue since this machine contains no out-of-distro software, and it is a fresh install of 11.10 -- since I don't really need 32-bit support, I can wait for the issue to right itself.

I was really worried because I tried every other multitrack kit in the ubuntu software catalog, and none came even close to Ardour for what we need.

---

### Post by Don-F on 2012-01-13
> **teledyn said:**
> If the libs are out of sync, then it likely is a Ubuntu issueIt's not really a matter of being out of sync. In at least some cases, Paul (Ardour's lead dev) has fixed bugs in library code, and submitted patches to the maintainer. But the maintaner has his/her own priorities, which are not always in line with Ardour's needs, and the patch is rejected or ignored. So essentially the embedded libraries in Ardour are forks.
 
Again, I'm only speculating about what may be going on in your case. Please do let me know whether installing the package from ardour.org solves your problem.
 
Don

---

### Post by teledyn on 2012-01-21
Other priorities taking precidence at the moment so I can't mess with ardour on that machine just now, but this is on my queue and I haven't forgotten ;)

---

### Post by keithpeter on 2012-01-21
Hello All

12.04 testing, and I've just imported a couple of wavs into the repository version of Ardour, messed about with them (stretched, gain automation) and exported them in float 32 bit with no problem.

I'll try this on 11.10 later on.

---

