---
title: "Burning movies and subtitles to a DVD"
date: 2009-01-03
forum: Ubuntu Studio
---

### Post by japtar10101 on 2009-01-03
This is the first time I'm burning movies to a DVD, and Google already got me confused.  How do you burn movies to a DVD?

I have 5 avi movie files and srt subtitle files, all probably in different formats because I've been experimenting with too many video editors.  From my understanding, I need to convert avi movies to MPEG-2, and srt files to VobSub for preparation.  Then I have to setup a bunch of directories and generate xml files corresponding to each movie and subtitle files.  Finally, I have to combine this all into a single iso file, then burn it to a disk.  What are all the programs and procedures I have to install to get this working?

---

### Post by binbash on 2009-01-04
you can do it easily with devede

---

### Post by axel206 on 2009-01-04
No need to get into so much trouble.

Check [devede guide](http://www.my-guides.net/en/content/view/75/26/)

---

### Post by japtar10101 on 2009-01-04
What the heck?  I'm using Devede with 4 23-minute movies and 1 30-second movie, all with subtitles, and it tells me the movie will be 44 times the size of a 120 minute DVD disk?

[IMG]http://i9.photobucket.com/albums/a87/japtar10101/Scrap/Screenshot-1-1.jpg[/IMG]

Does this have to do with some indexing file embedded in avi?  Some player tells me each movie is 2+ hours long.

---

### Post by japtar10101 on 2009-01-04
> **japtar10101 said:**
> Does this have to do with some indexing file embedded in avi?  Some player tells me each movie is 2+ hours long.

Apparently it did.  Fixed, though:
```
mencoder damaged_file.avi -idx -oac copy -ovc copy -o fixed_file.avi
```
Mencoder surprises me, sometimes.

---

### Post by japtar10101 on 2009-01-05
Is there a way to make a DVD so that the subtitles pop up automatically?  Or a way to put in the menu, "enable subtitles"?

Note: I'm using VLC player to test my newly generated iso.  When I play one chapter with subtitles, then continue off to the next, it doesn't keep the subtitle settings.  Is this just VLC, or the iso itself?

EDIT: yeah, it's vlc only.  I still prefer a graphical way of portraying subtitle options.

---

