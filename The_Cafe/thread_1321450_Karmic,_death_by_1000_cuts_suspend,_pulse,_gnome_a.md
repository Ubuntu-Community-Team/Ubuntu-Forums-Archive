---
title: "Karmic, death by 1000 cuts: suspend, pulse, gnome apps and more"
date: 2009-11-10
forum: The Cafe
---

### Post by karmakowski on 2009-11-10
Hello, 

I switched from another distribution (no, I'm not gonna compare) with kde3 to Ubuntu with Gnome just before the Karmic release and was pretty amazed. Installation, even with lvm and disk encryption, took me less than half an hour, everything worked ootb, dropbox, boxee, google and other software providers I use had separate repositories for Ubuntu... great. 

After upgrading to 9.10 and using the system for a while the experience got much worse. First, the suspend on my Inspiron 600m stopped working, it just freezes on resume, then I started to notice little inconveniences plaguing the system:
-- problems with pulse: video in smplayer was freezing after I skipped a few seconds, it turned out to be a problem with alsa and pulse, I switched smplayer to sole pulse and this particular problem went away, another occurred though -- now pulse doesn't remember the volume set for mplayer and starts every video at 100% loudness (I still hear a little bell in my head);
-- inability to play .arm files: not a big thing but it requires ffmpeg (iirc) compiled with support for this audio format, unfortunately, that version is not available for Karmic yet, I gave up before compiling ffmpeg myself;
-- inflexibility of gnome/gtk apps: I could give quite a few examples but [this one little feature that cannot get implemented for SIX YEARS]("https://bugzilla.gnome.org/show_bug.cgi?id=75420") just tops them all;
-- general slowness of the system: after a day or day and a half of using the system it gets really slow -- I know, my computer isn't the newest and greatest, but still -- and requires a reboot like... Windows. 

What I would like to ask you, the more experienced Ubuntu users, is whether you get over these little problems sometime or is it a constant battle against your own system with every upgrade breaking something?

---

### Post by 3rdalbum on 2009-11-10
My audio works perfectly here, as long as I have Pulseaudio.

I'm not familiar with .arm files. I know that Karmic's version of FFMPEG does not contain AAC encoding support because there is some concern that part of the code might be under a different license.

Ubuntu actually has two versions of "libav*" - there's the regular set of libav libraries under a free license, and there's the "extra" or "unstripped" versions which contain possibly patented codecs. You may need to install the "extra" version to get full support; except for AAC of course.

Sometimes the Gnome developers get percieved as "interface nazis", but in reality their desktop is designed to be consistent from the get-go, with their own human interface guidelines. Sometimes, people suggest ideas that don't fit with what Gnome wants the desktop to look and feel like.

If you want massive configurability, you should continue to use KDE. I personally hate seeing too many options in a "settings" window (it gets overwhelming, especially when you go into the Internet Settings control panel in Windows XP!), and this is one thing I like about Gnome - sane defaults, only the options I really need.

I haven't noticed a slowness of the system - what distro were you using before? I go ages in between reboots, I just suspend the system all the time.

---

### Post by Tibuda on 2009-11-10
> **karmakowski said:**
> -- inflexibility of gnome/gtk apps: I could give quite a few examples but [this one little feature that cannot get implemented for SIX YEARS]("https://bugzilla.gnome.org/show_bug.cgi?id=75420") just tops them all;

try terminator: [http://launchpad.net/terminator](http://launchpad.net/terminator)

---

### Post by mikewhatever on 2009-11-10
> **karmakowski said:**
> .........

What I would like to ask you, the more experienced Ubuntu users, is whether you get over these little problems sometime or is it a constant battle against your own system with every upgrade breaking something?

Some of the problems may get solved within a month or so by updating the system, while others will need searching for workarounds. It looks like people have less problems with clean installs, then with upgrades, so you might want to try that. Most importantly, take it easy, there is no need to fight it too much. If an older version of Ubuntu, say Jaunty, works for you, just use it.

---

### Post by gradinaruvasile on 2009-11-10
Use the previous release for 1-2 months. Then upgrade/reinstall. Never upgrade on the spot.

---

### Post by pelle.k on 2009-11-10
> Use the previous release for 1-2 months. Then upgrade/reinstall. Never upgrade on the spot.
That's actually really good advice. Canonical really should put up a big sign on their download page about that. It may not reflect very good on ubuntu as a distro though, so i can see why the don't.
The same is true for OS X, and Windows.

> or is it a constant battle against your own system with every upgrade breaking something?
There are regressions, sure. You can often prevent much of that by buying hardware that is "supported" in linux. I bet many ATI users have had their fare share of pain though, but that goes for most distros.
You should also remember that non LTS releases may not always be perfectly "stable". Karmic is probably the testing ground for a lot of new technologies ubuntu 10.04 LTS will be based on, hence the "rough ride".

---

### Post by DeadSuperHero on 2009-11-10
> **gradinaruvasile said:**
> Use the previous release for 1-2 months. Then upgrade/reinstall. Never upgrade on the spot.

Isn't that kind of off-putting to most people, though? As someone who uses Alpha after Alpha, I find that the latest OS always works great on my system after doing some bug reporting here and there. Karmic isn't perfect, but it's pretty good in my opinion.

---

### Post by andrew.46 on 2009-11-10
Hi karmakowski,

> **karmakowski said:**
> -- inability to play .arm files: not a big thing but it requires ffmpeg (iirc) compiled with support for this audio format, unfortunately, that version is not available for Karmic yet, I gave up before compiling ffmpeg myself

I suspect amr support will be available for Lucid as there is now a free implementation *libopencore-amr*. Although *playback* is not available in the stock Karmic there are development files in the repository for libopencore-amr and if you are keen to get amr playback under Karmic it can be done. 

Andrew

---

### Post by karmakowski on 2009-11-14
I apologize for leaving this topic like that, I had some file system troubles (a propos: [http://ubuntuforums.org/showthread.php?p=8318355](http://ubuntuforums.org/showthread.php?p=8318355))

> **3rdalbum said:**
> My audio works perfectly here, as long as I have Pulseaudio.

My audio is fine. It's just that every time mplayer (smplayer) opens a new file it restores the default volume, 40% only now for some reason, not 100 anymore so also not that annoying. 

> **3rdalbum said:**
> Sometimes the Gnome developers get percieved as "interface nazis", but in reality their desktop is designed to be consistent from the get-go

I understand that and I'm not suggesting it's a bad policy -- gnome is definitely better than kde4 in almost every way -- but not being able to set your greeting (is that what you call "On Thu, 2009-11-12 at 18:37 +0100, someone wrote:" in e-mail replies?) can be frustrating. 

> **danielrmt said:**
> try terminator: [http://launchpad.net/terminator](http://launchpad.net/terminator)

Will do, thanks. 

> **gradinaruvasile said:**
> Use the previous release for 1-2 months. Then upgrade/reinstall. Never upgrade on the spot.
> **mikewhatever said:**
> Some of the problems may get solved within a month or so by updating the system, while others will need searching for workarounds. It looks like people have less problems with clean installs, then with upgrades, so you might want to try that.

Hm, if I wanted to do reinstall every six months, I would still be using Windows. I'll try putting upgrades off a little though. 

> **andrew.46 said:**
>  there are development files in the repository for libopencore-amr and if you are keen to get amr playback under Karmic it can be done. 

Thanks for the tip.

---

