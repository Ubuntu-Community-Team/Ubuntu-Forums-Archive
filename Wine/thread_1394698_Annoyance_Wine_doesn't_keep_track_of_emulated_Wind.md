---
title: "Annoyance: Wine doesn't keep track of emulated Windows drives"
date: 2010-01-30
forum: Wine
---

### Post by pmooney78 on 2010-01-30
I regularly run several Windows programs under Wine, and one thing is a constant annoyance: Wine doesn't seem to keep track of my emulated drive settings properly. Between one invocation of a Windows program and the next (which may be several days), emulated drive settings are likely to disappear -- some drive letters that had been previously set up to map onto Linux paths have disappeared entirely, and some (removable) drives have multiple entries -- entries that were previously set up, and another entry that seems to have been automatically added. (This primarily applies to my CD-ROM drive and my iPod.)

This is really annoying. Not only do I need to remember to open the "configure Wine" dialog before running any Windows program, but sometimes, closing it means that they drives I've just set up disappear before the Windows program I'm trying to run starts up. Any suggestions for how I can convince Wine that I really do mean what I say on the Drives tab in the configuration dialog?

I'm running Wine 1.0.1. under Ubuntu Linux 8.10 on a Dell Latitude D420 laptop with 1 GB of RAM and a 1.2 GHz Core Duo processor.

---

### Post by JPPI-Stuart on 2010-02-12
This has been a problem for me also, using OpenSUSE 11.2 x86_64 with Wine 1.1.38.  I ran across this thread while researching the problem via Google.  I'm going to keep looking into this, but wanted to "subscribe" to this thread in case a solution is mentioned here.

---

### Post by pmooney78 on 2010-02-17
I've recently noticed that (at least part of) Wine's drive-tracking strategy involves maintaining symbolic links in ~/.wine/dosdevices. Manually creating symbolic links there with, e.g.,

```

cd ~/.wine/dosdevices
ln -s "e:" /media/Externa

```

creates a link that Wine won't override, making /media/Externa permanently map to drive E: in the emulated Windows environment. It's an awkward way to do it -- I'd rather just use the Wine setup dialog -- and it doesn't prevent Wine from creating duplicate references to my iPod or other removable locations, but it's better than nothing.

Any other suggestions greatly appreciated.

---

