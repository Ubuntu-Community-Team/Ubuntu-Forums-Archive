---
title: "To those who've installed Amarok 1.4.2..."
date: 2006-08-26
forum: The Cafe
---

### Post by GarethMB on 2006-08-26
Does playing a media CD use unreal amounts of system crushing RAM for you or is it just me that's suffering this?

(My specs FWIW: 1.3ghz, 1GB RAM, intel852chipset)

---

### Post by ComplexNumber on 2006-08-26
> **GarethMB said:**
> Does playing a media CD use unreal amounts of system crushing RAM for you or is it just me that's suffering this?

(My specs FWIW: 1.3ghz, 1GB RAM, intel852chipset)
amarok does for everyone. its not just you. Linux Format magazine reviewed it the other month and gave it about 3 or 4(out of 10) stars because its resource hogging nature and instability were 2 of the areas that gave it such  a low rating.
they suggested that the devs have "gone too far" now, and its now about time to get rid of  a lot of the bloat to make it leaner, faster, more efficient, more stable, and less resource hungry.

---

### Post by Kalinda on 2006-08-26
O__O!

Hmm... well, I love Amarok... but maybe that's why my system has been slow sometimes lately. It actually really started happening yesturday.. but when I checked KSysGuard, nothing was wrong.. maybe it's the new version of Azureus.. or my own lack of memory..

I've never played CDs with Amarok.. but hopefully they'll fix it.

---

### Post by Terracotta on 2006-08-26
> **ComplexNumber said:**
> amarok does for everyone. its not just you. Linux Format magazine reviewed it the other month and gave it about 3 or 4(out of 10) stars because its resource hogging nature and instability were 2 of the areas that gave it such  a low rating.
they suggested that the devs have "gone too far" now, and its now about time to get rid of  a lot of the bloat to make it leaner, faster, more efficient, more stable, and less resource hungry.

I do feel the same way about that, it's a great player, best music player/manager I've ever seen, but it does a bit too much, but I think they're working on it, and well Amarok 2.0 is qt4 based so I think that one's gonna use less resources, and I hope they'll polish the code a bit more.

@GarethMB: don't you mean amarok 1.4.1?

---

### Post by Colonel Kilkenny on 2006-08-26
1.4.2 debs are available at this site: [http://imbrandon.com/packages/pool/dapper/amarok/](http://imbrandon.com/packages/pool/dapper/amarok/)

---

### Post by Terracotta on 2006-08-26
> **Colonel Kilkenny said:**
> 1.4.2 debs are available at this site: [http://imbrandon.com/packages/pool/dapper/amarok/](http://imbrandon.com/packages/pool/dapper/amarok/)
I think I'll wait for Jonathan riddel to package it :). But once installed I'll let you know.

---

### Post by jdong on 2006-08-26
imbrandon is a kubuntu developer and his packages are basically the way they will be in official Ubuntu repositories.

I have already approved Backports requests for amarok 1.4.2, so as soon as the Ubuntu Archive Admin team gets around to processing the build, we'll start seeing Amarok 1.4.2 in Backports.

---

### Post by Jucato on 2006-08-27
yep, imbradon's a Kubuntu dev, and his packages are safe.

Amarok does use up quite a bit of RAM, but I have not experienced playing an Audio CD (is that what you mean by media CD?). But I haven't experienced it crushing my RAM, and I'm only on a 640MB RAM.

jdong: will it really be put in Backports? I always thought  that KDE, KOffice, and Amarok will always be in the special repos created for it (or I might have understood imbradon and Riddell wrong).

---

### Post by GarethMB on 2006-08-27
I've no problems with Amarok's memory consumtion listening to any other files that Audio CD's. And it's simply the best media player for KDE for my needs period.

But I try not to rip CD's i own, and just play them. But in this latest release, the first 15 seconds or so are just unbelievably stuttery, which just isn't usable.

---

### Post by .t. on 2006-08-27
Why don't you try with a different engine? You could always compile in support for the Helix engine, and see how that copes.

---

### Post by GarethMB on 2006-08-27
Amarok's huge. I don't feel confident (read competent) enough to compile it myself.

---

### Post by der_joachim on 2006-08-27
@Gareth: somewhere on the forum there is a HOWTO for compiling SVN versions of Amarok. Just run a shell script, sit back and relax and watch how your shiny new Amarok is being compiled.

---

### Post by GarethMB on 2006-08-27
Which Engine(s) is that for though?

---

### Post by jdong on 2006-08-27
> **Fenyx said:**
> 
jdong: will it really be put in Backports? I always thought  that KDE, KOffice, and Amarok will always be in the special repos created for it (or I might have understood imbradon and Riddell wrong).

In this case, the backport is fairly trivial and non-invasive. That is often not the case with, say, a KDE backport.

---

### Post by ChrisNiemy on 2006-08-28
Hi!

I installed the debs from imbrand and whoah 1.4.2 makes a small performance difference to previous. The package works great without complications.

"Working" with Amarok now seems a bit faster, and no GUI freezes anymore!! :D :D or less ;)

configuration was not altered from the new package.

THANKS A LOT FOR THE LINK!

Off topic:
I have to use ubuntu and amarok as a party jukebox ;) in november on my mum's 50th birthday. this will rock. gonna be an oldie party... (party with ubuntu always a good choice, you can hand out your friends than ubuntu cds when they're drunk ;) - mostly they were impressed by the many different gl screensavers and compiz of course...)

regards, -Chris

---

### Post by Terracotta on 2006-08-28
> **jdong said:**
> In this case, the backport is fairly trivial and non-invasive. That is often not the case with, say, a KDE backport.

So Koffice and Amarok will be ported to backports where for the new KDE one will need the jriddel repos? Or am I mistaken?

---

### Post by jdong on 2006-08-28
> **Terracotta said:**
> So Koffice and Amarok will be ported to backports where for the new KDE one will need the jriddel repos? Or am I mistaken?
Well, I can't say that for sure... It depends on how much I'd have to change the source code for Koffice or Amarok or whatever package in order to get it working on Dapper.

Backports really doesn't like to modify source packages at all -- it should be a clean recompile. If that can't be done, then it's more more appropriate in a jriddel repo.

---

### Post by Terracotta on 2006-08-28
> **jdong said:**
> Well, I can't say that for sure... It depends on how much I'd have to change the source code for Koffice or Amarok or whatever package in order to get it working on Dapper.

Backports really doesn't like to modify source packages at all -- it should be a clean recompile. If that can't be done, then it's more more appropriate in a jriddel repo.
Ah ok, just want to point out that I've tried the 1.4.2 version and the FLAC support bug is still not solved (a bit painfull when you've ripped all your music to flac :|).

---

### Post by Colonel Kilkenny on 2006-08-28
Isn't that flac-thing a bug in xine?
At least I got it fixed by using some xine*.debs I found here in these forums...

---

### Post by GarethMB on 2006-08-28
Yeah it was a xine bug. And mine works fine. I'm listening to FLAC songs now.

---

### Post by sultanoswing on 2006-08-28
Annoyingly, the new version (1.4.2) managed to lose all my folder.jpg album covers which had been working in 1.4.1. This is from the packaged version (J. Riddels 1.4.1 worked) from IMBrandon's and a self-compiled SVN version. Using MySQL 5.0.22 - but the bug is present in SQLite as well (and after recreating profiles and databases)

To answer another poster above, one advantage of a self-compile is that you can compile in alternative engines, as xmms dies on a few of my mp3's for some unknown reason.

---

### Post by mega on 2006-08-28
is this in a repository anyway?

I dont like doing apt by hand, always break dependencies

---

### Post by jdong on 2006-08-28
> **mega said:**
> is this in a repository anyway?

I dont like doing apt by hand, always break dependencies

[http://www.imbrandon.com/2006/08/23/get-it-hot-amarok-142-released/](http://www.imbrandon.com/2006/08/23/get-it-hot-amarok-142-released/)

Yes, from imbrandon's repository. It will also be available from dapper-backports soon if you wait... I've been told that the build request could be pushed through as early as tomorrow.

---

### Post by ChrisNiemy on 2006-08-29
> **Colonel Kilkenny said:**
> Isn't that flac-thing a bug in xine?
At least I got it fixed by using some xine*.debs I found here in these forums...

Hi! Have a link to it? thanks :)

EDIT: I think it is this one here:
[http://www.ubuntuforums.org/showthread.php?t=210683&page=2&highlight=xine+flac](http://www.ubuntuforums.org/showthread.php?t=210683&page=2&highlight=xine+flac)  (post no 17)

---

### Post by muz1 on 2006-08-29
> **ComplexNumber said:**
> amarok does for everyone. its not just you. Linux Format magazine reviewed it the other month and gave it about 3 or 4(out of 10) stars because its resource hogging nature and instability were 2 of the areas that gave it such  a low rating.
they suggested that the devs have "gone too far" now, and its now about time to get rid of  a lot of the bloat to make it leaner, faster, more efficient, more stable, and less resource hungry.

Hey.
It's funny you say that because I have noticed that it does tend to slow down and I am still on a 1.3. What have the major changes been since 1.3 that would be causing the bloatware and system resource munching effect?

Cheers
muz

---

### Post by ChrisNiemy on 2006-08-29
Hi!

Mhm, 1.3 wasnt slow, but for example playin CD Audio was complicated and not well done.

I think it had an performance boost since 1.4.1 generally. I would give it 8 of 10 points, or 9 :) Runs fast enough on my Athlon 1,4GHz with 512MB RAM.

greets, -Chris

---

### Post by sultanoswing on 2006-08-29
I'd be a little concerned about this one going into the Official Repos, as the missing album cover art bug seems to be hitting a few people. I filed a bug:

[http://bugs.kde.org/show_bug.cgi?id=133174](http://bugs.kde.org/show_bug.cgi?id=133174)

---

### Post by Jucato on 2006-08-31
Amarok 1.4.2 now available from Kubuntu.org!
[http://kubuntu.org/announcements/amarok-1.4.2.php](http://kubuntu.org/announcements/amarok-1.4.2.php)

It's still imbrandon's packages, signed by Riddell, for you doubters out there. Just kidding. Hehehe!

---

### Post by jdong on 2006-08-31
Just an explanation, amarok 1.4.2 did not make Dapper Backports because of a technicality (one of the libraries it needs to build with is in Edgy's main, but Dapper's universe). I intend on asking the launchpad folks to lift the main/universe restrictions on dapper-backports, but right now they are busy preparing Knot2, and I'd rather see a knot2 CD today so let's let them do their work :)

---

### Post by Jucato on 2006-08-31
IMHO maybe it would be good to just keep Amarok, KOffice, and KDE on separate repositories, seeing that they're always in a state of change. Other apps like KTorrent, Kopete, and Konversation would probably be the best ones to go into dapper-backports.

---

### Post by jdong on 2006-08-31
By some stroke of magic that I cannot explain, amarok managed to build and upload to dapper-backports. So, yay, I guess?

/me is utterly confused and goes back to bed.

---

### Post by Jucato on 2006-08-31
So I've heard you say in IRC.

(And btw, you still aren't asleep :D )

---

### Post by jdong on 2006-08-31
I decided dist-upgrading to edgy would be more fun than sleeping.

---

### Post by Jucato on 2006-08-31
I can knot be more fun than downloading Knot 2 RC... eheheh!

Ok, this is getting off-topic...

---

### Post by mariahoney on 2006-09-01
I had the "where did my album art go" problem at first... all I had to do was open the cover manager.  voila!

---

### Post by stoeptegel on 2006-09-01
Hmm, one thing i do not like in 1.4.2. is that it doesn't start playing automaticly anymore when the playlist is empty and you load a file from the file panel in the playlist. This should have better been optional in my view, but maybe this is just me and my habits on amarok usage. Maybe the program was just too well done before :tongue:

---

### Post by Skye on 2006-09-01
To reply to the original poster, my custom compile of amarok 1.4.2  went from using 48 megs of ram while playing mp3's from my NFS server to using 50 megs while listening to a CD, which doesn't seem like anything approaching massive bloat to me, to be honest.

I've never had a problem with amarok stability- I can run it continuously for weeks, and it doesn't slow down at all.  It's a truely wonderful application.

---

### Post by GarethMB on 2006-09-02
I've just done an SVN script install. It's fine now. That's one crappy build from imbrandon.:-\"

---

