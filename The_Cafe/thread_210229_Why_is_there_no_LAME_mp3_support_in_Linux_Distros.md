---
title: "Why is there no LAME mp3 support in Linux Distros?"
date: 2006-07-06
forum: The Cafe
---

### Post by taketheveil on 2006-07-06
I was wondering...if LAME is an open source codec of mp3, why doesn't Ubuntu or any other distro come packaged with it right out of the box?  Someone clear this up for me :-k

---

### Post by aysiu on 2006-07-06
I'll clear it up for you--I have no idea what you're talking about.

Ubuntu is one of the few Linux distros that does *not* have MP3 support out of the box. Linspire, Blag, Mepis, and PCLinuxOS have it.

I'm not 100% certain, but I believe SuSE, Xandros, and Mandriva also have it.

---

### Post by yaztromo on 2006-07-06
You install can lame 3.97 from the rarewares repository.

Add this to your sources file
deb [http://www.rarewares.org/debian/packages/unstable/](http://www.rarewares.org/debian/packages/unstable/) ./

You can see the whole list of packages here [http://www.rarewares.org/debian/packages/unstable/](http://www.rarewares.org/debian/packages/unstable/)

---

### Post by AndyCooll on 2006-07-06
I ain't sure what you are talking about either. 

As far as I'm aware (please correct me if I'm wrong) LAME isn't a codec at all. It is only a program which can _create_ mp3 audio files.

:cool:

---

### Post by FISHERMAN on 2006-07-06
I think the TS means: "Why don't FOSS Distro's have MP3-support out of the box, if LAME is FREE Software?

Answer: I don't know(but LAME is an encoder an not a codec)/Wikipedia talks about legal issues: [http://en.wikipedia.org/wiki/LAME#Legal_issues](http://en.wikipedia.org/wiki/LAME#Legal_issues)

---

### Post by aysiu on 2006-07-06
These two threads should help:
[http://ubuntuforums.org/showthread.php?t=143246](http://ubuntuforums.org/showthread.php?t=143246)
[http://ubuntuforums.org/showthread.php?t=167946](http://ubuntuforums.org/showthread.php?t=167946)

---

### Post by PatrickMay16 on 2006-07-06
[QUOTE=yaztromo]You install can lame 3.97 from the rarewares repository.

Add this to your sources file
deb [http://www.rarewares.org/debian/packages/unstable/](http://www.rarewares.org/debian/packages/unstable/) ./

You can see the whole list of packages here [http://www.rarewares.org/debian/packages/unstable/](http://www.rarewares.org/debian/packages/unstable/)[/QUOTE]
You can also get lame from the ubuntu universe or multiverse repository, too. Or is there something special about the version in the rarewares repository?

---

### Post by FredB on 2006-07-07
> **yaztromo said:**
> You install can lame 3.97 from the rarewares repository.

Add this to your sources file
deb [http://www.rarewares.org/debian/packages/unstable/](http://www.rarewares.org/debian/packages/unstable/) ./

You can see the whole list of packages here [http://www.rarewares.org/debian/packages/unstable/](http://www.rarewares.org/debian/packages/unstable/)

Well, lame 3.96 is available from multiverse repository. What are the big difference with 3.97 ?

---

### Post by FredB on 2006-07-07
> **aysiu said:**
> I'll clear it up for you--I have no idea what you're talking about.

Ubuntu is one of the few Linux distros that does *not* have MP3 support out of the box. Linspire, Blag, Mepis, and PCLinuxOS have it.

I'm not 100% certain, but I believe SuSE, Xandros, and Mandriva also have it.

OpenSuSE (at least 10.1), and Fedora Core don't have it too. Because of software patents which are the worse human idea for the last 50 years !

---

### Post by woedend on 2006-07-07
I don't think LAME is exactly legal in some countries.

---

### Post by krazyd on 2006-07-07
LAME can both encode and decode mp3 data.

---

### Post by luca.b on 2006-07-07
There is no LAME by default because the compression algorithm (it is not a software patent) is patented and requires a royalty for commercial use.

---

### Post by DoctorMO on 2006-07-07
Even if the patent is not software I class it under mathamatical and not patentable under most countires laws.

---

### Post by asimon on 2006-07-07
Of course patents alone are not a reason for Ubuntu to not include something. Ubuntu has for example no qualms about enabling patented code in the freetype library* which is in main. I dunno how they exactly decide when it's okay for them to infringe patents and when not to, but they don't seem to regard patented software generally as evil.

*) from the change log:
```
freetype (2.2.1-2)
 Enable full bytecode interpreter instead of just the "non-patented portions".
```

---

### Post by luca.b on 2006-07-07
It's a grey area, IMO. I believe though that MP3 is not included because of the specific requirement for royalties.

---

### Post by aysiu on 2006-07-07
> **luca.b said:**
> It's a grey area, IMO. I believe though that MP3 is not included because of the specific requirement for royalties.
Does anyone know how cost-free distros like PCLinuxOS, Mepis, and Blag get away with not paying royalties for all their proprietary codecs?

---

### Post by Adamant1988 on 2006-07-07
it's something about HOW they are installed.  They don't come as part of the package but you 'install' them yourself.  it's a really weird legal loophole.

---

### Post by luca.b on 2006-07-07
> **aysiu said:**
> Does anyone know how cost-free distros like PCLinuxOS, Mepis, and Blag get away with not paying royalties for all their proprietary codecs?

I'm not really sure. Non-commercial entities I believe are a different thing, but as I haven't checked the mp3 licensing in a long time, I may be wrong.

---

### Post by aysiu on 2006-07-07
> **Adamant1988 said:**
> it's something about HOW they are installed.  They don't come as part of the package but you 'install' them yourself.  it's a really weird legal loophole.
Not in PCLinuxOS, Mepis, and Blag. In those distros, MP3 playback (and a lot of other stuff) comes preinstalled.

---

### Post by yaztromo on 2006-07-18
> **FredB said:**
> Well, lame 3.96 is available from multiverse repository. What are the big difference with 3.97 ?

Huge encoding quality improvements, mainly in vbr mode with --vbr-new flag. See MP3 section of [www.hydrogenaudio.org](www.hydrogenaudio.org) for details.

---

### Post by claydoh on 2006-07-18
> **aysiu said:**
> Not in PCLinuxOS, Mepis, and Blag. In those distros, MP3 playback (and a lot of other stuff) comes preinstalled.

They probably have simply not been "caught" yet
two links:
[http://www.mepis.org/node/10515](http://www.mepis.org/node/10515)
directly relating to Lame
[http://kororaa.org/index.php?entry=entry060512-160752](http://kororaa.org/index.php?entry=entry060512-160752)
this one deals with proprietary (nvidia) video drivers

---

### Post by bonzodog on 2006-07-18
It's interesting to note that mp3 support comes out of the box with Slackware and all it's derived distros - 
I personally think that this is because Patrick is hoping that no one notices kinda thing and will wait until someone official drags him him up about it, then he will simply seperate it from the main install and tell people where to find the codecs.

---

### Post by Dragonbite on 2006-07-18
That's a bit like "it is easier to ask for forgivness than it is to ask for permission"

---

