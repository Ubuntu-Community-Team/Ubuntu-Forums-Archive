---
title: "Request: Backports of some Marillat packages"
date: 2005-05-04
forum: Ubuntu Backports
---

### Post by thully on 2005-05-04
Recently Marillat compiled some files against a new glibc in sid, leaving many packages
broken when used with Hoary.  I wondered if anyone is interested in backporting these
and adding them to ubuntu-backports (if it doesn't cause too many legal problems).
The packages in particular are:

gstreamer0.8-lame (for ripping MP3s in sound-juicer)
gstreamer0.8-faad (for listening to AAC/MP4 through Rhythmbox)
gstreamer0.8-faac (Same, but for ripping)
gtkpod-aac (gtkpod built with AAC support)

Also, it would be nice to see Amaranth's stuff in the hoary-extras (specifically,
pymusique and smeg).

---

### Post by Slo Mo Snail on 2005-05-04
I've ppc builds for the first 3 packages... compiled for hoary and working for me... so if you're on ppc I can send them to you

I don't think there will be no legal problems as faac, faad and lame are in multiverse and the gstreamer plugins for them just wrap around these libraries

---

### Post by Technoviking on 2005-05-04
I second this request.

Mike

---

### Post by poofyhairguy on 2005-05-04
[QUOTE=Mike Basinger]I second this request.

Mike[/QUOTE]


I third it. The less marillat is used the better....

---

### Post by thully on 2005-05-04
I'm on x86, and I already have these packages (the older version from Marillat that works).  I'm just requesting them to be backported so that other users don't have to hunt for the old Marillat version.

---

### Post by jdong on 2005-05-04
Ok, today I was planning to import everything in marillat/unstable into Backports Staging / restricted.

---

### Post by jdong on 2005-05-04
Ugh, can't find divx requirements for mplayer anywhere. Mplayer will be on hold for now.

---

### Post by jdong on 2005-05-04
The packages you requested, plus a few more, are all built and in various stages of uploading :)

Please test...

I'm gonna keep on importing stuff from Marillat :)

---

### Post by thully on 2005-05-04
[QUOTE=jdong]The packages you requested, plus a few more, are all built and in various stages of uploading :)

Please test...

I'm gonna keep on importing stuff from Marillat :)[/QUOTE]
 so, do you plan on importing gtkpod-aac from marillat?  This is of great use to iPod owners
who have songs in AAC format, as it allows them to be synced to the iPod.

BTW - why do you have to backport Mplayer?  It's already in Hoary and you have the w32codecs package, what more is needed?

---

### Post by jdong on 2005-05-04
Package "gtkpod-aac" has been imported and uploaded successfully into hoary-extras-staging/restricted.
 
As far as MPlayer... I don't know why I was trying ;)

---

### Post by thully on 2005-05-04
[QUOTE=jdong]Package "gtkpod-aac" has been imported and uploaded successfully into hoary-extras-staging/restricted.
 
As far as MPlayer... I don't know why I was trying ;)[/QUOTE]
 Great! Once all these make it out of staging and into the main backports archive, we can 
edit the RestrictedFormats wiki to use Ubuntu Backports rather than Marillat for Hoary and
fix the problem caused by Marillat's use of a new glibc from sid (because of this, RestrictedFormats wiki currently has non-working instructions for setting up a few things).

P.S. Any way we will see the pymusique deps in staging soon (python2.4-mcrypt, and also the strongly recommended python2.4-vlc(for audio preivews) and python2.4-mp4ff(for proper tagging)?

---

### Post by thully on 2005-05-04
[QUOTE=thully]Great! Once all these make it out of staging and into the main backports archive, we can 
edit the RestrictedFormats wiki to use Ubuntu Backports rather than Marillat for Hoary and
fix the problem caused by Marillat's use of a new glibc from sid (because of this, RestrictedFormats wiki currently has non-working instructions for setting up a few things).

P.S. Any way we will see the pymusique deps in staging soon (python2.4-mcrypt, and also the strongly recommended python2.4-vlc(for audio preivews) and python2.4-mp4ff(for proper tagging)?[/QUOTE]
 I just read the info on how Backports works, and noticed that packages have to stay in staging for at least 7 days before moving them into stable backports.  However, this poses somewhat of a problem with respect to the RestrictedFormats wiki.  

Since a few days ago, the directions for getting MP3 ripping in Sound Juicer, AAC ripping in Sound Juicer, and AAC playback in Rhythmbox have been broken because of the new glibc dependency in Marillat.  To resolve this issue, should we:

 1)Leave the broken Marillat instructions in the wiki until the packages hit stable backports
 2)Remove the instructions for these formats entirely for the time being 
 3)Direct people to staging to get these things (and the rest of the marillat stuff)
 4)Fast track all of the Marillat packages to stable before the 7 day period because of the circumstances with Marillat's breakage

If somebody doesn't handle this, I think the forums, mailing list, and IRC will start getting jammed with marillat problems.

---

### Post by jdong on 2005-05-04
The 7-day staging period is merely a **recommendation**.

If you look at the repository changelog, I break that rule on a daily basis :)


As soon as people start testing these packages in staging and coming back and saying they work, I'll promote them immediately. I understand the urgency.

---

### Post by thully on 2005-05-04
[QUOTE=jdong]The 7-day staging period is merely a **recommendation**.

If you look at the repository changelog, I break that rule on a daily basis :)


As soon as people start testing these packages in staging and coming back and saying they work, I'll promote them immediately. I understand the urgency.[/QUOTE]
 Here is my results with a few of these packages (including the ones used in RestrictedFormats)
* pymusique - works if you use python2.4-* from fuware.net/pymusique
(I use all of them - gives you full support for previews and tagging)
Add all of the python2.4-* to the backport repository before promoting pymusique (also, you may want to depend on all 3 to guarantee that pymusique works properly)

* gstreamer-faad - works, not sure about gstreamer-faac (I don't have anything that plays the RAW AAC files it makes)

* gstreamer-lame - I ripped a CD to MP3 with it (through sound juicer), and it worked fine

* netapplet - works better than Hoary's (I still had it crash once, but it's much better than the old netapplet was)

* gtkpod-aac - Transferred a block of MP3s to my iPod find - I haven't tested it with AACs yet, but I do know the program works fine.

---

### Post by tube013 on 2005-05-12
Has anyone been able to load songs bought from itunes via pymusique onto an ipod with gtkpod-aac?  I get the following popup error:

Could not open '/home/byron/Music/Assembly of Dust - The Honest Hour - Harrower.m4a' for reading, or file is not an mp4 file.


File plays fine with totem and rhythmbox (gstreamer versions).

---

### Post by marxist on 2005-05-21
hi!

i'm wondering what's the status on the marillat backports? it seems there is no mplayer package in the backports repository and the one from marillat is, of course, still broken for 5.04 users.

thanks for any info!

Tobias

---

### Post by jdong on 2005-05-21
Umm, I heard from other people that they don't want mplayer because it's already in Hoary.


I've tried messing with that backport, but the dependencies for all the plugins were so hairy that I couldn't resolve them.

---

### Post by Dr Gonzo on 2005-05-21
Hi.  Thanks for all the backports!

However, I still can't get gtkpod-aac to work with m4a files downloaded using pymusique from ITMS.  When it looks in a directory with m4a files in it, it says that it needs to be compiled with mp4v2 support.  Which I thought it already was.  If I rename the files .mp4, though, gtkpod will say it added the files, but they neither show up in the gtkpod list nor on the ipod after sync.

I tried compiling gtkpod from source to include mp4v2 support, and it took me quite a long time to find the libmp4-dev package in Marillat that would allow me to do this.  It finds the library, but it says it can't find 'mp4.h', which exists in /usr/include.

I'm getting quite frustrated with this, as pymusique sure would be pretty useless if I can't put the downloaded songs on the iPod.

Any ideas why this isn't working?

---

### Post by marxist on 2005-05-22
> Umm, I heard from other people that they don't want mplayer because it's already in Hoary. 

mhm, maybe that's just me, but i can't find mplayer in hoary. i did a standard install from kubuntu and commented in the universe entries in sources.list and added the marillat entries. when i do apt-cache policy mplayer-586 i only get packages from marillat...
what am i doing wrong?

thanks :)

---

### Post by jdong on 2005-05-22
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?exact=0&searchon=names&version=all&case=insensitive&release=all&keywords=mplayer&arch=any](http://packages.ubuntu.com/cgi-bin/search_packages.pl?exact=0&searchon=names&version=all&case=insensitive&release=all&keywords=mplayer&arch=any)

It's in Multiverse

---

### Post by marxist on 2005-05-22
ahh. thanks a lot!

i'm still a bit new to ubuntu and it's organisational structure. :)

bye

---

### Post by CyberLizard on 2005-06-09
[QUOTE=Dr Gonzo]Hi.  Thanks for all the backports!

However, I still can't get gtkpod-aac to work with m4a files downloaded using pymusique from ITMS.  When it looks in a directory with m4a files in it, it says that it needs to be compiled with mp4v2 support.  Which I thought it already was.  If I rename the files .mp4, though, gtkpod will say it added the files, but they neither show up in the gtkpod list nor on the ipod after sync.

I tried compiling gtkpod from source to include mp4v2 support, and it took me quite a long time to find the libmp4-dev package in Marillat that would allow me to do this.  It finds the library, but it says it can't find 'mp4.h', which exists in /usr/include.

I'm getting quite frustrated with this, as pymusique sure would be pretty useless if I can't put the downloaded songs on the iPod.

Any ideas why this isn't working?[/QUOTE]

I am having the same problem with the complaint about compiling with mp4v2 support.  I downloaded my AAC files directly from iTunes.  I didn't try renaming the files or recompiling.  Did you get it working? ](*,)

---

### Post by SteveRoth on 2005-08-14
I went looking for these backports -- particularly gtkpod-aac -- and couldn't find them.  After a little investigation I came to the conclusion that they don't exist in amd64 binaries.  Am I looking in the wrong place?  Or should I just grab the source from Marillat and compile them for amd64?  If the latter, what process should I follow to make the result available for others?

---

