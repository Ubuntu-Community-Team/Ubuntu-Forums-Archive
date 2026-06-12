---
title: "PanP5 can't get video+audio from most media/app tuples"
date: 2010-12-07
forum: System76 Support
---

### Post by tlroche on 2010-12-07
problem: my PanP5 won't display video when using `vlc` or `totem` to play any of a sample of DVDs and video files. But purely browser-based video (e.g. flash, mp4) plays both video and audio.

details:

I have a Pangolin Performance (model=panp5) running an up-to-date GNOME lucid:

> $ lsb_release -ds
> Ubuntu 10.04.1 LTS
$ uname -rv
> 2.6.32-26-generic #48-Ubuntu SMP Wed Nov 24 10:14:11 UTC 2010
$ sudo aptitude update ; sudo aptitude full-upgrade
...
> No packages will be installed, upgraded, or removed.

I haven't tried playing DVDs on it for awhile, though I seem to recall it working previously. However, a couple hours ago I put a DVD in the tray: it spun up, the OS offered to open it with totem, I accepted, and totem started. It appeared to be playing the menu track ("Title 0" of length=0:33 looped), but totem produced neither audio nor video, though the sound volume was turned up. Attempting to debug, I started totem from terminal, and got

> $ totem --version
> totem 2.30.2
$ totem &
> libdvdread: Using libdvdcss version 1.2.10 for DVD access
> libdvdnav: Using dvdnav version 4.1.3
> libdvdread: Using libdvdcss version 1.2.10 for DVD access

totem correctly read the DVD title, etc, then did

> > libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000012e
> libdvdread: Elapsed time 0
> libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00002d15
> libdvdread: Elapsed time 0
> libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000664f
> libdvdread: Elapsed time 0
> libdvdread: Found 1 VTS's
> libdvdread: Elapsed time 0

(I believe this indicates CSS is not the problem--please correct if I'm overinterpreting.)

But attempting to play the DVD in totem got neither audio nor video. Note this DVD is known to play in my GF's standalone DVD player, and I believe I have also played it in winxp.

I did some googling, and noticed repeated claims of the superiority of vlc to totem, so I did

> $ sudo aptitude install vlc

which completed normally. I then started vlc from terminal, and got

> $ vlc --version
> VLC media player 1.0.6 Goldeneye
> VLC version 1.0.6 Goldeneye
> Compiled by [email]buildd@yellow.buildd[/email]
> Compiler: gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) 
$ vlc &
> VLC media player 1.0.6 Goldeneye
> [0xbd84b8] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.

In vlc, I did mainmenu>Media>Open Disk..., took all defaults in resulting dialog="Open Media", and hit button=Play. It also looped the menu track (like totem), this time with audio! but still no video. In terminal, I got the same libdvdnav and libdvdread messages as above, followed by

> > [0x10d4618] main input error: ES_OUT_RESET_PCR called
> [0x10d4618] main input error: ES_OUT_RESET_PCR called
> [0x7f524401d558] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:224000
> [0x1258138] pulse audio output: No. of Audio Channels: 2
> QPainter::begin: Paint device returned engine == 0, type: 1
> QPainter::begin: Paint device returned engine == 0, type: 1
> [0x10d4618] main input error: ES_OUT_SET_(GROUP_)PCR  is called too late, increasing pts_delay to 300 ms
> [0x10d4618] main input error: ES_OUT_RESET_PCR called
> [0x7f5244014678] libmpeg2 decoder error: DpbUnlinkPicture called on an invalid picture
> [0x7f5244014678] libmpeg2 decoder error: DpbUnlinkPicture called on an invalid picture

And each time the menu track looped, I got a repeat of the last 3 lines above in the terminal:

> > [0x10d4618] main input error: ES_OUT_RESET_PCR called
> [0x7f5244014678] libmpeg2 decoder error: DpbUnlinkPicture called on an invalid picture
> [0x7f5244014678] libmpeg2 decoder error: DpbUnlinkPicture called on an invalid picture

Fiddling with the vlc GUI, I noted I could browse the DVD's titles and chapters via mainmenu>Playback>Navigation, but every time

[LIST]
[*]the audio was correct
[*]there was no video
[/LIST]

How to debug? First I restarted the OS (`sudo shutdown -r now`), then I tried reading the disk: first with totem, then vlc. This time, both totem and vlc played audio, but as before, no video.

Next I investigated playing other video sources. I have some creative-commons video files which I have previously played on the winxp box, from which I took a sample of different filetypes:

> She_Done_Him_Wrong.avi 
StoryofStuff_NTSCcompressed.mov 
his_girl_friday.mpeg 
PhysicsFundamentals1_20101111_publect_wilczek_pt1.mp4 

(FWIW, "She Done Him Wrong" and "His Girl Friday" were downloaded from [archive.org]("http://archive.org"), "Story of Stuff" is from [http://storyofstuff.force.com/download]("http://storyofstuff.force.com/download"), and the Frank Wilczek lecture is from [here]("http://www.princeton.edu/WebMedia/media/lectures/20101111_publect_wilczek_pt1.mp4").) In vlc, all these files played audio, but none played video. In totem, I got audio (but not video) from

> StoryofStuff_NTSCcompressed.mov 
PhysicsFundamentals1_20101111_publect_wilczek_pt1.mp4 

and neither audio nor video from

> She_Done_Him_Wrong.avi 
his_girl_friday.mpeg 

At this point I was very confused. Firstly, I play video content in the browser (formerly firefox, now mostly chrome) on the PanP5 all the time. Secondly, again, I'm pretty sure I've played video files and discs before on this box. Thinking about the browser, I decided to try to open the content above in chrome, and noted:

[LIST]
[*]file:///home/me/video/PhysicsFundamentals1_20101111_publect_wilczek_pt1.mp4 played both the video and audio! Note also that chrome plays this apparently without launching an external application. However the following all appeared (based on chrome's UI) to launch totem:
[*]file:///home/me/video/his_girl_friday.mpeg played neither audio nor video
[*]file:///home/me/video/AnnieLeonard/StoryofStuff_NTSCcompressed.mov played audio only (and took a loooong time to start)
[*]file:///home/me/video/She_Done_Him_Wrong.avi similarly played only audio, and after a long time.
[/LIST]

For a sanity check, I browsed to [storyofstuff.com]("http://storyofstuff.com") and played the online/flash version of Story of Stuff with no problems: both audio and video.

So I suspect the problem is not hardware. How then do I make these files and media play both audio and video from a local application other than the browser?

TIA, Tom Roche [Tom_Roche@pobox.com]

---

### Post by isantop on 2010-12-08
Just to cover all of our tracks, please open a terminal and run the following commands:
```
sudo apt-get install ubuntu-restricted-extras
sudo /usr/share/doc/libdvdread4/install-css.sh
```
then try it again to see if that works.

---

### Post by tlroche on 2010-12-08
> **isantop said:**
> ```
sudo apt-get install ubuntu-restricted-extras
sudo /usr/share/doc/libdvdread4/install-css.sh
```
then try it again

> $ sudo aptitude update
...
> No packages will be installed, upgraded, or removed.
...
$ sudo aptitude install ubuntu-restricted-extras
...
> No packages will be installed, upgraded, or removed.
...
$ sudo /usr/share/doc/libdvdread4/install-css.sh
> --2010-12-08 18:33:47--  [http://packages.medibuntu.org/dists/lucid/free/binary-amd64/Packages](http://packages.medibuntu.org/dists/lucid/free/binary-amd64/Packages)
...
> 2010-12-08 18:33:53 (76.1 KB/s) - `/tmp/dvdcss-2SA3JK/Packages' saved [8080/8080]
> --2010-12-08 18:33:53--  [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb)
...
> 2010-12-08 18:33:54 (89.0 KB/s) - `/tmp/dvdcss-2SA3JK/libdvdcss.deb' saved [38080/38080]
...
> Preparing to replace libdvdcss2 1.2.10-0.3medibuntu1 (using .../dvdcss-2SA3JK/libdvdcss.deb) ...
# apparently the script does not check to see if it's already installed :-(
> Unpacking replacement libdvdcss2 ...
> Setting up libdvdcss2 (1.2.10-0.3medibuntu1) ...
> 
> Processing triggers for libc-bin ...
> ldconfig deferred processing now taking place

Following uses same sources as previous (see above in thread for filenames matching filetypes/media). Unless otherwise noted sources were opened like

[LIST]
[*]chrome: (in address field) file://<FQ path/>
[*]totem: (in terminal) $ totem <FQ path/> &
[*]VLC: (in terminal) $ vlc <FQ path/> &
[/LIST]

and "no output" == "neither audio nor video":

```

+--------+--------------------------------------------+---------------------------+------------------------+
|        |                                   current results with                                          |
| source | chrome                                     | totem                     | vlc                    |
|--------+--------------------------------------------+---------------------------+------------------------|
| avi    | opens totem, audio only                    | audio only                | audio only             |
|--------+--------------------------------------------+---------------------------+------------------------|
| dvd    | file:///media/cdrom0/VIDEO_TS/VIDEO_TS.VOB | Movie>Play Disc[...]      | Media>Open Disc...     |
|        | opens totem, no output, one play only      | menu loops, but no output | menu loops, audio only |
|--------+--------------------------------------------+---------------------------+------------------------|
| mov    | opens totem, audio only                    | audio only                | audio only             |
|--------+--------------------------------------------+---------------------------+------------------------|
| mpeg   | opens totem, no output                     | no output                 | audio only             |
|--------+--------------------------------------------+---------------------------+------------------------|
| mp4    | audio and video                            | audio only                | audio only             |
+--------+--------------------------------------------+---------------------------+------------------------+
```

Current results appear almost completely identical with previous results (single diff in all caps):

```

+--------+--------------------------------------------+---------------------------+------------------------+
|        |                                  previous results with                                          |
| source | chrome                                     | totem                     | vlc                    |
|--------+--------------------------------------------+---------------------------+------------------------|
| avi    | opens totem, audio only                    | NO OUTPUT                 | audio only             |
|--------+--------------------------------------------+---------------------------+------------------------|
| dvd    | file:///media/cdrom0/VIDEO_TS/VIDEO_TS.VOB | Movie>Play Disc[...]      | Media>Open Disc...     |
|        | opens totem, no output, one play only      | menu loops, but no output | menu loops, audio only |
|--------+--------------------------------------------+---------------------------+------------------------|
| mov    | opens totem, audio only                    | audio only                | audio only             |
|--------+--------------------------------------------+---------------------------+------------------------|
| mpeg   | opens totem, no output                     | no output                 | audio only             |
|--------+--------------------------------------------+---------------------------+------------------------|
| mp4    | audio and video                            | audio only                | audio only             |
+--------+--------------------------------------------+---------------------------+------------------------+
```

So I'm wondering:

[LIST=1]
[*]Why can only chrome play the mp4 correctly (i.e. with both audio and video)?
[*]How to configure a local app (e.g. totem, vlc, but another would probably do) to play all these sources correctly?
[/LIST]

TIA, Tom Roche [Tom_Roche@pobox.com]

---

### Post by tlroche on 2010-12-10
Last night I burned and booted the [Linux Mint 10 64-bit Live DVD]("http://www.linuxmint.com/edition.php?id=70"), then used its included VLC to play the video files above (though not my video DVD). All played correctly, both audio and video.

So this is definitely a software problem (unless I'm missing something). The question is, how to fix it?

TIA, Tom Roche [Tom_Roche@pobox.com]

---

### Post by tlroche on 2010-12-14
I'm not marking this solved, because the following is definitely a kludge, but my PanP5 running lucid (described above) can now play video with vlc, as long as I **don't** try to play with totem="Movie Player". What I mean:

I first ran the script from this post. The script updated (installing nothing--I was uptodate), then attempted to install several repositories and packages that were already installed, before installing one package=w64codecs. Afterward I restarted, then tested the following, where

[LIST=1]
[*]the media are those listed in item 18.2 of my checklist (with the DVD ISO burned to disk)
[*]all media run from terminal with > vlc <filename/> &, except for DVD, which was run by whatever means noted below
[/LIST]

Initial results were excellent

```
+--------+----------------------------------+
| source | vlc                              |
+--------+----------------------------------+
| DVD    | choose VLC from insertion dialog |
|        | goes to menu                     |
|        | audio and video                  |
+--------+----------------------------------+
| DivX   | audio and video                  |
+--------+----------------------------------+
| mov    | audio and video                  |
+--------+----------------------------------+
```

then, while searching terminal history, I accidentally did

> me@it:~$ totem ~/video/his_girl_friday.mpeg &

when I meant to

> me@it:~$ vlc ~/video/his_girl_friday.mpeg &

Interestingly

[LIST=1]
[*]totem played audio only
[*]all subsequent runs of VLC, including runs of the media above, played audio only!
[/LIST]

After too long experimenting, I established that, after a restart (of ubuntu),

[LIST=1]
[*]all runs of VLC **prior to** any run of totem played correctly (both audio and video)
[*]all runs of totem played audio only
[*]all runs of VLC **subsequent to** any run of totem played audio only!
[/LIST]

So I first made vlc the default media player, by

[LIST=1]
[*]determining its path: > me@it:~$ which vlc
> /usr/bin/vlc
[*]setting mainmenu>System>Preferences>Preferred Applications>Multimedia>Custom=/usr/bin/vlc
[*]installing the VLC Firefox plugin, package=mozilla-plugin-vlc
[/LIST]

I then uninstalled totem with

> me@it:~$ sudo aptitude purge totem
...
> The following packages are BROKEN:
>   totem-gstreamer totem-mozilla totem-plugins 
> The following packages will be REMOVED:
>   totem{p} 
> 0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
> Need to get 0B of archives. After unpacking 1,700kB will be freed.
> The following packages have unmet dependencies:
>   totem-plugins: Depends: totem (= 2.30.2-0ubuntu1) but it is not installable
>   totem-gstreamer: Depends: totem (>= 2.27.1) but it is not installable
>   totem-mozilla: Depends: totem (= 2.30.2-0ubuntu1) but it is not installable
> The following actions will resolve these dependencies:

> Remove the following packages:
> totem-gstreamer
> totem-mozilla
> totem-plugins

> Leave the following dependencies unresolved:
> ubuntu-desktop recommends totem
> ubuntu-desktop recommends totem-mozilla
> Score is -143

> Accept this solution? [Y/n/q/?] Y
> The following packages will be REMOVED:
totem{p}
totem-gstreamer{a}
totem-mozilla{a}
totem-plugins{a} 
> 0 packages upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
> Need to get 0B of archives. After unpacking 3,084kB will be freed.


and restarted ubuntu. I inserted the DVD, and got default option="Start VLC media player" and was able to play all media correctly:

```
+--------+----------------------------------+
| source | vlc                              |
+--------+----------------------------------+
| DVD    | choose VLC from insertion dialog |
|        | goes to menu, navigation correct |
|        | audio and video                  |
+--------+----------------------------------+
| DivX   | audio and video                  |
+--------+----------------------------------+
| mov    | audio and video                  |
+--------+----------------------------------+
| mpeg   | audio and video                  |
+--------+----------------------------------+
| mp4    | audio and video                  |
+--------+----------------------------------+

```

So for now I'm declaring victory, though I suspect I'll need to reinstall the OS to **really** fix this.

---

