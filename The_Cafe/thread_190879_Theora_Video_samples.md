---
title: "Theora Video samples"
date: 2006-06-06
forum: The Cafe
---

### Post by disturbed1 on 2006-06-06
Not that thrilled with the example that comes with Ubuntu by default, so I created a couple of my own Ogg Theora samples.

These are from the trailer of Red Sonja, it's quite old, so the source video isn't what one would call pristine, but they look pretty good anyways ;)

They were created using the latest svn of ffmpeg2theora linked to svn libtheora 1.0alpha6. The 1.0alpha6 includes mmx instructions, so instead of 5fps with alpha5 I can achieve ~20fps.

The first one is ~19mb in size and has a peak bitrate ~1200kb/s. The second is ~7mb in size and has a peak bitrate of ~420kb/s. I don't recomend watching the second one full screen, maybe double sized at the most due to the low bit rate and resolution.

Tested playback with mplayer, gxine, totem (GStreamer) and VLC. I recomend VLC ;)



Command line for the first example
```

disturbed-linux:~$ ./theora -v 7 -a 1 --aspect 16:9 -x 576 -y 320 --inputfps 23.976 traler.mpg
```

The second
```

disturbed-linux:~$ ./theora -v 5 -a 0 --aspect 16:9 -x 352 -y 192 --inputfps 23.976 traler.mpg -o trailer_low.ogg
```


[Large sample](http://www.yousendit.com/transfer.php?action=download&ufid=F94E3BB35D2BAA82)

[Smaller sample](http://www.yousendit.com/transfer.php?action=download&ufid=F0B465427F6B500F)

---

