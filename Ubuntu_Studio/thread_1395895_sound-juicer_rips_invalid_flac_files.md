---
title: "sound-juicer rips invalid flac files"
date: 2010-02-01
forum: Ubuntu Studio
---

### Post by jis on 2010-02-01
I ripped a whole bunch of audio CDs using sound-juicer (2.26.1-0ubuntu1)
in ubuntu 9.04 and made Flac files by the same software. I found two problems:
– You can not move playback position of such files in alsaplayer (alsaplayer-gtk 0.99.80-3ubuntu1). However, playback position can be moved in e.g. VLC.
– Playback of some files stops in the middle of the track.

When I ripped by asunder (1.6.2-1) I did not have such problems.

I guess all my flac files are somehow broken. Is there a way to heal them painlessly?

---

### Post by jis on 2010-02-01
Bug report: [https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/515600](https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/515600)

---

### Post by jis on 2010-02-02
A way to heal the files is to re-encode them by flac, by which the original files are ok anyway.

---

