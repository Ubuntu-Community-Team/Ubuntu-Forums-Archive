---
title: "More trouble with linux simplification: package-x-generic ( This is just a rant )"
date: 2017-08-11
forum: The Cafe
---

### Post by arsenic23 on 2017-08-11
Over the last decade I have found my linux experience is becoming more and more troublesome.  It is becoming harder and harder to configure and use ubuntu. 

I blame two things:  Over simplification and the push towards horizontal integration of packages.  I'm going to briefly complain about the former; if you aren't interested please stop reading here, I would hate to waste your time.

Getting a decent setup where all of the scripts and shortcuts I've created over the years has become harder and harder.  My switch from 10.04 to 12.04 so many years ago was so frustrating that I kept that initial 12.04 install for the entire lifetime of my last computer.  I have a new computer now, and so I've started the trek into making 16.04 work for me.  Luckily a lot of the things that had to be done to 12.04 were applicable to 16, so I had a lot less research to do.  I've had a few hiccups, but most of the fixes were fairly easy to look up or create.  After 3 days of work I have a fairly usable system.

One of the last things I have on my list of issues is that my archives are no longer color coded.  Back in, I don't know, 2004/2006ish I created an icon theme for my personal use.  One of it's main goals was to color code more of the GUI.  To that effect I created different color icons for all of the archive and package types, among other things.  After loading it into 16.04 I discovered that all archives and packages were red.  My zip files were not orange, my 7zip files were not green, rars were not purple, lha files not blue.  I assumed this would be an easy fix.  After all, every few OS upgrades have caused me to add new information to the icon theme to keep compatibility with new standards and changes.  So, I saved this problem for last.  Having free time today I looked into the issue.

First I opened one of the icon themes that shipped with 16.04 to see if there were any changes in the icon names.  There were not.  This is normally the issue when something is up with my theme, so I was a little perplexed.
After digging around I discovered that at some time between 2012 and 2016, someone had decided that all of the archives and packages should point to a single icon.  I am going to have to go in and edit the mime information for a TON of files.  I can't figure out why anyone would do this other then to simplify for simplification's sake.  I just keep running into 'we removed these features to make things simpler'.  It is not simpler if you use them; it means that now I have to build/recreate them myself.

Let's look at all the mime types now using the package-x-generic icon instead of their own:
```
application/mac-binhex40:package-x-generic
application/x-source-rpm:package-x-generic
x-epoc/x-sisx-app:package-x-generic
application/x-java-archive:package-x-generic
application/x-stuffit:package-x-generic
application/zlib:package-x-generic
application/x-xz:package-x-generic
application/x-sv4crc:package-x-generic
application/x-archive:package-x-generic
application/x-lrzip:package-x-generic
application/x-lha:package-x-generic
application/x-lhz:package-x-generic
application/x-lz4:package-x-generic
application/x-java-pack200:package-x-generic
application/x-arc:package-x-generic
application/x-macbinary:package-x-generic
application/x-pak:package-x-generic
application/x-arj:package-x-generic
application/x-windows-themepack:package-x-generic
application/x-ace:package-x-generic
application/zip:package-x-generic
application/x-compress:package-x-generic
application/x-lrzip-compressed-tar:package-x-generic
application/x-slp:package-x-generic
application/x-tarz:package-x-generic
application/x-bzip:package-x-generic
application/x-tzo:package-x-generic
application/x-bzip-compressed-tar:package-x-generic
application/x-lzip:package-x-generic
application/x-doom-wad:package-x-generic
application/x-xz-compressed-tar:package-x-generic
application/vnd.debian.binary-package:package-x-generic
application/x-ustar:package-x-generic
application/x-rpm:package-x-generic
application/x-rar:package-x-generic
application/x-sv4cpio:package-x-generic
application/x-zoo:package-x-generic
application/gzip:package-x-generic
application/x-dar:package-x-generic
application/x-lzma-compressed-tar:package-x-generic
application/x-cpio:package-x-generic
application/x-bcpio:package-x-generic
application/x-theme:package-x-generic
application/x-shar:package-x-generic
application/x-partial-download:package-x-generic
application/x-lzma:package-x-generic
application/vnd.symbian.install:package-x-generic
application/x-7z-compressed:package-x-generic
application/x-ksysv-package:package-x-generic
application/x-qpress:package-x-generic
application/x-tar:package-x-generic
application/x-par2:package-x-generic
application/x-lzop:package-x-generic
application/vnd.ms-cab-compressed:package-x-generic
application/x-cpio-compressed:package-x-generic
application/x-compressed-tar:package-x-generic
application/x-alz:package-x-generic
application/vnd.emusic-emusic_package:package-x-generic
```

I'm hoping I can just edit /usr/share/mime/generic-icons and then rebuild the mime cache.  That should work, but it's still a pain in the ass.  I'm going to have to lookup the old icon name for those filetypes and then replace package-x-generic with that name; if I'm lucky that's all that I'll need to do.  The thing that gets me is that I can't find anyone talking about this.  I am the only person in the world that's inconvenienced by it?  That can't be, can it?


Here's another example:  I have certain mouse and keyboard shortcuts I have been using forever: workspace stuff mostly.  In 2004 when I made the switch to linux as my primary OS, several window managers/Desktop Environments supported the functionality.  Right now, as far as I know, only compiz does, and that is more then likely only because development stopped on it forever ago.  In 2011 or 2013 or something I sent an email to a KDE dev.  Why doesn't KDE have the option to do this list of things I want my interface to do?  There doesn't seem to be any reason why it can't be doing them now, it does things that are very similar after all.  The dev told me that there was nothing stopping KDE from being able to do those things except they were worried that having too many options would be hard on the user.  "Well, I don't need to be able to turn them on with a GUI, if you just give me a text document or something I can edit?"  The reply?  A firm no.

I can't help but worry that we are turning a rocket powered swiss army knife into a two slot toaster.  Well, I guess I might just be suborn, grumpy, and lacking the ability to get with the times.

---

