---
title: "Transmuter - Convert your FLAC collection to.... anything."
date: 2009-04-09
forum: The Cafe
---

### Post by MetalMusicAddict on 2009-04-09
[_**[SIZE="4"]Transmuter[/SIZE]**_]("https://launchpad.net/transmuter")
[I][SIZE="2"]
"Take your entire FLAC collection and convert it to another format. People are using FLAC for archival purposes but the lack of support in popular media devices usually means one has to re-rip their CDs to another supported format or convert files an album at an time with current, often complicated solutions. Transmuter was created to let you convert your ENTIRE music collection to a format of your choice with ease.

Supported output formats include: Vorbis, MP3, WAV, FAAC, FLAC (1 compression level to another), Wavpack, Musepack, AAC+, Apple Lossless (via FFMPEG) and MP3HD. *ANY* format that has a Linux encoder is planned to be supported.

All tagging is also retained as well as handling in-folder cover art."[/SIZE][/I]


So this is a little project I've been working for a bit after current solutions didn't fit what I needed. I maintain several versions of my collection for various reasons.

It's a python script that atm has the encoder values hard-coded but we're currently working out a user-configurable setup.

How this differs is in it's simplicity and it's future plans. (which we need help with)

You define 3 things.
[LIST]
[*]Root FLAC dir
[*]Output format
[*]Output dir
[/LIST]
All tagging is taken care of. As well as copying album art and even resizing it for use in your RockBox compatible player if you wish.

So if this might interest you come chat with us at #transmuter on Freenode. Python coders are wanted as well as someone willing to make a QT4 or GTK frontend.

---

### Post by gnomeuser on 2009-04-09
doesn't sound that different from soundconverter which is in the repos

---

### Post by MetalMusicAddict on 2009-04-09
> **gnomeuser said:**
> doesn't sound that different from soundconverter which is in the repos
Use it. ;)

---

### Post by gnomeuser on 2009-04-09
> **MetalMusicAddict said:**
> Use it. ;)

I already do, but I was thinking perhaps there was code to be shared. Also there is a GStreamer developer Thomas something dutch.. I forget his name who is doing transcoding work as well though for video mostly it seems.

Sounds like there is an opening for a core set of these functionalities split out on tasks and devices as predefined profiles.

---

### Post by MetalMusicAddict on 2009-04-09
> **gnomeuser said:**
> I already do, but I was thinking perhaps there was code to be shared. Also there is a GStreamer developer Thomas something dutch.. I forget his name who is doing transcoding work as well though for video mostly it seems.

Sounds like there is an opening for a core set of these functionalities split out on tasks and devices as predefined profiles.


"Use it" means use Transmuter. If that's what you meant, wow. That was fast. ;)

Some differences are that we use official upstream encoders not GST. (I'm just not a fan)

We also re-create the entire dir structure. We basically make a mirror of your FLAC collection but in another format. So FLAC needs to be the source. We won't go from 1 lossy format to another for instance. Future plans might include ability to convert from other lossless sources.

We also do a little cover image handling but that's a minor feature.

And making profiles for specific devices is part of the plan.

Maybe we're a mix between soundconverter and abcde? Haven't really thought about it.

This is for a **very specific** use-case. Taking ones FLAC collection and mirroring it in another format. It is defiantly not a general tool for everyone.

---

### Post by insane_alien on 2009-04-09
sounds like what i need. soundconverter takes far too long to process the tags before i can start converting(like 2 hours). where's the .deb? i can't find one on launchpad.

---

### Post by MetalMusicAddict on 2009-04-09
> **insane_alien said:**
> sounds like what i need. soundconverter takes far too long to process the tags before i can start converting(like 2 hours).
Well even that depends on how big your collection is. :) My 700+ CD collection takes 20hrs to convert to Vorbis. Tags are handled at file conversion time. Not *after* everything has been converted.

Planed features include:
[LIST]
[*]Resumable sessions [SIZE="1"](say you lose power or something you'll be able to start over but not at the beginning)[/SIZE]
[*]Convert new files only. [SIZE="1"](adding new CDs to your FLAC collection then rerun Transmuter. It will only convert what's new. If the output dir is the same as a previous convert that is)[/SIZE]
[/LIST]
> **insane_alien said:**
> where's the .deb? i can't find one on launchpad.
We'll have one up in the next week or so. Along with the packaging branch.

---

### Post by insane_alien on 2009-04-09
soundconverter takes ages to load the tags when you add the files to the queue is what i mean. actually transcoding the files takes about 36 hours.

---

### Post by Gary.M on 2009-09-24
This sounds very useful, is it still happening?

---

