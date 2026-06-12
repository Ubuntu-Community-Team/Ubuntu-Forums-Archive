---
title: "My Wish List"
date: 2004-12-20
forum: Ubuntu Backports
---

### Post by dawynn on 2004-12-20
Currently, I'm in Hoary, because of wanting xorg and usplash (when its available), but I'm planning to stick with the stable release after Hoary goes in.

That being said, these are a few things I would like to see made available in Ubuntu, whether in Universe, Multiverse, or Backport:

Lilypond.  Not sure why this wasn't picked up by either Warty or Hoary.  It's part of the GNU project, with a GPL license.  Debian keeps .debs, but Ubuntu ignores it, even while picking up the front-end for it (Denemo).  See [http://www.lilypond.org/web/](http://www.lilypond.org/web/).

Doomsday Engine.  (See "Source Code" at [http://sourceforge.net/project/showfiles.php?group_id=74815](http://sourceforge.net/project/showfiles.php?group_id=74815).  For more information, see [http://www.doomsdayhq.com/](http://www.doomsdayhq.com/))  jDoom, jHexen, jHeretic.  This is a source port of the Doom / Hexen / Heretic code that allows for 3D Models and enhanced textures.  It's also one of the few ports that fully supports Hexen.  Engine license: GPL, but like all Doom sourceports, needs the commercial or shareware data files.  It would also be nice to have separate packages for the three resource packs (jDoom Resources, jHeretic Resource Pack, jHexen Resource Pack -- can be found on the same page as the "Source Code").

Hammer of Thyrion (formerly Anvil of Thyrion).  See [http://sourceforge.net/projects/uhexen2/](http://sourceforge.net/projects/uhexen2/).  This is a port of Hexen 2 for Linux.  Anvil of Thyrion was quite buggy.  Hammer of Thyrion is trying to correct that.  They've already corrected the fullscreen issue.  Hopefully, they'll hit the sound problems soon.  Game runs quite well with sound disabled, though.  Engine license: GPL, but requires commercial version of data files.

---

### Post by tanari on 2004-12-20
I want to add some programms
I think there must be some cd burning programm (gnomebaker, coaster), 
programm for audio cd creation 
gparted (gparted.sf.net)
mplayer + all codecs

---

### Post by jdong on 2004-12-20
I'll definitely see to these when I come back from vacation.

Lilypond and gparted are definite possibilities.

I can't package mplayer codecs due to potential legal conflicts.


I'm not gonna test my luck with SF by packaging large games!

---

### Post by Averatec5400 on 2004-12-21
I have been trying to get pgadmin3, but there are a lot of extra deps needed for the compile, I wasn't sure if I wanted to take that step or not.

---

### Post by WW on 2004-12-21
Re: lilypond: [http://ubuntuforums.org/showthread.php?t=4956](http://ubuntuforums.org/showthread.php?t=4956)

---

### Post by dawynn on 2004-12-22
That's great.  Has anyone actually checked that reference?  The link points to a Debian bug that indicates that the problem was not with Lilypond, but with mftrace.  The bug also documents that mftrace was updated and is working fine now.  And Debian Unstable has Lilypond 2.2.6.  So, with an update of mftrace, Lilypond should also be compilable in Ubuntu.

I would be quite happy to see Lilypond in Hoary Universe (where it should be) instead of Backports.

---

### Post by nocturn on 2004-12-23
[QUOTE=jdong]I'll definitely see to these when I come back from vacation.

Lilypond and gparted are definite possibilities.

I can't package mplayer codecs due to potential legal conflicts.


I'm not gonna test my luck with SF by packaging large games![/QUOTE]

Is there any restriction on packaging mplayer without codecs?
If not, this would be nice as the codecs can be downloaded an dropped in easily.

---

