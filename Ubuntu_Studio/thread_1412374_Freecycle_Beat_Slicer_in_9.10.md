---
title: "Freecycle Beat Slicer in 9.10"
date: 2010-02-21
forum: Ubuntu Studio
---

### Post by rossco_50 on 2010-02-21
Hi,

Is anyone using freecycle without problems in 9.10?

For me there are are number of problems which are apparent in both the repository version and compiling myself. I use it with Jack, rt and my audigy 2.

When selecting a wav, the preview function is broken and has a loud buzzing noise along with stuttering playback. Not that big a deal, but the first indication that there is something wrong.

The wavs I am using are 48khz files, but freecycle states that the project is 44.1 even when jack is set to 48khz. Playback seems to be at the correct speed though. There are occasional crashes due to segmentation faults during extended use.

I am unable to manually edit beatlines i.e. insert my own or move those that were auto-detected. This the real deal breaker for me as the autodetect feature always fails to pick up the last slice of the break. The work around is to set auto detect sensitivity to maximum and delete beatlines I don't want - but this is messy and still doesn't allow me to adjust positions more precisely.

The bpm detection is way out - 100bpm wav shows as 197 bpm. Pressing the the timestretch button causes a crash regardless of the bpm value.

If the application is hopelessly broken (development seems to have stopped), is there a better alternative? I will file a bug report of course.

Rhythm Ferret in Ardour works well as a slicer and is very close to being a replacement to freecycle - it also uses rubberband which is much better than soundtouch. However, I want to sequence in midi with a controller and exporting 1 slice at a time is clumsy compared to the intended functionality of freecycle. Would be great if there is an easy fix to my set-up with freecycle.

Thanks,

Ross

---

### Post by prokoudine on 2010-02-21
> **rossco_50 said:**
> Hi,
Is anyone using freecycle without problems in 9.10?

Most everyone who tried, I'm afriad :(

> There are occasional crashes due to segmentation faults during extended use.

The README says: "if timestretch segfaults, try unlocking all locked beatlines."

> I am unable to manually edit beatlines i.e. insert my own or move those that were auto-detected. This the real deal breaker for me as the autodetect feature always fails to pick up the last slice of the break. The work around is to set auto detect sensitivity to maximum and delete beatlines I don't want - but this is messy and still doesn't allow me to adjust positions more precisely.

Check [docs]("http://mirrors.zerg.biz/nongnu/freecycle/freecycle-manual-1.0.0.tar.gz") just in case.

> If the application is hopelessly broken (development seems to have stopped), is there a better alternative?

Last time I checked the mailing list its developer said that it worked for him. Apparently there is newer code in SVN that at least has initials of Qt4 port, but I haven't given it a go yet.

There is also [Smasher]("http://smasher.sourceforge.net"), but the latest version fails to build on 9.10 for me -- I sent a mail to the developer.

> Rhythm Ferret in Ardour works well as a slicer

Blast! Lucky you :) It find it somewhat demanding for math savvy users.

Maybe together we could persuade Rui to integrate Freecycle into Qtractor, eh? :) [http://www.rncbc.org/drupal/node/61]("http://www.rncbc.org/drupal/node/61")

---

### Post by rossco_50 on 2010-02-21
Hi,

Sorry, just realised that I can move beatlines by using a right click (left click stated in manual). Also, using sox to upsample to 48K instead of audacity this displays correctly in freecycle. 

Thanks for your reply. I had smasher working in 9.10 (haven't tried agian after a reinstall), but I don't think you can export slices, only the whole processed loop. also, the slices are only made on the quatised beat and cant be adjusted as far as I can see. Interesting tool, but not really what I want.

Not sure how to make the bpm detection work properly in freecycle, but I don't really need it and I would prefer to timestretch using rubberband in qtractor or ardour.

I guess freecycle is now working as much as I need it to :D Pity the soundfont export is no longer included as a feature, that would be more useful for me than akai support.

beatslicer in qtractor (what I am also using) +1. Would love that.

I found rhythm ferret quite intuitive to use - same as freecycle really, but it is aimed at internal use in ardour rather than batch exporting ranges as wav to files/other apps. When arodur 3 comes out it might be more useable with midi.

Cheers,

Ross

---

### Post by AutoStatic on 2010-02-21
> **prokoudine said:**
> There is also [Smasher]("http://smasher.sourceforge.net"), but the latest version fails to build on 9.10 for me[https://launchpad.net/~autostatic/+archive/ppa/+sourcepub/946160/+listing-archive-extra](https://launchpad.net/~autostatic/+archive/ppa/+sourcepub/946160/+listing-archive-extra)

---

### Post by prokoudine on 2010-02-21
> **AutoStatic said:**
> [https://launchpad.net/~autostatic/+archive/ppa/+sourcepub/946160/+listing-archive-extra](https://launchpad.net/~autostatic/+archive/ppa/+sourcepub/946160/+listing-archive-extra)
Yay, thanks mate! ;)

---

