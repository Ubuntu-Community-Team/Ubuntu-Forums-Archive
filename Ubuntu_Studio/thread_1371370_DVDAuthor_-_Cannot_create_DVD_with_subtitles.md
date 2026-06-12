---
title: "DVDAuthor - Cannot create DVD with subtitles"
date: 2010-01-03
forum: Ubuntu Studio
---

### Post by Timokl on 2010-01-03
Hi guys and gals,

I have a japanese DVD without subtitles I understand. So my plan is to add the subtitles from an .srt file I downloaded from [http://www.opensubtitles.org](http://www.opensubtitles.org), author a new disc with the new subtitles and watch this new disc.

I copied the movie onto my hard disc with *vobcopy*. I got an .vob file with NTSC video and two audio tracks.

Then, I started *DVDStyler*, added a simple menu (just a Play-Button), the .vob file and added the downloaded .srt file to it. 

*DVDStyler* then started *Spumux*, and then *DVDAuthor*. And DVDAuthor encountered an error ...

```
Erstelle DVD
Ausführung des Befehls: dvdauthor -o "/tmp/dvd-out" -x "/tmp/dvd-tmp/dvdauthor.xml"
DVDAuthor::dvdauthor, version 0.6.14.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>
INFO: Locale=de_DE.UTF-8
INFO: Converting filenames to UTF-8
INFO: dvdauthor creating VTS
WARN: First cell is not marked as a chapter in PGC 0, setting chapter flag
STAT: Picking VTS 01
STAT: Processing /usr/share/dvdstyler/data/empty_ntsc_ac3.mpg...
INFO: Video pts = 0.178 .. 6.417
INFO: Audio[0] pts = 0.178 .. 6.194
STAT: VOBU 11 at 0MB, 1 PGCS
INFO: Generating VTSM with the following video attributes:
INFO: MPEG version: mpeg2
INFO: TV standard: ntsc
INFO: Aspect ratio: 4:3
INFO: Resolution: 720x480
INFO: Audio ch 0 format: ac3/2ch, 48khz drc
STAT: Processing /tmp/dvd-tmp/title0-0-0.vob...
STAT: VOBU 16 at 4MB, 1 PGCS
STAT: VOBU 32 at 9MB, 1 PGCS
STAT: VOBU 48 at 13MB, 1 PGCS
STAT: VOBU 64 at 18MB, 1 PGCS
STAT: VOBU 80 at 23MB, 1 PGCS
WARN: Audio pts for channel 32 moves backwards by 69079; please remultiplex input.
WARN: Previous sector: 47.647 - 49.741
WARN: Current sector: 48.973 - 48.973
WARN: Audio pts for channel 32 moves backwards by 19620; please remultiplex input.
WARN: Previous sector: 52.643 - 53.838
WARN: Current sector: 53.620 - 53.620
STAT: VOBU 96 at 27MB, 1 PGCS
WARN: Audio pts for channel 32 moves backwards by 57095; please remultiplex input.
WARN: Previous sector: 56.613 - 57.557
WARN: Current sector: 56.923 - 56.923
WARN: Audio pts for channel 32 moves backwards by 140783; please remultiplex input.
STAT: VOBU 112 at 32MB, 1 PGCS
WARN: Audio pts for channel 32 moves backwards by 229520; please remultiplex input.
STAT: VOBU 128 at 37MB, 1 PGCS
WARN: Previous sector: 80.173 - 84.201
STAT: VOBU 144 at 42MB, 1 PGCS
STAT: VOBU 160 at 47MB, 1 PGCS
STAT: VOBU 176 at 52MB, 1 PGCS
STAT: VOBU 192 at 57MB, 1 PGCS
STAT: VOBU 208 at 62MB, 1 PGCS
STAT: VOBU 224 at 67MB, 1 PGCS
STAT: VOBU 240 at 72MB, 1 PGCS
STAT: VOBU 256 at 76MB, 1 PGCS
[...]
STAT: VOBU 4224 at 1287MB, 1 PGCS
STAT: VOBU 4240 at 1291MB, 1 PGCS
STAT: VOBU 4256 at 1296MB, 1 PGCS
WARN: Audio pts for channel 32 moves backwards by 119823; please remultiplex input.
STAT: VOBU 4272 at 1301MB, 1 PGCS
STAT: VOBU 4288 at 1306MB, 1 PGCS
**ERR: procremap encountered unknown subtitle command: 30**
Fehlgeschlagen
```

Google does not give me much information on this. What can I do to add this English subtitle to the DVD.

(I'd prefer to watch the movie on my TV with surround sound than on my Notebook with a smaller screen and only stereo.)

Thanks for your advise,
Timo

---

### Post by Timokl on 2010-01-04
Hey,

I found the mistake. In DVDStyler, I deselected "Don't transcode/multiplex" -- which means that I let it multiplexed first. Then DVDAuthor processed the subtitles smoothly.

Best regards,
Timo

---

### Post by civetta on 2010-02-19
Glad you figured it out. Sorry to hijack this thread, but I've been searching the web because I've got a different problem with subtitles. I've got an .srt file and when I add it in dvdstyler, it gives me a message:

```
ERR: New_Face failed. Maybe the font path is wrong.
Please supply the text font file (arial.ttf).
WARN: subtitle font: load_sub_face failed.
```

---

### Post by ddefillo on 2010-03-31
civetta:

I was having your exact problem so what I did was copy my fonts folder into my home folder (/home/.fonts -with the dot in front of the name so it is hidden) and now I am encoding without a hitch!

Hope this helps

---

### Post by hanciong on 2010-08-14
> **ddefillo said:**
> civetta:

I was having your exact problem so what I did was copy my fonts folder into my home folder (/home/.fonts -with the dot in front of the name so it is hidden) and now I am encoding without a hitch!

Hope this helps

ddefillo, I already have .fonts folder in my home folder, and inside, I already have arial.ttf. But I still have the problem:

ERR: New_Face failed. Maybe the font path is wrong.
Please supply the text font file (arial.ttf).
WARN: subtitle font: load_sub_face failed.


and I already try to change the .srt file into .sub file, but same problem still happens. why is that?? you know how to fix it? thx a lot:confused::confused::confused:

---

### Post by hanciong on 2010-08-14
> **ddefillo said:**
> civetta:

I was having your exact problem so what I did was copy my fonts folder into my home folder (/home/.fonts -with the dot in front of the name so it is hidden) and now I am encoding without a hitch!

Hope this helps
ddefillo, I already have .fonts folder in my home folder, and inside, I already have arial.ttf. But I still have the problem:

ERR: New_Face failed. Maybe the font path is wrong.
Please supply the text font file (arial.ttf).
WARN: subtitle font: load_sub_face failed.


and I already try to change the .srt file into .sub file, but same  problem still happens. why is that?? you know how to fix it? thx a lot:confused::confused::confused:

---

