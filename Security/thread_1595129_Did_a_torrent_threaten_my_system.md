---
title: "Did a torrent threaten my system?"
date: 2010-10-12
forum: Security
---

### Post by Jonny87 on 2010-10-12
The other week I was downloading two torrents and I left it going over night as i was over quoter and my speeds were reduced. The each file was about 600-700MB and I had about 40-50GB (at least) of free space. When I got up in the morning, found that the torrent had stopped due to not enough space.
:confused::confused::confused::confused:

How does a download that is supposed to only take up say 1.4GB at the most, take up over 40GB?????
Under some hasty investigation I found the source of the problem or well what was taking up the space.
~/.xsession-errors
Yes, some how a the plain text file .xsessions-errors had become 42GB in size.
:confused::confused::confused::confused:

How does a plain text file get to be 42GB in size over night? Thats a lot of text...

I quickly deleted that file and both torrents and shut the computer down. When I later rebooted it my free space had come back. And all but one other thing was normal, my evolution account had mysteriously been deleted. all my mail and stuff was still there? but no accounts. Thankfully I was able to restore this though.

So what I want to know is does any of this sound like an attack of any kind? All seems to have been perfectly fine since.

---

### Post by lloyd_b on 2010-10-12
In this case, you've probably already destroyed the info needed to diagnose the problem - the error messages in .xsession-errors would probably have provided a good clue as to what the root problem was...

What was most likely happening is that a particular error was repeating over and over.  I have no guess as to what that error may have been.

Lloyd B.

---

### Post by Jonny87 on 2010-10-13
> **lloyd_b said:**
> In this case, you've probably already destroyed the info needed to diagnose the problem - the error messages in .xsession-errors would probably have provided a good clue as to what the root problem was...

What was most likely happening is that a particular error was repeating over and over.  I have no guess as to what that error may have been.

Lloyd B.

Yea unfortunately that is probably the case. At the time i tried opening it but everything was running slowly and when i viewed it in the terminal I was didn't make much sense of it at the time and I was more concerned about getting my system going again, and getting my free space back. I regret deleting it now though would have been curious to know what it said. I mean 42GB, thats a lot of text. It was just the fact that this is the first time it's happened and as I was downloading torrents at the time which I never truly trust, I was concerned/curious about the nature of it.

---

### Post by lloyd_b on 2010-10-13
> **Jonny87 said:**
> Yea unfortunately that is probably the case. At the time i tried opening it but everything was running slowly and when i viewed it in the terminal I was didn't make much sense of it at the time and I was more concerned about getting my system going again, and getting my free space back. I regret deleting it now though would have been curious to know what it said. I mean 42GB, thats a lot of text. It was just the fact that this is the first time it's happened and as I was downloading torrents at the time which I never truly trust, I was concerned/curious about the nature of it.

I'd be willing to bet against it having anything to do with the torrents themselves, though it could very well be a bug in the torrent software you were using.  Or potentially a bug in any other program that was running at the time.

Since the errors were piling up in .xsession-errors, it has to be from something you had running in your X session at the time.  Which includes any programs that you were running, the desktop itself, any applets running under the desktop, etc.

AFAIK, there has never been an exploit that used torrents to take over a system, other than the obvious "trick them into downloading a trojan via torrents" method (which is no different than any other "trick them into downloading a trojan" attack).  As long as you're not grabbing programs and running them, it's very unlikely you'll ever have a security-related issue from using torrents.

Lloyd B.

---

### Post by Jonny87 on 2010-10-13
> **lloyd_b said:**
> I'd be willing to bet against it having anything to do with the torrents themselves, though it could very well be a bug in the torrent software you were using.  Or potentially a bug in any other program that was running at the time.

Since the errors were piling up in .xsession-errors, it has to be from something you had running in your X session at the time.  Which includes any programs that you were running, the desktop itself, any applets running under the desktop, etc.

AFAIK, there has never been an exploit that used torrents to take over a system, other than the obvious "trick them into downloading a trojan via torrents" method (which is no different than any other "trick them into downloading a trojan" attack).  As long as you're not grabbing programs and running them, it's very unlikely you'll ever have a security-related issue from using torrents.

Lloyd B.

Well yea I guess it was probably the bug/miss hap in the torrent downloader. I usually use Transmission, but his time I was using ktorrent I think. As I left it running over night I think thats the only thing that would have been running, and perhaps evolution but I'm always running that and never had such an issue.

---

