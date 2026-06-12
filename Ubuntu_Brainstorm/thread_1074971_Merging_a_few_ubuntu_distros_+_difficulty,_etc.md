---
title: "Merging a few ubuntu distros + difficulty, etc"
date: 2009-02-19
forum: Ubuntu Brainstorm
---

### Post by TristanM-Tx on 2009-02-19
Hi everyone,
I have been messing with UbuntuStudio lately and have enjoyed it quite a bit since it has a good set of multimedia tools with it in a small amount of space.  I am also interested in security and like the BackTrack2 distros of Knoppix, and have been checking into installing nbuntu to see if it measures up to BackTrack2's capabilities package-wise.  

I am not a developer anymore, and dont know C++ enough to contribute, yet I later started thinking about a unification of the various versions of Ubuntu in one DVD image.  Some people are going to say this is a stupid idea, and others won't.  I would personally like to see the multimedia toolbox attributes of the UbuntuStudio distros merged with a security toolbox similar too BackTrack2 (or nBuntu), but also with applications for scientific research built in.  I am actually surprised that there is not a SciBuntu for researchers and scientific applications, but I get the impression that is in the EdBuntu realm (I havent tried EdBuntu yet)

Anyway- 4.3 gigs could hold alot for such an endeavor, and Ubuntu Studio is only about a gig and a half.  I have no idea of how hard it would be to merge distributions.  I presume a transition from nBuntu for security applications would be alot easier than trying to migrate BackTrack2 from Knoppix to Debian architecture.  (It would also be neato if the LiveDVD installer boot disk had a boot option to operate like the Ophtcrack distro to help our poor Windows users get their admin passwords if we need it (I had to use Ophtcrack at my job when I inherited an XP box and didn't want to call tech support)

That gets into another addition to a security distribution- the addition of a suite of systems and network troubleshooting tools for IT workers.

Anyway- I think such a unified distribution would be red hot.  I haven't looked at Ubuntu Ultimate in a long time, but if I recall it was more filled with things like games and themes rather than putting those things on the backburner entirely, and I am thinking of something more along the lines of a multimedia, security, network and systems administration, and scientific toolbox distro that would be all in one on a LiveDVD.  The installer would as it does now provide packages for each and all as optional during the install.

Anyway, again, it will be viewed as a dumb idea to some, but I wanted to heard other's thoughts about it, and was also curious about how hard it is to actually make a custom distro like that - or- a better way to describe it would be to merge existing distros, and how hard that would be.

(I guess if I was a real moron I would suggest throwing in the MythTV stuff too!  LOL)
Thanks,
-T in Texas

---

### Post by benj1 on 2009-02-19
Good idea 
a good idea would be to put all the main buntus on to a single DVD for the shipit service, wouldn't cost any more (would be easier just having the one DVD) and would mean we could get Xubuntu by shipit aswell.

---

### Post by TristanM-Tx on 2009-02-19
I forgot considering the custom cd distros that are sent out in snail mail, which is another additional benefit as you say, but did consider that it would take the load off of servers hosting packages since the only thing that is crucial would be on the DVD, and the only thing left for the servers would have to do once people have the ISO is to download the updates for the apps they choose to install

---

### Post by smartboyathome on 2009-02-20
Already been thought of. Since some paths are hard coded, it isn't possible to combine the images (at least last I tried, which was admittedly last year).

---

### Post by TristanM-Tx on 2009-02-20
I figured someone may have attempted it on their own, and what you say is sortof what I suspected and was afraid of.  What I was thinking is it might be a good venture for the various developer teams to collaborate on, so that they could merge what is hardcoded collectively (as well as addressing similar issues).  It might help to defragment the development tree by merging these teams.  I recall Linus Torvalds being asked in Revolution OS or The Code Linux about what he felt about the fragmentation of the various linux kernels out there.  It seems like the various types of Ubuntu has a similar fragmentation in distros, even though that would arguably be more of a issue of fragmentation of the Debian distros.

---

### Post by bobbocanfly on 2009-02-20
From what I can tell, the OP is thinking about a standard Ubuntu disk, with a "derivative migration assistant tool thing" on it, which would let you install different derivatives. I could be getting this utterly wrong, but that would be quite easy to do with a shell or Python script. Read the CD seed lists, when apt-get install everything. Apt would do all the hard work of working out what is isntalled, conflicts etc.

Of course, if (he|she) means merging the disks, (he|she) has a lot more work ahead of him.

---

### Post by TristanM-Tx on 2009-02-20
Actually, I was talking about a merged distro disk, with a installation menu that would query which stuff you want [Ubuntu Studio, for example gives you three choices I think- Audio, Video or Graphics production packages)... But I was thinking of it as also having a science package, security package, IT/Sysadmin, etc.]

BUT- what you mention as those being omnibus package groupings option in the Add/Remove Apps window would be just fine too (e.g. "Install security package suite"- which would be like the apps that Backtrack2 and nBuntu come with).  But really, it just would be cool to have them unified on a DVD as well as a download option, partially to conserve server load, but also just because it would be cool..

---

