---
title: "DVD probs: disc recog hit-or-miss, noises, drives won't open... (but works in XP)"
date: 2008-05-14
forum: Ubuntu Studio
---

### Post by mrowth on 2008-05-14
Seems DVD Playback got a lot worse for me with Gutsy (playback kept halting at seemingly random moments, or discs stopped being readable while navigating the DVD menu) -- 

-- now, with Heron, I'm extremely lucky if it recognises inserted DVDs at all (i.e. KDE pop ups the icon and a What-do-you-want-to-do-with-this-disc dialogue).

Even then I can't necessarily play the movie! 

kaffeine: "The Source can't be read. Maybe you don't have enough rights for this, or source doesn't contain data (e.g: no disc in drive). (/dev/scd0)"

mount: "medium not found"

mplayer: "Playing dvd://1. Couldn't open DVD device: /dev/scd0 No stream found to handle url dvd://1" 

Sometimes it sounds promising at first but then the drive makes rumbling, grinding noises and I can't get the disc back out until I power the whole PC off first!

It does feel like a hardware problem - but I booted into Windows and played a movie, no waiting time recognising the disc, no problem getting it back out. And one drive is just a couple days old... the other used to work, too.

Not to mention that the drives now change randomly between hdc/hdd and scd0/scd1 on reboot, forcing me to edit fstab and re-train player software... even though they're IDE drives, secondary master & slave. (Same issue with the harddisks, but using UUIDs keeps them in line.)
 

Got the DVD lib from medibuntu.

If there's any info I can provide, I'll gladly do so, but I don't know what right now.

---

### Post by mrowth on 2008-05-14
Nautilus shows the drives under "Computer" but thinks they're empty.

Oh, and this did not affect data DVDs/CDs at first. But then, video DVDs once used to work also. It's like Ubuntu was breaking down slowly.

Right now I've got a Gutsy i386 install CD-RW in scd0 and it's just making funny noises.

---

### Post by mrowth on 2008-05-14
**When I try kaffeine, it dumps this in the console:**

ASSERT: "i <= nodes" in /usr/share/qt3/include/qvaluelist.h (376)
ASSERT: "i <= nodes" in /usr/share/qt3/include/qvaluelist.h (376)
ASSERT: "i <= nodes" in /usr/share/qt3/include/qvaluelist.h (376)
ASSERT: "i <= nodes" in /usr/share/qt3/include/qvaluelist.h (376)
libdvdnav: Using dvdnav version 1.1.11.1 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Attempting to use device /dev/sdb2 mounted on / for CSS authentication
libdvdread: Could not open /dev/sdb2 with libdvdcss.
libdvdread: Can't open /dev/sdb2 for reading
libdvdread: Device /dev/sdb2 inaccessible, CSS authentication not available.
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/nowth/.dvdnav/.map'
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: faild to read VIDEO_TS.IFO
libdvdnav: Using dvdnav version 1.1.11.1 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: BABYLON5_SEASON5_DISC6
libdvdnav: DVD Serial Number: 31556D4C
libdvdnav: DVD Title (Alternative): BABYLON5_SEASON5_DISC6
libdvdnav: Unable to find map file '/home/username/.dvdnav/BABYLON5_SEASON5_DISC6.map'
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: faild to read VIDEO_TS.IFO
/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)

**VLC:**

VLC media player 0.8.6e Janus
[00000287] dvdread demuxer error: DVDRead cannot open source: /dev/scd0
[00000288] vcd access error: no movie tracks found
ioctl(): Input/output error
[00000288] vcdx access error: error reading Info sector (150)
[00000288] access_file access error: file /dev/scd0 is empty, aborting
[00000289] main private error: cannot pre fill buffer
[00000292] cdda access error: could not read block 0 from disc
[00000292] cdda access error: cannot read sector 0
[00000292] cdda access error: could not read block 1 from disc
[00000292] cdda access error: cannot read sector 1
[00000292] cdda access error: could not read block 2 from disc

And so forth for sectors and blocks 3, 4, 5... 238...

---

### Post by mrowth on 2008-05-15
Yep, hit the wrong forum. This isn't about multimedia production. Sorry!

I found an existing thread about what I believe might be the same problem: [http://ubuntuforums.org/showthread.php?t=767449](http://ubuntuforums.org/showthread.php?t=767449)

Though in the meantime I had gone back to Gutsy... which still only works half the time. In the unlikely case anyone's reading this:

1) When I'm **lucky**, KDE actually discovers an inserted video DVD and shows its little what-do-you-want-to-do dialogue - or else I click the desktop icon for its context menu...
2) ...from there I select "Play DVD with Kaffeine".
3) If Kaffeine thinks DVDs ought to be in /dev/hdc rather than /hdd, or vice versa, it doesn't just fail to start, it also leaves a kaffeine process running that I have to kill manually.
4) It leaves something for me to kill even when I do manage to use and exit it normally.
5) I must do this every time before running Kaffeine again.

Also

1) Totem autoplays inserted DVDs, but starts somewhere in the "special features" area rather than at the beginning or the DVD menu.
2) Totem won't play DVDs when I try to open them from within Totem (through the menu), will complain about codecs etc.
3) I've got no experience running Totem, just wondering.

Also

After a while, attempting to play a DVD results in hopelessly stuck-sounding mechanical whining from within the drive, the tray won't open anymore then.

Both drives are set to region 2, like the DVDs I have.

---

