---
title: "anti-aliased subtitles"
date: 2008-06-02
forum: Ubuntu Studio
---

### Post by cesera on 2008-06-02
I recently have tried to author some DVD's using tovid and am generally very happy with the result. However I have now come across a problem tovid does not solve satisfactory:

I have some .mkv files with subtitles in .srt files, that I want to burn to DVD. When I use tovid to combine these two I end up with mpeg files with either smooth, anti-aliased subtitles that are hard coded, or with rough, blocky subtitles I can switch on and off.

Is there a way to create mpeg files with smooth, anti-aliased subtitles I can switch on and off?

Thank you,

Kees

---

### Post by aeiah on 2008-06-02
do they appear jagged on dvd players? i always thought that dvd subtitles (real ones that you can turn on or off, not ones embedded onto the video) were just text files that were read by the dvd player using its default font. perhaps there is somewhere where you can specify a font. in which case, that'll be what you have to do.

if you are just testing these on a pc, then its more likely that whatever software dvd player you use is using a really bad font, and is a setting you can change from within the dvd player config

---

### Post by cesera on 2008-06-03
> **aeiah said:**
> I always thought that dvd subtitles were just text files that were read by the dvd player
 
I thought so too, but it looks like DVD subtitles are actually transparent background bitmap images that are displayed over the top of the actual movie (see for instance: [http://en.wikipedia.org/wiki/DVD-Video#Subtitles](http://en.wikipedia.org/wiki/DVD-Video#Subtitles)). Closed Captioning is apparently also somehow possible and that is just the text, but you either need a closed caption decoder or a TV/DVD-player that is capable of that.
 
So there has to be a tool that produces those bitmap with a nice anti-aliased font. I just haven't found it yet.

---

### Post by aeiah on 2008-06-03
hmm i dunno. you could try using [subtitle editor](http://home.gna.org/subtitleeditor) and see if exporting to any of the formats it supports will result in nice looking subs i guess

you could also try replacing the font tovid uses i guess, or perhaps using submux-dvd and seeing if that helps. i havent used it myself though

---

