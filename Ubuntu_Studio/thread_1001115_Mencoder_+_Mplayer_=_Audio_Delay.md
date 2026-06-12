---
title: "Mencoder + Mplayer = Audio Delay?"
date: 2008-12-03
forum: Ubuntu Studio
---

### Post by fatalGlory on 2008-12-03
I've been encoding dvds to x264 and mp3 with a command resembling this:

```
mencoder -dvd-device /media/cdrom0 -alang en -ovc x264 -oac mp3lame -x264encopts "bitrate=1000" -o "/path/to/movie.avi" dvd://1
```

When I play back the resulting avi file in totem, it plays fine.  However, when I play it back with mplayer, the audio is out and I have to set audio delay to -500ms with the numpad minus key.

Anyone have any idea why the audio would only play off-time in mplayer?

---

### Post by andrew.46 on 2008-12-03
Hi,

Is it possible to post your file somewhere? It would be interesting to have a look at it.

Have a look at:

[http://www.andrews-corner.org/matrix.html](http://www.andrews-corner.org/matrix.html)

which demonstrates 2 pass h264 encoding. This is a technique I have been using for some time (it is my page) and there is no problem with AV sync. This might help you out  little.

Are you using a current mplayer? This can be demonstrate as follows:

```
andrew@skamandros~$ mplayer | head -n 1
MPlayer dev-SVN-r28012-4.2.3 (C) 2000-2008 MPlayer Team
```

All the best,

  Andrew

---

### Post by fatalGlory on 2008-12-03
My version is just the one from the intrepid repos:
```
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
```

I've attached the avi file.  It's a whole dvd movie so I just started encoding and hit Ctrl-C after 4 secs (tell me if this means it is not in tact somehow).

I don't think it is anything to do with x264 and passes because I get the same result when encoding to xvid.  Having said that, I've never tried 2 pass x264 or xvid encoding (does xvid even support it?)  My guess is that the problem is with the avi container, but other media players handle it fine.

---

### Post by andrew.46 on 2008-12-03
Hi,

Unfortunately there was not enough to see the AV sync but I suspect there is probably a file size limit on these forums anyway. The MPlayer docs usually ask for file samples as follows:

```
dd if=*yourfile* of=*smallfile* bs=1024k count=5
```

but this would probably still be a little big ...

Have you thought of trying the svn MPlayer? There have been some improvements in decoding h264 videos since the old days of rc2 and this may help things a little. There is a guide on these forums for this:

[http://ubuntuforums.org/showthread.php?t=558538](http://ubuntuforums.org/showthread.php?t=558538)

Xvid has 2 and even 3 pass available. Simply specify a first pass with:

```
-ovc xvid -xvidencopts pass=1
```

and direct the output to /dev/null and then run:

```
-ovc xvid -xvidencopts pass=2
```

with output to your filename.

All the best,

  Andrew

---

### Post by fatalGlory on 2008-12-03
Thanks for the ideas.  I'll try some multi-pass encoding I guess.  It still puzzles me why other media players handle the video properly.

EDIT: Found a solution.  I first rip the dvd to the hard disk with:
```
mplayer -dvd-device /media/cdrom0 -dumpstream -dumpfile /path/to/uncompressed.VOB dvd://1
```

Then run something like this:
```
mencoder -oac mp3lame -ovc xvid -xvidencopts "bitrate=1024" -o /path/to/compressed.avi /path/to/uncompressed.VOB
```

This will also work with x264.  My new guess is that the av-delay issue I was having had something to do with reading data from the dvd drive while encoding.  Maybe DMA is not working properly?  But then shouldn't I notice skippy dvd playback?  Who knows.  The point being, doing a rip to the hard disk first, then encoding from there solves the issue.

---

