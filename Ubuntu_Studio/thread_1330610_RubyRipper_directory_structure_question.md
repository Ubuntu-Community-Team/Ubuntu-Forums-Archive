---
title: "RubyRipper directory structure question"
date: 2009-11-18
forum: Ubuntu Studio
---

### Post by mjpatey on 2009-11-18
Hi, all-

I'm trying to rip a CD track to 64Kbps mono mp3, with ID3 tags, to a folder in my /home directory.  I've tried various rippers, including ABCDE (the command-line script) and have settled on RubyRipper, as it worked for me once, but has now turned on me after I changed the output directory.

In RubyRipper's preferences under the "Other" tab, I have the base directory set to "~/Music/sermons/" and next to "Standard" (meaning a standard rip of a single track from a single-artist CD), my naming convention is "newsermon-%t" (just a temp name until I rename it before uploading to the Web.

The problem is, when I click "Rip cd now," I get the following message:

> The directory /home/mjpatey/Music/sermons already exist. What do you want rubyripper to do?"...and I can cancel the rip, overwrite the directory, or auto-rename the directory, none of which does what I want.  When I tell it to overwrite (which I tried once), rubyripper exits with some cryptic Ruby errors in the log.  I just tried auto-rename, and it did just that, creating an additonal directory called "sermons#1".  I assume it would continue doing that (sermons#2, etc.) on future runs.

Any idea how to overcome this weird output directory behavior in RubyRipper?

Thanks in advance for any insight you may have!

-Mark

---

