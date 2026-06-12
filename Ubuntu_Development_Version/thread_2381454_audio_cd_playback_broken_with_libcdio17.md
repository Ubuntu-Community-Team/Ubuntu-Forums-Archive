---
title: "audio cd playback broken with libcdio17"
date: 2017-12-31
forum: Ubuntu Development Version
---

### Post by mc4man on 2017-12-31
Any player or file manager that uses libcdio, libcdio-paranoia2, libcdio-cdda2 or gvfsd-cdda will crash trying to access.
Probably a couple of players don't use above & are unaffected, ex. vlc
Hard to understand why those uploading the new libcdio & rebuilding off of it just didn't bother to insert an audio cd to test..
[https://bugs.launchpad.net/ubuntu/+source/audacious/+bug/1740644](https://bugs.launchpad.net/ubuntu/+source/audacious/+bug/1740644)

---

### Post by #&amp;thj^% on 2017-12-31
Thanks for the link. I would add me also but a very long subject shortened I plain can not login to Launchpad any more. ;)
Oopps forgot to add audacious is unaffected.

---

### Post by mc4man on 2017-12-31
> **1fallen said:**
> Thanks for the link. I would add me also but a very long subject shortened I plain can not login to Launchpad any more. ;)
Oopps forgot to add audacious is unaffected.
audacious is definitely affected here, are you fully updated?

Ex. with current libcdio-cdda2 & libcdio-paranoia2 using libcdio17
```
$ audacious -E cdda://
Checking /dev/cdrom for cdrom...
		CDROM sensed: MATSHITA DVD-RAM UJ8DB    8.51 SCSI CD-ROM

Verifying drive can read CDDA...
	Expected command set reads OK.
*** Error in `audacious': double free or corruption (out): 0x00007f7078032250 ***
Aborted (core dumped)
```

With downgraded libs using libcdio16
```
$ audacious -E cdda://
Checking /dev/cdrom for cdrom...
		CDROM sensed: MATSHITA DVD-RAM UJ8DB    8.51 SCSI CD-ROM

Verifying drive can read CDDA...
	Expected command set reads OK.
And playback begins..
```

the same 'double free or corruption (out): .....' would be seen with nautilus, nemo, rhythmbox, ect...

---

### Post by #&amp;thj^% on 2018-01-01
> **mc4man said:**
> audacious is definitely affected here, are you fully updated?

the same 'double free or corruption (out): .....' would be seen with nautilus, nemo, rhythmbox, ect...
I should be. :)
NOTE: I have downgraded to: (Not Mentioned in my first reply)
```
libcdio16_0.94-0ubuntu1_amd64.deb
libcdio-cdda2_10.2+0.94+2-2_amd64.deb
libcdio-paranoia2_10.2+0.94+2-2_amd64.deb
```
Results:
```
audacious -E cdda://
Checking /dev/cdrom for cdrom...
		CDROM sensed: hp PLDS  DVDRW  DU8AESH   6HS3 SCSI CD-ROM

Verifying drive can read CDDA...
	Expected command set reads OK.
ERROR mixer.cc:192 [start]: Converting 2 to 4 channels is not implemented.
```

---

### Post by mc4man on 2018-01-01
> **1fallen said:**
> 
ERROR mixer.cc:192 [start]: Converting 2 to 4 channels is not implemented.[/CODE]
that's an audacious thing, seen here in code
[https://github.com/audacious-media-player/audacious-plugins/blob/master/src/mixer/mixer.cc](https://github.com/audacious-media-player/audacious-plugins/blob/master/src/mixer/mixer.cc)

Did it ever work? (I've only laptops here so no clue..

---

### Post by #&amp;thj^% on 2018-01-01
> **mc4man said:**
> that's an audacious thing, seen here in code
[https://github.com/audacious-media-player/audacious-plugins/blob/master/src/mixer/mixer.cc](https://github.com/audacious-media-player/audacious-plugins/blob/master/src/mixer/mixer.cc)

Did it ever work? (I've only laptops here so no clue..
Nope :(
I included that part to see if that was the case. ( an audacious thing,)
Thanks mc4man.
EDIT: In 16.04 with equalizer interface for the LADSPA had it working somewhat..

---

### Post by mc4man on 2018-01-01
> **1fallen said:**
> Nope :(
I included that part to see if that was the case. ( an audacious thing,)
Thanks mc4man.
EDIT: In 16.04 with equalizer interface for the LADSPA had it working somewhat..
Have you ever tried opening aud's preferences > audio > output settings > switching to alsa then fooling around with the alsa output setting (click on settings  button in middle

---

### Post by #&amp;thj^% on 2018-01-01
> **mc4man said:**
> Have you ever tried opening aud's preferences > audio > output settings > switching to alsa then fooling around with the alsa output setting (click on settings  button in middle

:D Till I'm blue in the face, just breaks sound on buntu.>>> 2.1 breaks Pulseaudio for me 4.1 breaks all players I use anyway.
I'm still studying that link you gave me though, for some insight.

---

### Post by mc4man on 2018-01-04
Solved via this commit, should make it's way into Ubuntu at some point
[http://git.savannah.gnu.org/cgit/libcdio.git/commit/?id=f6f9c48fb40b8a1e8218799724b0b61a7161eb1d](http://git.savannah.gnu.org/cgit/libcdio.git/commit/?id=f6f9c48fb40b8a1e8218799724b0b61a7161eb1d)

---

### Post by mc4man on 2018-02-16
> **mc4man said:**
> Solved via this commit, should make it's way into Ubuntu at some point
[http://git.savannah.gnu.org/cgit/libcdio.git/commit/?id=f6f9c48fb40b8a1e8218799724b0b61a7161eb1d](http://git.savannah.gnu.org/cgit/libcdio.git/commit/?id=f6f9c48fb40b8a1e8218799724b0b61a7161eb1d)
Or maybe not.. could be falling thru the crack of Canonical Ubuntu Desktop indifference.

---

### Post by mc4man on 2018-02-19
Will  remove solved until such time actually fixed, if not there will be a ppa package that does work correctly

---

### Post by mc4man on 2018-03-17
Finally fixed with latest libcdio (currently in proposed), only took about 4 months but better late than never
(- was only fixed because it was considered a security risk, not because no one could open  audio cd's..jeez..
[https://nvd.nist.gov/vuln/detail/CVE-2017-18201](https://nvd.nist.gov/vuln/detail/CVE-2017-18201)

So i guess any time I see a crasher that has a double free  will mark bug as a security issue..

---

### Post by amano on 2018-03-18
> **mc4man said:**
> Finally fixed with latest libcdio (currently in proposed), only took about 4 months but better late than never
(- was only fixed because it was considered a security risk, not because no one could open  audio cd's..jeez..
[https://nvd.nist.gov/vuln/detail/CVE-2017-18201](https://nvd.nist.gov/vuln/detail/CVE-2017-18201)

So i guess any time I see a crasher that has a double free  will mark bug as a security issue..

Hmm. It seems to be in the release pocket now.

---

