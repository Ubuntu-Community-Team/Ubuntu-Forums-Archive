---
title: "Local Archive Mirror too big"
date: 2006-06-08
forum: Server Platforms
---

### Post by ximok on 2006-06-08
We started using Ubuntu in a lab at in our school district.  We may use it for more computers.  To reduce the bandwidth load we built an internal mirror of the repository with 400Gigs for storage.  We thought we would be ok with this number size, but it appears to be too small as we are slowly reaching that 400 Gig mark.  Is there a way to retain only the packages pertinant to Breezy Badger and Above?  Or even the last few revisions of each package?

Here is the pertinant part of the script we use (activated by cron) to update the local repository:
>  rsync -qau --progress rsync://archive.ubuntu.com/ubuntu /pkg-archive/ 

Anyone have any advice or expertise in this area?

We are currently at 231 Gigs (Ok, so we aren't that close, but it does increase nightly)  5.2Gigs are used up just by the openoffice.org package!!!


By the way, we use Ubuntu very effectively in our Junior High Lab.  We do make use of VMWare for a few of those programs that we can't run under Linux, like Game Maker.  Does anyone have a good open source alternative to this program that provides the same functionality?

---

### Post by ximok on 2006-06-09
I have solved my own problem!

```
rsync -au --progress --delete rsync://archive.ubuntu.com/ubuntu /pkg-archive/
```
Note: You need to have a directory /pkg-archive/ for this to work (change this to whatever you want)

This corrected code (using the --delete syntax) will campare the two archives and delete the files from the destination that are not existing in the source.

This reduced my archive from the 231 Gigs down to 125 Gigs!!!!  

In a nutshell, I was creating a very historical archive of the repositories.

So, if you also need to make a mirror of the cd-releases:
```
rsync -au --progress --delete rsync://releases.ubuntu.com/releases /releases/
```
Note: You need to have a directory /releases/ for this to work (change this to whatever you want)

---

