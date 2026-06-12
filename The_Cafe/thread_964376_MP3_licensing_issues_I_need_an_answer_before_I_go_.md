---
title: "MP3 licensing issues: I need an answer before I go crazy"
date: 2008-10-30
forum: The Cafe
---

### Post by Keyper7 on 2008-10-30
Okay, the title is a little bit over-dramatic, but hey, I got your attention if you're reading this. :)

OKay, so I googled and forum-searched and whined and cried for answer for these two questions, but didn't find a satisfactory one so far. The few attempts to answer similar questions I found were more like guesses, without the backing up of an official statement from Canonical or the MP3 patent holders.

So here's hoping that the wonderful community here can help me on this and put an end to my terrible doubts. ;)

1) The fact that MP3 codecs are made available on the official Ubuntu repositories puts Canonical in which legal position?

It's claimed that licensing issues are the reason why MP3 codecs are not distributed with Ubuntu. I can understand that, but why can't the patent holders sue Canonical for hosting easy-to-get compiled binary codecs on the official repositories?

The official LAME site only gives away the source code, and not compiled binaries, to avoid legal problems. Furthermore, it seems that for packages like libdvdcss there's problem even in putting on the official repositories, as they're not there.

Which brings me, by the way, to a sub-question: why the maintainers of Medibuntu are not being sued for giving away libdvdcss?

2) What's the technical and legal differences between downloading gstreamer-ugly and gstreamer-fluendo to decode mp3? Furthermore, what's the difference between the fluendo packages on the repositories and the fluendo packages on the Canonical store?

---

### Post by cardinals_fan on 2008-10-30
mp3 may not be the best example.  If I remember correctly, the owners of the mp3 patents publicly agreed not to sue over them.

The Fluendo codecs are licensed, while the gstreamer-ugly plugins aren't.

I could be wrong, so don't trust my legal advice :D

---

### Post by Jackelope on 2008-10-30
OK, I'm not a lawyer (nor would I want to be), but as far as I know, they can't put the codecs on the CD because the CD is released in America and Japan (countries where it might possibly be illegal to distribute), as well as everywhere else. The repositories are also available to every country, but they require you to acknowledge that it may have legal issues before you download the codecs. In order to include the codecs on the disk, they would have to legally release an alternate version without the codecs (like Linux Mint does). Besides all that, it might go against the Ubuntu philosophy to include them on the disk...not sure. 

Why haven't they been sued? Because they're only distributing them to people who claim they have the right to use the codecs. Canonical's in the legal clear as far as a I know since they shift the burden of proof to the actual user. People would have to sue the users, which is completely improbable because it would take more lawyers to fight the battle and prove it was infringement than it would be worth....in short, no one cares because we're not hurting anything at all and its done the way it is because its easier to skirt the law than fight it.

Still, I wish Canonical would issue a final word on it. This is just my best guess BTW, so if anyone would like to correct this feel free.

---

### Post by SunnyRabbiera on 2008-10-31
Well from what I hear the MP3 format owners do not really 100% object ot linux use or distribution, but the laws themselves are in the way of making MP3 a format everyone can use by default.

---

