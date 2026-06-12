---
title: "Tovid command files"
date: 2010-01-10
forum: Ubuntu Studio
---

### Post by Dandee on 2010-01-10
Tovid commands "makexml" and "makedvd" are present in the Tovid directory (/usr/share/Tovid) but do not respond when called using the terminal. The Ubuntu terminal displays an error message - no such file or command. Rather than a simple makexml it is necessary to use /usr/share/tovid/makexml. I neither understand the cause of this nor the fix for it. My impressio9n from googling this problem is that others may be experiencing  similar difficulties. Comments will be appreciated.

Ubuntu 9.10
64 bit AMD

---

### Post by dannyboy79 on 2010-01-25
> **Dandee said:**
> Tovid commands "makexml" and "makedvd" are present in the Tovid directory (/usr/share/Tovid) but do not respond when called using the terminal. The Ubuntu terminal displays an error message - no such file or command. Rather than a simple makexml it is necessary to use /usr/share/tovid/makexml. I neither understand the cause of this nor the fix for it. My impressio9n from googling this problem is that others may be experiencing  similar difficulties. Comments will be appreciated.

Ubuntu 9.10
64 bit AMD

that's because /usr/share/tovid/ is NOT in your users $PATH. you can either add /usr/share/tovid/ to you $PATH or you can copy all the files from /usr/share/tovid/ to a location that is in your $PATH like /usr/bin/ or /usr/local/bin/ (any ouput from issueing $PATH) or you can create symlinks from the /usr/share/tovid/ to again some folder that's in your $PATH and I am sure there are other ways to solve the issue.

---

### Post by ron999 on 2010-01-29
Hi
I came on this problem when I upgraded to Karmic.
It's just what dannyboy79 said.
I got instructions how to make the links from another thread.
This is what I used:-
```
sudo ln -s /usr/share/tovid/makemenu /usr/bin/makemenu
sudo ln -s /usr/share/tovid/makexml /usr/bin/makexml
sudo ln -s /usr/share/tovid/makedvd /usr/bin/makedvd
sudo ln -s /usr/share/tovid/makevcd /usr/bin/makevcd
```

---

### Post by acreech on 2010-02-13
I am having a problem with Tovid. This seems to be a new new problem since upgrading to karmic. I get the error:

> :-[ PERFORM OPC failed with SK=4h/ASC=44h/ACQ=D9h]: Input/output error


> :-[ WRITE@LBA=310h failed with SK=4h/ASC=44h/ACQ=D9h]: Input/output error
:-( write failed: Input/output error


I am not sure what I need to do to fix these errors, or what they mean. I ran this command in the terminal and through Tovid GUI

```
makedvd -quiet -author -burn -device /dev/dvdrw /tmp/Texting_Fatality.xml

```

This was the output of the command:

> makedvd
A script to create a DVD-Video file structure and burn it to DVD
Part of the tovid suite, version 0.31
[http://www.tovid.org](http://www.tovid.org)
--------------------------------
Authoring disc from file: /tmp/Texting_Fatality.xml
=========================================================
Creating disc structure with the following command:
dvdauthor -x "/tmp/Texting_Fatality.xml"
=========================================================
DVDAuthor::dvdauthor, version 0.6.14.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>

INFO: Locale=en_US.UTF-8
INFO: Converting filenames to UTF-8
INFO: dvdauthor creating VTS
STAT: Picking VTS 09

STAT: Processing /tmp/Utah_Texting_Fatality.mpg...

INFO: Video pts = 0.133 .. 4.104
INFO: Audio[0] pts = 0.133 .. 4.133
INFO: Audio[32] pts = 0.133 .. 0.133
STAT: VOBU 7 at 0MB, 1 PGCS
INFO: Generating VTSM with the following video attributes:
INFO: MPEG version: mpeg2
INFO: TV standard: ntsc
INFO: Aspect ratio: 4:3
INFO: Resolution: 720x480
INFO: Audio ch 0 format: ac3/2ch, 48khz drc

STAT: Processing /tmp/Texting Fatality.mpg.tovid_encoded.mpg...
STAT: VOBU 2496 at 320MB, 1 PGCS
INFO: Video pts = 0.133 .. 912.177
INFO: Audio[0] pts = 0.133 .. 912.229
STAT: VOBU 2510 at 321MB, 1 PGCS
INFO: Generating VTS with the following video attributes:
INFO: MPEG version: mpeg2
INFO: TV standard: ntsc
INFO: Aspect ratio: 4:3
INFO: Resolution: 720x480
INFO: Audio ch 0 format: ac3/2ch, 48khz drc

STAT: fixed 7 VOBUS                         
STAT: fixed 2510 VOBUS                         
INFO: dvdauthor creating table of contents
INFO: Scanning /tmp/Texting_Fatality/VIDEO_TS/VTS_01_0.IFO
INFO: Scanning /tmp/Texting_Fatality/VIDEO_TS/VTS_02_0.IFO
INFO: Scanning /tmp/Texting_Fatality/VIDEO_TS/VTS_03_0.IFO
INFO: Scanning /tmp/Texting_Fatality/VIDEO_TS/VTS_04_0.IFO
INFO: Scanning /tmp/Texting_Fatality/VIDEO_TS/VTS_05_0.IFO
INFO: Scanning /tmp/Texting_Fatality/VIDEO_TS/VTS_06_0.IFO
INFO: Scanning /tmp/Texting_Fatality/VIDEO_TS/VTS_07_0.IFO
INFO: Scanning /tmp/Texting_Fatality/VIDEO_TS/VTS_08_0.IFO
INFO: Scanning /tmp/Texting_Fatality/VIDEO_TS/VTS_09_0.IFO
=========================================================
Authoring completed.
=========================================================
Found blank DVD-R.
=========================================================
Burning with growisofs 7.1 using the following command:
growisofs -use-the-force-luke=dao -dvd-compat  -Z /dev/dvdrw -dvd-video -V "TEXTING_FATALITY" "/tmp/Texting_Fatality"
=========================================================
Executing 'genisoimage -dvd-video -V TEXTING_FATALITY /tmp/Texting_Fatality | builtin_dd of=/dev/dvdrw obs=32k seek=0'
I: -input-charset not specified, using utf-8 (detected in locale settings)
  0.34% done, estimate finish Fri Feb 12 23:17:59 2010
  0.68% done, estimate finish Fri Feb 12 23:17:59 2010
  1.01% done, estimate finish Fri Feb 12 23:17:59 2010
/dev/dvdrw: engaging DVD-R DAO upon user request...
:-[ PERFORM OPC failed with SK=4h/ASC=44h/ACQ=D9h]: Input/output error
/dev/dvdrw: reserving 1481504 blocks
/dev/dvdrw: "Current Write Speed" is 8.2x1352KBps.
:-[ WRITE@LBA=310h failed with SK=4h/ASC=44h/ACQ=D9h]: Input/output error
:-( write failed: Input/output error
/dev/dvdrw: flushing cache
/dev/dvdrw: reloading tray
:-( unable to reload tray: Input/output error
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
makedvd encountered an error during the DVD creation process:
Could not burn the disc to /dev/dvdrw
See if anything in the above output helps you diagnose the
problem, and please file a bug report at tovid.org (_not_
the dvdauthor list) containing the above output.
Sorry for the inconvenience!
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!


Thanks for any help. 


acreech

---

