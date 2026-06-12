---
title: "Best Video Codec?"
date: 2006-05-08
forum: The Cafe
---

### Post by justintime32 on 2006-05-08
I was going to archive some of my DVDs on my computer, probably using Handbrake (or possibly AcidRip). Although, I want to know what the best encoder is for file size. I don't really care about general compatibility, as long as I can play it (I can always transcode it later if necessary).

My general opinion is H.264 with AAC audio, but I'm not sure if it's actually better than MPEG-4/XviD. So here's my question... Which video codec has the best compression for the quality? Also, if it is XviD/MPEG-4, should I use the xvid codec or lavc?

---

### Post by kingmonkey on 2006-05-08
hmmm, thats a big qyestion your asking.

My personal fav is xvid with AC3,

It is really down to how much quality you want to sacrafice for space. [www.doom9.org](www.doom9.org) I find has lots of usefull info about such matters.

---

### Post by Parkotron on 2006-05-08
I don't think there's reallly to much debate over this at the moment. H.264 is a "next generation" codec that currently blows the likes of DivX and XviD out of the water. From what I understand, it's still quite "cutting edge", so support is limited. Apparently at high definition resolutions, most current video cards aren't even able to handle H.264.

Back in my DVD ripping days I mostly used XviD for video, Ogg Vorbis for audio and the Matroska container format with embedded chapter information and SRT subs. But that was a year ago, so I'm sure a lot has change since then.

---

### Post by Immaculate on 2006-05-08
You will most likly notice better quality with h.264 over XviD. But you will have a hard time accually encoding to it I assume, as its not that simple. Atleast not in windows, but I doubt there is better support in linux for it. Or there is just XviD, basically the standard. Much lower encoding times.

Or for backing up your DVDs, if you have windows installed, you can install AutoGK. Set it to the .IFO file in your DVD video folder and set it to 700MB, wait, and you will have a 700MB XviD.

---

### Post by nalmeth on 2006-05-09
What most ripping apps use now is good for all around quality, and low file size.
I've never used handbrake, so I'll recommend aciprip, which lets you rip to AVI or MPEG.
I'm not sure that AAC will have much advantage, doesn't it have DRM incorporated into it? Will you even be able to encode with AAC?

---

### Post by papangul on 2006-05-09
The video in dvd is already compressed, if you backup by encoding to some other format, then the same video is getting compressed twice, which is not a pretty situation for backup purposes.
Ideally what is needed is a program which will rip the video file in the dvd as-it-is, without any alteration so that it can be restored later on. Dat files in vcd's can be ripped off without altering them but I'm not aware about dvd's.

---

### Post by kingmonkey on 2006-05-09
Papangul is right in this, it is the best way to backup without losing quality but it does require a lot of space. I would still recommend xvid as it is well supported and future proof.

there is bound to be loads of DVD *rippers*, wont "cat" do it to some degree?

---

### Post by Immaculate on 2006-05-09
>  doesn't it have DRM incorporated into it?

Only if it is AAC bought from iTunes.

> The video in dvd is already compressed, if you backup by encoding to some other format, then the same video is getting compressed twice, which is not a pretty situation for backup purposes.
Ideally what is needed is a program which will rip the video file in the dvd as-it-is, without any alteration so that it can be restored later on. Dat files in vcd's can be ripped off without altering them but I'm not aware about dvd's.

As far as I know, DVD is lossless. XviD is lossy. Compare it to music. DVD/MPEG2 = CD/PCM, XviD/h.264 = MP3/MPC.

You can get really great quality on a 700MB XviD, or even better quality on a 1400MB XviD.

---

### Post by papangul on 2006-05-09
DVD is *lossy*.
> DVD video is usually encoded from digital studio master tapes to MPEG-2 format. The encoding process uses lossy compression that removes redundant information (such as areas of the picture that don't change) and information that's not readily perceptible by the human eye. The resulting video, especially when it is complex or changing quickly, may sometimes contain visual flaws, depending on the processing quality and amount of compression.
[http://www.dvddemystified.com/dvdfaq.html#1.3](http://www.dvddemystified.com/dvdfaq.html#1.3)

---

### Post by nalmeth on 2006-05-09
You CAN copy some DVD's directly to your harddrive, and not lose any quality.
The problem is that a lot of DVD's now have copy-protection measures, and will fool you with hidden folders that take away functionality.
Space (and DRM measures) permitting, you can get as great quality as you like.

---

### Post by samir85 on 2006-05-10
Video DVDs are endoded in MPEG-2 format, which is lossy format.
So if you convert a video from DVD into another fromat (ie XviD) you will loose quality.

---

### Post by samir85 on 2006-05-10
btw:

Does somebody know how to encode a video into an mp4 container with mpeg4 h246 videostream and aac audiostream ?

Of course I'd prefer a GUI solution for this.

Maybe somebody has a howto ?

---

### Post by Immaculate on 2006-05-10
[QUOTE=papangul]DVD is *lossy*.

[http://www.dvddemystified.com/dvdfaq.html#1.3](http://www.dvddemystified.com/dvdfaq.html#1.3)[/QUOTE]


I stand corrected ;P

But my point was... DVD -> XviD doesent loose that much quality. Though I highly dont recomend to back up DVDs to XviD you plan to burn back to DVDs later, I do recomend XviD if you just want to watch them on your computer.

---

### Post by Iandefor on 2006-05-10
[quote=samir85]btw:

Does somebody know how to encode a video into an mp4 container with mpeg4 h246 videostream and aac audiostream ?

Of course I'd prefer a GUI solution for this.

Maybe somebody has a howto ?[/quote] You can check out vive ([http://vive.sourceforge.net/)](http://vive.sourceforge.net/)). Works like a charm.

---

### Post by samir85 on 2006-05-11
[QUOTE=Iandefor]You can check out vive ([http://vive.sourceforge.net/)](http://vive.sourceforge.net/)). Works like a charm.[/QUOTE]

Hey, that's the thing i was searching for ! :D

---

