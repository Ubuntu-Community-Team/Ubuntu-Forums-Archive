---
title: "xubuntu 12.04 &amp; gmusicbrowser"
date: 2011-11-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by loukingjr on 2011-11-10
installed xfce 12.04 in VirtualBox 4.1.6 and thiings seem fine except gmusicbrowser closes immediately after launch.

this is what I get when launched in the terminal...
```
louis@louis-VirtualBox:~$ gmusicbrowser
print() on closed filehandle $fifofh at /usr/bin/gmusicbrowser line 286.
GStreamer::Interfaces perl module not found -> visuals not available
@Fields=album_shuffle replaygain_album_gain skipcount file grouping compilation replaygain_track_peak modif lastskip replaygain_reference_level genre embedded_pictures label title replaygain_album_peak album_artist samprate filetype bitrate missing added channel title_or_file size rating album_artist_raw lastplay shuffle playcount embedded_lyrics replaygain_track_gain extension version track path length artist album comment disc year barefilename fullfilename_raw ratingnumber artists first_artist album_picture album_years version_or_empty uri artist_picture missingkey fullfilename at /usr/bin/../share/gmusicbrowser/gmusicbrowser_songs.pm line 1066.
These commands were not found : flac123, ogg123
 => these file types won't be played by the 123 output : oga, flac
/org/mpris/MediaPlayer2 at /usr/bin/../share/gmusicbrowser/plugins/mpris2.pm line 30.
Use of uninitialized value $_[0] in vec at (eval 97) line 1.
Ignoring unknown column playandqueueandtrack
SongArray_changed replace,filter Filter=HASH(0x4270ac0)
Use of uninitialized value $_[0] in vec at (eval 97) line 1.
process 1699: Array or variant type requires that type boolean be written, but double was written.
The overall signature expected here was 'a{sb}' and we are on byte 4 of that signature.
process 1699: Array or variant type requires that type boolean be written, but string was written.
The overall signature expected here was 'a{sb}' and we are on byte 4 of that signature.
process 1699: Array or variant type requires that type boolean be written, but string was written.
The overall signature expected here was 'a{sb}' and we are on byte 4 of that signature.

```

---

### Post by loukingjr on 2011-12-22
not many responses yet... :shock:

---

### Post by cariboo on 2011-12-22
Have you created a bug report?

---

### Post by loukingjr on 2011-12-22
> **cariboo907 said:**
> Have you created a bug report?
not yet. I was waiting to see if anyone was aware of it or had a fix. I know there was one for 11.10 awhile ago.

---

### Post by Toz on 2011-12-23
See: [https://bugs.launchpad.net/ubuntu/+source/gmusicbrowser/+bug/880435]("https://bugs.launchpad.net/ubuntu/+source/gmusicbrowser/+bug/880435") for fix.

---

### Post by loukingjr on 2011-12-23
> **Toz said:**
> See: [https://bugs.launchpad.net/ubuntu/+source/gmusicbrowser/+bug/880435](https://bugs.launchpad.net/ubuntu/+source/gmusicbrowser/+bug/880435) for fix.
that's not the issue I am having but tried the fix anyway. didn't work :lolflag:

thanks though.

---

### Post by Toz on 2011-12-23
I had the same error messages that you had. The fix didn't work for me either the first time. I had to run:
```
gmusicbrowser -nodbus
```
...and
```
gmusicbrowser -plugin MPRIS2
```
first. Not sure why. Then suddenly it started working again.

---

### Post by loukingjr on 2011-12-23
that worked. danke :D

---

