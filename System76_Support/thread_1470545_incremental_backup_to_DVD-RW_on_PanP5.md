---
title: "incremental backup to DVD-RW on PanP5"
date: 2010-05-02
forum: System76 Support
---

### Post by tlroche on 2010-05-02
summary: I'd like to do incremental backup from my PanP5 to DVD-RW discs with `rsync`, as I formerly did on winxp. What do I need to do differently?

details:

My former daily-work box was a TP with winxp, cygwin, and DLA, which I still have. I also still have the bash scripts I used on it for incremental backups of various parts of the HD to DVD-RW. The lifecycle was like

[LIST=1]
[*](once) initialize/format a blank DVD-RW (using DLA UI)
[*](many) run script to rsync files to the DVD-RW
[*](once) once DVD-RW filled, finalize it (using DLA UI)
[/LIST]

I want to resume doing this on my current daily-work box, a PanP5 running karmic (and soon hopefully lucid), with a built-in DVD-RW drive. I'm wondering,

[LIST=1]
[*]What do I need to do differently, esp for initialization and finalization?
[*]Which packages/tools do folks recommend? brasero? dvd+rw-tools? wodim?
[*]Is there any way to make the DVDs compatible with winxp, so that I could read and write from either OS?
[*]Are there gotchas, tips, or tricks I should know about?
[/LIST]

TIA, Tom Roche <Tom_Roche@pobox.com>

---

### Post by PatrickVogeli on 2010-05-03
not that I know anything about your problem, but may I ask why DVD-RW? External hard drives are extremely cheap these days, and they are faster, bigger and more secure that DVD-RW. I'm really curious about this one.

---

### Post by tlroche on 2010-05-03
> **PatrickVogeli said:**
> why DVD-RW? External hard drives are extremely cheap these days

HDs and SSDs are not nearly as cheap as DVDs (esp if one has access to a bulk supply :-) 

> **PatrickVogeli said:**
> [External hard drives] are faster [than] DVD-RW.

No doubt, but I typically run backups in downtime, and incrementals usually don't involve too much data, so the speed delta doesn't matter much in practice.

> **PatrickVogeli said:**
> [External hard drives are] bigger [than] DVD-RW.

True again, but, again, not a big win for the incremental usecase, esp if one rolls them over (see next point).

> **PatrickVogeli said:**
> [External hard drives are] more secure [than] DVD-RW.

Really? DVDs are so cheap that one can regularly take a backup disk, secure it offsite, and start backup to a new disk. Maybe you've got the cash to do that with HD/SSD, but to me, the opportunity cost seems pretty high.

Also, DVDs are a helluva lot easier to label :-)

---

### Post by isantop on 2010-05-04
Before I get you going in rsync, have you thought about cloud backup options? Dropbox and Ubuntu One offer 2 GB free, and 50 GB for $10 per month. Not a bad deal. Plus, it is nearly invisible and pretty secure these days.

---

### Post by tlroche on 2010-05-04
> **tlroche said:**
> summary: I'd like to do incremental backup from my PanP5 to DVD-RW discs with `rsync`, as I formerly did on winxp. [...] I'm wondering,
[LIST=1]
[*]What do I need to do differently, esp for initialization and finalization?
[*]Which packages/tools do folks recommend? brasero? dvd+rw-tools? wodim?
[*]Is there any way to make the DVDs compatible with winxp, so that I could read and write from either OS?
[*]Are there gotchas, tips, or tricks I should know about?
[/LIST]


> **isantop said:**
> Before I get you going in rsync,

Just to clarify, I've already got working rsync scripts. I wanna know,
what do I need to do to mount a DVD-RW before, and umount after, I run
the scripts, so I can reuse the disks for repeated incremental backups.

> **isantop said:**
> have you thought about cloud backup options?

I have, but

[LIST=1]
[*]I've only got 10-20 GB to backup. It's more than I can get on the free plans, and less than it seems worth to pay for.
[*]I have access to a stock of very cheap DVDs.
[/LIST]

---

