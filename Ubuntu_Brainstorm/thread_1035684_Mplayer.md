---
title: "Mplayer"
date: 2009-01-10
forum: Ubuntu Brainstorm
---

### Post by kingleer on 2009-01-10
Probably a noob question, but why can't Ubuntu come with mplayer or Vlc installed? Both can play anything out there out of the box. Or is there some legal barrier? 

I'm pretty sure that mplayer is GLP 3.0

---

### Post by andrew.46 on 2009-01-10
Hi kingleer,

> **kingleer said:**
> Probably a noob question, but why can't Ubuntu come with mplayer or Vlc installed? Both can play anything out there out of the box. Or is there some legal barrier? 

I can only speak of MPlayer because my experience lies chiefly there. Not just Ubuntu but several other distros feel there is a *potential* legal problem with the codecs available for MPlayer and distribute either a crippled version or chose not to distribute it at all. Small wonder then that MPlayer is not part of a default install :-).

Another greater problem is the development model of MPlayer. A 'release' version rarely occurs and development is instead focused on a more cutting edge version that is released to the public via subversion. This runs counter to the policy of some distros which prefer the rubber stamp of 'release version'. For Ubuntu this means the oficial MPlayer is datestamped 2007 while the 2009 version is out an solid as a rock, although I can only speak for r28288 :-).

While MPlayer will probably never feature as part of a default install you do have a few choices:

[LIST=1]
[*]Just use the outdated MPlayer from the Ubuntu repository.
[*]Use the slightly 'spiced-up' version from Medibuntu.
[*]Compile your own svn MPlayer, there is a guide on these forums.
[/LIST]

Nice to have some choice, pity about the politics of it all :-).

Andrew

---

### Post by gnomeuser on 2009-01-10
That would be:

a) Illegal, since both mplayer and vlc bundle patented codec support which cannot be disabled easily (and let's be honest, nobody is requesting them not for the interface but because generally they play everything you throw at them, if we start ripping out this functionality to comply with the law then the demand fades). 

b) Senseless, gstreamer offers us a technologically advanced platform for integrating multimedia in the desktop, it is not a separate program. Additionally gstreamer is the only multimedia framework that does testing with each commit and has many paid developers with a track record of fixing bugs swiftly. This increases code quality and supportability.

---

### Post by andrew.46 on 2009-01-10
Hi again,

And there you have both sides of the disagreement :-). I found an interesting comment in a [wiki article]("http://en.wikipedia.org/wiki/FFmpeg") that actually was talking about ffmpeg that speaks of the legal issues:

> FFmpeg's legal status varies by country. Some included codecs, such as Sorenson 3, are claimed by patent holders. Such claims may be enforceable in countries like the United States which have implemented software patents, but are considered unenforceable or void in countries that have not implemented software patents. Furthermore, many of these codecs are only released under terms that forbid reverse engineering, even for purposes of interoperability. However, these terms of use are forbidden in certain countries. For example, some European Union nations have not implemented software patents and/or have laws expressly allowing reverse engineering for purposes of interoperability. In any case, many Linux distributions do not include FFmpeg to avoid legal complications.

It is a tangled mess that as usual has a lot to do with money, power and ownership.

 Andrew

---

