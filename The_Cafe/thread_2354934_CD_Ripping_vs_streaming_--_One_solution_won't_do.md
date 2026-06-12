---
title: "CD Ripping vs streaming -- One solution won't do"
date: 2017-03-07
forum: The Cafe
---

### Post by ethanay on 2017-03-07
This is a response to this thread:
[https://ubuntuforums.org/showthread.php?t=2219616](https://ubuntuforums.org/showthread.php?t=2219616)

Which covers two things:
1.  suggesting Morituri as an option for CD ripping ([https://ubuntuforums.org/showthread.php?t=2219616&p=13115624#post13115624](https://ubuntuforums.org/showthread.php?t=2219616&p=13115624#post13115624))
2. "The end of the audio cd"

1. I still recommend having RubyRipper (.6.2 not .7) or RipperX installed as a backup (I had to manually install the "flac" package for some reason to enable ripping to FLAC in those programs). In theory, Morituri works well as an easy to use automated CD ripper.  In practice, however, it only works under the following conditions:
[LIST]
[*]the CD is already in the MusicBrainz db (otherwise it's a pain in the @$$ to enter metadata)
[*]the CD is either perfect or has only very minor data flaws (serious flaws -- even those that cause no discernable problem for the listener, cause the program to fail)
[/LIST]
In such cases, I fall back to RubyRipper, or even RipperX to get the job done.  What good is an "error correcting ripper" that just "gives up" (in its own words!) when it thinks the errors are too great?  This is a design flaw.  Design the program to finish its work with a note, "check these X tracks for any audible errors and re-rip if necessary."  Usually, I don't notice an error.  In theory, uncorrectable errors are unacceptable.  In practice, the errors are usually very small, unnoticeable and thus easy to live with.

2. The second reply of the thread points toward RubyRipper's developer noting the "end of the audio CD." [https://code.google.com/archive/p/rubyripper/](https://code.google.com/archive/p/rubyripper/)
>  I just don't see the need to rip cd's anymore. Streaming services like Spotify and Google Music seem to be so much less time consuming and much more convenient.

As far as streaming...I do not 
[INDENT]a. want to repurchase my music library over again or "pay rent" to a "music landlord" and
b. have to be connected to the internet constantly to listen to music.[/INDENT]

Philosophically, I think dependence on streaming media is deeply flawed.  It abuses (and hammers) internet infrastructure (we now regularly see "rush hour traffic" thanks to streaming, and the ever-expanding infrastructure demands are, like automobile infrastructure, basically a pyramid scheme) and somewhat-centralizes points of access.  Relying on streaming models hurts artists, labels and music.  [http://www.digitalmusicnews.com/2017/01/26/bandcamp-relying-streaming-models-hurts-music/](http://www.digitalmusicnews.com/2017/01/26/bandcamp-relying-streaming-models-hurts-music/) compares the "end of the CD" via streaming vs an evolution of digital media distribution (e.g., Bandcamp's model, which is proving quite successful for artists both large and small).

Plus, how many people globally have access (logistically and financially) to fast optical connections and unlimited data?  I think it's important for developers in "developed nations" to consider the needs of the "developing world" when considering the design, use and whether to continue or discontinue software.  In the "developing world" where internet access is more intermittent, usage metrics like "downloads" and "hardware sold" become meaningless as gauges of the impact of a certain piece of software or hardware.  One piece of used/recycled hardware and one download can have several times the impact and importance.

We are seeing a switch from "lock in" to one media to distributed, flexible on-demand media to meet a variety of needs.  Some of that is streaming.  Some of it will continue to be point-of-access. Most of it will be flexible models such as Bandcamp's (which offers DRM-free flac and ogg as standard options, plus content streaming.)  Why?  Because the Bandcamp model works with rather than against a diversity of technologies.  Once it's digitized, media access and distribution becomes incredibly flexible, inhibited only by artificial impositions (such as DRM or patented formats).  Bandcamp leverages that flexibility to address real market needs (which still includes limited runs of on-demand CDs!).

But even Bandcamp doesn't address the fact that many people still own music that they still want to access via the latest hardware.  That is why we are seeing the rise in services that offer archive (or CD) quality digital downloads of popular classic media.  When I don't want to rip and tag something (especially DVDs!), I search to see if a viable flac torrent of it exists.  It's not stealing (I already own access to the content), it's just sharing the workload  In the mean time, I have a library of old CDs to archive as flac, many of which are relatively obscure, some aren't available anymore in any format!

Basically, I see a tenant of FLOSS playing out:  diversity.  One solution (whether hardware or software) will never meet all needs.  Which is also the point of the first part of this post...and of unix-like systems:  identify and meet diverse demands in direct and discrete ways.

---

### Post by DuckHook on 2017-03-07
Not a support request.

*Thread moved to **The Cafe** as the more appropriate forum.*

---

### Post by mastablasta on 2017-03-08
> **ethanay said:**
> 
Plus, how many people globally have access (logistically and financially) to fast optical connections and unlimited data?  I think it's important for developers in "developed nations" to consider the needs of the "developing world" when considering the design, use and whether to continue or discontinue software. 

which is why opensource is important so people with interest can pick it up and at the very least continue to maintain it.

---

### Post by ethanay on 2017-03-28
Whipper:  
[https://github.com/JoeLametta/whipper](https://github.com/JoeLametta/whipper)
and
[https://cd-rw.org/t/make-perfect-audio-cd-rips-on-linux-using-whipper-morituri/24/12](https://cd-rw.org/t/make-perfect-audio-cd-rips-on-linux-using-whipper-morituri/24/12)

is a current fork of now-abandoned Morituri ([https://github.com/thomasvs/morituri/issues/153](https://github.com/thomasvs/morituri/issues/153)), but looks like it has no packaging for Ubuntu/Debian yet:
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=850541](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=850541)

---

