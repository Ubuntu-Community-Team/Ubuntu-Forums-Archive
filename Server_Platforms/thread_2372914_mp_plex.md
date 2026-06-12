---
title: "mp plex"
date: 2017-09-30
forum: Server Platforms
---

### Post by akeunde on 2017-09-30
well, I am not sure is it appropriate to ask my problem here, but I really need help, so, if disturbing, please forgive me. What would the easiest, quickest way be to get 800-900 DVD's ripped and put into some format so I can share them into Plex? I am running a PC and a MAC, Which file extension am I aiming for? AVI? MKV? Is there a way to just drag off the VIDEO_TS folder and use that? A friend asked me to download this program([http://www.videoconverterfactory.com/tips/plex-dvd.html](http://www.videoconverterfactory.com/tips/plex-dvd.html)) while I have no idea about the program, anybody uses it? any idea? thanks

---

### Post by TheFu on 2017-09-30
No, I do not use that program. Almost all those video converters are just re-using ffmpeg.

If you can automate things, that would be fastest.  I'd use vobcopy, ffmpeg, and a script to put the processing and output file placement where it needs to go.

As for plex - there are very specific directory organization requirements.  TV shows and Movies must be split into their own directories. Do not mix those. Each show and movie must be in their own directory.

To get the metadata filled in for each show/movie, there are tools built-into plex.  The transcoding will take 1000x longer, so it really isn't a concern.

Steps:
* vobcopy to get a mirror image of the disk onto a fast SSD/HDD.
* Transcode to h.264/multi-channel vorbis inside an mkv container.  I'd use either ffmpeg or HandBrakeCLI for that.  Handbrake (the GUI) might be easier for new people, but it will take longer with all that point-n-click effort for each DVD.
* Move the resulting file(s) into the required directory structure.
* Place the already processed DVDs into a box for the attic.
* Make a 100%-know-you-can-restore backup of the resulting files along the way. Think of all the effort.  A $160 8TB HDD should be able to backup that number of disks.  Having to re-create all the files would suck.  You'll see.

I would not leave the files as mpeg2 (the mirror from the DVD).  Those are 3x larger than the h.264 transcoded files. 
I would not use h.265 video at this point since most existing players do not support it and transcoding takes 2x longer than h.264.  I find h.265 to show more artifacts today as well.  The only plus is that the files are half the size of h.264 video.

---

### Post by rubylaser on 2017-10-02
I just stumbled across this the other day.  This looks like a nice, free, open source way to automate the transcoding of disks.  You could even extend the scripts to automatically scan for the new movies.

[https://b3n.org/automatic-ripping-machine/](https://b3n.org/automatic-ripping-machine/)

---

### Post by TheFu on 2017-10-02
> **rubylaser said:**
> [https://b3n.org/automatic-ripping-machine/](https://b3n.org/automatic-ripping-machine/)

MakeMKV in that link is **NOT** F/LOSS and last time I used it it didn't handle captions at all, only subtitles.  OTOH, I've come across a few discs that no other method was able to read over the years.  Some of the other tools his script is dependent on are different than I would select - for example, I have zero use for flac, zero.  

For batch processing, I prefer TaskSpooler over at/batch that are built-into most Unix-like systems.  **sudo apt install tsp** will get it. It is a nice task-batching queue tool.  Keep the system busy, but not slammed with work.  I tried for years to use at/batch BEFORE finding taskspooler.

And his name for this system, while cleaver isn't something google will ever find since there are many, many, many, millions of other sites using that term for something else.  

His code: [https://github.com/ahnooie/automatic-ripping-machine](https://github.com/ahnooie/automatic-ripping-machine)

---

